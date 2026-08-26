
# Centre de Processament de Dades (CPD) - Criteris d'Ubicació i Disseny

## Introducció-Nou!!

Un Centre de Processament de Dades (CPD) o Data Center és la instal·lació física que allotja els servidors, dispositius de xarxa i sistemes de suport necessaris per a l'operació de sistemes informàtics. Ubicar-lo adequadament és crític per garantir disponibilitat, seguretat i rendiment.

---

## 📍 Part 1: Elecció de l'Edifici i la Zona Geogràfica

### 1.1 Evitar Zones de Risc Natural

**Problemes:**

- **Inundacions**: Zones prop de rius, plans al·luvials, àrees baixes
- **Terratrèmols**: Regions sismicament actives
- **Huracans/Tempestes**: Zones costaneres amb risc de vents violents
- **Nevades extremes**: Zones de muntanya amb risc d'allissos

**Recomanacions:**

- 📊 Estudiar l'historial meteorològic dels últims 20-30 anys
- 🗺️ Consultar mapes de riscos naturals de l'Agència de Protecció Civil
- 📋 Verificar plans urbanístics per assegurar que la zona no serà inundable
- 🏘️ Evitar zones de construcció recent (sòl potencialment inestable)

### 1.2 Seguretat de l'Entorn (Criminalitat)

**Problemes:**

- **Robatoris** de dispositius i equipament
- **Vandalisme** i sabotatge
- **Intents de trencament** de la seguretat

**Recomanacions:**

- 📊 Investigar índexs de criminalitat del barri
- 👮 Proximitat a commissaria de policia (idealment < 5 km)
- 🏢 Zona amb presència empresarial
- 🚔 Patrulles de seguretat a la zona

### 1.3 Proximitat a Instal·lacions Perilloses

**Amenaces Externes:**

| Instal·lació | Risc | Distancia Mínima |
|:---|:---|:---|
| Benzineres | Explosió, incendi | > 500 m |
| Fàbriques químiques | Toxicitat, explosió | > 1 km |
| Magatzems combustibles | Incendi, explosió | > 1 km |
| Zones industrials | Vibració, contaminació | > 500 m |
| Aeroports | Crash aeri | > 10 km |
| Línies ferroviàries | Vibració | > 300 m |
| Centrals elèctriques | Radiació, EMF | > 500 m |

**Recomanacions:**

- 📍 Ubicar en zona comercial o residencial tranquila
- 🗺️ Consultar plànols urbans per identificar instal·lacions properes
- 📞 Contactar amb autoritats per confirmar seguretat

### 1.4 Accés a Subministraments Crítics

#### Electricitat

- **Redundancia**: Connexió a múltiples subestacions elèctriques
- **Tensió**: Verificar estabilitat de voltatge
- **Capacitat**: Suministre suficient per a demanda actual + creixement
- **Qualitat**: Baixa taxa de talls (< 99.5% interrupcions anuals)

#### Internet

- **Múltiples operadores** (fibra òptica òptim)
- **Ample de banda**: > 1 Gbps (recomendable 10 Gbps)
- **SLA**: 99.9% mínim de disponibilitat garantida
- **Cobertura**: Diversos proveïdors

#### Aigua

- **Accés fiable** a abasteciment d'aigua
- **Qualitat**: Baixa salinitat
- **Pressió**: > 2 bar

### 1.5 Accessibilitat per al Personal i Emergències

**Requisits 24/7:**

- ✅ Accés les 24 hores del dia, 7 dies per setmana
- ✅ Tècnics TI disponibles en < 30 minuts
- ✅ Accés immediat per a bombers i policia
- ✅ Via d'accés sense peatges ni restriccions
- ✅ Aparcament per a vehicles d'emergència

**Infraestructura:**

- 🚗 Carreteres principals properes
- 🚌 Accés a transports públics
- ⛽ Serveis propers (gasolinera, etc.)

---

## 🏢 Part 2: Ubicació dins del Mateix Edifici

### 2.1 Planta on Ubicar la Sala

#### ❌ Plantes a Evitar

**Soterranis:**

