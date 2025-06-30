# 🌐 Etappe 2 – Cloudflare Tunnel Setup (ohne Account)

!!! info "Etappenziel"

    Auf dieser Etappe deiner *Route* lernst du, wie du deinen lokalen Dienst über das Internet sicher zugänglich machst – **per HTTPS**, ganz ohne eigene Domain oder Cloudflare-Account.

---

## 🚧 Hintergrund

In unserem Projekt wurde das Frontend separat auf **Netlify** deployed. Da Netlify standardmäßig HTTPS verwendet, muss auch das Backend über HTTPS erreichbar sein, damit die Kommunikation funktioniert.  
Hier biegt unsere Route Richtung **Cloudflare Tunnel** ab.

Cloudflare stellt uns einen temporären HTTPS-Tunnel zur Verfügung:  
Das Frontend kommuniziert mit Cloudflare, und Cloudflare leitet die Anfragen sicher an das lokale Backend weiter – ohne Zertifikate oder Domain.

---

## ✅ Voraussetzungen

!!! tip "Was du brauchst"

    - 🐧 Ein Linux-Server mit Internetzugang
    - 🔁 Ein lokal laufender Dienst auf `http://localhost:8080`
    - 📦 `nohup` installiert (standardmäßig bei den meisten Linux-Systemen)

---

## 🛠️ 1. Cloudflare Tunnel installieren

```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```

---

## 🚀 2. Tunnel im Hintergrund starten

Starte den Tunnel im Hintergrund, damit er auch nach SSH-Trennung weiterläuft:

```bash
nohup cloudflared tunnel --url http://localhost:8080 > tunnel.log 2>&1 &
```

!!! info "Was passiert hier?"

- nohup sorgt dafür, dass der Tunnel im Hintergrund weiterläuft – auch nach einer SSH-Trennung.
- Die Ausgabe (inkl. HTTPS-URL) wird in die Datei tunnel.log geschrieben.
---

## 🔎 3. HTTPS-Tunnel-URL auslesen

Verwende diesen Befehl, um die generierte URL herauszufiltern:

```bash
grep -oP 'https://.*\.trycloudflare\.com' tunnel.log
```

Beispielausgabe:

```bash
https://raise-operational-will-gentle.trycloudflare.com
```

👉 Diese URL kannst du z. B. im Frontend (Netlify) eintragen, um das Backend erreichbar zu machen.

---

## ⚠️ Hinweis zur Etappe

!!! warning "Nur temporär!"

Der hier genutzte "Account-less"-Tunnel ist **nur für temporäre Tests** gedacht.  
Er ist nicht garantiert verfügbar, nicht wiederverwendbar und nicht für Produktivsysteme geeignet.

Für einen stabilen, benannten Tunnel solltest du ein Cloudflare-Konto nutzen.

## 📚 Weitere Infos 
👉 [Cloudflare Tunnel Quickstart](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)
