# 💽 Sistemes RAID (Redundant Array of Independent Disks)

Un sistema **RAID** combina diversos discs durs o unitats SSD físiques en una única unitat lògica. Els seus objectius principals són augmentar la **tolerància a fallades** (disponibilitat) i/o millorar el **rendiment** d'escriptura i lectura de les dades.

---

## 📚 Tipus d'Implementació de RAID

* **RAID per Maquinari (*Hardware RAID*):** Gestionat per una targeta controladora dedicada (*RAID Controller*) amb el seu propi processador i memòria cau. És independent del sistema operatiu i ofereix el màxim rendiment.
* **RAID per Programari (*Software RAID*):** Gestionat directament pel sistema operatiu. No requereix maquinari addicional, utilitza recursos del processador del sistema i és molt flexible.

---

## 📐 Nivells de RAID Principals

### 1. RAID 0 (Striping / Seccionament)
* **Descripció:** Distribueix els blocs de dades entre tots els discs de la matriu.
* **Discs mínims:** 2.
* **Tolerància a fallades:** **Nul·la (0)**. Si falla un sol disc, es perden totes les dades.
* **Capacitat útil:** $N \times \text{Mida del disc més petit}$.
* **Ús:** Entorns on només importa el rendiment extrem i les dades són temporals.

