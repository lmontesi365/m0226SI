# 🛡️ Seguretat Informàtica: Activa, Passiva, Física i Lògica

Per protegir un sistema informàtic cal aplicar diferents tipus de mesures segons **quan s'activen** (abans o després de l'atac) i **on s'apliquen** (en el món real o en el programari).

---

## 1. Seguretat Activa (Prevenció)

La **seguretat activa** és el conjunt de mesures que s'encarreguen de **prevenir, evitar o bloquejar** que es produeixi un incident de seguretat o un atac informàtic. El seu objectiu és que l'amenaça mai arribi a tenir èxit.

### Exemples de Seguretat Activa:
* **Antivirus i Tallafocs (Firewall):** Cerca programari maliciós en temps real i bloqueja connexions no autoritzades.
* **Control d'accés (Contrasenyes i Biometria):** Impedeix que persones no autoritzades entrin als sistemes o a les instal·lacions.
* **Actualitzacions de seguretat:** Corregixen vulnerabilitats del sistema abans que un atacant les pugui aprofitar.
* **Xifratge de dades:** Fa que la informació sigui il·legible si algú la intercepteix.

---

## 2. Seguretat Passiva (Recuperació)

La **seguretat passiva** entra en acció quan la seguretat activa ha fallat o quan es produeix un desastre inevitable (com un atac de *Ransomware*, una avaria o un incendi). El seu objectiu és **minimitzar els danys i recuperar el sistema** el més ràpid possible.

### Exemples de Seguretat Passiva:
* **Còpies de seguretat (Backups):** Permeten restaurar la informació si els discs originals es fan malbé o es xifren.
* **Sistemes d'Alimentació Ininterrompuda (SAI / UPS):** Bateries que mantenen els equips encesos quan marxa la llum per evitar que s'apaguin bruscament.
* **Sistemes d'extinció d'incendis:** Apaguen el foc per reduir la pèrdua d'equips físics.
* **Pla de Recuperació de Desastres (DRP):** Document amb els passos a seguir per tornar a posar l'empresa en marxa després d'un incident greu.

---

<Image src="image_agent_tag_21122399785327417" alt="Esquema d'infraestructura de seguretat informàtica" caption="Arquitectura de seguretat amb protecció física i lògica" />

---

## 3. Integració: Seguretat Física i Lògica

Tant la seguretat **activa** com la **passiva** es divideixen en dues àrees segons el mitjà on s'apliquen:

* **Seguretat Física:** Protegeix els elements materials, el maquinari i les instal·lacions (equips, sales, cables, servidors).
* **Seguretat Lògica:** Protegeix la informació, els programes, els sistemes operatius i la xarxa.

### 📊 Matriu Resum de Combinacions

Així és com es combinen aquests 4 conceptes a la pràctica:

| | Seguretat Activa (Evitar l'atac) | Seguretat Passiva (Reduir el dany) |
|---|---|---|
| **Seguretat Física**<br>*(Món material / Maquinari)* | **Evita danys físics:**<br>• Lector de fingerprint a la porta del CPD.<br>• Murs ignífugs i detectors de fums.<br>• Climatització per evitar sobreescalfament. | **Optimitza la recuperació física:**<br>• SAI / UPS (bateries) en anar-se'n la llum.<br>• Extintors automàtics de gas (no aigua).<br>• Ubicació del CPD en plantes elevades (anti-inundació). |
| **Seguretat Lògica**<br>*(Programari / Dades)* | **Evita atacs informàtics:**<br>• Tallafocs (Firewall) i Antivirus.<br>• Autenticació Multifactor (MFA).<br>• Permisos d'accés (ACLs) a fitxers. | **Optimitza la recuperació de dades:**<br>• Còpies de seguretat (Backups).<br>• Punts de restauració / *Snapshots*.<br>• Discs en RAID (redundància de dades). |
