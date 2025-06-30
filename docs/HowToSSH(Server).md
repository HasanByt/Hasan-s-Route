# 🔐 SSH-Zugriff per Passwort (ohne Public Key)

Diese Etappe auf _Hasan’s Route_ führt dich zur Vorbereitung deines Ubuntu-Servers für den SSH-Zugriff – **per Passwort**, ganz ohne Public-Key-Konfiguration.

Unsere Route startete ursprünglich mit **Railway**, wo Backend und Datenbank gehostet wurden. Als das Test-Abo endete, bogen wir auf einen neuen Pfad ab: ein eigener Ubuntu-Server.  
In diesem Abschnitt erfährst du, wie du ihn für den sicheren Fernzugriff vorbereitest.

Da unsere **CI/CD-Pipeline** direkten Zugriff auf den Server benötigt, ist dieser SSH-Zugriff ein zentraler Wegpunkt auf dem Deployment-Weg.

---

## 1. OpenSSH-Server installieren

Führe auf dem **Ubuntu-Server** folgende Befehle aus:

```bash
sudo apt update
sudo apt install openssh-server -y
```

Anschliessend prüfen, ob der Dienst läuft:

```bash
sudo systemctl status ssh
```

Wenn nicht aktiv: Dienst starten und beim Boot aktivieren:

```bash
sudo systemctl enable --now ssh
```

## 2. SSH für Passwort-Login konfigurieren

Öffne die SSH-Konfigurationsdatei:

```bash
sudo nano /etc/ssh/sshd_config
```

Suche und ändere (bzw. ergänze) folgende Zeilen:

```bash
PasswordAuthentication yes
PermitRootLogin no
```

💡 `PermitRootLogin` sollte auf `no` gesetzt sein, um direkte Root-Logins zu verhindern.
Datei speichern und schliessen.

## 3. SSH-Dienst neu starten

```bash
sudo systemctl restart ssh
```

## 4. Passwort für Benutzer setzen

Falls der Benutzer noch kein Passwort hat, kannst du eins vergeben:

```bash
sudo passwd dein-benutzername
```

## 5. Verbindung herstellen

Von einem Client aus (Linux, macOS, Windows PowerShell/CMD):

```bash
ssh wiss@<server-ip>
```

Gib das gesetzte Passwort ein und du bist verbunden.

### ⚠️ Hinweis

Die Anmeldung per Passwort ist einfach, aber weniger sicher als Public-Key-Authentifizierung.
Für produktive Systeme wird dringend empfohlen, stattdessen auf Public-Key-Login umzustellen.
