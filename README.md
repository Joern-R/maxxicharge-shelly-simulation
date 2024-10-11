# maxxicharge-shelly-simulation
Simulation der von der Maxxicharge CCU verwendeten Shelly Pro 3EM Datenschnittstelle 

# Motivation
Das Maxxicharge System benötigt für eine sinnvolle Nutzung den aktuelle Stromverbrauch 
aus des jeweils verbauten Zählers. Um diesen Verbrauch zu ermitteln bietet Maxxisun
derzeit drei verschiedene Optionen an.

- PowerOpti
- Shelly 3EM
- Shelly 3EM Pro

Der PowerOpti wird direkt auf der optischen Schnittstelle des Zählers montiert und
übernimmt so die "echten" vom Zähler gemessenen Verbrauchswerte. Die Shellies müssen vom Elektriker im Hausauschlussschrank
installiert werden und liefern ihre eigenen Messwerte.

Beide Systeme haben Vor- und Nachteile, die hier nicht im Detail diskutiert werden.

# Fragestellung
Kann man einen "beliebigen" Tasmota basierten optischen Zählersensor verwenden, um die 
notwendigen Zählerwerte (ohne PowerOpti oder Shelly) für eine Maxxicharge CCU bereitzustellen.

# Lösung - JA - es funktioniert
Es müssen allerdings ein paar Voraussetzungen erfüllt sein, damit man der Maxxicharge CCU
einen Tasmota basierten Lesekopf für Stromzähler als "Shelly 3EM Pro" unterjubeln kann.

Notwendig ist:
1. Einen Lesekopf für den Stromzähler, der auf der Tasmota OpenSource Firmware beruht und
   für den es ein passendes Script zum Auslesen der Zählerdaten gibt.
   Die aktuellen Scripte finden sich hier: https://tasmota.github.io/docs/Smart-Meter-Interface/
2. Man benötigt ein geeignetes System (z.B. Smart Home System), das zu einen die Daten
   des Lesekopfes auslesen kann, zum anderen für den Maxxicharge einen "kleine" Webserver
   mit einem dem Shelly (auf einfachsten Pro 3EM) angepassten API mit den ausgelesenen Daten
   zur Verfügung stellt.
3. Das ganze muss noch bei http://maxxi.app konfiguriert werden und natürlich 7x24 durchlaufen.

# Lösungsdetails
Die nachfolgend beschriebene Lösung ist ein Ansatz, der m.E. nach technisch nicht superkompliziert
ist, da er auf bewährten Komponenten und Integrationen im Bereich OpenSource zurückgreift, ohne
dass selbst ge-scriptet oder sogar programmiert werden muss.

## Technische Komponenten (in meinem Beispiel)
- Tasmota kompatibler Lesekopf für Stromzähler mit integriertem WiFi
  **Wichtig:** Vorher prüfen, ob der Lesekopf für den eigenen Zähler passt und ob ein entsprechenden Script
  zum Auslesen der Zählerwerte vorhanden ist - sonst wirds m.E. extrem schwierig.
- HomeAssistant (Aktuelle Softwareversion)
  **Hardware:** Keine Empfehlung von mir. Ich nutze selbst ein fertiges System von NabuCasa, da ich kein
  Hardwarebastler bin.






