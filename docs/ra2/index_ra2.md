
# 💾 RA2 - Disponibilitat, Integritat i Recuperació de la Informació

El **RA2** tracta les tècniques i tecnologies encarregades de garantir la **disponibilitat** i la **integritat** de les dades davant de fallades de maquinari, errors humans o atacs informàtics. S'analitza l'emmagatzematge redundant (**RAID**), la gestió de **còpies de seguretat** en entorns Linux i Windows, i els fonaments de la **criptografia** per protegir la informació.

---

## 📌 Índex de Continguts del RA2

Fes clic a qualsevol dels apartats per accedir a la documentació extensa i les guies pràctiques:

### 💽 1. [Sistemes RAID i Emmagatzematge Redundant](raid.md)
* **Descripció:** Configuració de matrius de discs per augmentar el rendiment i la tolerància a fallades de maquinari.
* **Guia d'estudi:** Repassa els nivells principals (RAID 0, 1, 5, 6, 10), el càlcul de capacitat útil i les eines de gestió per programari com **`mdadm`** a Linux i els **Espais d'Emmagatzematge** (*Storage Spaces*) / `diskmgmt.msc` a Windows.

### 📦 2. [Còpies de Seguretat i Plans de Recuperació](copies_seguretat.md)
* **Descripció:** Estratègies i eines per dur a terme la salvaguarda de les dades i la seva restauració.
* **Guia d'estudi:** Enfoca't en la regla **3-2-1**, la diferència entre còpies completes, incrementals i diferencials, així com l'ús d'eines pràctiques com **`rsync`** / **`tar`** a Linux i **`robocopy`** / **`wbadmin`** a Windows.

### 🔑 3. [Criptografia i Integritat de Dades](criptografia.md)
* **Descripció:** Mecanismes per garantir la confidencialitat de la informació i verificar que no ha estat alterada.
* **Guia d'estudi:** Estudia les funcions hash (SHA-256, MD5) per comprovar la integritat de fitxers, la diferència entre xifratge simètric (AES) i asimètric (RSA) i la generació de signatures digitals.
* **Funcions Hash:** MD5, SHA-1, SHA-256 i comprovació d'integritat en Linux i Windows.
* **Tipus de Xifratge:**
  * **Simètric:** AES-256, velocitat i xifratge en disc.
  * **Asimètric:** RSA, ECC, claus públiques i privades.
* **Certificats Digitals i PKI:** Funcionament de les Autoritats de Certificació (CA), X.509 i TLS/HTTPS.
* **Xifratge en Repòs:** Protecció de discs amb BitLocker i LUKS.

---

## 🛠️ Activitats i Laboratoris Pràctics

1. **Verificació d'integritat:** Comprovar la suma HASH de fitxers descarregats amb `sha256sum` i `Get-FileHash`.
2. **Xifratge simètric i asimètric:** Executar el laboratori pràctic d'OpenSSL i GPG.
3. ### 3. [Pràctica Pas a Pas: OpenSSL i GnuPG](./GPG.md#-pràctica-pas-a-pas-openssl-i-gnupg-gpg)
Guia d'ordres pràctiques per a la línia de comandes:
* **OpenSSL:** Xifratge simètric amb `AES-256`, generació de claus `RSA` de 4096 bits i xifratge asimètric.
* **GnuPG (GPG):** Creació de claus OpenPGP, exportació/importació de claus públiques, xifratge de documents i signatura digital amb fitxers de verificació `.sig`.
* **Taula comparativa:** Resum ràpid de sintaxi entre OpenSSL i GnuPG.
4. **Còpies de seguretat i DRP:** Implementació de plans de recuperació davant desastres (RTO / RPO).

---

## 🔗 Recursos Addicionals
* [Documentació Oficial d'OpenSSL](https://www.openssl.org/docs/)
* [Manual d'usuari de GnuPG (GPG)](https://gnupg.org/documentation/)

---

## 📊 Taula Resum dels Apartats del RA2

| Apartat | Àmbit principal | Concepte clau | Documentació |
| :--- | :--- | :--- | :---: |
| **Sistemes RAID** | Maquinari / Disc | Tolerància a fallades i nivells RAID (0, 1, 5, 6, 10) | [Anar ➡️](raid.md) |
| **Còpies de Seguretat** | Sistemes / Dades | Estratègia 3-2-1, `rsync` i `robocopy` | [Anar ➡️](copies_seguretat.md) |
| **Criptografia** | Seguretat de Dades | Hashing (`sha256sum`/`certutil`) i xifratge simètric/asimètric | [Anar ➡️](criptografia.md) |

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
