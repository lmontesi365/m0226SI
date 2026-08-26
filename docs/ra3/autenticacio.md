# 🔑 Autenticació i Control d'Accés (Linux i Windows)

L'**autenticació** és el procés de verificar la identitat d'un usuari, equip o servei abans de concedir-li accés als recursos del sistema. Un cop autenticat, el **control d'accés** determina quines accions i permisos té permesos executar.

---

## 📚 Mètodes i Factors d'Autenticació

* **Basat en quelcom que saps:** Contrasenyes, codis PIN, preguntes de seguretat.
* **Basat en quelcom que tens:** Targetes intel·ligents, claus de seguretat fressades (FIDO2/YubiKey), aplicacions d'autenticació (TOTP).
* **Basat en quelcom que ets (Biometria):** Petjada dactilar, reconeixement facial, escàner d'iris.
* **Autenticació Multifactoret (MFA):** Combinació de dos o més factors diferents per augmentar dràsticament la seguretat.

---

## 🐧 Autenticació a Linux

A Linux, la gestió de l'autenticació es basa principalment en l'arquitectura **PAM** (*Pluggable Authentication Modules*) i en serveis d'accés remot com **SSH**.

### 1. Mòduls d'Autenticació Modulars (PAM)

PAM permet als administradors configurar les polítiques d'autenticació d'aplicacions i serveis sense haver de modificar el codi font d'aquests.

* **Ubicació de la configuració:** `/etc/pam.d/`
* **Principals fitxers de configuració:**
  * `/etc/pam.d/common-auth`: Regles d'autenticació generals.
  * `/etc/pam.d/common-password`: Polítiques per al canvi de claus.
  * `/etc/pam.d/sshd`: Polítiques d'accés per al servei SSH.

**Tipus de mòduls PAM:**
1. `auth`: Verifica la identitat de l'usuari (demana contrasenya/biometria).
2. `account`: Comprova si el compte està actiu, no ha caducat o té permís d'accés a l'hora actual.
3. `password`: S'encarrega de l'actualització de les credencials.
4. `session`: Executa tasques abans/després de la sessió d'usuari (muntar carpetes home, registre de logs, etc.).

### 2. Autenticació Segura per SSH (Clau Pública/Privada)

Per eliminar l'ús de contrasenyes febles en l'accés remot, s'utilitza l'autenticació per parell de claus.

```bash
# 1. Generar un parell de claus SSH (Ed25519 recomanat o RSA 4096)
ssh-keygen -t ed25519 -C "admin@empresa.com"

# 2. Copiar la clau pública al servidor remot
ssh-copy-id usuari@servidor_remot

# 3. Desactivar l'autenticació per contrasenya a /etc/ssh/sshd_config
# Afegir o modificar:
# PasswordAuthentication no
# PubkeyAuthentication yes
# PermitRootLogin no

# 4. Reiniciar el servei SSH
sudo systemctl restart sshd

```

---

## 🪟 Autenticació a Windows

Windows gestiona l'autenticació mitjançant mecanismes locals (SAM) o centralitzats de domini (**Active Directory**).

### 1. Autenticació Local vs. Domini

* **SAM (*Security Account Manager*):** Base de dades local on s'emmagatzemen els usuaris i els seus *hashes* de contrasenya (NTLM) en màquines aïllades.
* **Active Directory Domain Services (AD DS):** Gestió centralitzada d'usuaris, grups i equips en entorns corporatius.

### 2. Protocols d'Autenticació

* **Kerberos:** Protocol per defecte en dominis Active Directory. Utilitza un Centre de Distribució de Claus (**KDC**) i tiquets d'autenticació (*Tickets*) per validar usuaris sense enviar la contrasenya per la xarxa.
* **NTLM (*NT LAN Manager*):** Protocol llegat basat en desafiament/resposta. Més vulnerable i desaconsellat en entorns moderns.

### 3. Windows Hello for Business i MFA

Permet substituir les contrasenyes convencionals per una autenticació forta de dos factors integrada al sistema operatiu:

* **Factor 1:** Dispositiu físic vinculat a l'usuari (TPM de l'equip).
* **Factor 2:** Biometria (Windows Hello facial/petjada) o un codi PIN local enllaçat directament al TPM.

#### Configuració de Seguretat d'Autenticació via PowerShell:

```powershell
# Comprovar els intents fallits d'inici de sessió i el bloqueig de comptes
Get-LocalUser | Select-Name, Enabled, LastLogon

# Bloquejar l'ús de comptes locals per a connexions de xarxa via Directiva Local
# secpol.msc -> Directives locals -> Opcions de seguretat

```

---

## 📊 Taula Comparativa: Linux vs Windows

| Característica | Linux 🐧 | Windows 🪟 |
| --- | --- | --- |
| **Arquitectura d'Autenticació** | **PAM** (*Pluggable Auth Modules*) | **LSA** (*Local Security Authority*) |
| **Base de Dades Local** | `/etc/passwd` i `/etc/shadow` | Base de dades **SAM** |
| **Autenticació Centralitzada** | OpenLDAP / FreeIPA / SSSD | **Active Directory** (AD DS) |
| **Protocol de Xarxa Principal** | SSH (Clau Pública) / Kerberos | **Kerberos** / NTLM |
| **Accés Remot Administratiu** | SSH (`sshd`) | **WinRM** / RDP |

---

## 🧪 Pràctica Guiada per a l'Alumnat

```bash
# PRÀCTICA A LINUX: Configuració d'autenticació per clau SSH sense contrasenya

# 1. Crear un usuari de prova
sudo useradd -m -s /bin/bash alumne_test
sudo passwd alumne_test

# 2. Generar claus des del client
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa_test -N ""

# 3. Instal·lar la clau pública en el compte de l'usuari de prova
sudo mkdir -p /home/alumne_test/.ssh
sudo cp ~/.ssh/id_rsa_test.pub /home/alumne_test/.ssh/authorized_keys
sudo chown -R alumne_test:alumne_test /home/alumne_test/.ssh
sudo chmod 700 /home/alumne_test/.ssh
sudo chmod 600 /home/alumne_test/.ssh/authorized_keys

# 4. Provar la connexió fent ús de la clau privada
ssh -i ~/.ssh/id_rsa_test alumne_test@localhost

```

---

## ✅ Checklist de Comprovació

* [ ] Comprensió dels diferents factors d'autenticació (MFA)
* [ ] Conneixement de l'estructura i funcionament dels mòduls PAM a Linux
* [ ] Capacitat per configurar un servidor SSH per acceptar només claus públiques
* [ ] Detecció de les diferències entre l'autenticació SAM local i Kerberos en domini
* [ ] Entesa del paper del xip TPM en solucions d'autenticació moderna (Windows Hello)

```

```
