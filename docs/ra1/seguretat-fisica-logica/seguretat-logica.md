# 🛡️ Seguretat Lògica

## 📖 Definició

Conjunt de mesures tècniques i de control aplicades als sistemes informàtics i a la informació per protegir-les de ciberamenaces digitals:

- **Malware** (virus, trojans, ransomware, worms)
- **Accessos no autoritzats** a sistemes/dades
- **Exfiltració de dades** sensibles
- **Atacs de negació de servei** (DDoS)
- **Corrupció de dades**
- **Espionatge industrial** i phishing
- **Ransomware** i criptobloqueig

---

## 🛠️ Mesures de Seguretat Lògica

### 1️⃣ **Autenticació i Gestió d'Identitats**

#### Contrasenyes Fortes

**Exemple de contrasenya forta:**
- ❌ `Password123`
- ❌ `Admin2024`
- ✅ `Tr0pic@lSun$2026!Sec`

#### Autenticació Multifactor (MFA/2FA)

#### Gestió d'Identitats

---

### 2️⃣ **Control d'Accés i Permisos**

#### Models de Control d'Accés (AC)

**DAC (Discretionary Access Control)**

**MAC (Mandatory Access Control)**

**RBAC (Role-Based Access Control)** ← **Recomanat**

**ABAC (Attribute-Based Access Control)**

#### Principi de "Least Privilege"

#### Separació de Funcions

---

### 3️⃣ **Protecció Perimetral (Network)**

#### Firewall (Tallafocs)

**Exemple de regla:**

#### IDS/IPS (Intrusion Detection/Prevention Systems)


---

### 9️⃣ **Gestió de Dependencies i Vulnerabilitats**

---

## ✅ Bones Pràctiques de Seguretat Lògica

| Pràctica | Descripció |
|----------|------------|
| **No compartir contrasenyes** | Cada usuari amb contrasenya única |
| **No obrir fitxers sospitosos** | Verificar origen de correus/fitxers |
| **Connexions segures** | Always HTTPS, VPN en xarxes públiques |
| **MFA activat** | Activar 2FA en tots els comptes crítics |
| **Actualizaciones automàtiques** | Mantenir SO i aplicacions always updated |
| **Còpies de seguretat regulars** | Test mensuales de restauració |
| **Formació d'usuaris** | Awareness sobre phishing i enginyeria social |
| **Auditoria de permisos** | Revisió trimestral d'accesos |
| **Incident response** | Procediment establert per a incidents |
| **Zero Trust** | Verificar tot, no confiar en xarxa interna |

---

## 📋 Checklist de Seguretat Lògica

- [ ] Contrasenyes fortes + MFA activat
- [ ] Firewall corporatiu funcionant
- [ ] IDS/IPS operatiu
- [ ] Antivirus actualitzat en tots els equips
- [ ] EDR deployat als endpoints crítics
- [ ] DLP configurat per a dades sensibles
- [ ] WAF protegint aplicacions web
- [ ] Còpies de seguretat automàtiques (estratègia 3-2-1)
- [ ] SIEM recopilant i analitzant logs
- [ ] Alertes en temps real configurades
- [ ] Logs retinguts 6+ mesos
- [ ] Polítiques d'accés basades en rols (RBAC)
- [ ] Auditoria trimestral de permisos
- [ ] Formació de seguretat per tots els usuaris
- [ ] Incidents response plan documented
- [ ] Xifratge activat en trànsit i en repòs
- [ ] HSM per a gestió de claus
- [ ] Test de restauració mensual
- [ ] Análisis de vulnerabilitats mensual
- [ ] Penetration testing annual

---

## 🎯 Objectius de Seguretat Lògica

✅ **Disponibilitat:** Els sistemes estan sempre operatius  
✅ **Integritat:** Les dades no són corrompudes ni modificades  
✅ **Confidencialitat:** Solo personal autoritzat accedeix  
✅ **Autenticitat:** Verificar identitat d'usuaris i sistemes  
✅ **No repudi:** Usuari no pot negar les seves accions  

---

*Última actualització: 2026-08-26*



