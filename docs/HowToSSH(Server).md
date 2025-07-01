
# 🔐 Etappe 1 – SSH-Zugriff per Passwort (ohne Public Key)

!!! info "Etappenziel"

    Diese Etappe auf *Hasan’s Route* führt dich zur Vorbereitung deines Ubuntu-Servers für den SSH-Zugriff – **per Passwort**, ganz ohne Public-Key-Konfiguration.

---

## Hintergrund

Unsere Route startete ursprünglich mit **Railway**, wo Backend und Datenbank gehostet wurden.  
Als das Test-Abo endete, bogen wir auf einen neuen Pfad ab: ein eigener Ubuntu-Server.  

Da unsere **CI/CD-Pipeline** direkten Zugriff auf den Server benötigt, ist der SSH-Zugriff ein zentraler Wegpunkt auf dem Deployment-Weg.

---

## 1. OpenSSH-Server installieren

Führe auf dem Ubuntu-Server folgende Befehle aus:

```bash
sudo apt update
sudo apt install openssh-server -y
```

Prüfe anschliessend, ob der Dienst läuft:

```bash
sudo systemctl status ssh
```

Falls nicht aktiv, starte den Dienst und aktiviere den Autostart:

```bash
sudo systemctl enable --now ssh
```

---

## 2. Passwort-Login aktivieren

Bearbeite die Konfigurationsdatei:

```bash
sudo nano /etc/ssh/sshd_config
```

Suche und ändere (oder ergänze) folgende Zeilen:

```text
PasswordAuthentication yes
PermitRootLogin no
```

!!! tip "Sicherheit"

    `PermitRootLogin no` verhindert direkte Root-Logins – das erhöht die Sicherheit.

Speichere und schliesse die Datei (`CTRL + O`, `Enter`, dann `CTRL + X`).

---

## 3. SSH-Dienst neu starten

```bash
sudo systemctl restart ssh
```

---

## 4. Passwort für Benutzer setzen

Falls der Benutzer noch kein Passwort hat:

```bash
sudo passwd dein-benutzername
```

Beispiel:

```bash
sudo passwd wiss
```

---

## 5. Verbindung testen

Von einem Client aus (Linux, macOS oder Windows PowerShell/CMD):

```bash
ssh wiss@<server-ip>
```

Gib das gesetzte Passwort ein – und du bist verbunden ✅

---

## 6. Verbindungsdaten für externen Zugriff ermitteln

Um dich **von ausserhalb deines Netzwerks** (z. B. von Zuhause auf den Schulserver) per SSH zu verbinden, brauchst du:

- die **öffentliche IP-Adresse** deines Servers
- den **Benutzernamen**, unter dem du dich einloggst
- ggf. eine **Portfreigabe** im Router oder der Firewall

## Öffentliche IP-Adresse herausfinden

Auf dem Server:

```bash
curl ifconfig.me
```

Beispielausgabe:

```
31.123.45.67
```

Diese IP-Adresse verwendest du auf dem Client (Laptop, Heim-PC) für den SSH-Zugriff.

### Benutzername anzeigen

```bash
whoami
```

Damit erhältst du den Benutzernamen (z. B. `wiss`), den du beim Verbindungsaufbau benötigst.

---

## Zusätzliche Voraussetzungen für externen Zugriff

Damit der Zugriff von aussen funktioniert, beachte Folgendes:

- Der Server muss **über das Internet erreichbar** sein (z. B. durch eine öffentliche IP oder Portweiterleitung)
- Port **22 (SSH)** muss in der **Firewall** freigegeben sein
- Falls der Server hinter einem Router steht: **Portweiterleitung** einrichten (`TCP 22` → Server-IP im LAN)

!!! warning "Achtung bei Schulnetzwerken"

    In Schul- oder Firmennetzwerken kann der Zugriff durch Firewalls oder NAT blockiert sein.  
    In solchen Fällen kann ein externer SSH-Zugang über einen Tunnel (z. B. Cloudflare Tunnel) nötig sein.

---

## Verbindung von aussen

Auf dem Client:

```bash
ssh wiss@31.123.45.67
```

Mit dem vorher gesetzten Passwort einloggen – und los geht’s!

---

## ⚠️ Hinweis zur Sicherheit

!!! warning "Nicht für produktive Systeme empfohlen"

    Die Anmeldung per Passwort ist einfach, aber deutlich unsicherer als die Public-Key-Authentifizierung.  
    Für produktive Server wird dringend empfohlen, auf **Public-Key-Login** umzustellen.

---

!!! tip "Zur nächsten Etappe"

    👉 [SSH-Zugriff zum Ununtu-Server »](HowToSSH.md)

