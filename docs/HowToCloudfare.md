# Cloudflare Tunnel Setup (ohne Account)

Diese Anleitung beschreibt, wie ein Cloudflare-Tunnel eingerichtet und im Hintergrund betrieben wird, sodass man über eine öffentliche HTTPS-URL auf einen lokalen Dienst zugreifen kann.

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
grep -oP 'https://[a-zA-Z0-9-]+\.trycloudflare\.com' tunnel.log
```

Beispielausgabe:
```bash
https://raise-operational-will-gentle.trycloudflare.com
```

Diese URL kann z. B. im Frontend eingetragen werden, um das Backend erreichbar zu machen.

---

## Hinweis

Dieser „Account-less“-Tunnel ist nur temporär und hat keine Garantien bezüglich Verfügbarkeit oder Wiederverwendbarkeit. Für den produktiven Einsatz sollte ein benannter Tunnel mit Cloudflare-Account erstellt werden.

Weitere Informationen:  
👉 [Cloudflare Tunnel Quickstart](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)