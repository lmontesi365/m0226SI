# 🛡️ RA3 - Seguretat Activa

Aquest bloc cobreix les tècniques, eines i configuracions necessàries per prevenir, detectar i mitigar amenaces als sistemes operatius **Windows** i **Linux**.

---

## 📂 Fitxers i Continguts del RA3

### 1. 🔐 Llistes de Control d'Accés (ACL)
* **Linux:** Gestió de permisos avançats POSIX amb `getfacl` i `setfacl` (assignació a usuaris/grups específics i permisos per defecte `-d`).
* **Windows:** Configuració de permisos NTFS (Lectura, Modificació, Control Total) i herència de permisos des de la pestanya de seguretat o mitjançant la consola amb `icacls`.

### 2. 🦠 Antimalware i Protecció
* **Linux:** Instal·lació i ús d'eines d'escaneig com **ClamAV** (`clamscan`), eines de detecció de *rootkits* (**rkhunter**, **chkrootkit**) i integració de signatures.
* **Windows:** Configuració de **Microsoft Defender Antivirus**, programació d'escanejos, protecció en temps real, aïllament en quarantena i regles de reducció de la superfície d'atac (ASR).

### 3. 🔑 Autenticació i Control d'Accés
* **Linux:** Configuració de mòduls d'autenticació plugables (**PAM** - `/etc/pam.d/`), autenticació per claus SSH (parell clau pública/privada) i restricció d'accés a `root`.
* **Windows:** Autenticació local i en domini (**Active Directory**), protocols Kerberos i NTLM, i implementació d'autenticació multifactoret (**MFA**).

### 4. 🔒 Polítiques de Contrasenyes
* **Linux:** Configuració de complexitat, caducitat i historial de claus als fitxers `/etc/login.defs` i `/etc/security/pwquality.conf`.
* **Windows:** Aplicació de polítiques de directiva de grup (**GPO**) per a la longitud mínima, edat màxima, historial i bloqueig de compte darrere intents fallits.

### 5. 📜 Certificats Digitals i PKI
* **Linux:** Generació de claus i sol·licituds de certificat (CSR) amb **OpenSSL**, gestió de gestors de certificats de l'entitat de certificació (CA) i instal·lació a `/etc/ssl/certs/`.
* **Windows:** Gestió del magatzem de certificats (`certmgr.msc`), desplegament de certificats mitjançant **Active Directory Certificate Services (AD CS)** i configuració a IIS.

### 6. 🔐 Encriptació de Dades i Disc
* **Linux:** Xifrat de disc complet amb **LUKS** (`cryptsetup`), xifrat de directoris individuals (`eCryptfs`) i xifrat de dades en tràsit (TLS/SSH).
* **Windows:** Xifrat de unitats de disc amb **BitLocker** (amb o sense xip TPM) i xifrat de fitxers/carpetes amb **EFS** (Encrypting File System).

### 7. 📋 Polítiques de Seguretat Global
* **Linux:** Hardening del sistema, aplicació de perfils de seguretat amb **AppArmor** o **SELinux**, i auditories del sistema amb **auditd**.
* **Windows:** Implementació de **Directives de Seguretat Local** (`secpol.msc`) i **GPOs de domini**, polítiques d'execució d'aplicacions (**AppLocker** / **WDAC**).

---

## 📊 Taula Comparativa Resum: Windows vs Linux

| Concepte | Implementació a Linux 🐧 | Implementació a Windows 🪟 |
| :--- | :--- | :--- |
| **ACLs** | `getfacl` / `setfacl` | Interfície NTFS / `icacls` |
| **Antimalware** | ClamAV / rkhunter | Windows Defender |
| **Autenticació** | PAM / SSH Keys | Active Directory / Kerberos |
| **Contrasenyes** | `/etc/login.defs` / `pwquality` | Directives de grup (GPO) |
| **Certificats** | OpenSSL / `/etc/ssl/` | `certmgr.msc` / AD CS |
| **Encriptació** | LUKS / `cryptsetup` | BitLocker / EFS |
| **Polítiques** | SELinux / AppArmor / `auditd` | GPO (`secpol.msc`) / AppLocker |
