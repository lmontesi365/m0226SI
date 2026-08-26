# 🔑 Criptografia i Integritat de les Dades

La **criptografia** i la **verificació d'integritat** són els pilars fonamentals per garantir la **confidencialitat**, l'**autenticitat** i la **no alteració** de la informació, tant en trànsit per la xarxa com en emmagatzematge (en disc).

---

## 1. Conceptes Fonamentals

* **Confidencialitat:** Garanteix que només les persones autoritzades puguin llegir la informació. S'aconsegueix mitjançant el **xifratge**.
* **Integritat:** Assegura que la informació no ha estat modificada, alterada o corrompuda (ja sigui per una fallada tècnica o per un atacant). S'aconsegueix mitjançant funcions **Hash** i **signatures digitals**.
* **Autenticitat:** Confirma la identitat de l'emissor d'un missatge o del propietari d'un recurs.
* **No repudi:** Impedeix que un emissor pugui negar haver enviat un missatge o realitzat una acció.

---

## 2. Funcions Hash i Verificació d'Integritat

Una funció **Hash** (o resum criptogràfic) és un algorisme matemàtic unidireccional que transforma qualsevol conjunt de dades d'entrada en una cadenes de caràcters de longitud fixa.

### Característiques principals

1. **Unidireccional (*One-way*):** És impossible obtenir el contingut original a partir del hash.
2. **Efecte allau (*Avalanche effect*):** Un canvi d'un sol bit en el document original produeix un hash completament diferent.
3. **Resistència a col·lisions:** Dos documents diferents no han de generar mai el mateix hash.

### Algorismes Hash Més Comuns

* **MD5 / SHA-1:** Desaconsellats per a ús de seguretat a causa de vulnerabilitats i col·lisions trobades. S'usen només per a comprovacions d'error simples.
* **SHA-256 / SHA-512 (Família SHA-2):** Estàndard actual recomanat per a qualsevol entorn de producció.
* **SHA-3:** Última generació d'algorismes hash dissenyats com a alternativa a SHA-2.

---

### Exemples Pràctics de Verificació d'Integritat

#### En Linux (Bash)

```bash
# Calcular el hash SHA-256 d'un fitxer
sha256sum document.pdf

# Guardar el hash en un fitxer de comprovació
sha256sum document.pdf > document.pdf.sha256

# Verificar la integritat del fitxer
sha256sum -c document.pdf.sha256

```

#### En Windows (PowerShell)

```powershell
# Calcular el hash SHA-256 d'un fitxer
Get-FileHash -Path .\document.pdf -Algorithm SHA256

# Comparar si un hash coincideix amb l'esperat
(Get-FileHash -Path .\document.pdf -Algorithm SHA256).Hash -eq "HASH_ESPERAT_EN_MAJUSCULES"

```

---

## 3. Tipus de Xifratge

```
                            ┌─────────────────────────────────┐
                            │    Tipus de Criptografia        │
                            └────────────────┬────────────────┘
                                             │
                    ┌────────────────────────┴────────────────────────┐
                    ▼                                                 ▼
        ┌───────────────────────┐                         ┌───────────────────────┐
        │   Xifrat Simètric     │                         │  Xifrat Asimètric     │
        │ (Clau compartida)     │                         │ (Clau pública/privada)│
        └───────────┬───────────┘                         └───────────┬───────────┘
                    │                                                 │
            ┌───────┴───────┐                                 ┌───────┴───────┐
            ▼               ▼                                 ▼               ▼
         Ràpid       Una sola clau                         Llent        Dos claus
       (AES-256)    per xifrar/desxifrar                  (RSA, ECC)    (Pública / Privada)

```

---

### A. Xifrat Simètric

Usa la **mateixa clau secreta** tant per xifrar com per desxifrar la informació.

* **Avantatges:** Molt ràpid i eficient per a grans volums de dades.
* **Inconvenients:** El problema principal és com intercanviar la clau secreta de forma segura entre les parts.
* **Algorismes principals:** **AES** (AES-128, AES-256), ChaCha20. *(Desaconsellats: DES, 3DES, RC4)*.

