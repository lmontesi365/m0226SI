# Centre de Processament de Dades (CPD) - Criteris d'Ubicació i Disseny

## Introducció

Un Centre de Processament de Dades (CPD) o Data Center és la instal·lació física que allotja els servidors, dispositius de xarxa i sistemes de suport necessaris per a l'operació de sistemes informàtics. L'ubicació i el disseny són factors crítics per assegurar la disponibilitat, seguretat i rendiment dels sistemes.

---

## 📍 Part 1: Elecció de l'Edifici i la Zona Geogràfica

### 1.1 Evitar Zones de Risc Natural

**Problemes:**
- **Inundacions**: Zones prop de rius, plans al·luvials, àrees baixes propendes a acumular aigua
- **Terratrèmols**: Regions sismicament actives
- **Huracans/Tempestes**: Zones costaneres amb risc de vents violents
- **Nevades extremes**: Zones de muntanya amb risc d'allissos

**Recomanacions:**
- 📊 **Estudiar l'historial meteorològic** dels últims 20-30 anys
- 🗺️ **Consultar mapes de riscos naturals** de l'Agència de Protecció Civil
- 📋 **Verificar plans urbanístics** per assegurar que la zona no serà inundable
- 🏘️ **Evitar zones de construcció recent** (sòl potencialment inestable)

### 1.2 Seguretat de l'Entorn (Criminalitat)

**Problemes:**
- **Robatoris** de dispositius i equipament
- **Vandalisme** i sabotatge
- **Intents de trencament** de la seguretat

**Recomanacions:**
- 📊 **Investigar índexs de criminalitat** del barri
- 👮 **Proximitat a commissaria de policia** (idealment < 5 km)
- 🏢 **Zona amb presència empresarial** (no sola, millor amb altres negocis)
- 🚔 **Patrulles de seguretat** a la zona

### 1.3 Proximitat a Instal·lacions Perilloses

**Amenaces Externes:**

| Instal·lació | Risc | Distancia Mínima Recomanada |
|---|---|---|
| Benzineres | Explosió, incendi | > 500 metres |
| Fàbriques químiques | Toxicitat, explosió, radiació | > 1 km |
| Magatzems de combustibles | Incendi, explosió | > 1 km |
| Zones industrials | Vibració, contaminació | > 500 metres |
| Aeroports | Crash aeri, radiació | > 10 km |
| Línies ferroviàries | Vibració, descarrils | > 300 metres |
| Centrals elèctriques | Radiació, EMF | > 500 metres |

**Recomanacions:**
- 📍 **Ubicar en zona comercial o residencial tranquila**
- 🗺️ **Consultar plànols urbans** per identificar instal·lacions properes
- 📞 **Contactar amb autoritats** per confirmar seguretat

### 1.4 Accés a Subministraments Crítics

#### Electricitat
- **Redundancia**: Connexió a múltiples subestacions elèctriques (idealment 2-3 independents)
- **Tensió**: Verificar estabilitat de voltatge
- **Capacitat**: Suministre suficient per a la demanda actual + creixement
- **Qualitat**: Baixa taxa de talls (< 99.5% interrupcions anuals)

#### Internet
- **Múltiples operadores** (fibra òptica òptim)
- **Ample de banda** > 1 Gbps (recomendable 10 Gbps)
- **SLA (Service Level Agreement)** amb % de disponibilitat garantit (99.9% mínim)
- **Cobertura geogràfica** de proveïdors

#### Aigua (per climatització i extinció d'incendis)
- **Accés fiable** a abasteciment d'aigua
- **Qualitat** de l'aigua (baixa salinitat)
- **Pressió** suficient (> 2 bar)

### 1.5 Accessibilitat per al Personal i Emergències

**Requisits 24/7:**
- ✅ Accés les 24 hores del dia, 7 dies per setmana
- ✅ Disponibilitat de tècnics TI en < 30 minuts
- ✅ Accés immediat per a bombers i policia
- ✅ Via d'accés sense peatges ni restriccions de trànsit
- ✅ Aparcament suficient per a vehicles d'emergència

**Infraestructura:**
- 🚗 Carreteres principals properes (no callejons)
- 🚌 Accés a transports públics
- ⛽ Gasolineres i altres serveis propers

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

**Últimes Plantes (Cobertes):**
- 💧 Filtracions d'aigua de la pluja
- ☀️ Escalfor excessiva (> 35ºC)
- 🌪️ Major exposició a vents

