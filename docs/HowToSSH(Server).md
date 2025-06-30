# 🔐 SSH-Zugriff per Passwort (ohne Public Key)

In diesem Abschnitt lernst du, wie du deinen Ubuntu-Server für den SSH-Zugriff vorbereitest – **mit Passwort-Anmeldung**, ganz ohne Public-Key-Konfiguration.

Im Projekt wurde anfangs **Railway** für das Hosting des Backends und der MySQL-Datenbank verwendet. Da das Test-Abo jedoch nach kurzer Zeit ablief, wurde stattdessen ein Ubuntu-Server zur Verfügung gestellt.  
Mit dieser Anleitung erfährst du, wie du den Server für den Fernzugriff per SSH vorbereitest.

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
