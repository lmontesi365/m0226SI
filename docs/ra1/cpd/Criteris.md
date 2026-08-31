---

# 🏢 Criteris de Disseny i Ubicació per a la Sala de Servidors (CPD)

---

## 1. Elecció de l’Edifici i la Zona Geogràfica

* **Evitar zones de risc natural:** No ubicar la sala en àrees propenses a inundacions (rius, planes al·luvials), terratrèmols, huracans o qualsevol desastre natural recurrent a la regió.
* **Seguretat de l’entorn:** Prioritzar edificis en zones amb baixos índexs de criminalitat per reduir el risc de robatoris o vandalisme.
* **Proximitat a riscos externs:** Allunyar-se d’instal·lacions perilloses (benzineres, fàbriques químiques, magatzems de combustibles, zones industrials amb risc d’explosió o incendi).
* **Accés a subministraments:** Escollir ubicacions amb accés fiable a electricitat, preferiblement amb redundància des de més d’una subestació. Verificar bona cobertura de proveïdors d’internet d’alta velocitat (fibra òptica amb rutes d'entrada redactades/diverses).
* **Accessibilitat per al personal autoritzat:** Ha d’estar disponible les 24/7 per a tècnics i serveis d’emergència (bombers, policia).

---

## 2. Ubicació Dins del Mateix Edifici

* **Evitar plantes crítiques:**
* **Soterranis i plantes baixes:** Risc d’inundació per pluges, riades o trencament de canonades generals, així com major humitat ambiental.
* **Últimes plantes:** Risc de filtracions d'aigua per la coberta/teulada i major càrrega tèrmica solar directament sobre el sostre.
* **Planta recomanada:** Plantes intermèdies (ex. 2a o 3a planta segons l'edifici).


* **Ubicació discreta:**
* Sala interior, **sense finestres** a l’exterior per evitar radiació solar directa i punts de vulnerabilitat d'intrusió.
* Allunyada de zones d'alt trànsit com recepcions, cafeteries, lavabos i passadissos principals.
* **Sense senyalització evident:** No rotular com a “Sala de Servidors” o “CPD” → usar identificadors neutres (ex. *Sala Tècnica 2.04*).


* **Accés logístic i de càrrega:**
* Si els equips són molt pesats (racks de gran densitat, SAI/UPS, bateries), la sala ha de tenir accés directe mitjançant un muntacàrregues o ascensor d'alta capacitat de càrrega des del moll de descàrrega.
* Les portes d'accés han de tenir una amplada i alçada suficients (mínim 1,20 m d'amplada per 2,10 m d'alçada).


* **Allunyada de fonts de perill intern:**
* **Vibracions:** Evitar la proximitat immediata a motors d'ascensors, molls de càrrega, sales de calderes o maquinària pesada.
* **Aigua i desaigües:** No col·locar mai sota lavabos, cuines, terrasses o canonades de distribució d'aigua general.
* **Interferències electromagnètiques (EMI):** Lluny de transformadors d'alta tensió, antenes de radiocomunicació, quadres elèctrics generals o motors elèctrics de gran mida.


* **Consideracions estructurals:**
* **Capacitat de càrrega del sòl (forjat):** El sòl ha de suportar el pes concentrat dels racks, SAI/UPS i equips de Climatització (mínim recomanat: 750 a 1.000 kg/m²).
* **Alçada lliure suficient:** Alçada mínima de 2,80 a 3,00 metres per permetre la instal·lació de sòl tècnic (30-50 cm), cablejat superior/safates, conductes de climatització i garantir un flux d’aire adequat.



---

## 3. Climatització i Control Ambiental

La climatització en una sala de servidors no cerca el confort humà, sinó mantenir l'equipament dins dels marges operatius de temperatura i humitat recomanats per l'estàndard **ASHRAE**.

```
  [ Unitat CRAC / CRAH ] ──► (Aire Fred sota Sòl Tècnic) ──► [ Passadís Fred ] ──► [ Racks ]
                                                                                   │
  [ Retorn d'Aire Calent ] ◄──────────────────────────────── [ Passadís Calent ] ◄──┘

```

* **Gestió del Flux d'Aire (Passadissos Freds i Calents):**
* **Arquitectura de passadissos:** Disposició dels racks cara a cara (fronts enfrontats absorbint aire fred) i esquena amb esquena (expulsant aire calent).
* **Confinament de passadís:** Confinar el passadís fred (o el calent) amb estructures de metacrilat/portes per evitar que l'aire fred es barregi amb el calent, millorant l'eficiència energètica fins a un 30%.


* **Paràmetres Ambientals Recomanats (ASHRAE):**
* **Temperatura d'entrada als equips:** Entre **18 °C i 27 °C** (idealment al voltant de 22 °C).
* **Humitat relativa:** Entre el **40% i el 60%**.
* *Humitat baixa (< 30%):* Incrementa el risc d'descàrregues electroostàtiques (ESD).
* *Humitat alta (> 60%):* Risc de condensació i corrosió en components electrònics.




* **Equips de Climatització de Precisió (CRAC / CRAH):**
* Utilitzar unitats de climatització de precisió dissenyades per a funcionament continu **24/7/365**, capaces de controlar tant la temperatura com la humitat de manera exacta.
* **Redundància N+1 o 2N:** Garantir que si una unitat de climatització falla o entra en manteniment, les restants puguin refredar el 100% de la càrrega tèrmica de la sala.


* **Sòl Tècnic Elevat (*Raised Floor*):**
* Instal·lació de rajoles sobre estructures metàl·liques a una alçada de 30 a 50 cm.
* Ús del buit del sòl tècnic (*plenum*) per a la distribució de l'aire fred impulsat des dels equips de climatització cap a les rajoles perforades del passadís fred.



---

## 4. Detecció i Extinció d'Incendis

El sistema de protecció contra incendis en un CPD ha de protegir els equips electrònics sense fer servir aigua (ja que l'aigua destruiria els equips i podria provocar curtcircuits).

* **Sistemes de Detecció Precoç (VESDA):**
* **Detecció per Aspiració d'Aire (VESDA):** Sistema que mostra l'aire de la sala de forma contínua a través d'una xarxa de tubs perforats, capaç de detectar micro-partícules de fum abans que sigui visible la flama (*fase incipient del foc*).
* detectors de fum i calor puntuals (en sostre i sota el sòl tècnic) com a sistema secundari de confirmació per creuament de senyals.


* **Sistemes d'Extinció per Gas d'Agents Nets:**
* **Gasos Inerts (IG-55, IG-541, Nitrogen):** Redueixen el percentatge d'oxigen a la sala per sota del nivell que manté la combustió (del 21% a l'12-14%), essent totalment segurs per a l'electrònica i sense residus.
* **Sistemes de Gas Químic (Novec 1230 / FK-5-1-12, ECARO-25):** Actuen per absorció tèrmica, no deixen residus i permeten una extinció en menys de 10 segons sense danyar la capa d'ozó.


* **Estructures i Resistència al Foc:**
* **Murs i portes RF-120 / REI 120:** Tota l'estructura de la sala ha de resistir el foc durant almenys 120 minuts.
* **Portes ignífugues i d'obertura cap a l'exterior:** Amb barra antipànic i tancament automàtic.
* **Segellat de passos de cables (*Firestop*):** Tots els passos de canonades i cablejat a través de les parets o sostres han de ser segellats amb materials intumescents resistents al foc.


* **Integració amb el Sistema Elèctric (Disparador EPO):**
* En activar-se l'extinció per gas, el sistema ha de tallar automàticament la climatització (per evitar extreure el gas) i desconnectar el subministrament elèctric dels racks mitjançant el botó d'Aturada d'Emergència (*EPO - Emergency Power Off*).



---

## 🧪 Pràctica: Selecció de la Millor Ubicació sobre Plànols

### 🎯 Objectiu

Analitzar el plànol d'un edifici corporatiu de 4 plantes i seleccionar l'espai idoni per ubicar-hi la nova Sala de Servidors aplicant la metodologia de descarte i matriu de valoració.

---

### 📋 Pas 1: Anàlisi i Descarte d'Espais als Plànols

Davant d'un plànol d'edifici, realitza els descartes en el següent ordre:

1. **Descarte de Plantes Extremes:**
* Marca en **roig** la Planta Baixa, Soterranis i l'Última Planta.
* *Filtre:* Resten només les plantes intermèdies (ex. Planta 2a).


2. **Descarte de Zones Perimetrals i Humides:**
* Talla les sales que tinguin parets exteriors amb finestres.
* Elimina sales contigües o situades directament a sota de: lavabos, cuines/oficines, sales de calderes o terrasses.


3. **Descarte per Riscos Electromagnètics i Vibracions:**
* Elimina sales contigües als buits dels ascensors, cambres de motors o la sala del quadre elèctric general de l'edifici.


4. **Validació d'Accessibilitat Logística:**
* Comprova des del plànol que des del moll de descàrrega hi ha un recorregut directe via muntacàrregues fins a la sala seleccionada sense escales ni passos estrets.



---

### 📊 Pas 2: Matriu d'Avaluació de Candidats (Exemple d'Exercici)

Suposem que al plànol de la **Planta 2** queden 3 sales candidates: **Sala A**, **Sala B** i **Sala C**. Avalua cada criteri de 1 a 5 punts:

| Criteri | Sala A (Façana Est) | Sala B (Interior, costat lavabos) | Sala C (Central Interior) |
| --- | --- | --- | --- |
| **Sense finestres a l'exterior** | ❌ 1 pt (Té finestres) | 🟢 5 pts | 🟢 5 pts |
| **Distància a xarxes d'aigua/lavabos** | 🟢 5 pts | ❌ 1 pt (Lavabo a sobre) | 🟢 5 pts |
| **Accés a muntacàrregues** | 🟡 3 pts | 🟢 5 pts | 🟢 4 pts |
| **Absència de canonades/grans estructures** | 🟢 4 pts | 🟡 2 pts | 🟢 5 pts |
| **Resistència del forjat / Càrrega** | 🟢 4 pts | 🟢 4 pts | 🟢 5 pts |
| **PUNTUACIÓ TOTAL** | **17 pts** | **17 pts** | **24 pts (GUANYADORA)** |

> **Resultat de la pràctica:** La **Sala C** és la ubicació ideal segons el plànol, ja que compleix el criteri de sala central interior, lliure de filtracions d'aigua, sense exposició solar directa i amb bona accessibilitat de càrrega.

---
