## ⚡ Tecnologies de SAI: Off-Line, Line-Interactive i On-Line

A l'hora de triar un Sistema d'Alimentació Ininterrompuda, no només importa la potència en VA, sinó la **tecnologia de funcionament intern** (topologia). Segons l'aïllament elèctric i el temps de commutació, trobem tres tipus principals:

---

### 📊 Taula Comparativa de Tecnologies

| Característica | Off-Line (Standby) | Line-Interactive | On-Line (Doble Conversió) |
|---|---|---|---|
| **Funcionament habitual** | Passa el corrent directe de la xarxa elèctrica. | Filtra la tensió mitjançant un regulador automàtic (AVR). | Converteix el corrent $AC \rightarrow DC \rightarrow AC$ contínuament. |
| **Temps de commutació** | **2 a 10 ms** (microtallat imperceptible per a PC bàsics). | **2 a 6 ms** (molt ràpid). | **0 ms** (Sense cap temps de commutació). |
| **Protecció elèctrica** | Bàsica (només talls de llum i picos grans). | Mitjana-Alta (talls, picos i fluctuacions de voltatge). | Total (aïllament complet de qualsevol anomalia). |
| **Ona de sortida** | Ona sinusoïdal simulada / quadrada. | Ona sinusoïdal pura o simulada. | Ona **sinusoïdal pura perfecta**. |
| **Preu i Eficiència** | Molt econòmic / Alta eficiència elèctrica. | Preu mitjà / Bona eficiència. | Preu elevat / Major consum energètic. |
| **Ús recomanat** | Ordinadors d'oficina, domèstic, routers, TPVs. | Servidors d'oficina, switches, equips de xarxa. | **CPDs, servidors de missió crítica, equips mèdics.** |

---

<Image src="image_agent_tag_3743172430069365225" alt="Icona d'alimentació ininterrompuda SAI" caption="Equip de gestió d'alimentació elèctrica per a servidors" />

---
![tipus de SAI](/img/sai-rack.png)


### 🔍 Detall de cada tecnologia

#### 1. Off-Line (Standby)
El corrent elèctric de la xarxa passa directament als equips. Les bateries només entren en funcionament quan la xarxa falla completament.
* **Avantatge:** És l'opció més barata i no fa soroll.
* **Inconvenient:** Triga uns mil·lisegons a actuar. Si la xarxa té microtallats o variacions de voltatge constants, els equips les pateixen.

#### 2. Line-Interactive
Inclou un microprocessador i un **regulador automàtic de tensió (AVR)**. Si la tensió baixa o puja lleugerament, el SAI la corregeix sense haver de recórrer a la bateria.
* **Avantatge:** Protegeix contra alts i baixos de tensió allargant la vida útil de les bateries.
* **Inconvenient:** Manté un petit temps de commutació (2-6 ms) quan falla la llum per complet.

#### 3. On-Line (Doble Conversió)
El corrent que arriba de la xarxa es converteix primer en corrent continu ($DC$) per carregar les bateries i, immediatament, es torna a convertir en corrent altern ($AC$) per als servidors. Els equips **sempre s'alimenten de l'inversor del SAI**, mai directament de la xarxa.
* **Avantatge:** Zero mil·lisegons de commutació. La qualitat del corrent és perfecta, independentment de com d'inestable sigui la xarxa elèctrica externa.
* **Inconvenient:** Preu més elevat i major generació de calor (requereix ventilació constant). És la tecnologia **obligatòria en qualsevol CPD professional**.