- 💧 Alt risc d'inundació
- 💨 Acumulació de humitat
- 🦊 Accés més fàcil de vulnerar
- 🚪 Menys sortides d'emergència

**Plantes Baixes:**

- 💧 Inundacions per aiguals
- 🏃 Accessibilitat a vianants
- 🚪 Portes exposades al carrer

**Últimes Plantes:**

- 💧 Filtracions d'aigua de pluja
- ☀️ Escalfor excessiva (> 35ºC)
- 🌪️ Major exposició a vents

#### ✅ Plantes Recomanades

- **Plantes intermedies** (2a a 5a planta)
- Allunyades de cobertes i base
- Equilibri entre seguretat i accessibilitat

### 2.2 Ubicació dins del Pis (Interior vs Exterior)

#### Sala Interior (RECOMANAT ✅)

**Avantatges:**

- Sense finestres externes
- Menor risc d'accés
- Millor aïllament tèrmic
- Menor humitat de l'exterior

**Ubicació ideal:**

- Al centre del pis
- Allunyada de façanes externes
- Enrevolada d'altres espais

#### Sala Exterior (EVITAR ❌)

- Finestres = risc d'accés
- Variacions extremes de temperatura
- Major evaporació
- Visible des del carrer

### 2.3 Discreció i Ocultació

#### Signalització

- ❌ NO marcar com a "Sala de Servidors"
- ✅ Noms neutres: "Sala Tècnica 01", "Magatzem"
- ✅ Porta sense vidre transparent
- ✅ Sense indicadors visuals de valor

#### Ubicació Estratègica

- 🚫 NO pròxim a recepcions
- 🚫 NO adjacent a cafeteries
- 🚫 NO al costat de passadissos principals
- ✅ Allunyada de flux de personal
- ✅ Accés restringit addicional si possible

### 2.4 Accés per Trasllat de Material Pesant

**Problema**: Servidors, racks i UPS pesen 200-500 kg

**Solucions:**

- 📦 Ascensor gran (mínim 2000 kg capacitat)
- 🚪 Portes d'ascensor > 1.2m d'ample
- 📍 Muntacàrregues disponible
- 🛤️ Passadissos amples per maniobra
- 🪜 Porta de sala suficientment gran
- 🔄 Corbes amples en passadissos

### 2.5 Allunyament de Fonts de Perill Interior

#### 🔊 Vibracions

**Problemes:**

- Dany en components electrònics
- Fallos en discs durs
- Desajustament de connexions

**Evitar proximitat a:**

- 🛗 Ascensors
- 📦 Molls de càrrega
- ⚙️ Maquinària de climatització
- 🔩 Compressors d'aire comprimit

**Distancia mínima**: > 10 metres

#### 💧 Aigua i Fuites

**Problemes:**

- Electrocució del personal
- Corrosió de components
- Fallos en cascada de servidors

**Evitar proximitat a:**

- 🚰 Lavabos i banys
- 🍳 Cuines i sales de menjar
- 🔌 Canonades verticals
- 🪟 Finestres en dies plujosos

**Recomanacions:**

- NO col·locar servidors sota canonades
- Inspecció regular per humitat
- Sistema de detecció de fuites

#### ⚡ Interferències Electromagnètiques

**Problemes:**

- Corrupció de dades
- Falsos errors de xarxa
- Interferència en senyals

**Evitar proximitat a:**

- 🔌 Transformadors elèctrics
- 📡 Antenes de comunicació
- ⚙️ Motors elèctrics grans (>3 kW)
- 🔆 Línies d'alta tensió

**Distancia mínima**: > 5-10 metres

### 2.6 Consideracions Estructurals de l'Edifici

#### 🏗️ Capacitat de Càrrega del Sòl

**Problema**: Servidors concentrats en poc espai

**Càlculs aproximats:**

- Rack de servidors: 200-400 kg
- SAI/UPS: 100-300 kg
- Climatització: 50-200 kg
- Cablejat i altres: 50-100 kg
- **TOTAL**: 500-1000 kg en ~20 m²

**Recomanacions:**

- 📊 Verificar càrrega admissible del sòl (500-1000 kg/m²)
- 🔍 Inspecció estructural per enginyer
- 🦶 Distribució uniforme de racks
- 🛠️ Sòl tècnic elevat (millor distribució)

