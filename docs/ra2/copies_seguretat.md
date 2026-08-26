# 📦 Còpies de Seguretat i Plans de Recuperació (Backup & Disaster Recovery)

Les **còpies de seguretat** (*backups*) són la darrera línia de defensa en la seguretat informàtica. Permeten recuperar la informació i restablir els serveis davant de fallades de maquinari, atacs de programari maliciós (com el *ransomware*), errors humans o catàstrofes naturals.

---

## 📐 Principis Fonamentals i l'Estratègia 3-2-1

Per garantir que les dades siguin realment recuperables, s'aplica l'estratègia **3-2-1**:

* **3 Còpies de les dades:** La dada original en producció més dues còpies de seguretat addicionals.
* **2 Suports diferents:** Emmagatzemar les còpies en mitjans físics o tecnològics diferents (ex: disc dur intern, NAS, cinta magnètica, disc extern).
* **1 Còpia fora de la instal·lació (*Off-site*):** Salvar almenys una còpia en una ubicació física diferent o al núvol per protegir les dades en cas d'incendi o robatori.

---

## 📊 Tipus de Còpies de Seguretat

<Image src="image_agent_tag_1933538191940240804" alt="Diagrama comparatiu de tipus de còpia de seguretat: Completa, Incremental i Diferencial" caption="Comparativa del funcionament de les còpies de seguretat" />

---

### 1. Còpia Completa (*Full Backup*)
* **Funcionament:** Copia la totalitat de les dades seleccionades independentment de si s'han modificat o no.
* **Avantatges:** Restauració molt simple i ràpida (només es requereix un sol conjunt de dades).
* **Inconvenients:** Ocupa molt espai i requereix un temps d'execució elevat.

### 2. Còpia Incremental
* **Funcionament:** Copia **només les dades que han canviat des de l'última còpia de seguretat** (sigui aquesta completa o incremental).
* **Avantatges:** Molt ràpida de realitzar i ocupa molt poc espai de disc.
* **Inconvenients:** La restauració és lenta i complexa, ja que requereix la còpia completa inicial i **totes** les còpies incrementals posteriors en ordre.

### 3. Còpia Diferencial
* **Funcionament:** Copia **totes les dades que han canviat des de l'última còpia completa**.
* **Avantatges:** Restauració més ràpida que l'incremental (només es requereix la còpia completa i l'última diferencial).
* **Inconvenients:** Ocupa més espai i triga més a fer-se a mesura que passa el temps respecte a l'última completa.

---

## 📋 Taula Comparativa dels Tipus de Còpia

| Característica | Completa (*Full*) | Incremental | Diferencial |
| :--- | :---: | :---: | :---: |
| **Temps d'execució** | Molt lent | **Molt ràpid** | Mitjà |
| **Espai ocupat** | Molt alt | **Molt baix** | Mitjà |
| **Complexitat de restauració** | **Molt senzilla** (1 pas) | Complexa (N passos) | Senzilla (2 passos) |
| **Risc en cas de fallada d'un fitxer** | Baix | **Alt** (si falla 1 incremental, es trenca la cadena) | Baix |

---

## 🐧 Còpies de Seguretat a Linux

### 1. Sincronització eficient amb `rsync`
L'eina **`rsync`** és el standard a Linux per realitzar còpies de seguretat gràcies a la seva capacitat de transferir només les diferències entre fitxers.

```bash
# Còpia incremental/sincronització mirenllant permisos i enllaços
sudo rsync -avz --delete /var/www/html/ /mnt/backup/www/

# Explicació d'opcions:
# -a (archive): Preserva permisos, propietaris, dates i enllaços.
# -v (verbose): Mostra el detall dels fitxers processats.
# -z (compress): Comprimeix les dades durant la transferència.
# --delete: Esborra al destinatari els fitxers eliminats a l'origen.

```

### 2. Empaquetat i compressió amb `tar`

Per generar fitxers d'arxiu puntuals comprimits:

```bash
# Crear un arxiu tar.gz del directori de configuració /etc
sudo tar -cvzf /mnt/backup/etc_backup_$(date +%Y%m%d).tar.gz /etc

# Extreure la còpia de seguretat en un directori de destinació
sudo tar -xvzf /mnt/backup/etc_backup_20260826.tar.gz -C /tmp/restauracio/

```

