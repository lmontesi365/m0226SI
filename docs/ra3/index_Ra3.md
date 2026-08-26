# 🛡️ RA3 - Seguretat Activa

Aquest bloc cobreix les tècniques, eines i configuracions necessàries per prevenir, detectar i mitigar amenaces als sistemes operatius **Windows** i **Linux**.

---

## 📌 Index de Continguts del RA3

Fes clic a qualsevol dels temes per accedir a la documentació extensa i comandes pràctiques:

* **[🔐 Llistes de Control d'Accés (ACL)](acl.md)**
  * Permisos avançats a Linux (`getfacl`/`setfacl`) i permisos NTFS a Windows (`icacls`).
* **[🦠 Antimalware i Protecció](antimalware.md)**
  * Escaneig amb ClamAV i rkhunter a Linux; Microsoft Defender i regles ASR a Windows.
* **[🔑 Autenticació i Control d'Accés](autenticacio.md)**
  * Mòduls PAM i claus SSH a Linux; Active Directory, Kerberos i MFA a Windows.
* **[🔒 Polítiques de Contrasenyes](contrasenyes.md)**
  * Gestió de complexitat a `/etc/security/pwquality.conf` i GPOs de domini a Windows.
* **[📜 Certificats Digitals i PKI](certificat_digital.md)**
  * Generació amb OpenSSL a Linux i gestió amb AD CS / `certmgr.msc` a Windows.
* **[🔐 Encriptació de Dades i Disc](encriptacio.md)**
  * Xifrat de disc amb LUKS (`cryptsetup`) a Linux i BitLocker / EFS a Windows.
* **[📋 Polítiques de Seguretat Global](politicas.md)**
  * Hardening amb SELinux/AppArmor a Linux i Directives de Seguretat (`secpol.msc`) a Windows.

---

## 📊 Taula Comparativa Resum: Windows vs Linux

| Concepte | Implementació a Linux 🐧 | Implementació a Windows 🪟 | Documentació |
| :--- | :--- | :--- | :---: |
| **ACLs** | `getfacl` / `setfacl` | Interfície NTFS / `icacls` | [Anar ➡️](acl.md) |
| **Antimalware** | ClamAV / rkhunter | Microsoft Defender | [Anar ➡️](antimalware.md) |
| **Autenticació** | PAM / SSH Keys | Active Directory / Kerberos | [Anar ➡️](autenticacio.md) |
| **Contrasenyes** | `/etc/login.defs` / `pwquality` | Directives de grup (GPO) | [Anar ➡️](contrasenyes.md) |
| **Certificats** | OpenSSL / `/etc/ssl/` | `certmgr.msc` / AD CS | [Anar ➡️](certificat_digital.md) |
| **Encriptació** | LUKS / `cryptsetup` | BitLocker / EFS | [Anar ➡️](encriptacio.md) |
| **Polítiques** | SELinux / AppArmor / `auditd` | GPO (`secpol.msc`) / AppLocker | [Anar ➡️](politicas.md) |
