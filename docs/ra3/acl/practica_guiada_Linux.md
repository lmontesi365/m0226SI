## 🧪 Pràctica Guiada per als Alumnes

Pots executar aquesta seqüència de comandes a la terminal per comprovar el funcionament de les ACL:

```bash
# 1. Crear un directori de treball i un fitxer de prova
mkdir /tmp/practica_acl
echo "Document secret de seguretat" > /tmp/practica_acl/secret.txt

# 2. Assignar permisos base estrictes (només el propietari pot llegir i escriure)
chmod 600 /tmp/practica_acl/secret.txt

# 3. Comprovar els permisos inicials
getfacl /tmp/practica_acl/secret.txt

# 4. EXERCI: Permet que l'usuari 'usuari2' pugui llegir el fitxer sense canviar-ne el grup
setfacl -m u:usuari2:r-- /tmp/practica_acl/secret.txt

# 5. EXERCI: Configura la carpeta perquè qualsevol fitxer nou hereti permisos per al grup 'alumnes'
setfacl -d -m g:alumnes:rwx /tmp/practica_acl

# 6. Verifica el resultat final de la carpeta i del fitxer
getfacl /tmp/practica_acl
getfacl /tmp/practica_acl/secret.txt

```

---

## ✅ Checklist de Comprovació ACL

* [ ] Comanda `getfacl` utilitzada per verificar l'estat inicial
* [ ] Permís d'usuari específic afegit amb `setfacl -m u:nom:permisos`
* [ ] Permís de grup especificat afegit amb `setfacl -m g:nom:permisos`
* [ ] Presència del símbol `+` comprovada amb `ls -l`
* [ ] Permisos per defecte en carpeta configurats amb `-d`
* [ ] Neteja de permisos realitzada amb `-x` o `-b`

```

## ✅ solució final de la pràctica guiada .

Quan executes les dues comandes `getfacl`, aquesta és la sortida exacta a la terminal:

```bash
# 1. Verificació de la carpeta /tmp/practica_acl
getfacl /tmp/practica_acl

```

**Sortida esperada per a la carpeta:**

```text
# file: tmp/practica_acl
# owner: usuari1
# group: usuari1
user::rwx
group::r-x
other::r-x
default:user::rwx
default:group::---
default:group:alumnes:rwx
default:mask::rwx
default:other::---

```

---

```bash
# 2. Verificació del fitxer /tmp/practica_acl/secret.txt
getfacl /tmp/practica_acl/secret.txt

```

**Sortida esperada per al fitxer:**

```text
# file: tmp/practica_acl/secret.txt
# owner: usuari1
# group: usuari1
user::rw-
user:usuari2:r--
group::---
mask::r--
other::---

```

> **Comprovació addicional amb `ls -l`:**
> Si els alumnes fan un `ls -l /tmp/practica_acl/secret.txt`, els permisos han de mostrar el signe **`+`** al final:
> `-rw-r-----+ 1 usuari1 usuari1 28 aug 26 17:47 secret.txt`
