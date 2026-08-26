# 🛡️ RA1 - Introducció a la Seguretat Informàtica i Protecció del Sistema

El **RA1** estableix les bases teòriques i pràctiques per entendre com protegir la informació i els sistemes informàtics. Aquest mòdul aborda des dels conceptes fonamentals de la seguretat fins a la implementació de mesures de protecció física (CPD, SAI) i lògica (ACLs a Linux i Windows).

---

## 📌 Índex de Continguts del RA1

Fes clic a qualsevol dels apartats per accedir a la documentació extensa i les guies pràctiques:

### 📖 1. [Conceptes Fonamentals de Seguretat](conceptos.md)
* **Descripció:** Introducció a la seguretat informàtica i els principis bàsics de la protecció de la informació.
* **Guia d'estudi:** Enfoca't en entendre la **Triada CID** (Confidencialitat, Integritat i Disponibilitat), l'autenticitat i el no-repudi, així com la diferència entre amenaça, vulnerabilitat i risc.

### 🏢 2. [Seguretat Física](seguretat-fisca-logica/seguretat-fisica.md)
* **Descripció:** Conjunt de mesures per protegir el maquinari i les instal·lacions contra amenaces naturals o humanes.
* **Guia d'estudi:** Revisa els controls d'accés físic (targetes, biometria), sistemes de protecció contra incendis, climatització i control ambiental per evitar fallades en el hardware.

### 💻 3. [Seguretat Lògica](../seguretat_logica.md)
* **Descripció:** Protecció de la informació en format digital i dels programes mitjançant eines de software.
* **Guia d'estudi:** Estudia els mecanismes de control d'accés digital, polítiques d'autenticació, xifratge de dades, utilització de tallafocs (*firewalls*) i actualitzacions del sistema.

### 🏙️ 4. [Centre de Processament de Dades (CPD)](servidors.md)
* **Descripció:** Disseny i requisits de seguretat per a les sales de servidors corporatives.
* **Guia d'estudi:** Aprèn les característiques principals d'un CPD: terra tècnic, cablatge estructurat, redundància de subministrament, canals de comunicació i zonificació de seguretat.

### 🔋 5. [Sistemes d'Alimentació Ininterrompuda (SAI / UPS)](SAI.md)
* **Descripció:** Dispositius encarregats de mantenir el subministrament elèctric quan falla la xarxa principal.
* **Guia d'estudi:** Diferencia entre els tipus de SAI (**Off-line**, **Line-interactive** i **On-line / Doble conversió**) i aprèn a calcular l'autonomia i la potència necessària (VA/Watts) per als equips.

### 🐧 6. [Llistes de Control d'Accés (ACL) a Linux](../ra3/acl.md)
* **Descripció:** Gestió avançada de permisos POSIX sobre fitxers i directoris en entorns Linux.
* **Guia d'estudi:** Domina les eines de consola `getfacl` i `setfacl`, la modificació de permisos per usuari/grup (`-m`), l'eliminació (`-x`/`-b`) i els permisos per defecte (`-d`).

### 🪟 7. [Llistes de Control d'Accés (ACL) a Windows](../ra3/acl_windows.md)
* **Descripció:** Control d'accés detallat i permisos NTFS sobre fitxers i carpetes en entorns Windows.
* **Guia d'estudi:** Revisa l'assignació de permisos des de la GUI (pestanya *Seguretat*), l'ús de la consola amb `icacls` (`/grant`, `/deny`, `/remove`), el concepte d'herència NTFS i la prioritat del *Deny* explícit.

---

## 📊 Taula Resum dels Apartats del RA1

| Apartat | Àmbit principal | Concepte clau | Documentació |
| :--- | :--- | :--- | :---: |
| **Conceptes** | Teòric | Triada CID (Confidencialitat, Integritat, Disponibilitat) | [Anar ➡️](conceptos.md) |
| **Seguretat Física** | Instal·lacions / Entorn | Protecció contra incendis, aigua i accesos | [Anar ➡️](seguretat_fisica.md) |
| **Seguretat Lògica** | Software / Dades | Control d'accés digital i xifratge | [Anar ➡️](seguretat_logica.md) |
| **CPD** | Infraestructura | Redundància, clima i terra tècnic | [Anar ➡️](cpd.md) |
| **SAI / UPS** | Energia | SAI On-line vs Line-interactive | [Anar ➡️](sai.md) |
| **ACL Linux** | Permisos de Sistema | Comandes `getfacl` i `setfacl` | [Anar ➡️](../ra3/acl.md) |
| **ACL Windows** | Permisos de Sistema | Permisos NTFS i comanda `icacls` | [Anar ➡️](../ra3/acl_windows.md) |

```
