
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

```
Requisits mínims:
✓ Longitud: 12+ caràcters
✓ Majúscules: Almenys 1 (A-Z)
✓ Minúscules: Almenys 1 (a-z)
✓ Números: Almenys 1 (0-9)
✓ Símbol especial: Almenys 1 (!@#$%)
✗ No reutilitzar últimes 5 contrasenyes
✗ No incloure nom d'usuari o data
```

**Exemple de contrasenya forta:**
- ❌ `Password123`
- ❌ `Admin2024`
- ✅ `Tr0pic@lSun$2026!Sec`

#### Autenticació Multifactor (MFA/2FA)

```
✓ Factor 1: Algo que saps (contrasenya)
✓ Factor 2: Algo que tens (telèfon, targeta)
✓ Factor 3: Algo que ets (biometria)

Opcions:
- OTP (One-Time Password): Google Authenticator, Microsoft Authenticator
- SMS/Email: Codi rebut per text o correu
- Biometria: Empremta, reconeixement facial
- Targeta de seguretat: YubiKey, Titan
```

#### Gestió d'Identitats

```
✓ SSO (Single Sign-On): LDAP, OAuth2, SAML
✓ Directori centralitzat: Active Directory (Microsoft) o FreeIPA (Linux)
✓ Auditoria de connexions: Registre complet de logins
✓ Caducitat de contrasenyes: 90 dies máximo
✓ Bloqueig de compte: Després de 5 intents fallits (15 min)
✓ Historial de canvi: No permetre reutilització
```

---

### 2️⃣ **Control d'Accés i Permisos**

#### Models de Control d'Accés (AC)

**DAC (Discretionary Access Control)**
```
- L'usuari propietari controla els permisos
- Usuari pot compartir fitxers amb altres
- Menys segur
- Exemple: Permisos en Linux (chmod)
```

**MAC (Mandatory Access Control)**
```
- Administrador central defineix polítiques
- Usuaris no poden canviar permisos
- Molt segur però rígid
- Exemple: SELinux
```

**RBAC (Role-Based Access Control)** ← **Recomanat**
```
- Accés basat en rols
- Rols: Admin, Developer, User, Guest
- Polítiques clares per rol
- Exemple: Admin té accés a tot, User a només dades pròpies
```

**ABAC (Attribute-Based Access Control)**
```
- Accés basat en atributs (departament, horari, IP...)
- Más flexible i potent
- Exemple: "Usuaris de IT poden accedir a BD només entre 8-18h"
```

#### Principi de "Least Privilege"

```
✓ Cada usuari té SOLO l'accés necessari per a la seva feina
✓ Revisar permisos cada 3 mesos
✓ Eliminar accés quan l'usuari canvia de rol
✓ Registrar tots els canvis de permisos

Exemple:
- Developer de web: Accés a BD de producció? ❌ NO
- DBA: Accés a còpies de seguretat? ✅ SÍ
- HR: Accés a salaris? ✅ SÍ, però solo dels seus empleats
```

#### Separació de Funcions

```
✓ Nessun usuari pot crear I aprovar una transacció
✓ Desenvolupador no pot fer deploy a producció
✓ Comptable no pot crear ni pagar factures solo
✓ Admin no pot revisar els seus propis logs

Objectiu: Prevé fraude i errors
```

---

### 3️⃣ **Protecció Perimetral (Network)**

#### Firewall (Tallafocs)

```
✓ Corporatiu: Gateway a l'entrada de la xarxa
✓ Personal: Cada ordinador té el seu
✓ Regles ingress: Quins ports permetre
✓ Regles egress: Quin tràfic cap a fora
✓ Logging: Totes les connexions registrades

Ports comuns:
- 22: SSH (accés remot)
- 80: HTTP (web no segur)
- 443: HTTPS (web segur) ← PERMETRE
- 3306: MySQL (BD)
- 5432: PostgreSQL (BD)
```

**Exemple de regla:**
```
Ingress: Permetre port 443 desde qualsevol
Egress: Permetre solo port 443 i 53 (DNS)
Bloc: Port 22 desde internet
```

#### IDS/IPS (Intrusion Detection/Prevention Systems)

```
IDS (Detection):
- Monitora tràfic
- Detecta patrons d'atac
- Llança alerta
- Exemple: Snort, Suricata

IPS (Prevention):
- Igual que IDS
- + Bloqueja automàticament tràfic maliciós
- + Abandona connexió
```

#### DLP (Data Loss Prevention)

```
✓ Prevé exfiltració de dades sensibles
✓ Bloqueja enviament de:
  - Números de tarjeta de crèdit
  - Números de seguridad social
  - Contrasenyes
  - Dades de clients

✓ Monitora:
  - Correus electrònics
  - Transferencies de fitxers
  - Impressió
  - USB
```

#### WAF (Web Application Firewall)

