# 🔐 Etappe 2 – SSH-Zugriff zum Ubuntu-Server

!!! info "Etappenziel"

    Bevor du dich auf deiner *Route* per SSH mit dem Server verbindest, lernst du hier, wie du unter **Linux** oder **Windows** OpenSSH installierst und dich **per Passwort** sicher anmeldest – ganz ohne Public-Key-Konfiguration.

---

## Hintergrund

Diese Etappe deiner _Route_ führt dich zu einem entscheidenden Ausgangspunkt: dem **Zugang zu deinem Server**.

Bevor du ein neues Projekt startest oder ein laufendes System anpasst, brauchst du Zugriff auf den Server.  
Der SSH-Zugriff ist dabei der erste technische Schritt – sozusagen das Eingangstor auf deinem Deployment-Weg.

Du lernst, wie du dich per **Passwort-Anmeldung** sicher mit einem Ubuntu-Server verbindest, den wir zuvor entsprechend vorbereitet haben – ganz ohne SSH-Keys.  
Besonders praktisch, wenn du **schnell loslegen**, **etwas überprüfen** oder **manuell eingreifen** möchtest.

Egal ob du mit **Linux**, **Windows PowerShell**, **CMD** oder **PuTTY** arbeitest – hier erfährst du, wie du dich unkompliziert und **passwortbasiert** verbindest.

## Für Linux

!!! tip "1. OpenSSH Client installieren"

    Installiere den SSH-Client mit folgendem Befehl:

    ```bash
    sudo apt update
    sudo apt install openssh-client -y
    ```

    Prüfe danach, ob SSH korrekt installiert wurde:

    ```bash
    ssh -V
    ```

---

!!! tip "2. Verbindung mit dem Server herstellen"

    Beispiel:

    ```bash
    ssh wiss@31.XXX.XXX.XXX
    ```

---

## Für Windows

### Option 1: PowerShell / CMD (OpenSSH vorinstalliert)

1. Öffne **PowerShell** oder **CMD**
2. Verbinde dich mit dem Server:

   ```powershell
   ssh wiss@31.XXX.XXX.XXX
   ```

---

### Option 2: `ssh` wird nicht erkannt

!!! note "OpenSSH Client aktivieren"

1. Öffne: **Einstellungen → Apps → Optionale Features**
2. Suche nach **OpenSSH Client**
3. Installiere ihn, falls nicht vorhanden
4. Danach wie gewohnt verbinden:

   ```powershell
   ssh wiss@31.XXX.XXX.XXX
   ```

---

### Option 3: Mit PuTTY (grafisch)

1. Lade PuTTY herunter: [https://www.putty.org/](https://www.putty.org/)
2. Öffne PuTTY
3. Trage ein:
   - **Host Name**: `31.XXX.XXX.XXX`
   - **Port**: `22`
   - **Connection type**: `SSH`
4. Klicke auf **Open**
5. Melde dich an:
   - **Benutzername**: `wiss`
   - **Passwort**: `XXXX`

---

## Erfolgreiche Verbindung

Wenn alles geklappt hat, siehst du etwas wie:

```bash
Welcome to Ubuntu ...
```

Du bist nun per SSH mit dem Server verbunden.
