# DEAD EVIDENCE – Multiplayer-Mordfallspiel

Spielbare erste Version von **Das Schweigen der Villa**. Komplett als statische Website auf GitHub Pages nutzbar.

## Funktionen
- Modernes dunkles Interface, responsives Layout
- Private Lobby mit sechsstelligen Einladungscodes
- 2–6 Spieler über direkte PeerJS/WebRTC-Verbindungen (ohne selbst gehosteten Server)
- Elf visuelle Point-and-Click-Räume, 22 anklickbare Hinweise
- Fünf Verdächtige mit interaktiven Fragen, freien Texteingaben und durch Beweise freigeschalteten Aussagen
- Gemeinsame Beweise, Live-Ermittlungsfeed und Teamstatus
- Beweiswand, Täteranklage und vollständige Auflösung
- Fünf Ermittlungs-Kapitel, die mit wachsender Beweissammlung automatisch aufsteigen\n- Unterschiedliche Raumszenen und neue UI-Animationen\n- Einzelspieler-Demo

## GitHub Pages aktivieren
1. Öffne **Settings → Pages** deines Repositories.
2. Unter **Build and deployment**: **Deploy from a branch** auswählen.
3. **Branch: main**, **Folder: / (root)**, **Save**.
4. Nach erfolgreicher Veröffentlichung aufrufen: https://skibidifusion200810-star.github.io/mordfall/

## Gemeinsam spielen
Host: Namen eingeben → **Private Lobby erstellen** → Einladungslink kopieren.
Mitspieler: Link öffnen, Namen eingeben → **Lobby beitreten**.
Alle klicken **Bereit**, Host startet den Fall. Jeder kann unterschiedliche Räume und Personen untersuchen.

## Technische Hinweise
- Die App lädt PeerJS über ein öffentliches CDN und benutzt dessen kostenlosen Standard-Signalisierungsserver. Die eigentlichen Spielnachrichten laufen über WebRTC. Das ist **kein professionell garantiert verfügbarer Multiplayer-Backend-Dienst**: NAT-/Firewall-Probleme, Dienst-Ausfälle oder abweichende Netzwerkbedingungen können Verbindungen verhindern.
- Host muss online bleiben, damit die Gruppe spielen kann. Kein Speichern von Multiplayer-Fortschritt nach Reload; bei Host-Ausfall bricht die Session ab.
- Die Lösung befindet sich bei diesem statischen Prototyp im Client-Code und ist daher technisch auslesbar. Für produktionssichere Fälle sind serverseitige Logik und Datenbank nötig.
- Noch nicht enthalten: Accountsystem, dauerhaft gespeicherte Ermittlung, KI-Dialoge, animierte 3D-Räume, weitere vollständig spielbare Fälle.
- Die Tatorte sind **gezeichnete SVG-Illustrationen mit echten klickbaren Markierungen**, noch keine fotorealistischen Raumgrafiken.
- PeerJS wird unter MIT-Lizenz bereitgestellt. Bilder und Schriften kommen über externe Dienste; ohne diese bleibt die Kernoberfläche nutzbar.

## Projekt
Die ganze Website liegt bewusst in `index.html`, damit sie direkt per GitHub Pages läuft. Lokal einfach `index.html` in einem Browser oder über einen lokalen HTTP-Server öffnen. Für Multiplayer braucht der Browser Internetzugang.

## Freie Fragen und echte KI

Auf der Seite unter **KI-Verhör einrichten** eine HTTPS-URL eines eigenen KI-Backends eintragen. Das Spiel sendet dann eine JSON-POST-Anfrage mit `question`, `character` und den bereits gesicherten `evidence`. Erwartete Antwort: `{"answer":"..."}`.

Ein Beispiel für einen Cloudflare Worker liegt in `ai-worker/worker.js`. Deployment:
1. Einen Cloudflare-Worker anlegen und den Worker-Code hineinkopieren.
2. `OPENAI_API_KEY` als **Secret**, nicht als Klartext in Dateien hinterlegen.
3. `ALLOWED_ORIGIN` als Variable auf `https://skibidifusion200810-star.github.io` setzen.
4. Worker veröffentlichen und dessen HTTPS-Adresse in der Spieloberfläche speichern.
5. Bei öffentlichem Einsatz unbedingt Authentifizierung, Rate-Limits, Budget-Grenzen und Missbrauchsschutz ergänzen. Das Worker-Beispiel ist ein Integrationsstartpunkt, **kein gehärteter öffentlicher KI-Dienst**.

Ohne eingerichteten KI-Dienst werden freie Fragen von der lokalen kontextbasierten Dialoglogik beantwortet. Das ist **kein generatives KI-Modell**. Ein kostenloser öffentlicher GitHub-Pages-Host kann API-Schlüssel nicht sicher verwahren.

## Kapitel und weitere Fälle

Es gibt fünf Ermittlungsphasen innerhalb des Falls Villa Winter. Die Kapitelanzeige steigt mit gesammelten Beweisen auf. Die geplanten vollständig eigenständigen Fälle **Zimmer 309** und **Letzte Nachricht** sind derzeit **noch nicht implementiert**. Die zusätzlichen Räumlichkeiten gehören zunächst zum ersten Fall.

## Prüfung

Die JavaScript-Syntax der aktuellen `index.html` wurde geprüft. Ein vollständiger End-to-End-Test in GitHub Pages inklusive echter Peer-Verbindung oder KI-Worker wurde nicht durchgeführt.
