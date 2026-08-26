
# 🔒 Polítiques de Contrasenyes (Linux i Windows)

Les **polítiques de contrasenyes** són el primer nivell de defensa en la seguretat d'un sistema operatiu. Defineixen els requisits mínims que han de complir les credencials dels usuaris (longitud, complexitat, caducitat i historial) per dificultar els atacs de força bruta, diccionari o reutilització de claus.

---

## 📚 Paràmetres Clau d'una Política de Contrasenyes

* **Longitud mínima:** Nombre mínim de caràcters permesos (recomanat: ≥ 12-14 caràcters).
* **Complexitat:** Obligatorietat de barrejar diferents tipus de caràcters (majúscules, minúscules, números i símbols).
* **Caducitat / Edat màxima:** Temps límit abans que l'usuari hagi de canviar la contrasenya (ex. 90 dies).
* **Historial de contrasenyes:** Nombre de claus anteriors que el sistema recorda per evitar-ne la reutilització immediata.
* **Bloqueig de compte:** Nombre d'intents fallits consecutius admesos abans de inhabilitar temporals o permanentment el compte (protecció contra atacs de força bruta).

---

## 🐧 Polítiques de Contrasenyes a Linux

A Linux, la configuració de la caducitat de les claus es gestiona a `/etc/login.defs` o amb la comanda `chage`, mentre que la complexitat s'aplica mitjançant mòduls **PAM** (`pam_pwquality`).

### 1. Gestió de la Caducitat (`/etc/login.defs` i `chage`)

Per definir valors globals per defecte per a **nous usuaris**, s'edita el fitxer `/etc/login.defs`:

```text
PASS_MAX_DAYS   90    # Temps màxim de validesa d'una clau (dies)
PASS_MIN_DAYS   1     # Dies mínims abans de poder tornar a canviar la clau
PASS_WARN_AGE   14    # Dies d'avís abans de la caducitat
PASS_MIN_LEN    12    # Longitud mínima de la clau

```

#### Modificar la caducitat d'un usuari existent amb `chage`:

```bash
# 1. Veure l'estat actual de la caducitat de l'usuari 'marta'
sudo chage -l marta

# 2. Assignar caducitat de 60 dies i avís de 10 dies
sudo chage -M 60 -W 10 marta

# 3. Forçar un usuari a canviar la contrasenya en el seu proper inici de sessió
sudo chage -d 0 marta

```

### 2. Complexitat de les Contrasenyes (`pam_pwquality`)

Per forçar la complexitat de les noves contrasenyes, s'utilitza el mòdul `pam_pwquality` configurant el fitxer `/etc/security/pwquality.conf`.

#### Configuració d'exemple a `/etc/security/pwquality.conf`:

```text
minlen = 12        # Longitud mínima de 12 caràcters
minclass = 3       # Mínim 3 classes de caràcters diferents (majúscules, minúscules, números, símbols)
maxrepeat = 2      # Màxim de caràcters consecutius iguals (ex: "aaa" serà rebutjat)
ucredit = -1       # Com a mínim 1 majúscula
lcredit = -1       # Com a mínim 1 minúscula
dcredit = -1       # Com a mínim 1 número
ocredit = -1       # Com a mínim 1 símbol/caràcter especial
remember = 5       # Historial: recorda les darreres 5 contrasenyes (integrat amb pam_unix)

```

### 3. Bloqueig de Comptes per Intents Fallits (`pam_faillock`)

Per evitar atacs de força bruta, s'utilitza el mòdul `pam_faillock` a `/etc/pam.d/common-auth`:

```bash
# Llistar els intents fallits d'un usuari
sudo faillock --user marta

# Desbloquejar manualment un compte bloquejat
sudo faillock --user marta --reset

```

---

## 🪟 Polítiques de Contrasenyes a Windows

A Windows, les polítiques es gestionen mitjançant la **Directiva de Seguretat Local** (`secpol.msc`) en equips aïllats o mitjançant **Directives de Grup (GPO)** en un domini Active Directory (`gpmc.msc`).

### 1. Configuració des de la Interfície Gràfica (`secpol.msc`)