#### Exemples pràctics:

* **Linux (OpenSSL):**
```bash
# Xifrar un fitxer amb AES-256
openssl enc -aes-256-cbc -salt -in dades.txt -out dades.enc -pbkdf2

# Desxifrar el fitxer
openssl enc -d -aes-256-cbc -in dades.enc -out dades_desxifrades.txt -pbkdf2

```



---

### B. Xifrat Asimètric (Clau Pública / Privada)

Utilitza un parell de claus matemàticament relacionades:

1. **Clau Pública:** Es pot compartir amb tothom. S'utilitza per **xifrar** el missatge o per **verificar** una signatura.
2. **Clau Privada:** És secreta i només la té el propietari. S'utilitza per **desxifrar** el missatge o per **signar**.

* **Avantatges:** Resol el problema de la distribució de claus.
* **Inconvenients:** Computacionalment molt més lent que el xifrat simètric.
* **Algorismes principals:** **RSA** (mínim 2048 o 4096 bits), **ECC** (Criptografia de Corba El·líptica).

#### Funcionament basat en el propòsit:

| Objectiu | Qui xifra / signa? | Amb quina clau? | Qui desxifra / verifica? | Amb quina clau? |
| --- | --- | --- | --- | --- |
| **Confidencialitat** | Emissor | Clau **Pública** del destinatari | Destinatari | Clau **Privada** del destinatari |
| **Autenticitat / Signatura** | Emissor | Clau **Privada** de l'emissor | Destinatari | Clau **Pública** de l'emissor |

---

## 4. Xifratge Híbrid i Enllaços Segurs (TLS/HTTPS)

A la pràctica, els sistemes reals (com el protocol HTTPS/TLS, SSH o VPNs) no utilitzen únicament un tipus de xifratge, sinó que **combinen tots dos**:

1. S'utilitza **Criptografia Asimètrica (RSA/ECC)** per autenticar el servidor i intercanviar de forma segura una clau de sessió temporal.
2. Un cop establerta la clau temporal, es passa a utilitzar **Criptografia Simètrica (AES)** per xifrar tot el trànsit de dades (per la seva velocitat).
3. S'apliquen **Funcions Hash (SHA-256)** per assegurar que cap paquet de dades ha estat alterat durant el trànsit.

---

## 5. Infraestructura de Clau Pública (PKI) i Certificats Digitals

Una **PKI (Public Key Infrastructure)** és l'ecosistema de maquinari, programari, polítiques i procediments necessaris per crear, gestionar, distribuir, utilitzar i revocar certificats digitals.

### Elements principals d'una PKI

* **CA (Certifying Authority / Autoritat de Certificació):** Entitat de confiança (p. ex., *Let's Encrypt*, *DigiCert*, *FNMT*) que signa digitalment i valida els certificats associant una clau pública a una identitat real.
* **RA (Registration Authority / Autoritat de Registre):** Verifica la identitat dels sol·licitants abans que la CA emeti el certificat.
* **CRL (Certificate Revocation List) / OCSP:** Llistes o protocols de consulta en temps real per comprovar si un certificat ha estat revocat abans de la seva data d'expiració.
* **Certificat Digital (Estàndard X.509):** Document digital que conté la clau pública, informació del titular, data de caducitat i la signatura de la CA.

---

## 6. Xifratge en Repòs (Emmagatzematge en Disc)

A part de xifrar les comunicacions per la xarxa, cal protegir les dades quan estan emmagatzemades en disc (*Data at Rest*):

* **Linux (LUKS / dm-crypt):** Estàndard per al xifratge de volums i particions completes en sistemes GNU/Linux.
* **Windows (BitLocker):** Característica integrada en Windows per xifrar discs de sistema i unitats d'emmagatzematge secundàries o USBs.
* **Eines Multiplataforma (VeraCrypt):** Programari de codi obert per crear contenidors o volums xifrats en qualsevol sistema operatiu.

---
