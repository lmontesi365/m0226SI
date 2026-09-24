# 🔋 Sistema d'Alimentació Ininterrompuda (SAI / UPS)

## 📌 Què és un SAI i per a què servei?

Un **SAI** (*Sistema d'Alimentació Ininterrompuda*), en anglès **UPS** (*Uninterruptible Power Supply*), és un dispositiu de **seguretat passiva física** que es connecta entre la xarxa elèctrica i els equips informàtics. Conté bateries internes capaços de subministrar energia de forma immediata quan falla el corrent principal.

### Funcions principals:
1. **Evitar l'apagat brusc:** Manté els equips funcionant durant un tall de llum perquè els usuaris o sistemes puguin desar la feina i tancar de forma segura.
2. **Filtratge del senyal elèctric:** Protegeix el maquinari contra picos de tensió, sobretensions, microtallats i soroll elèctric que podrien fer malbé les fonts d'alimentació.
3. **Mantenir la continuïtat del servei:** En entorns de servidors (CPD), dona temps a que s'engeguin els grups electrògens (generadors de dièsel) sense que els servidors es reiniciïn.

---

## 🧮 Com es calcula la potència necessària d'un SAI?

Per triar el SAI adequat cal calcular la **potència aparent**, expressada en **Volt-Ampères (VA)**.

### Fórmula fonamental:
$$\text{Potència Aparent (VA)} = \frac{\text{Potència Real (Wats)}}{\text{Factor de Potència (FP)}}$$

* **Potència Real (W):** La suma del consum elèctric de tots els dispositius que connectarem al SAI.
* **Factor de Potència (FP):** Eficiència del SAI. Sol variar entre **0.7** (SAIs bàsics) i **0.9 - 1.0** (SAIs professionals d'alta eficiència).
* **Marge de seguretat:** Es recomana **afegir un 20% - 30% addicional** a la potència obtinguda per evitar que el SAI funcioni al 100% de la seva capacitat i permetre futures ampliacions.

---

<Carousel>
  <Image src="image_agent_tag_16571883388794755307" alt="SAI en format torre" caption="SAI tipus torre per a llocs de treball o petits servidors" />
  <Image src="image_agent_tag_16571883388794755880" alt="SAI en format Rack 19 polzades" caption="SAI tipus Rack per instal·lar en armaris de servidors CPD" />
</Carousel>

---

## 📝 Exemples Pràctics de Càlcul

### 🏢 Exemple 1: SAI en format Torre (Puesto de treball / Petit servidor)

**Escenari:** Volem protegir un servidor de fitxers en format torre i el seu encaminador (router) en una petita oficina.

* **Dispositius a connectar:**
  * 1 Servidor Torre: **350 W**
  * 1 Router / Switch: **30 W**
  * 1 Monitor LED: **20 W**
* **Dades tècniques del SAI:** Factor de potència ($\text{FP}$) = **0.7**

#### Passos del càlcul:
1. **Calcular la potència total en Wats:**
   $$\text{Wats totals} = 350\text{ W} + 30\text{ W} + 20\text{ W} = 400\text{ W}$$

2. **Convertir Wats a Volt-Ampères (VA):**
   $$\text{VA teòrics} = \frac{400\text{ W}}{0.7} \approx 571.43\text{ VA}$$

3. **Aplicar el marge de seguretat del 25% ($\times 1.25$):**
   $$\text{VA recomanats} = 571.43 \times 1.25 = 714.28\text{ VA}$$

> **Elecció comercial:** Es triarà un SAI en format Torre d'almenys **800 VA** o **1000 VA** per garantir una bona autonomia.

---

### 🗄️ Exemple 2: SAI en format Rack (Armari CPD / Servidors)

**Escenari:** Protecció d'un armari Rack de 19 polzades en un CPD que conté diversos servidors de processament.

* **Dispositius a connectar:**
  * 2 Servidors Rack 2U: $2 \times 500\text{ W} = 1000\text{ W}$
  * 1 Switch d'alta velocitat (PoE): **150 W**
  * 1 Sistema d'emmagatzematge NAS: **250 W**
* **Dades tècniques del SAI:** Format Rack 2U amb Factor de potència ($\text{FP}$) = **0.9** (Línia On-Line)

#### Passos del càlcul:
1. **Calcular la potència total en Wats:**
   $$\text{Wats totals} = 1000\text{ W} + 150\text{ W} + 250\text{ W} = 1400\text{ W}$$

2. **Convertir Wats a Volt-Ampères (VA):**
   $$\text{VA teòrics} = \frac{1400\text{ W}}{0.9} \approx 1555.55\text{ VA}$$

3. **Aplicar el marge de seguretat del 30% ($\times 1.30$):**
   $$\text{VA recomanats} = 1555.55 \times 1.30 = 2022.21\text{ VA}$$

> **Elecció comercial:** Es triarà un SAI de format **Rack 19" (ex. 2U o 3U)** d'almenys **2200 VA** o **3000 VA** (*On-Line Double Conversion*).