```
✓ Protegeix aplicacions web
✓ Bloqueja atacs específics:
  - SQL Injection
  - XSS (Cross-Site Scripting)
  - CSRF (Cross-Site Request Forgery)
  - File Upload
  - Padding Oracle
```

---

### 4️⃣ **Protecció del Client (Endpoints)**

#### Antivirus i Antimalware

```
Funcions:
✓ Exploració en temps real
✓ Quarantine de fitxers sospitosos
✓ Actualizaciones automàtiques de definicions
✓ Scan complert semanal
✓ Alertes d'infeccions

Recomendacions:
- Microsoft Defender (Windows)
- ClamAV (Linux)
- Sophos, Norton, Kaspersky (Corporatiu)
```

#### EDR (Endpoint Detection & Response)

```
✓ Telemetria contínua de tots els endpoints
✓ Detecta comportaments anòmals
✓ Response automàtica a incidents
✓ Aïllament de sistema infectat
✓ Análisis forense posterior

Exemples: CrowdStrike, Defender for Endpoint
```

#### Personal Firewall

```
✓ Cada PC/portàtil ha de tenir firewall
✓ Regles per aplicació
✓ Notificacions quan app intenta accedir a xarxa
✓ Bloqueig de connexions desconegudes
```

#### Bloqueig de Software No Autoritzat

```
✓ MDM (Mobile Device Management)
✓ AppLocker (Windows)
✓ SELinux (Linux)
✓ Whitelisting d'aplicacions
✓ Prohibir instal·lació sense permís
```

#### Actualizacions i Patches

```
Política de patchig aggressiva:
- Crítics: 24-48 hores
- Important: 7 dies
- Moderats: 30 dies
- Baixos: 60 dies

✓ Test previ a producció
✓ Rollback plan
✓ Finestres de manteniment planificades
✓ Notificació als usuaris
```

---

### 5️⃣ **Xifratge de Dades**

#### Xifratge en Trànsit (Transit Encryption)

```
✓ TLS 1.3+ (Protocol criptogràfic)
✓ HTTPS per a web
✓ SSH per a accés remot
✓ Certificats SSL/TLS vàlids
✓ HSTS (obliga HTTPS)
✓ VPN per a connexions públiques

Algoritmes:
- AES-256 (Estàndard)
- ChaCha20-Poly1305 (Modern)
```

#### Xifratge en Repòs (Rest Encryption)

```
✓ Full Disk Encryption:
  - BitLocker (Windows)
  - FileVault (macOS)
  - LUKS (Linux)

✓ Xifratge de bases de dades:
  - TDE (Transparent Data Encryption) en SQL Server
  - Xifratge de taules en MySQL

✓ Xifratge de fitxers:
  - VeraCrypt
  - 7-Zip amb contrasenya
  - PGP

✓ Xifratge de còpies de seguretat:
  - AES-256 en almacenament
```

#### Gestió de Claus Criptogràfiques

```
✓ HSM (Hardware Security Module): Gestionador de claus
✓ Claus mai en clar
✓ Rotació de claus cada 90 dies
✓ Backup de claus en bóveda
✓ Accés restringit a claus
✓ Audit de totes les operacions
```

---

### 6️⃣ **Còpies de Seguretat i Recuperació**

#### Estratègia 3-2-1

```
📋 3 còpies de dades
   - Original
   - Còpia 1 (nearline)
   - Còpia 2 (offline)

💿 2 medis de almacenament diferentes
   - Disc dur + Tape
   - SSD + Disc dur

🌍 1 còpia fora del lloc (offsite)
   - Física: Bóveda segura a altres ciutat
   - Cloud: AWS S3, Azure Backup
```

#### RTO/RPO

```
RTO (Recovery Time Objective): Temps máximo per recuperar
- Sistema crític: < 1 hora
- Sistema important: < 4 hores
- Sistema normal: < 24 hores

RPO (Recovery Point Objective): Pèrdua de dades acceptada
- Crític: < 15 minuts
- Important: < 1 hora
- Normal: < 1 dia
```

#### Implementació

```
✓ Backup automàtic diari
✓ Backup incremental cada hora
✓ Test de restauració mensual
✓ Almacenament segur i encriptat
✓ Replicació a cloud
✓ Versionado de dades (snapshots)
✓ RAID per a redundancia local
```

---

### 7️⃣ **Monitoratge i Auditoria (SIEM)**

#### Centralització de Logs

```
✓ SIEM (Security Information & Event Management)
✓ Recopila logs de totes les fonts:
  - Firewall
  - IDS/IPS
  - Servidors
  - Aplicacions
  - Base de dades
  - Active Directory

Exemples: Splunk, ELK Stack, Wazuh
```

#### Alertes en Temps Real

```
✓ Login fallits múltiples (> 5 en 10 min)
✓ Accés a fitxers sensibles
✓ Modificació de fitxers crítics
✓ Canvis en politiques de firewall
✓ Tentatives de privilegi escalation
✓ Tràfic anormal
✓ Malware detectat
```

