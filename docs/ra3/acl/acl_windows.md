# 🔐 Llistes de Control d'Accés (ACL) a Windows (Permisos NTFS)

A **Windows**, el control d'accés detallat a nivell de sistema de fitxers s'implementa mitjançant els **permisos NTFS**. De la mateixa manera que les ACL a Linux, els permisos NTFS permeten definir amb precisió quins usuaris o grups poden llegir, modificar, crear o eliminar fitxers i carpetes.

---

## 📚 Conceptes Clau de les ACL a Windows

* **DACL (*Discretionary Access Control List*):** Llista associada a cada objecte (fitxer/carpeta) que especifica quins usuaris o grups tenen permís o denegació d'accés.
* **ACE (*Access Control Entry*):** Cada una de les entrades individuals dins d'una DACL (ex: `Marta: Permís de Modificació - Permetre`).
* **Permisos d'Herència (*Inheritance*):** Per defecte, els fitxers i subcarpetes hereten automàticament els permisos de la carpeta pare on estan continguts.
* **Denegació explícita (*Explicit Deny*):** Si un permís es configura explícitament com a **Denegar (*Deny*)**, té prioritat absoluta sobre qualsevol permís de **Permetre (*Allow*)**.

---

## 🛠️ Permisos Principals de Fitxers i Carpetes

| Permís NTFS | Descripció |
| :--- | :--- |
| **Control Total (*Full Control*)** | Permet fer qualsevol acció, incloent canviar permisos i prendre la propietat de l'objecte. |
| **Modificar (*Modify*)** | Permet llegir, escriure, executar i eliminar el fitxer o carpeta. |
| **Lectura i execució (*Read & Execute*)** | Permet veure el contingut i executar fitxers (ex: `.exe`, `.bat`). |
| **Llistar contingut de la carpeta (*List Folder Contents*)** | Permet veure els noms de fitxers i subcarpetes (exclusiu de carpetes). |
| **Lectura (*Read*)** | Permet obrir i veure el contingut del fitxer o carpeta. |
| **Escriptura (*Write*)** | Permet crear nous fitxers/carpetes i escriure canvis. |

---

## 🪟 Gestió d'ACLs a Windows

### 1. Gestió des de la Interfície Gràfica (GUI)

1. Fes botó dret sobre el fitxer o carpeta > **Propietats**.
2. Selecciona la pestanya **Seguretat**.
3. Prem **Editar...** per afegir/eliminar usuaris o modificar permisos admesos (`Allow` / `Deny`).
4. Per gestionar l'herència: Prem **Opcions avançades** > **Deshabilitar l'herència** (*Disable inheritance*).

---

### 2. Gestió per Línia de Comandes amb `icacls`

`icacls` és l'eina de línia de comandes nativa de Windows equivalent a `getfacl` i `setfacl` de Linux.

#### A. Consultar permisos d'un fitxer o carpeta (`getfacl` equivalent)

```cmd
REM Consultar permisos d'una carpeta
icacls C:\Dades\Projectes

```

#### B. Assignar o modificar permisos (`setfacl -m` equivalent)

Sintaxi dels permisos a `icacls`: `(F)` Control Total, `(M)` Modificació, `(RX)` Lectura/Execució, `(R)` Lectura, `(W)` Escriptura.

```cmd
REM Donar permís de modificació a l'usuari 'Marta' sobre un fitxer
icacls C:\Dades\informe.docx /grant Marta:(M)

REM Donar permís de només lectura al grup 'Alumnes' a tota una carpeta i el seu contingut (recursia)
icacls C:\Dades\Compartit /grant Alumnes:(RX) /t

REM Denegar permís d'escriptura a l'usuari 'Joan'
icacls C:\Dades\informe.docx /deny Joan:(W)

```

#### C. Eliminar un permís específic (`setfacl -x` equivalent)

```cmd
REM Eliminar l'entrada d'accés (ACE) de l'usuari 'Marta'
icacls C:\Dades\informe.docx /remove Marta

```

#### D. Desactivar o Activar l'Herència

```cmd
REM Desactivar herència i copiar els permisos heretats com a permisos explícits
icacls C:\Dades\Privat /inheritance:d

REM Restaurar l'herència de la carpeta pare
icacls C:\Dades\Privat /inheritance:e

```

---

### 3. Gestió d'ACLs amb PowerShell

PowerShell ofereix els cmdlets `Get-Acl` i `Set-Acl` per a una gestió automatitzada.

```powershell
# 1. Veure els permisos ACL d'un fitxer
Get-Acl -Path "C:\Dades\informe.docx" | Format-List

# 2. Afegir una nova regla d'accés a una carpeta
$Ruta = "C:\Dades\Projectes"
$ACL = Get-Acl -Path $Ruta$Regla = New-Object System.Security.AccessControl.FileSystemAccessRule("Marta", "Modify", "ContainerInherit, ObjectInherit", "None", "Allow")
$ACL.AddAccessRule($Regla)
Set-Acl -Path $Ruta -AclObject$ACL

```

---

## 📊 Taula Comparativa d'ACL: Linux vs Windows

| Operació | Linux 🐧 | Windows 🪟 |
| --- | --- | --- |
| **Comanda per consultar ACLs** | `getfacl fitxer` | `icacls fitxer` / `Get-Acl` |
| **Comanda per modificar ACLs** | `setfacl -m u:usuari:rwx fitxer` | `icacls fitxer /grant usuari:(M)` |
| **Comanda per eliminar una ACL** | `setfacl -x u:usuari fitxer` | `icacls fitxer /remove usuari` |
| **Eliminar totes les ACLs** | `setfacl -b fitxer` | `icacls fitxer /reset` |
| **Prioritat de denegació** | No existeix *Deny* explícit (s'eliminen permisos) | **Deny explícit** s'imposa a qualsevol *Allow* |
| **Herència en carpetes** | ACLs per defecte (`setfacl -d`) | Herència automàtica NTFS (modificable) |

---

## 🧪 Pràctica Guiada per a l'Alumnat

```cmd
REM 1. Crear directori de prova i fitxer
mkdir C:\PracACL
echo "Fitxer de prova" > C:\PracACL\document.txt

REM 2. Consultar els permisos inicials heretats
icacls C:\PracACL\document.txt

REM 3. Desactivar herència a la carpeta de treball
icacls C:\PracACL /inheritance:d

REM 4. Otorgar permisos de Modificació a un usuari local de prova (ex: UsuariTest)
icacls C:\PracACL\document.txt /grant UsuariTest:(M)

REM 5. Comprovar que els permisos s'han aplicat correctament
icacls C:\PracACL\document.txt

```

---

## ✅ Checklist de Comprovació

* [ ] Comprensió del concepte de DACL, ACE i el paper de la Denegació explícita
* [ ] Capacitat per veure i modificar permisos des de la pestanya **Seguretat** a la GUI
* [ ] Ús de la comanda `icacls` per atorgar (`/grant`), denegar (`/deny`) i eliminar (`/remove`) permisos
* [ ] Domini del concepte d'herència NTFS i com activar-la/desactivar-la (`/inheritance`)
* [ ] Conneixement de l'ús bàsic de `Get-Acl` i `Set-Acl` en PowerShell

```
