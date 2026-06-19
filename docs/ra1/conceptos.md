# 📂 RA1: Seguretat Passiva

# 📖 1.1: Definició de Seguretat Informàtica

La seguretat informàtica és el conjunt de procediments, tècniques i eines destinades a protegir els sistemes informàtics i la informació que contenen davant accessos no autoritzats, danys, robatoris o alteracions.

## 🎯 Objectius de la Seguretat Informàtica

Els objectius fonamentals són garantir que la informació i els sistemes es mantinguin protegits davant d’amenaces i vulnerabilitats. Els **quatre pilars principals** són:

### 1. Confidencialitat
* **Definició:** Garantir que només les persones autoritzades poden accedir a la informació.
* **Exemple concret:** Els expedients mèdics d’un hospital només són consultables pel personal mèdic autoritzat mitjançant usuari i contrasenya.

### 2. Integritat
* **Definició:** Assegurar que la informació no sigui alterada o manipulada per persones no autoritzades i que es mantingui correcta i completa.
* **Exemple concret:** Utilitzar una suma de comprovació (**checksum**) en enviar un fitxer per Internet per assegurar que no ha estat modificat. Si algú manipula una nota d’un examen sense permís, es vulnera la integritat.

### 3. Disponibilitat
* **Definició:** Garantir que la informació i els sistemes estiguin disponibles i accessibles quan els usuaris autoritzats ho necessitin.
* **Exemple concret:** Un servidor de correu ha d'estar actiu 24/7. 

!!! danger "Amenaça Clau"
    Un atac **DDoS** (Denegació de Servei Distribuït) afecta directament a la **disponibilitat**, deixant el servei inoperatiu per als usuaris.

### 4. No repudi
* **Definició:** Assegurar que un usuari no pugui negar una acció que ha realitzat (enviament d'un missatge o transacció).
* **Exemple concret:** En un correu electrònic o document **signat digitalment**, l’emissor no pot negar de cap manera que l’ha enviat o signat.

---

## 📊 Resum dels Pilars (Tríada CIA + No Repudi)

| Objectiu | Què garanteix? | Exemple pràctic |
| :--- | :--- | :--- |
| **Confidencialitat** | Només accés autoritzat | Accés amb credencials a expedients |
| **Integritat** | Informació intacta i sense alteracions | Comprovació de *checksum* en fitxers |
| **Disponibilitat** | Accés a la informació quan calgui | Servidor de correu sempre actiu |
| **No repudi** | No poder negar una acció realitzada | Document o correu signat digitalment |