### 2. RAID 1 (Mirroring / Mirall)
* **Descripció:** Duplica exactament la mateixa informació en tots els discs de la matriu.
* **Discs mínims:** 2.
* **Tolerància a fallades:** Alta. Suporta la fallada de la meitat dels discs (mentre en quedi 1 d'actiu per parell).
* **Capacitat útil:** $1 \times \text{Mida del disc més petit}$.
* **Ús:** Sistemes operatius, servidors de bases de dades i fitxers crítics.

### 3. RAID 5 (Paritat Distribuïda)
* **Descripció:** Distribueix les dades i un bloc de paritat calculat entre tots els discs. Permet reconstruir les dades en cas que falli un disc.
* **Discs mínims:** 3.
* **Tolerància a fallades:** 1 disc.
* **Capacitat útil:** $(N - 1) \times \text{Mida del disc}$.
* **Ús:** Servidors d'arxius corporatius i servidors d'aplicacions generals.

### 4. RAID 6 (Doble Paritat Distribuïda)
* **Descripció:** Similar al RAID 5, però utilitza dos blocs de paritat diferents distribuïts.
* **Discs mínims:** 4.
* **Tolerància a fallades:** 2 discs simultanis.
* **Capacitat útil:** $(N - 2) \times \text{Mida del disc}$.
* **Ús:** Emmagatzematge massiu de gran capacitat on els temps de reconstrucció són llargs.

### 5. RAID 10 (RAID 1+0 / Mirall de Seccions)
* **Descripció:** Combina la velocitat del RAID 0 amb la redundància del RAID 1.
* **Discs mínims:** 4 (en nombres parells).
* **Tolerància a fallades:** Fins a 1 disc per cada parell en mirall.
* **Capacitat útil:** $50\%$ de la capacitat total dels discs.
* **Ús:** Servidors de bases de dades d'alt rendiment i entorns de virtualització crítics.

---

## 📊 Taula Comparativa de Nivells RAID

| Nivell RAID | Discs Mínims | Tolerància a Fallades | Capacitat Aprofitada | Velocitat Lectura | Velocitat Escriptura |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **RAID 0** | 2 | 0 discs | $100\%$ | Molt alta | Molt alta |
| **RAID 1** | 2 | 1 disc | $50\%$ | Alta | Normal |
| **RAID 5** | 3 | 1 disc | $\frac{N-1}{N}$ | Alta | Mitjana (càlcul paritat) |
| **RAID 6** | 4 | 2 discs | $\frac{N-2}{N}$ | Alta | Baixa (doble paritat) |
| **RAID 10** | 4 | 1 per parell | $50\%$ | Molt alta | Alta |

---

## 🐧 Gestió de RAID a Linux (`mdadm`)

A Linux, el mòdul del nucli `md` (*Multiple Devices*) permet crear i administrar RAID per programari mitjançant la comanda **`mdadm`**.

### 1. Creació d'un RAID 5 amb 3 discs

```bash
# 1. Crear la matriu RAID 5 utilitzant /dev/sdb, /dev/sdc i /dev/sdd
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

# 2. Comprovar l'estat de la creació/sincronització del RAID
cat /proc/mdstat
sudo mdadm --detail /dev/md0

# 3. Crear el sistema de fitxers sobre el dispositiu RAID creat
sudo mkfs.ext4 /dev/md0

# 4. Guardar la configuració del RAID per al reinici del sistema
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
sudo update-initramfs -u

```

### 2. Simulació de fallada i substitució d'un disc

```bash
# 1. Marcar un disc com a defectuós (fictíciament)
sudo mdadm /dev/md0 --fail /dev/sdb

# 2. Eliminar el disc fallit del RAID
sudo mdadm /dev/md0 --remove /dev/sdb

# 3. Afegir un nou disc de recanvi (Hot Spare) per iniciar la reconstrucció
sudo mdadm /dev/md0 --add /dev/sde

```

---

## 🪟 Gestió de RAID a Windows

A Windows, es poden crear volums RAID per programari des del **Administrador de discs** o utilitzant la tecnologia d'**Espais d'Emmagatzematge** (*Storage Spaces*).

### 1. Administrador de Discs (`diskmgmt.msc`)

* **Volum distribuït (*Striped*):** Equivalent a RAID 0.
* **Volum en mirall (*Mirrored*):** Equivalent a RAID 1.
* **Volum RAID-5:** Disponible en edicions de Windows Server.

### 2. Gestió d'Espais d'Emmagatzematge amb PowerShell

```powershell
# 1. Obtenir els discs físics disponibles per afegir al fons (Pool)
Get-PhysicalDisk -CanPool $True

# 2. Crear un fons d'emmagatzematge (Storage Pool) amb els discs trobats
New-StoragePool -FriendlyName "PoolDades" -StorageSubsystemFriendlyName "*Storage Spaces*" -PhysicalDisks (Get-PhysicalDisk -CanPool $True)

# 3. Crear un disc virtual amb redundància de Paritat (Equivalent a RAID 5)
New-VirtualDisk -StoragePoolFriendlyName "PoolDades" -FriendlyName "VolumParitat" -ResiliencySettingName Parity -Size 500GB

# 4. Inicialitzar i formatar el nou disc virtual
Get-VirtualDisk -FriendlyName "VolumParitat" | Get-Disk | Initialize-Disk -PartitionStyle GPT -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "DadesRAID"

```

---

## 🧪 Pràctica Guiada per a l'Alumnat

```bash
# PRÀCTICA A LINUX: Creació d'un RAID 1 amb dispositius de bucle (Loop devices)

# 1. Crear dos fitxers de 100MB per simular dos discs físics
dd if=/dev/zero of=~/disc1.img bs=1M count=100
dd if=/dev/zero of=~/disc2.img bs=1M count=100

# 2. Assignar els fitxers a dispositius de bucle (loop)
sudo losetup -fP ~/disc1.img
sudo losetup -fP ~/disc2.img
# Suposem que se'ls assigna /dev/loop0 i /dev/loop1

# 3. Crear el RAID 1 amb els dispositius creats
sudo mdadm --create /dev/md10 --level=1 --raid-devices=2 /dev/loop0 /dev/loop1

# 4. Verificar l'estat del RAID
sudo mdadm --detail /dev/md10

```

---

## ✅ Checklist de Comprovació

* [ ] Comprensió de les diferències entre Hardware RAID i Software RAID
* [ ] Conneixement de les característiques, discs mínims i tolerància de RAID 0, 1, 5, 6 i 10
* [ ] Capacitat per calcular la capacitat útil d'una matriu RAID
* [ ] Configuració i administració de RAID a Linux amb `mdadm`
* [ ] Creació d'espais d'emmagatzematge redundants a Windows via PowerShell o GUI

```