#### 📏 Alçada Suficient de la Sala

**Espai necessari:**

- Racks: 2-2.5 metres
- Sòl tècnic: 30-60 cm
- Climatització superior: 20-30 cm
- Cablejat en braguetes: 30-50 cm
- **ALTURA MÍNIMA**: 3.5 metres

**Beneficis:**

- ✅ Millor circulació d'aire calent
- ✅ Espai per cablejat
- ✅ Flexibilitat per futurs upgrades
- ✅ Millor ventilació

#### 🌡️ Aïllament Tèrmic

- Parets i sostre ben aïllats
- Porta aïllada (no metàl·lica)
- Sense fuites d'aire
- Sellar forats per canonades i cables

---

## 🔧 Part 3: Infraestructura Tècnica de la Sala

### 3.1 Sistemes de Climatització

| Aspecte | Especificació |
|:---|:---|
| **Temperatura** | 18-27 ºC (idealment 20-24 ºC) |
| **Humitat relativa** | 40-55% (idealment 45-50%) |
| **Canvis/hora** | < 5 ºC |
| **Redundancia** | Mínim 2 sistemes |
| **Monitorització** | Sensors continus amb alarma |

**Tipus:**

- 🌀 AC de precisió: Refrigeració distribuïda uniforme
- 🚀 Ventilació en cambra fria: Sòl tècnic amb aire fred
- 🧊 Evaporadors: Per espais petits

### 3.2 Protecció contra Incendis

- 🚨 Detectores de fums automàtiques
- 🧯 Sistemes d'extinció amb gas inert
- 💨 Detecció de fums incident
- 🚪 Compuertes tallafocs automàtiques
- 📋 Pla d'evacuació clar

### 3.3 Control d'Accés

- 🔑 Acceso per tarjeta o biometria
- 📹 Càmera de seguretat a la porta
- 📊 Registre de tots els accessos
- 🔔 Alarma sense autorització

### 3.4 SAI/UPS (Alimentació Ininterrompuda)

- ⏱️ Autonomia mínima: 10-15 minuts
- 🔌 Connectat a sistemes crítics
- 📈 Capacitat proporcional a demanda
- 🔄 Prova mensual de transferència

---

## 📋 Checklist de Verificació per a CPD

### ✓ Ubicació Geogràfica

- [ ] Zona sense desastres naturals
- [ ] Baixa criminalitat documentada
- [ ] Allunyada de instal·lacions perilloses
- [ ] Accés a electricitat redundant
- [ ] Internet de múltiples operadores
- [ ] Accés 24/7 per personal i emergències

### ✓ Ubicació dins l'Edifici

- [ ] Planta intermedia (2a-5a planta)
- [ ] Sala interior sense finestres
- [ ] Allunyada de recepcions
- [ ] No senyalitzada externament
- [ ] Accés per muntacàrregues
- [ ] > 10 m d'ascensors i molls
- [ ] > 5-10 m de transformadors
- [ ] NO sota canonades ni banys

### ✓ Infraestructura Tècnica

- [ ] Climatització de precisió
- [ ] Temperatura 18-27 ºC
- [ ] Humitat 40-55%
- [ ] Detectores de fums i extinció
- [ ] Control d'accés físic
- [ ] Càmares 24/7
- [ ] SAI/UPS ≥ 15 min autonomia
- [ ] Sòl tècnic elevat
- [ ] Alçada ≥ 3.5 m
- [ ] Capacitat de càrrega verificada

---

## 🎯 Conclusió

L'ubicació i el disseny d'un CPD és **crítica per a la disponibilitat i seguretat** de les operacions informàtiques. Una bona ubicació prevé la majoria de problemes físics.

**Seleccionar correctament:**

- 🌍 La zona geogràfica (riscos naturals baixos)
- 🏢 La localització dins l'edifici (allunyada de perills)
- 🔧 La infraestructura tècnica (climatització, seguretat, alimentació)

**Recorda:** Un centre de dades ben dissenyat és una inversió que es recupera en menys temps de funcionament sense incidents.