### 3. Automatització amb `cron`

Per executar les còpies de seguretat periòdicament:

```bash
# Editar la taula de tasques cron de l'usuari root
sudo crontab -e

# Afegir la següent línia per executar el backup cada dia a les 02:00 AM:
0 2 * * * rsync -avz /home/usuari/documents/ /mnt/backup/documents/

```

---

## 🪟 Còpies de Seguretat a Windows

### 1. Sincronització de fitxers amb `robocopy`

**Robocopy** (*Robust File Copy*) és l'eina integrada en línia de comandes de Windows per a la gestió professional de backups.

```cmd
REM Copiar la carpeta de Projectes a una unitat externa mantenint permisos NTFS
robocopy C:\Dades\Projectes E:\Backup\Projectes /MIR /COPYALL /R:3 /W:5 /LOG:C:\Logs\backup.log

REM Explicació d'opcions:
REM /MIR : Mode mirall (sincronitza canvis i esborra el que s'hagi eliminat a l'origen).
REM /COPYALL : Copia tota la informació del fitxer (dades, atributs, permisos NTFS, AUDIT).
REM /R:3 : Reintenta 3 vegades si un fitxer està bloquejat.
REM /W:5 : Espera 5 segons entre reintentos.

```

### 2. Imatges de sistema amb `wbadmin`

A entorns Windows Server i Windows 10/11, es pot utilitzar **`wbadmin`** per realitzar còpies de seguretat completes de l'estat del sistema (*Bare Metal Recovery*).

```cmd
REM Iniciar una còpia de seguretat de la unitat C: cap a la unitat E:
wbadmin start backup -backupTarget:E: -include:C: -quiet

```

### 3. Instantànies de Volum (**VSS** / *Shadow Copies*)

El servei **VSS** (*Volume Shadow Copy Service*) de Windows permet fer còpies de seguretat de fitxers fins i tot quan estan oberts o en ús per aplicacions (ex: bases de dades o arxius d'Outlook). També permet a l'usuari restaurar versions anteriors des de l'explorador de fitxers.

---

## 🧪 Pràctica Guiada per a l'Alumnat

```bash
# ==========================================
# PRÀCTICA A LINUX (Script de Backup Incremental amb rsync i cron)
# ==========================================

# 1. Crear el directori per als scripts de backup
mkdir -p ~/scripts

# 2. Crear un script executable anomenat backup.sh
cat << 'EOF' > ~/scripts/backup.sh
#!/bin/bash
ORIGEN="/home/usuari/dades/"
DESTI="/mnt/backup_disc/"
LOG="/var/log/backup_daily.log"

echo "--- Inici de backup: $(date) ---" >> $LOG
rsync -avz --delete $ORIGEN $DESTI >>$LOG 2>&1
echo "--- Fi de backup: $(date) ---" >> $LOG
EOF

# 3. Donar permisos d'execució a l'script
chmod +x ~/scripts/backup.sh

```

```powershell
# ==========================================
# PRÀCTICA A WINDOWS (Script automatitzat amb PowerShell)
# ==========================================

# 1. Crear un script en PowerShell per copiar directori amb la data d'avui
$Data = Get-Date -Format "yyyy-MM-dd"
$Origen = "C:\Dades"
$Desti = "D:\Backups\Backup_$Data"

# 2. Executar la còpia amb Robocopy des de PowerShell
Robocopy.exe $Origen $Desti /E /NP /LOG:"D:\Backups\log_$Data.txt"

```

---

## ✅ Checklist de Comprovació

* [ ] Comprensió i aplicació de la regla de backup **3-2-1**
* [ ] Diferenciació clara entre còpia Completa, Incremental i Diferencial
* [ ] Domini de les eines `rsync` i `tar` a Linux per a la gestió de còpies
* [ ] Domini de les eines `robocopy` i `wbadmin` a Windows
* [ ] Ús i programació de tasques automàtiques amb `cron` (Linux) i el Programador de Tasques (Windows)

```
