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
Opcions Més UtilitzadesOpcióParàmetreDescripció-mu:usuari:rwx / g:grup:rwxAfegeix o modifica una regla d'ACL (modify).-xu:usuari / g:grupElimina una regla d'ACL específica (remove).-b(cap)Esborra totes les ACL d'un fitxer o directori (remove-all).-R(cap)Aplica els canvis de forma recursiva a subcarpetes (recursive).-d(cap)Estableix permisos per defecte per a futurs fitxers en un directori (default).🛠️ Exemples Pràctics de Comandes1. Consultar Permisos (getfacl)Per comprovar els permisos d'un fitxer anomenat examen.txt:Bashgetfacl examen.txt
Exemple de sortida:Plaintext# file: examen.txt
# owner: joan
# group: professors
user::rw-
group::r--
other::---
2. Afegir o Modificar Permisos (setfacl -m)A. Donar permisos a un usuari concretAssignar a l'usuari marta permisos de lectura i escriptura (rw-) sobre examen.txt:Bashsetfacl -m u:marta:rw- examen.txt
💡 Nota: Si fas un ls -l examen.txt, veuràs un símbol de més (+) al final dels permisos (ex: -rw-r-----+), indicant que el fitxer té una ACL activa.B. Donar permisos a un grup concret
