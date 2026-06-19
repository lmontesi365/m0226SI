# 📂 RA1: Seguretat Passiva

# 📖 1.1: Definició de Seguretat Informàtica

La seguretat informàtica és el conjunt de procediments, tècniques i eines destinades a protegir els sistemes informàtics i la informació que contenen davant accessos no autoritzats, danys, robatoris o alteracions.

## 🎯 Objectius de la Seguretat Informàtica

Els objectius fonamentals són garantir que la informació i els sistemes es mantinguin protegits davant d’amenaces i vulnerabilitats. Els **quatre pilars principals** són:

### 1. Confidencialitat
* **Definició:** Garantir que només les persones autoritzades poden acceder a la informació.

??? example "🔍 Veure exemple pràctic de Confidencialitat"
    Quan un sistema requereix usuari i contrasenya per accedir a dades personals, només les persones autoritzades podran veure aquesta informació.
    
    * **Exemple concret:** Els expedients mèdics d’un hospital només són consultables pel personal mèdic autoritzat.

### 2. Integritat
* **Definició:** Assegurar que la informació no sigui alterada o manipulada per persones no autoritzades i que es mantingui correcta i completa.

??? example "🔍 Veure exemple pràctic d'Integritat"
    Quan enviem un fitxer a través d’Internet, s’utilitza una suma de comprovació (*checksum*) per assegurar que el fitxer no ha estat modificat durant la transmissió.
    
    * **Exemple concret:** Si algú manipula una nota en un sistema d’avaluació escolar sense permís, s’està vulnerant la integritat.

### 3. Disponibilitat
* **Definició:** Garantir que la informació i els sistemes estiguin disponibles i accessibles quan els usuaris autoritzats ho necessitin.

??? example "🔍 Veure exemple pràctic de Disponibilitat"
    Un servidor de correu electrònic ha d’estar en funcionament perquè els usuaris puguin enviar i rebre missatges sempre que ho requereixin.

!!! danger "Amenaça Clau (DDoS)"
    Un atac **DDoS** (Denegació de Servei Distribuït) afecta directament a la **disponibilitat**, deixant un servei totalment inoperatiu per als usuaris.

### 4. No repudi
* **Definició:** Assegurar que un usuari no pugui negar una acció que ha realitzat, com ara l’enviament d’un missatge o una transacció.

??? example "🔍 Veure exemple pràctic de No Repudi"
    Quan es signa digitalment un document, el signant no pot negar que ha realitzat aquella signatura.
    
    * **Exemple concret:** En un correu electrònic signat digitalment, l’emissor no pot negar de cap manera que l’ha enviat.

---

## 📊 Resum dels Pilars (Tríada CIA + No Repudi)

| Objectiu | Què garanteix? | Exemple pràctic |
| :--- | :--- | :--- |
| **Confidencialitat** | Només accés autoritzat | Accés amb contrasenya a expedients mèdics |
| **Integritat** | Informació intacta i sense alteracions | Comprovació de *checksum* en fitxers |
| **Disponibilitat** | Accés a la informació quan calgui | Servidor de correu sempre actiu |
| **No repudi** | No poder negar una acció realitzada | Document signat digitalment |
