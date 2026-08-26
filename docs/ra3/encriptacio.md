# 🔐 Encriptació de Dades i Disc (Linux i Windows)

L'**encriptació** (o xifratge) és la tècnica principal per protegir la confidencialitat de la informació. Assegura que, en cas de robatori de discs, dispositius USB o intercepció de dades en xarxa, ningú pugui accedir al contingut sense la clau corresponent.

---

## 📚 Tipus de Xifratge

* **Xifratge en repòs (*Data at Rest*):** Protecció de dades emmagatzemades en discs durs, SSDs o unitats USB (ex. BitLocker, LUKS, EFS).
* **Xifratge en diàleg / tràsit (*Data in Transit*):** Protecció de dades mentre viatgen per la xarxa (ex. TLS/SSL, IPsec, SSH).
* **Xifratge simètric vs asimètric:**
  * **Simètric:** Utilitza la mateixa clau per xifrar i desxifrar (ràpid, ideal per a discs; ex. AES-256).
  * **Asimètric:** Utilitza un parell de claus (pública/privada; ex. RSA, ECC).

---

## 🐧 Encriptació a Linux

En entorns Linux, l'estàndard per al xifratge de discs i particions és **LUKS** (*Linux Unified Key Setup*), gestionat mitjançant l'eina **`cryptsetup`**.

### 1. Xifratge de Particions amb LUKS (`cryptsetup`)

#### A. Preparar i formatar la partició xifrada
```bash
# 1. Formatar la partició amb el format LUKS (demanarà contrasenya)
sudo cryptsetup luksFormat /dev/sdb1

# 2. Obrir la partició xifrada i assignar-li un nom virtual (ex: disc_protegit)
sudo cryptsetup open /dev/sdb1 disc_protegit

# 3. Crear el sistema de fitxers sobre el dispositiu creat a /dev/mapper/
sudo mkfs.ext4 /dev/mapper/disc_protegit

```

#### B. Muntar i utilitzar el disc xifrat

```bash
# 1. Crear el punt de muntatge i muntar la unitat
sudo mkdir -p /mnt/dades_segures
sudo mount /dev/mapper/disc_protegit /mnt/dades_segures

# 2. Treballar de forma segura dins la carpeta...

```

#### C. Desmuntar i tancar la unitat

```bash
# 1. Desmuntar la carpeta
sudo umount /mnt/dades_segures

# 2. Tancar el volum LUKS per protegir-lo de nou
sudo cryptsetup close disc_protegit

```

### 2. Xifratge de Directoris de Fitxers (`fscrypt` / `eCryptfs`)

Si no es vol xifrar una partició sencera, es poden xifrar carpetes individuals de l'usuari amb utilitats com `fscrypt` o `ecryptfs-utils`.

---

## 🪟 Encriptació a Windows

Windows ofereix dues tecnologies principals de xifratge segons el nivell d'aplicació: **BitLocker** (per a volums sencers) i **EFS** (per a fitxers i carpetes individuals).

### 1. Xifrat de Disc Complet amb BitLocker

BitLocker xifra volums de disc complets utilitzant l'algorisme AES. Es pot integrar amb el xip **TPM** (*Trusted Platform Module*) de la placa base per validar la integritat del sistema durant l'arrencada.

#### A. Configuració des de la Interfície Gràfica

1. Obrir el **Tauler de Control** > **Xifratge de disc BitLocker** (o botó dret sobre la unitat a l'Explorador).
2. Seleccionar **Activar BitLocker**.
3. Triar el mètode de desbloqueig (Contrasenya, Clau USB o integració TPM).
4. Guardar la **Clau de Recuperació** (en un fitxer, compte de Microsoft o Active Directory).

#### B. Gestió de BitLocker per Comandes (`manage-bde` i PowerShell)

```powershell
# 1. Comprovar l'estat del xifratge de les unitats
manage-bde -status

# 2. Activar BitLocker a la unitat C: i guardar la clau a Active Directory
Enable-BitLocker -MountPoint "C:" -EncryptionMethod Aes256 -UsedSpaceOnly -ProtectorType Tpm

# 3. Desbloquejar una unitat externa (USB) des de PowerShell
Unlock-BitLocker -MountPoint "E:" -Password (Read-Host -AsSecureString "Introdueix la contrasenya")

```

### 2. Encrypting File System (EFS)

EFS permet xifrar fitxers i carpetes individuals sobre sistemes de fitxers **NTFS**. Les dades es xifren de manera transparent per a l'usuari que té el certificat de xifratge associat.

* **Ús des de la interfície:**
1. Fes botó dret sobre el fitxer/carpeta > **Propietats** > **Avançats...**
2. Marcar la casella **Xifrar el contingut per protegir les dades**.


* **Ús des de la línia de comandes (`cipher`):**
```cmd
REM Xifrar un directori concret
cipher /e C:\Ruta\CarpetaSecretes

REM Comprovar l'estat de xifratge dels fitxers
cipher /c C:\Ruta\CarpetaSecretes\*

```



---

## 📊 Taula Comparativa: Linux vs Windows

| Característica | Linux 🐧 | Windows 🪟 |
| --- | --- | --- |
| **Xifrat de Volum / Disc** | **LUKS** (`cryptsetup`) | **BitLocker** |
| **Xifrat de Fitxers / Carpetes** | `fscrypt` / `eCryptfs` | **EFS** (*Encrypting File System*) |
| **Algorisme per defecte** | AES-256 (XTS-PLAIN64) | AES-128 / AES-256 |
| **Suport de Maquinari** | TPM 2.0 (`tpm2-tools`) | Xip TPM integrat |
| **Gestió Centralitzada** | Scripting / Ansible | Directives de Grup (GPO) / Intune |

---

## 🧪 Pràctica Guiada per a l'Alumnat

```bash
# PRÀCTICA A LINUX (Creació d'un volum xifrat en un fitxer imatge)

# 1. Crear un fitxer buit de 100MB per simular un disc
dd if=/dev/zero of=~/disc_virtual.img bs=1M count=100

# 2. Assignar el fitxer com a dispositiu loop
sudo losetup -fP ~/disc_virtual.img
# Suposem que se li assigna /dev/loop0

# 3. Formatar i obrir amb LUKS
sudo cryptsetup luksFormat /dev/loop0
sudo cryptsetup open /dev/loop0 el_meu_volum

# 4. Crear sistema de fitxers i muntar
sudo mkfs.ext4 /dev/mapper/el_meu_volum
sudo mkdir /mnt/volum_xifrat
sudo mount /dev/mapper/el_meu_volum /mnt/volum_xifrat

```

---

## ✅ Checklist de Comprovació

* [ ] Entesa la diferència entre xifratge de disc complet i xifratge de fitxers
* [ ] Domini del procés `luksFormat`, `open` i `close` amb `cryptsetup`
* [ ] Comprensió del paper del xip TPM en el xifratge amb BitLocker
* [ ] Capacitat per gestionar BitLocker mitjançant la consola `manage-bde`
* [ ] Domini del xifratge EFS i la comanda `cipher` en Windows

```

```