#### Audit Trail Complet

```
✓ Retenció de logs: Mínim 6 mesos (legal: 1 any)
✓ Immutabilitat: Els logs no es poden borrar
✓ Autenticació: Qui va fer què i quan
✓ Cadena de custòdia: Trazabilidad total
✓ Análisis post-mortem: Reconstrucció d'incidents
```

#### Análisis d'Anomalies (ML)

```
✓ Machine Learning detecta comportaments anòmals
✓ "Baseline normal" compartibu amb activitat actual
✓ Alertes d'usuari comportant-se diferent
✓ Execució de commands sense precedents
```

---

### 8️⃣ **Seguretat d'Aplicacions**

#### Validació d'Entrada

```
❌ SQL Injection: INPUT: '; DROP TABLE users;--
✓ Validació: Solo números si es número
✓ Prepared Statements (consultes parametritzades)

❌ XSS: INPUT: <script>alert('hack')</script>
✓ Sanitització: Retirar tags HTML
✓ Encoding: < devient &lt;
```

#### Proves de Seguretat

```
SAST (Static Application Security Testing):
- Análisi del codi font
- Detecta vulnerabilitats abans de compilar
- Tools: SonarQube, Checkmarx

DAST (Dynamic Application Security Testing):
- Prova l'app en execució
- Simula atacs reals
- Tools: OWASP ZAP, Burp Suite

Penetration Testing:
- Test manual per experts
- Intenta accés no autoritzat
- Reporta vulnerabilitats reals
```

#### OWASP Top 10

```
1. Broken Access Control
2. Cryptographic Failures
3. Injection (SQL, OS)
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable Components
7. Authentication Failures
8. Data Integrity Failures
9. Logging Monitoring Failures
10. SSRF (Server-Side Request Forgery)
```

---

### 9️⃣ **Gestió de Dependencies i Vulnerabilitats**

```
✓ Software Composition Analysis (SCA)
✓ Detecta llibreries vulnerables
✓ Alertes d'actualitzacions
✓ SBOM (Software Bill of Materials)
✓ Scanig automàtic en CI/CD

Tools: Snyk, Black Duck, WhiteSource
```

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

## 📊 Comparativa: Seguretat Física vs Seguretat Lògica

| Aspecte | Seguretat Física | Seguretat Lògica |
|---------|------------------|------------------|
| **Amenaces** | Robatori, incendis, sabotatge | Malware, hacking, ransomware |
| **Protecció** | Equipaments, infraestructura | Dades, sistemes |
| **Perimitral** | Portes, murs, vigilants | Firewall, IDS/IPS |
| **Accés** | Targetes, biometria | Contrasenya, MFA |
| **Detecció** | Càmeres, alarmes | Logs, SIEM, antivirus |
| **Resposta** | Evacuació, bomberos | Bloqueig, aïllament, incident response |
| **Coste** | Alt (infraestructura) | Moderat-Alt (software+personal) |
| **Visibilitat Fallos** | Immediata | Pot demorar hores/dies |

---

## 🔄 Model Integrat: Seguretat Física + Seguretat Lògica

```
┌─────────────────────────────────────────────┐
│      SEGURETAT INTEGRAL D'INFORMACIÓ        │
├─────────────────────────────────────────────┤
│  Seguretat Física  +  Seguretat Lògica      │
├─────────────────────────────────────────────┤
│  • Control accés físic + Control accés digital
│  • Monitoratge CCTV + Monitoratge logs
│  • Protecció ambiental + Firewall
│  • SAI + Backup encriptat
│  • Personal format + Conciencia digital
└─────────────────────────────────────────────┘
```

---

## 🔐 Conclusió

> **"La seguretat és una cadena tan forta com l'anell més feble."**

Per garantir la **protecció integral** de la informació i els sistemes d'una organització, és **imprescindible**:

✅ Implementar **mesures físiques robustes**  
✅ Implementar **controles lògics avançats**  
✅ **Integrar** ambdues estratègies  
✅ **Former** el personal continuament  
✅ **Revisar** regularment els controls  
✅ **Adaptar-se** a noves amenaces  

**Una organització segura és una organització que sobreviu i prospera.**

---

## 📚 Recursos Addicionals

- [ISO 27001](https://www.iso.org/isoiec-27001-information-security-management.html) - Estàndard internacional de seguretat de la informació
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework) - Marc de seguretat dels EUA
- [CIS Controls](https://www.cisecurity.org/controls) - Controls de seguretat crítiques
- [OWASP Top 10](https://owasp.org/Top10/) - Vulnerabilitats més comunes en aplicacions web
- [NISTIR 8286](https://nvlpubs.nist.gov/nistpubs/ir/2021/NIST.IR.8286.pdf) - Auditoria de seguretat física

---

*Última actualització: 2026-08-26*
```