#### ✅ Plantes Recomanades
- **Plantes intermedies** (2a a 5a planta)
- **Allunyades de cobertes** (evitar filtracions)
- **Allunyades de base** (evitar inundacions)

### 2.2 Ubicació dins del Pis (Interior vs Exterior)

#### Sala Interior (RECOMANAT ✅)

**Avantatges:**
- Sense finestres a l'exterior → menor risc d'accés
- Menor exposició a luz, radiació solar
- Millor aïllament tèrmic i de soroll
- Menor humitat de l'exterior

**Ubicació ideal:**
- Al centre del pis (no als extrems)
- Allunyada de façanes externes
- Enrevolada d'altres espais (oficines, magatzems)

#### Sala Exterior (EVITAR ❌)
- Finestres = risc d'accés i robatori
- Escalfor/fred del exterior
- Major evaporació d'aire humit
- Visible des del carrer

### 2.3 Discreció i Ocultació

#### Signalització
- ❌ NO marcar com a "Sala de Servidors" a la porta
- ✅ Usar noms neutres: "Sala Tècnica 01", "Magatzem", "Sala de Manteniment"
- ✅ Porta sense vidre transparent
- ✅ Sense indicadors visuals de que hi ha equip costós

#### Ubicació Estratègica
- 🚫 NO pròxim a recepcions (menys vigilants)
- 🚫 NO adjacent a cafeteries (accés de moltes persones)
- 🚫 NO al costat de passadissos principals
- ✅ Allunyada de flux de personal
- ✅ Si possible, amb un accés restringit addicional

### 2.4 Accés per Trasllat de Material Pesant

**Problema:** Servidors, racks i SAI/UPS són equipaments molt pesats (200-500 kg cada un)

**Solucions:**
- 📦 **Ascensor gran** (mínim 2000 kg de capacitat)
- 🚪 **Portes d'ascensor suficientment grans** (> 1.2m d'ample)
- 📍 **Planta accessible** amb muntacàrregues (no pisos alts sense elevador)
- 🛤️ **Passadissos amples** per maniobrar carros de transport
- 🪜 **Porta de la sala suficientment gran** per passar racks
- 🔄 **Corbes amples** en passadissos (evitar eixarxos)

### 2.5 Allunyament de Fonts de Perill Interior

#### 🔊 Vibracions

**Problemes:**
- Dañen components electrònics
- Provoquen fallos en discs durs
- Desajustament de connexions

**Evitar proximitat a:**
- 🛗 Ascensors (especialment nit quan més ús)
- 📦 Molls de càrrega (camions descàrregant)
- ⚙️ Sales de maquinària de climatització
- 🔩 Compressors d'aire comprimit

**Distancia mínima:** > 10 metres

#### 💧 Aigua i Fuites

**Problemes:**
- Electrocució del personal
- Corrosió de components
- Fallos en cascada en servidors

**Evitar proximitat a:**
- 🚰 Lavabos i banys
- 🍳 Cuines i sales de menjar
- 🔌 Canonades verticals (especialment per planta)
- 🪟 Finestres en dies plujosos

**Recomanacions:**
- NO col·locar servidor sota canonades
- Inspeccionar regularment per humitat
- Sistema de detecció de fuites amb alarma

#### ⚡ Interferències Electromagnètiques (EMF)

**Problemes:**
- Corrupció de dades
- Falsos errors de xarxa
- Interferència en senyals

**Evitar proximitat a:**
- 🔌 Transformadors elèctrics
- 📡 Antenes de comunicació
- ⚙️ Motors elèctrics grans (>3kW)
- 🔆 Línies d'alta tensió

**Distancia mínima:** > 5-10 metres

### 2.6 Consideracions Estructurals de l'Edifici

#### 🏗️ Capacitat de Càrrega del Sòl

**Problema:** Els servidors en racks pesen molt i estan concentrats en poc espai

**Càlculs aproximats:**
- Rack de servidors: 200-400 kg
- SAI/UPS: 100-300 kg
- Climatització: 50-200 kg
- Cablejat i altres: 50-100 kg
- **TOTAL PER SALA:** 500-1000 kg en ~20m²

**Recomanacions:**
- 📊 **Verificar càrrega admissible** del sòl (típicament 500-1000 kg/m²)
- 🔍 **Inspecció estructural** per un enginyer
- 🦶 **Distribució uniforme** de racks en tot l'espai
- 🛠️ **Sòl tècnic elevat** (permet distribució de pes millor)

#### 📏 Alçada Suficient de la Sala