Ruta a la consola de seguretat local:
`Directives de compte` > `Directiva de contrasenyes`

* **Comprovar complexitat de la contrasenya:** *Habilitat* (Requereix majúscules, minúscules, números i símbols).
* **Longitud mínima de la contrasenya:** Definir en 12-14 caràcters.
* **Edat màxima de la contrasenya:** Definir en 60 o 90 dies.
* **Historial de contrasenyes:** Recordar les últimes 5-10 contrasenyes.

Ruta per al bloqueig de comptes:
`Directives de compte` > `Directiva de bloqueig de comptes`

* **Umbrall de bloqueig de compte:** Bloquejar després de 3 o 5 intents fallits.
* **Durada del bloqueig de compte:** 15-30 minuts (o fins que l'administrador el restableixi).

### 2. Gestió mitjançant PowerShell i Línia de Comandes

#### Visualitzar i modificar la política local amb `net accounts`:

```cmd
REM 1. Veure la configuració actual de la política de comptes
net accounts

REM 2. Establir una longitud mínima de 12 caràcters
net accounts /minpwlen:12

REM 3. Establir una edat màxima de 60 dies per a les contrasenyes
net accounts /maxpwage:60

REM 4. Establir un historial de 5 contrasenyes
net accounts /UNIQUEPW:5

```

#### Gestió d'usuaris des de PowerShell:

```powershell
# 1. Obtenir l'estat d'un usuari i veure si la contrasenya caduca
Get-LocalUser -Name "Marta" | Select-Object Name, PasswordExpirationDate, PasswordRequired

# 2. Forçar que l'usuari hagi de canviar la contrasenya al pròxim inici de sessió
Set-LocalUser -Name "Marta" -PasswordNeverExpires $false

# 3. Desbloquejar un compte bloquejat per intents fallits
Unlock-LocalUser -Name "Marta"

```

---

## 📊 Taula Comparativa: Linux vs Windows

| Paràmetre de Seguretat | Linux 🐧 | Windows 🪟 |
| --- | --- | --- |
| **Caducitat i Avís** | `/etc/login.defs` / `chage` | `secpol.msc` / `net accounts /maxpwage` |
| **Regles de Complexitat** | `/etc/security/pwquality.conf` | GPO (`secpol.msc`) / Password Policy |
| **Historial de Claws** | Mòdul `pam_unix` (`remember=X`) | GPO / `net accounts /UNIQUEPW:X` |
| **Protecció Força Bruta** | Mòdul `pam_faillock` / `faillock` | Directiva de bloqueig de comptes / `Unlock-LocalUser` |
| **Consola d'Auditoria** | `/var/log/auth.log` / `journalctl` | Visualitzador d'esdeveniments (*Event Viewer*) |

---

## 🧪 Pràctica Guiada per a l'Alumnat

```bash
# PRÀCTICA A LINUX: Aplicar una política de caducitat i comprovar-ne l'efecte

# 1. Crear un usuari de prova
sudo useradd -m -s /bin/bash alumne_pass
sudo passwd alumne_pass

# 2. Configurar la clau de l'usuari perquè caduqui cada 30 dies i avisi 7 dies abans
sudo chage -M 30 -W 7 alumne_pass

# 3. Comprovar que la política s'ha aplicat correctament
sudo chage -l alumne_pass

# 4. Simular la caducitat immediata de la clau
sudo chage -d 0 alumne_pass

# 5. Iniciar sessió amb l'usuari per verificar que el sistema demana canviar la clau
su - alumne_pass

```

---

## ✅ Checklist de Comprovació

* [ ] Comprensió dels 5 paràmetres essencials d'una política de contrasenyes
* [ ] Capacitat per gestionar la caducitat i avisos a Linux amb `chage` i `/etc/login.defs`
* [ ] Configuració de regles de complexitat amb `pwquality.conf`
* [ ] Gestió del bloqueig de comptes locals a Windows (`secpol.msc`) i Linux (`pam_faillock`)
* [ ] Ús de comandes de consola (`net accounts`, PowerShell i `faillock`) per a tasques d'administració

```

```
