
# 🔐 Etappe 1a – SSH-Zugriff per Passwort (ohne Public Key)

!!! info "Etappenziel"

    Diese Etappe auf *Hasan’s Route* führt dich zur Vorbereitung deines Ubuntu-Servers für den SSH-Zugriff – **per Passwort**, ganz ohne Public-Key-Konfiguration.

---

## 🚧 Hintergrund

Unsere Route startete ursprünglich mit **Railway**, wo Backend und Datenbank gehostet wurden.  
Als das Test-Abo endete, bogen wir auf einen neuen Pfad ab: ein eigener Ubuntu-Server.  

Da unsere **CI/CD-Pipeline** direkten Zugriff auf den Server benötigt, ist der SSH-Zugriff ein zentraler Wegpunkt auf dem Deployment-Weg.

---

## 🛠️ 1. OpenSSH-Server installieren

Führe auf dem Ubuntu-Server folgende Befehle aus:

```bash
sudo apt update
sudo apt install openssh-server -y
```

Prüfe anschließend, ob der Dienst läuft:

```bash
sudo systemctl status ssh
```

Falls nicht aktiv, starte den Dienst und aktiviere den Autostart:

```bash
sudo systemctl enable --now ssh
```

---

## ⚙️ 2. Passwort-Login aktivieren

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

Speichere und schließe die Datei (`CTRL + O`, `Enter`, dann `CTRL + X`).

---

## 🔄 3. SSH-Dienst neu starten

```bash
sudo systemctl restart ssh
```

---

## 🔑 4. Passwort für Benutzer setzen

Falls der Benutzer noch kein Passwort hat:

```bash
sudo passwd dein-benutzername
```

Beispiel:

```bash
sudo passwd wiss
```

---

## 🧪 5. Verbindung testen

Von einem Client aus (Linux, macOS oder Windows PowerShell/CMD):

```bash
ssh wiss@<server-ip>
```

Gib das gesetzte Passwort ein – und du bist verbunden ✅

---

## ⚠️ Hinweis zur Sicherheit

!!! warning "Nicht für produktive Systeme empfohlen"

    Die Anmeldung per Passwort ist einfach, aber deutlich unsicherer als die Public-Key-Authentifizierung.  
    Für produktive Server wird dringend empfohlen, auf **Public-Key-Login** umzustellen.

---

!!! tip "Zurück zur vorherigen Etappe"

    👉 [SSH-Zugriff von Windows/Linux einrichten »](HowToSSH.md)
