
## 🛠️ Pràctica Pas a Pas: OpenSSL i GnuPG (GPG)

Aquesta secció recull les comandes essencials per xifrar, desxifrar, generar claus i gestionar la integritat de la informació des de la línia de comandes.

---

### 1. Operacions amb OpenSSL

OpenSSL és la eina per defecte en la majoria de sistemes Linux i macOS per a tasques criptogràfiques ràpides.

#### A. Xifratge i Desxifratge Simètric (AES-256)

Utilitza la mateixa contrasenya per xifrar i desxifrar un fitxer.

```bash
# 1. Crear un fitxer de prova
echo "Aquest és un missatge confidencial d'exemple." > document.txt

# 2. Xifrar el fitxer amb AES-256 (demanarà una contrasenya)
openssl enc -aes-256-cbc -pbkdf2 -salt -in document.txt -out document.txt.enc

# 3. Desxifrar el fitxer
openssl enc -d -aes-256-cbc -pbkdf2 -in document.txt.enc -out document_restaurat.txt

```

#### B. Generació i Ús de Parells de Claus Asimètriques (RSA)

```bash
# 1. Generar la clau privada RSA de 4096 bits
openssl genpkey -algorithm RSA -out clau_privada.pem -pkeyopt rsa_keygen_bits:4096

# 2. Extreure la clau pública a partir de la clau privada
openssl rsa -in clau_privada.pem -pubout -out clau_publica.pem

# 3. Xifrar un fitxer utilitzant la CLAU PÚBLICA del destinatari
openssl pkeyutl -encrypt -pubin -inkey clau_publica.pem -in document.txt -out document_asimetric.enc

# 4. Desxifrar el fitxer utilitzant la CLAU PRIVADA del destinatari
openssl pkeyutl -decrypt -inkey clau_privada.pem -in document_asimetric.enc -out document_desxifrat.txt

```

---

### 2. Gestió Avançada amb GnuPG (GPG)

GnuPG utilitza l'estàndard **OpenPGP** i és la millor opció per a l'intercanvi segur de fitxers, missatges i signatures digitals.

#### A. Generació i Gestió del Parell de Claus PGP

```bash
# 1. Generar un nou parell de claus (seguir les instruccions en pantalla)
gpg --full-generate-key

# 2. Llistar les claus públiques disponibles al nostre repositori local
gpg --list-keys

# 3. Exportar la teva clau pública per compartir-la amb altres usuaris
gpg --armor --export "el_teu_email@exemple.com" > la meva_clau_publica.asc

# 4. Importar la clau pública d'un altre usuari/company
gpg --import clau_publica_company.asc

```

#### B. Xifratge i Desxifratge Asimètric amb GPG

```bash
# 1. Xifrar un fitxer per a un destinatari concret (utilitzant la seva clau pública)
gpg --encrypt --recipient "destinatari@exemple.com" document.txt
# (Generarà el fitxer 'document.txt.gpg')

# 2. Desxifrar el fitxer rebut (s'utilitzarà la teva clau privada automàticament)
gpg --decrypt document.txt.gpg > document_desxifrat.txt

```

#### C. Signatura Digital i Verificació d'Integritat

La signatura permet a qualsevol usuari comprovar que el fitxer no ha estat modificat i que realment prové de l'emissor.

```bash
# 1. Signar un fitxer generant una signatura separada (.sig)
gpg --detach-sign document.txt
# (Generarà el fitxer 'document.txt.sig')

# 2. Verificar la signatura del fitxer
gpg --verify document.txt.sig document.txt

```

---

### 📊 Resum de Comandes OpenSSL vs GnuPG

| Tasca | OpenSSL | GnuPG (GPG) |
| --- | --- | --- |
| **Xifrat Simètric** | `openssl enc -aes-256-cbc ...` | `gpg --symmetric fitxer` |
| **Generar Claus** | `openssl genpkey ...` | `gpg --full-generate-key` |
| **Xifrat Asimètric** | `openssl pkeyutl -encrypt ...` | `gpg --encrypt --recipient ...` |
| **Signar Fitxers** | `openssl dgst -sign ...` | `gpg --detach-sign ...` |

---
