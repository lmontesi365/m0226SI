# 🔐 Llistes de Control d'Accés (ACL) a Linux

Les **ACL (Access Control Lists)** permeten assignar permisos d'accés detallats (lectura, escriptura i execució) a usuaris o grups específics que no són el propietari ni el grup principal del fitxer o directori.

Aquest sistema amplia el model tradicional de permisos POSIX (`rwx` per a Usuari, Grup i Altres), oferint una gestió de la seguretat molt més flexible.

---

## 📚 Teoria Base i Comandes Principals

Per gestionar les ACL en sistemes Linux es fan servir dues eines fonamentals:

* **`getfacl`**: Utilitzada per **consultar** les ACL actives en un fitxer o directori.
* **`setfacl`**: Utilitzada per **establir, modificar o eliminar** regles d'ACL.

### Sintaxi del comandament `setfacl`

```bash
setfacl [opcions] [regla] fitxer_o_directori

# 🔐 Llistes de Control d'Accés (ACL) a Linux

Les **ACL (Access Control Lists)** permeten assignar permisos d'accés detallats (lectura, escriptura i execució) a usuaris o grups específics que no són el propietari ni el grup principal del fitxer o directori.

Aquest sistema amplia el model tradicional de permisos POSIX (`rwx` per a Usuari, Grup i Altres), oferint una gestió de la seguretat molt més flexible.

---

## 📚 Teoria Base

Per gestionar les ACL en sistemes Linux es fan servir dues eines fonamentals:

- **`getfacl`**: Utilitzada per **consultar** les ACL actives en un fitxer o directori.
- **`setfacl`**: Utilitzada per **establir, modificar o eliminar** regles d'ACL.

### Sintaxi del comandament `setfacl`

```bash
setfacl [opcions] [regla] fitxer_o_directori

```

### Opcions Més Utilitzades

| Opció | Paràmetre | Descripció |
| --- | --- | --- |
| **`-m`** | `u:usuari:rwx` / `g:grup:rwx` | Afegeix o modifica una regla d'ACL (`modify`). |
| **`-x`** | `u:usuari` / `g:grup` | Elimina una regla d'ACL específica (`remove`). |
| **`-b`** | *(cap)* | Esborra **totes** les ACL d'un fitxer o directori (`remove-all`). |
| **`-R`** | *(cap)* | Aplica els canvis de forma recursiva a subcarpetes (`recursive`). |
| **`-d`** | *(cap)* | Estableix permisos per defecte per a futurs fitxers en un directori (`default`). |

---

## 🛠️ Exemples Pràctics de Comandes

### 1. Consultar Permisos (`getfacl`)

Per comprovar els permisos d'un fitxer anomenat `examen.txt`:

```bash
getfacl examen.txt

```

**Exemple de sortida:**

```text
# file: examen.txt
# owner: joan
# group: professors
user::rw-
group::r--
other::---

```

---

### 2. Afegir o Modificar Permisos (`setfacl -m`)

#### A. Donar permisos a un usuari concret

Assignar a l'usuari `marta` permisos de lectura i escriptura (`rw-`) sobre `examen.txt`:

```bash
setfacl -m u:marta:rw- examen.txt

```

> 💡 **Nota:** Si fas un `ls -l examen.txt`, veuràs un símbol de més (**`+`**) al final dels permisos (ex: `-rw-r-----+`), indicant que el fitxer té una ACL activa.

#### B. Donar permisos a un grup concret

Assignar al grup `alumnes` permisos de només lectura (`r--`) sobre `informe.txt`:

```bash
setfacl -m g:alumnes:r-- informe.txt

```

#### C. Aplicar permisos recursivament

Donar permís de lectura i execució al grup `tutors` en tota la carpeta `/projectes`:

```bash
setfacl -R -m g:tutors:r-x /projectes

```

---

### 3. Eliminar Permisos ACL (`setfacl -x` / `-b`)

#### A. Eliminar l'ACL d'un usuari o grup específic

Treure tots els permisos especials que té l'usuari `marta` sobre el fitxer:

```bash
setfacl -x u:marta examen.txt

```

#### B. Esborrar totes les ACL (Restaurar permisos normals)

Eliminar qualsevol regla d'ACL aplicada sobre `examen.txt`:

```bash
setfacl -b examen.txt

```

---

### 4. Permisos per Defecte en Directoris (`-d`)

Si vols que **tots els fitxers o subcarpetes nous** creats dins d'un directori heretin automàticament determinats permisos, s'utilitza la sintaxi de permisos per defecte (`d:`).

Donar permís de lectura, escriptura i execució per defecte al grup `professors` per a qualsevol element creat dins de `/compartit`:

```bash
setfacl -d -m g:professors:rwx /compartit

```

---

## 🧪 Pràctica Guiada

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

```
