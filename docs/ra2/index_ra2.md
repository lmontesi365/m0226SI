
# 💾 RA2 - Disponibilitat, Integritat i Recuperació de la Informació

El **RA2** tracta les tècniques i tecnologies encarregades de garantir la **disponibilitat** i la **integritat** de les dades davant de fallades de maquinari, errors humans o atacs informàtics. S'analitza l'emmagatzematge redundant (**RAID**), la gestió de **còpies de seguretat** en entorns Linux i Windows, i els fonaments de la **criptografia** per protegir la informació.

---

## 📚 Eixos Temàtics del RA2


```

```
                   ┌─────────────────────────────────────────┐
                   │          DISPONIBILITAT I DADES         │
                   └────────────────────┬────────────────────┘
                                        │
     ┌──────────────────────────────────┼──────────────────────────────────┐
     ▼                                  ▼                                  ▼

```

┌──────────────────┐               ┌──────────────────┐               ┌──────────────────┐
│   Sistemes RAID  │               │Còpies de Seguretat│              │   Criptografia   │
│ (Tolerància a    │               │(Recuperació davant│              │(Confidencialitat │
│   fallades)      │               │  desastres/DRP)  │               │   e Integritat)  │
└──────────────────┘               └──────────────────┘               └──────────────────┘

```

---

## 💽 1. Sistemes RAID (Redundant Array of Independent Disks)

Els sistemes RAID combinen múltiples discs físics en una única unitat lògica per millorar el rendiment, la capacitat o la **tolerància a fallades**.

### Nivells de RAID Principals
* **RAID 0 (Striping):** Distribueix les dades entre discs. Millora el rendiment però **no té tolerància a fallades** (si falla 1 disc, es perden totes les dades).
* **RAID 1 (Mirroring):** Duplica les dades en mirall. Ofereix alta disponibilitat (tolera la fallada de la meitat dels discs).
* **RAID 5 (Paritat distribuïda):** Distribueix les dades i la paritat. Requereix com a mínim 3 discs i tolera la fallada d'1 disc.
* **RAID 6 (Doble paritat):** Semblant al RAID 5, però tolera la fallada simultània de fins a 2 discs (requereix mínim 4 discs).
* **RAID 10 / 01 (Nivells combinats):** Combina el rendiment del RAID 0 amb la redundància del RAID 1.

### Gestió de RAID a Linux i Windows
* **Linux:** Es gestiona per programari mitjançant l'eina **`mdadm`** o la gestió de volums lògics (**LVM**).
* **Windows:** Es gestiona des del **Administrador de discs** (`diskmgmt.msc`) o PowerShell utilitzant **Espais d'Emmagatzematge** (*Storage Spaces*).

---

## 📦 2. Còpies de Seguretat (Backup & Disaster Recovery)

Les còpies de seguretat asseguren la recuperació de les dades en cas de pèrdua total o destrucció del sistema.

### Tipus de Còpies de Seguretat
1. **Completa (*Full*):** Copia totes les dades. Triga més i ocupa més espai, però la restauració és directa.
2. **Incremental:** Copia només les dades modificades des de l'última còpia (sigui completa o incremental). Ràpida de realitzar, però la restauració requereix la còpia completa i totes les incrementals posteriors.
3. **Diferencial:** Copia les dades modificades des de l'última còpia completa. Ocupa un punt mig en velocitat i mida.

### Estratègia 3-2-1
* **3** còpies de les dades (la principal i 2 còpies de seguretat).
* **2** suports d'emmagatzematge diferents (ex: disc dur intern i unitat NAS/cinta).
* **1** còpia fora de l'oficina o al núvol (*Off-site*).

### Eines de Backup segons el Sistema Operatiu

| Funció | Linux 🐧 | Windows 🪟 |
| :--- | :--- | :--- |
| **Línia de comandes / Scripting** | `rsync`, `tar`, `dd` | `robocopy`, `wbadmin` |
| **Eines Avançades / Programades** | `BorgBackup`, `Bacula`, `Restic` | Windows Server Backup, Veeam Agent |
| **Còpies de la Imatge del Sistema** | `dd`, `Clonezilla` | Imatge del sistema Windows (`wbadmin start backup`) |
| **Punts de Restauració / Instantànies** | LVM Snapshots, ZFS/Btrfs Snapshots | Instantànies de volum (**VSS** / *Shadow Copies*) |

---

## 🔑 3. Criptografia i Integritat de les Dades

La criptografia permet mantenir la **confidencialitat** de la informació i verificar-ne la **integritat** per detectar manipulacions.

### Principals Mecanismes
* **Funcions Hash (Resum de Hash):** Algorismes d'una sola via (SHA-256, MD5) per generar una signatura única d'un fitxer. Si el fitxer es modifica, el hash canvia completament.
* **Xifratge Simètric:** Utilitza la mateixa clau per xifrar i desxifrar (ex: AES-256). Utilitzat per xifrar volums i fitxers grans.
* **Xifratge Asimètric:** Utilitza un parell de claus (Pública i Privada; ex: RSA, ECC). Base de les signatures digitals i el protocol HTTPS.

---

## 🛠️ Pràctiques Guiades per a l'Alumnat

```bash
# ==========================================
# PRÀCTICA A LINUX (Backup incremental i Hash)
# ==========================================

# 1. Crear un backup d'un directori amb rsync mantenint permisos
rsync -avz --delete /home/usuari/documents/ /mnt/backup/documents/

# 2. Generar el checksum SHA-256 d'un fitxer per verificar la seva integritat
sha256sum /mnt/backup/documents/informe.pdf > informe.pdf.sha256

# 3. Comprovar la integritat del fitxer
sha256sum -c informe.pdf.sha256

```

```cmd
REM ==========================================
REM PRÀCTICA A WINDOWS (Robocopy i Hash)
REM ==========================================

REM 1. Sincronitzar dues carpetes amb Robocopy (Mode de còpia mirall / MIR)
robocopy C:\Dades\Projectes D:\Backup\Projectes /MIR /R:3 /W:5

REM 2. Calcular el hash SHA256 d'un fitxer amb CertUtil a Windows
certutil -hashfile D:\Backup\Projectes\informe.docx SHA256

```

---

## ✅ Checklist de Comprovació del RA2

* [ ] Diferenciació clara entre els nivells de RAID (0, 1, 5, 6, 10) i els seus requeriments de discs
* [ ] Comprensió del funcionament de les còpies Completes, Incrementals i Diferencials
* [ ] Domini de la regla de backup **3-2-1**
* [ ] Ús de les eines `rsync` (Linux) i `robocopy` / `wbadmin` (Windows)
* [ ] Capacitat per calcular i verificar hashes (`sha256sum` / `certutil`) per comprovar la integritat

```

<ElicitationsGroup message="Vols que redactem algun dels fitxers específics d'aquesta unitat en profunditat?">
  <Elicitation label="Desenvolupar el fitxer de Sistemes RAID" query="Redacta el contingut extens del fitxer raid.md per al RA2 adaptat a Linux i Windows."/>
  <Elicitation label="Desenvolupar el fitxer de Còpies de Seguretat" query="Redacta el contingut extens del fitxer copies_seguretat.md per al RA2 adaptat a Linux i Windows."/>
</ElicitationsGroup>

```
