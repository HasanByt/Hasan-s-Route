# 🌐 Cloudflare Tunnel Setup (ohne Account)

Auf dieser Etappe der _Route_ geht es darum, deinen lokalen Dienst über das Internet sicher zugänglich zu machen – **per HTTPS**, ohne eigene Domain.

Diese Anleitung zeigt dir, wie du mit **Cloudflare Tunnel** einen temporären, verschlüsselten Zugang zu deinem lokalen Backend einrichtest und den Dienst dabei im Hintergrund betreibst.

In unserem Projekt wurde das Frontend separat auf **Netlify** deployed. Da Netlify standardmässig HTTPS verwendet, muss auch das Backend über HTTPS erreichbar sein, damit die Kommunikation zwischen Frontend und Backend funktioniert.  
Hier biegt unsere Route Richtung **Cloudflare** ab.

Cloudflare erstellt für uns einen HTTPS-Tunnel: Das Frontend spricht mit Cloudflare, und Cloudflare leitet die Anfragen sicher an unser Backend weiter – ganz ohne Domain und Zertifikatsaufwand.

Da dieser Tunnel nur während der Laufzeit aktiv ist, starten wir ihn im Hintergrund. Die dabei generierte HTTPS-URL wird im Terminal ausgegeben.  
Weil das Terminal beim Hintergrundstart nicht sichtbar ist, speichern wir die Ausgabe automatisch in eine Datei. So können wir die Tunnel-URL später gezielt auslesen und z. B. im Frontend verwenden.

## Voraussetzungen

- Ein Linux-Server mit Internetzugang
- Lokaler Dienst läuft unter http://localhost:8080
- nohup ist installiert (Standard bei den meisten Linux-Systemen)

---

## 1. Cloudflare installieren

```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```

---

## 2. Tunnel im Hintergrund starten

Führe folgenden Befehl aus, um den Tunnel im Hintergrund zu starten:

```bash
nohup cloudflared tunnel --url http://localhost:8080 > tunnel.log 2>&1 &
```

Erklärung:

- nohup sorgt dafür, dass der Tunnel im Hintergrund weiterläuft – auch nach einer SSH-Trennung.
- Die Ausgabe (inkl. HTTPS-URL) wird in die Datei tunnel.log geschrieben.

---

## 3. Tunnel-URL auslesen

Um die erzeugte HTTPS-Adresse zu finden, verwende:

```bash
grep -oP 'grep -oP 'https://.*\.trycloudflare\.com' tunnel.log
```

Beispielausgabe:

```bash
https://raise-operational-will-gentle.trycloudflare.com
```

Diese URL kann z. B. im Frontend eingetragen werden, um das Backend erreichbar zu machen.

---

## ⚠️ Hinweis

Dieser „Account-less“-Tunnel ist nur temporär und hat keine Garantien bezüglich Verfügbarkeit oder Wiederverwendbarkeit. Für den produktiven Einsatz sollte ein benannter Tunnel mit Cloudflare-Account erstellt werden.

Weitere Informationen:  
👉 [Cloudflare Tunnel Quickstart](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)
