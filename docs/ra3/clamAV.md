# Antivirus

## 📌 ClamAV

🌍 [ClamAV](https://www.clamav.net/)

### Instal·lar els paquets

```bash
sudo apt update
sudo apt install -y clamav clamav-freshclam clamav-daemon clamav-testfiles
```

### Aturar els serveis

```bash
sudo systemctl stop clamav-freshclam clamav-daemon
```

### Actualitzar l'antivirus automàticament

```bash
sudo freshclam
```

### Actualitzar l'antivirus manualment

Descarrega els fitxers des de:
- 🌍 https://database.clamav.net/main.cvd
- 🌍 https://database.clamav.net/daily.cvd

Després mou els fitxers:

```bash
sudo mv main.cvd /var/lib/clamav/
sudo mv daily.cvd /var/lib/clamav/
```

### Reiniciar el servei

```bash
sudo systemctl restart clamav-freshclam
```

### Iniciar l'escaneig d'una carpeta específica o de tot el disc

```bash
sudo clamscan /usr/share/clamav-testfiles/
sudo clamscan -r /
```

### Mostrar les comandes d'ajuda

```bash
sudo clamscan --help
```

### Comprovar el funcionament de l'antivirus

Crea un fitxer amb el següent contingut per provar la detecció de virus (EICAR test file):

```
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
```

### Comprovar els fitxers d'events

```bash
sudo cat /var/log/clamav/freshclam.log
sudo cat /var/log/clamav/clamav.log
```

### Iniciar l'escaneig i eliminar arxius infectats

```bash
sudo clamscan --infected --remove /usr/share/clamav-testfiles/
sudo clamscan --infected --remove -r /
```