**Espai necessari:**
- Racks: 2-2.5 metres d'altura
- Sòl tècnic (si n'hi ha): 30-60 cm altura
- Climatització superior: 20-30 cm
- Cablejat en braguetes: 30-50 cm
- **ALTURA TOTAL MÍNIMA:** 3.5 metres

**Beneficis de gran alçada:**
- ✅ Millor circulació d'aire calent cap a dalt
- ✅ Espai per a col·locació de cablejat
- ✅ Flexibilitat per a futurs upgrades
- ✅ Millor ventilació de climatització

#### 🌡️ Aïllament Tèrmic

**Recomanacions:**
- Parets i sostre ben aïllats
- Porta aïllada (no metàl·lica)
- Sense fuites d'aire
- Sellar forats per canonades i cables

---

## 🏗️ Part 3: Infraestructura Tècnica de la Sala

### 3.1 Sistemes de Climatització

| Aspecte | Especificació |
|---|---|
| **Temperatura** | 18-27ºC (idealment 20-24ºC) |
| **Humitat relativa** | 40-55% (idealment 45-50%) |
| **Canvis de temperatura/hora** | < 5ºC |
| **Redundancia** | Mínim 2 sistemes independents |
| **Monitorització** | Sensors continus amb alarma |

**Tipus:**
- 🌀 **AC de precisió**: Refrigeració distribuïda uniforme
- 🚀 **Ventilació en cambra fria**: Sòl tècnic amb aire fred
- 🧊 **Evaporadors**: Per espais petits

### 3.2 Protecció contra Incendis

- 🚨 Detectores de fums (automàtiques)
- 🧯 Sistemes d'extinció amb gas inert (no afecta els equips)
- 💨 Detecció de fums incident (pre-incendi)
- 🚪 Compuertes tallafocs automàtiques
- 📋 Plan d'evacuació clara

### 3.3 Control d'Accés

- 🔑 Acceso per tarjeta o biometria
- 📹 Càmera de seguretat apuntant a la porta
- 📊 Registre de tots els accessos (qui, quan)
- 🔔 Alarma si algú entra sense autorització

### 3.4 SAI/UPS (Alimentació Ininterrompuda)

- ⏱️ Autonomia mínima: 10-15 minuts (permet aturada controlada)
- 🔌 Connectat a tots els sistemes crítics
- 📈 Capacitat proporcional a la demanda
- 🔄 Prova mensual de transferencia automàtica

---

## 📋 Checklist de Verificació per a CPD

### Ubicació Geogràfica
- [ ] Zona sense desastres naturals recurrents
- [ ] Baixa criminalitat documentada
- [ ] Allunyada de instal·lacions perilloses (> 500m-1km)
- [ ] Accés a electricitat redundant
- [ ] Accés a internet de múltiples operadores
- [ ] Accés 24/7 per a personal i emergències

### Ubicació dins l'Edifici
- [ ] Planta intermedia (evitar base i cobertes)
- [ ] Sala interior sense finestres externes
- [ ] Allunyada de recepcions i passadissos
- [ ] No senyalitzada externament
- [ ] Accés per muntacàrregues/ascensor gran
- [ ] > 10m d'ascensors i molls de càrrega
- [ ] > 5-10m de transformadors i antenes
- [ ] NO sota canonades ni lavabos

### Infraestructura Tècnica
- [ ] Climatització de precisió i redundant
- [ ] Temperatura 18-27ºC, humitat 40-55%
- [ ] Detectores de fums i extinció automàtica
- [ ] Control d'accés físic (tarjeta/biometria)
- [ ] Càmares de vigilancia 24/7
- [ ] SAI/UPS amb >= 15 min autonomia
- [ ] Sòl tècnic elevat (si espai)
- [ ] Alçada suficient (>3.5m)
- [ ] Capacitat de càrrega verificada

---

## 🎯 Conclusió

L'ubicació i el disseny d'un CPD és **crítica per a la disponibilitat i seguretat** de les operacions informàtiques. Una bona ubicació prevé la majoria de fallos físics i permet que la seguretat dels sistemes sigui robusta.

Seleccionar correctament:
- 🌍 La zona geogràfica (amb riscos naturals baixos i serveis essencials accessibles)
- 🏢 La localització dins l'edifici (allunyada de perills i discreta)
- 🔧 La infraestructura tècnica (climatització, seguretat, alimentació)

són inversions que es recuperen ràpidament en forma de menor nombre d'incidents i menys temps d'inactivitat.

**Recorda:** Un centre de dades ben dissenyat és una inversió que es recupera en menys temps de funcionament sense incidents.

