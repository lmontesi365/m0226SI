# 📜 Certificats Digitals i Infraestructura de Clau Pública (PKI)

Els **certificats digitals** s'utilitzen per autenticar la identitat d'equips, usuaris o serveis i per xifrar les comunicacions en xarxa (com HTTPS, TLS/SSL o IPsec). Es basen en la **criptografia asimètrica**, utilitzant un parell de claus (una de pública i una de privada).

---

## 📚 Conceptes Clau

* **CA (Certificate Authority):** Entitat de Certificació encarregada d'emetre, signar i revocar certificats.
* **CSR (Certificate Signing Request):** Sol·licitud formal que conté la clau pública i les dades de l'entitat per demanar la signatura d'una CA.
* **Formats habituals:**
  * `.crt` / `.pem`: Formats codificats en ASCII Base64 molt utilitzats en Linux/Apache/Nginx.
  * `.pfx` / `.p12`: Formats binaris (PKCS#12) que inclouen tant el certificat com la clau privada (protegits per contrasenya), molt utilitzats en Windows.

---

## 🐧 Certificats Digitals a Linux

A Linux, l'eina de referència per gestionar claus i certificats és **OpenSSL**.

### 1. Generació d'una CA pròpia i parell de claus

```bash
# 1. Generar la clau privada de la CA
openssl genrsa -out ca.key 4096

# 2. Generar el certificat autofirmat de la CA (vàlid per 3650 dies)
openssl req -x509 -new -nodes -key ca.key -sha256 -days 3650 -out ca.crt

```

### 2. Creació d'una sol·licitud CSR i signatura del certificat

```bash
# 1. Generar la clau privada del servidor
openssl genrsa -out servidor.key 2048

# 2. Crear la sol·licitud de signatura (CSR)
openssl req -new -key servidor.key -out servidor.csr

# 3. Signar el certificat del servidor amb la nostra CA
openssl x509 -req -in servidor.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out servidor.crt -days 365 -sha256

```

### 3. Instal·lació de certificats al magatzem del sistema

Perquè el sistema operatiu confiï en una CA pròpia o corporativa:

* **Ubuntu / Debian:**
```bash
sudo cp ca.crt /usr/local/share/ca-certificates/la_meva_ca.crt
sudo update-ca-certificates

```


* **RHEL / CentOS / Rocky Linux:**
```bash
sudo cp ca.crt /etc/pki/ca-trust/source/anchors/
sudo update-ca-trust

```



### 4. Conversió de formats amb OpenSSL

```bash
# Convertir de PEM (.crt + .key) a PKCS#12 (.pfx per a Windows)
openssl pkcs12 -export -out certificat.pfx -inkey servidor.key -in servidor.crt

# Convertir de PFX (.pfx) a PEM (.crt + .key)
openssl pkcs12 -in certificat.pfx -nocerts -out clau_privada.key
openssl pkcs12 -in certificat.pfx -clcerts -nokeys -out certificat.crt

```

---

## 🪟 Certificats Digitals a Windows

A Windows, la gestió de certificats es realitza mitjançant interfícies gràfiques, eines de línia de comandes i serveis de domini.

### 1. Gestor de Certificats del Sistema (`certmgr.msc` i `certlm.msc`)

* **`certmgr.msc`:** Obre el magatzem de certificats de l'**usuari actual**.
* **`certlm.msc`:** Obre el magatzem de certificats de la **màquina local** (*Local Machine*).

**Estructura principal del magatzem:**

* **Personal:** Certificats d'usuari o de l'equip utilitzats per autenticació o xifrat.
* **Entitats d'autenticació arrel de confiança:** Certificats de les CA en les quals l'equip confia plenament.

### 2. Gestió amb PowerShell

```powershell
# 1. Llistar els certificats instal·lats a la màquina local
Get-ChildItem -Path Cert:\LocalMachine\My

# 2. Crear un certificat autofirmat per a proves
New-SelfSignedCertificate -DnsName "servidor.local" -CertStoreLocation "Cert:\LocalMachine\My"

# 3. Exportar un certificat amb clau privada a format PFX
$Cert = Get-ChildItem -Path Cert:\LocalMachine\My\THUMBPRINT_DEL_CERTIFICAT$Pwd = ConvertTo-SecureString -String "LaSevaContrasenya123" -Force -AsPlainText
Export-PfxCertificate -Cert $Cert -FilePath "C:\certificats\servidor.pfx" -Password $Pwd

# 4. Importar un certificat a la màquina local
Import-PfxCertificate -FilePath "C:\certificats\servidor.pfx" -CertStoreLocation "Cert:\LocalMachine\My" -Password $Pwd

```

### 3. Active Directory Certificate Services (AD CS)

En entorns corporatius amb Windows Server, s'instal·la el rol **AD CS** per crear una PKI integrada a Active Directory:

* **Emissió automàtica (*Autoenrollment*):** Permet distribuir certificats d'usuari i d'equip automàticament mitjançant directives de grup (GPO).
* **Plantilles de certificats:** Defineixen els permisos, el període de validesa i els usos admesos (ex. Autenticació d'equip, SSL/TLS web, signatura de codi).

---

## 📊 Taula Comparativa: Linux vs Windows

| Operació / Concepte | Linux 🐧 | Windows 🪟 |
| --- | --- | --- |
| **Eina principal per línia de comandes** | `openssl` | `certutil` / PowerShell (`Cert:\`) |
| **Magatzem del sistema** | `/etc/ssl/certs/` o `/etc/pki/` | Console MMC (`certmgr.msc` / `certlm.msc`) |
| **Formats habituals** | `.crt`, `.pem`, `.key` | `.pfx`, `.p12`, `.cer` |
| **Actualitzar certificats de confiança** | `update-ca-certificates` | Desplegament per GPO o importació a `Cert:\LocalMachine\Root` |
| **PKI Corporativa** | OpenSSL CA / Easy-RSA | Active Directory Certificate Services (AD CS) |

---

## 🧪 Pràctica Guiada

```bash
# 1. Generar un certificat autofirmat de prova a Linux amb OpenSSL
openssl req -x509 -newkey rsa:2048 -keyout prova.key -out prova.crt -days 365 -nodes

# 2. Inspeccionar el contingut i les dates de validesa del certificat creat
openssl x509 -in prova.crt -text -noout

# 3. Convertir el certificat i la clau a format PKCS#12 (.pfx) per importar-lo a Windows
openssl pkcs12 -export -out prova.pfx -inkey prova.key -in prova.crt

```

---

## ✅ Checklist de Comprovació

* [ ] Entesa la diferència entre clau pública, clau privada i certificat
* [ ] Domini del procés de creació d'una CSR i de signatura amb OpenSSL
* [ ] Saber instal·lar una CA d'arrel al magatzem de confiança (Linux i Windows)
* [ ] Capacitat per convertir formats de certificats (`.pem` ↔ `.pfx`)
* [ ] Ús de `certmgr.msc` i comandes PowerShell per a la gestió de certificats en Windows

```


```
