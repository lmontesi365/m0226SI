
# 🔧 Infraestructura Tècnica de la Sala

Aquest apartat detalla tots els sistemes crítics necessaris per mantenir els servidors i equips de xarxa operatius, protegits i en funcionament ininterromput les 24 hores del dia.

---

## 1. Sistemes de Climatització (HVAC)

- **Control de Temperatura:**
  - Mantener la sala entre **18 °C i 27 °C** segons els estàndards ASHRAE.
  - Prevenir el sobreescalfament del maquinari.
- **Control d'Humitat:**
  - Humitat relativa recomanada entre el **40% i el 60%**.
   - ❌ Humitat < 40%: Risc de descàrregues d'electricitat estàtica.
   - ❌ Humitat > 60%: Risc de condensació d'aigua sobre components elèctrics.
- **Disseny de Passadissos Fred / Calent:**
  - **Passadís Fred:** L'aire fred s'injecta pel terra tècnic a la part frontal dels *racks*.
  - **Passadís Calent:** L'aire calent s'expulsa per la part posterior i es recull al sostre.
- **Redundància:**
  - Configurar sistemes de climatització secundaris ($N+1$).

---

## 2. Protecció contra Incendis

- **Sistemes de Detecció Precoç:**
  - Utilització de detectors d'aspiració d'aire (sistemes *VESDA*).
  - Detectar partícules de fum abans que hi hagi flama visible.
- **Sistemes d'Extinció Neta (Sense Aigua):**
  - **Gasos Inerts:** Argonite o Inergen.
  - **Gasos Químics Sintètics:** Novec 1230 o FK-5-1-12.
   - ✅ Extingeixen el foc reduint l'oxigen o la calor.
    -✅ No deixen residus ni danyen els equips electrònics.
- **Sectorització:**
  - Murs i portes amb resistència al foc de com a mínim **RF-120**.

---

## 3. Control d'Accés Físic

- **Autenticació Multifactoret (MFA Físic):**
  - Targetes de proximitat (RFID / NFC).
  - Codi PIN d'accés.
  - Biometria (petjada dactilar, reconeixement d'iris o facial).
- **Registre i Auditoria:**
  - Gravació automàtica de totes les entrades i sortides (*Audit Logs*).
- **Mesures de Seguretat Extra:**
  - **CCTV:** Videovigilància 24/7 amb gravació contínua de tots els passadissos.
  - **Esclusa de seguretat (*Man-trap*):** Doble porta interlocking per evitar el *tailgating* (accés no autoritzat darrere d'un usuari).

---

## 4. SAI / UPS (Alimentació Ininterrompuda)

- **Sistemes SAI / UPS:**
  - Bateries de resposta immediata davant tall de subministrament o pics de tensió.
  - Proporcionen autonomia temporal fins que arrenquen els generadors.
- **Generadors Auxiliars (Genset):**
  - Motors dièsel d'arrencada automàtica per a tallades elèctriques prolongades.
- **Línies Elèctriques Redundants:**
  - Doble font d'alimentació per a cada servidor (Font A + Font B).
  - Conmutadors de transferència estàtica (*STS*) per canviar de línia sense interrupció.

---

## ✅ Checklist d'Infraestructura Tècnica

- [ ] Climatització redundant ($N+1$) amb rang de 18-27 °C
- [ ] Control d'humitat entre el 40% i el 60%
- [ ] Distribució de passadissos freds i calents
- [ ] Detecció precoç de fum (VESDA)
- [ ] Extinció d'incendis per gas inert/químic (sense aigua)
- [ ] Control d'accés multifactoret (biometria / RFID / PIN)
- [ ] Sistema de videovigilància CCTV 24/7
- [ ] SAI / UPS instal·lat i amb manteniment al dia
- [ ] Generador elèctric auxiliar de suport
- [ ] Doble línia d'alimentació elèctrica als servidors
