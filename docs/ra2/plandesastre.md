# Pla de Recuperació de Desastres (DRP)

Un **Pla de Recuperació de Desastres (DRP)** és la guia amb els passos a seguir per recuperar els sistemes i les dades de l'empresa quan es produeix una fallada greu (atac informàtic, avaria de maquinari o error humà).

---

## 1. Mètriques Clau (RTO i RPO)

A l'hora de dissenyar el pla, cal definir dos conceptes bàsics:

* **RPO (*Recovery Point Objective*):** Quantes dades ens podem permetre perdre?
* *Exemple:* Si es fan còpies cada 24 hores, l'RPO és de 24 hores.


* **RTO (*Recovery Time Objective*):** Quant de temps podem estar amb el servei caigut?
* *Exemple:* Si el sistema ha de tornar a funcionar en menys de 2 hores, l'RTO és de 2 hores.



---

## 2. Passos per a la Recuperació

Quan hi ha un incident greu, se segueix aquest procés:

1. **Aïllament i Diagnòstic:** Deconnectar els equips afectats de la xarxa per evitar que el problema s'escampi (especialment en atacs de tipus *ransomware*).
2. **Priorització dels Serveis:**
* **1r:** Serveis base de xarxa (DNS, usuaris i seguretat).
* **2n:** Bases de dades i emmagatzematge principal.
* **3r:** Aplicacions de treball i correu electrònic.


3. **Restauració de Còpies de Seguretat:**
* Primer es restaura la **còpia completa** més recent.
* Després s'apliquen les **incrementals** o la **diferencial** corresponent.


4. **Comprovació d'Integritat:** Validar que les dades són correctes i que els serveis funcionen abans de donar accés als usuaris.
5. **Retorn a la Normalitat:** Restablir tots els usuaris al sistema principal un cop corregida la causa de la fallada.

---

## 3. Bones Pràctiques per al Web

* **Provar les còpies periòdicament:** Una còpia de seguretat no és vàlida si no s'ha provat de restaurar mai.
* **Regla 3-2-1:** Guardar **3** còpies de les dades, en **2** suports diferents, i **1** d'elles fora de l'oficina (al núvol o en una altra ubicació).
* **Documentació accessible:** Guardar una còpia impressa o accessible fora de la xarxa principal del document de DRP.
