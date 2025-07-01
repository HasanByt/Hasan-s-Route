# 🧭 Willkommen auf _Hasan's Route_

> _„Jede Route beginnt mit einem ersten Schritt – hier beginnt deiner.“_

---

## Projektüberblick

!!! info "Was erwartet dich auf dieser Route?"

    Diese Dokumentation begleitet dich auf meinem Weg zu einer funktionierenden und sicheren Entwicklungsumgebung.
    Du lernst **Schritt für Schritt**, wie du deinen Ubuntu-Server vorbereitest und einen **Cloudflare-Tunnel** einrichtest – alles dokumentiert anhand eines echten Projekts.

---

## Projekthintergrund

Im Modul **324** haben wir ein Projekt gestartet, bei dem verschiedene **Sortieralgorithmen** mit **Spring Boot** umgesetzt wurden.  
Die **MySQL-Datenbank** speichert zu jedem Algorithmus den Namen, die Beschreibung und die Komplexität. Mithilfe von **Insomnia** testeten wir erfolgreich unsere HTTP-Endpunkte.

Da wir bereits mit **React** gearbeitet hatten, entwickelten wir ein passendes **Frontend**:

- Ein Dropdown-Menü listet die Algorithmen aus der Datenbank
- Nach Auswahl erscheinen Beschreibung & Komplexität
- Ein Eingabefeld erlaubt das Einfügen eines Arrays
- Per Button wird das Array sortiert – samt Ausgabe von Sortierdauer & Vergleichszahl

Das Projekt wurde zunächst über **Railway (Backend & DB)** und **Netlify (Frontend)** deployed. Zusätzlich nutzten wir **CI/CD-Pipelines mit GitLab**.

🛑 Nach kurzer Zeit lief jedoch das kostenlose Railway-Abo ab.  
✅ Unsere Lösung: Deployment von **Backend & Datenbank auf einem eigenen Ubuntu-Server** – erfolgreich umgesetzt!

---

## Neue Projektphase & Ziel

Wir arbeiteten in zwei Gruppen und fassten unser Wissen zusammen.  
Das Ziel: Die bisherigen Algorithmen in ein gemeinsames **Maven-Projekt** überführen und daraus eine `.jar`-Datei erstellen. Diese soll im bestehenden System integriert und darüber ausgeführt werden – zwei Projekte, eine gemeinsame Route.

🎯 Und genau hier setzt diese Dokumentation an.

Mit **Hasan's Route** möchte ich zeigen, wie ich den Weg vom lokalen Setup bis zur Deployment- und Tunnel-Lösung gegangen bin – damit **jede\*r Beteiligte** diesen Weg ebenfalls meistern kann.

---

## Etappen der Route

!!! tip "Etappe 1 & 2 – SSH-Zugriff einrichten"

    🔐 Zugriff auf deinen Server vorbereiten:

    - Installation des **OpenSSH-Servers**
    - Aktivierung des **Passwort-Logins**
    - Verbindung über **Linux**, **Windows CMD**, **PowerShell** oder **PuTTY**

    👉 [Zur Server-Konfiguration »](HowToSSH(Server).md)
    👉 [Zur SSH-Anleitung »](HowToSSH.md)

---

!!! tip "Etappe 3 – Cloudflare Tunnel starten"

    🌐 Lokalen Dienst sicher erreichbar machen – ohne eigene Domain:

    - Cloudflare Tunnel einrichten
    - HTTPS-Zugang erzeugen
    - Ausgabe in Datei speichern & URL weiterverwenden

    👉 [Zur Tunnel-Anleitung »](HowToCloudflare.md)

---

!!! tip "Etappe 4 – Eigene Route dokumentieren"

    📝 Willst du auch eine solche Website erstellen wie *Hasan’s Route*?

    Dann zeige ich dir, wie du mit **MkDocs** und dem modernen **Material for MkDocs**-Theme deine eigene Dokumentation entwickelst – lokal im Browser und deployt über **GitHub Pages**.

    - MkDocs & Material installieren  
    - Projektstruktur aufbauen  
    - Navigation und Styling konfigurieren  
    - Veröffentlichung mit `mkdocs gh-deploy`  

    👉 [Zur MkDocs-Anleitung »](HowToMkdocs.md)


## So navigierst du durch die Route

!!! note "Hinweis"

    - Die Etappen sind **unabhängig voneinander** nutzbar
    - Die Navigation erfolgt über das Menü oder die Direktlinks
    - Du kannst jederzeit zu einem späteren Thema springen – ganz wie bei einer echten Route

---

## Dein erster Schritt

Bereit? Starte mit der ersten Etappe:  
👉 [SSH auf dem Server einrichten »](<HowToSSH(Server).md>)

---

!!! quote "Hasan’s Route"

    _„Diese Doku soll nicht nur erklären – sie soll dich begleiten.“_
