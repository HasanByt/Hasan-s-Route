# 🔐 SSH-Zugriff auf den Ubuntu-Server (für neue Benutzer)

Bevor du dich auf deiner Route per SSH mit dem Server verbindest, lernst du hier, wie du unter **Linux** oder **Windows** OpenSSH installierst und dich **per Passwort** sicher anmeldest – ohne Public-Key-Konfiguration.

## Für Linux

### 1. OpenSSH Client installieren

```bash
sudo apt update
sudo apt install openssh-client -y
```

Prüfen, ob SSH installiert ist:

```bash
ssh -V
```

---

### 2. Verbindung mit dem Server herstellen

bsp.

```bash
ssh wiss@31.XXX.XXX.XXX
```

## Für Windows

### 1. Windows

1. Öffne **PowerShell** oder **CMD**
2. Verbinde dich mit dem Server:

bsp.

```powershell
ssh wiss@31.XXX.XXX.XXX
```

---

### 2. `ssh` nicht erkannt

1. Gehe zu **Einstellungen → Apps → Optionale Features**
2. Installiere **OpenSSH Client**
3. Danach:

bsp.

```powershell
ssh wiss@31.XXX.XXX.XXX
```

### 3. Mit PuTTY

1. Lade PuTTY herunter: https://www.putty.org/
2. Öffne PuTTY
3. Gib ein:
   - **Host Name**: `31.XXX.XXX.XXX`
   - **Port**: `22`
   - **Connection type**: SSH
4. Klicke auf **Open**
5. Melde dich an:
   - Benutzer: `wiss`
   - Passwort: `XXXX`

## Erfolgreiche Verbindung

Wenn alles geklappt hat, erscheint:

```
Welcome to Ubuntu ...
```

Du bist nun per SSH mit dem Server verbunden.
