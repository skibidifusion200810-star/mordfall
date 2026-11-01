# DEAD EVIDENCE – Multiplayer-Mordfallspiel

Spielbare erste Version von **Das Schweigen der Villa**. Komplett als statische Website auf GitHub Pages nutzbar.

## Funktionen
- Modernes dunkles Interface, responsives Layout
- Private Lobby mit sechsstelligen Einladungscodes
- 2–6 Spieler über direkte PeerJS/WebRTC-Verbindungen (ohne selbst gehosteten Server)
- Sieben visuelle Point-and-Click-Räume, 12 anklickbare Hinweise
- Fünf Verdächtige mit interaktiven Fragen und durch Beweise freigeschalteten Aussagen
- Gemeinsame Beweise, Live-Ermittlungsfeed und Teamstatus
- Beweiswand, Täteranklage und vollständige Auflösung
- Einzelspieler-Demo

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
