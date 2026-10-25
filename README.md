# Gleisfieber

Kooperatives Gleisbau-Spiel in Godot 4 für 1–4 Spieler (auch online): Wälder und Felsfelder durchhacken, Holz und Stein in den Zug laden, Gleise herstellen und rechtzeitig vor der Lok verlegen – bis die Strecke den nächsten Bahnhof erreicht. Zwischen den Levels steht man im begehbaren Bahnhof, kauft neue Waggons, baut den Zug aus und wählt die Route.

Spielgefühl, Kamera und Ablauf orientieren sich an *Unrailed! 2: Back on Track*. Alle Modelle, Shader, Sounds und der gesamte Code sind eigenständig erstellt – es werden keine Inhalte des Originals verwendet.

**Stand: Version 0.10.0** – Tunnel durch Berge (mit durchsichtigem Fels), neues Gebirge-Biom, eine Quest pro Level, Admin-Testwelt, neu gestalteter Bahnhof mit gut lesbaren Preisen.

Die ausführliche Spielanleitung steht in **[ANLEITUNG.md](ANLEITUNG.md)** (und im Spiel unter F1). Was getestet wurde – und was nicht –, steht in **[docs/TESTBERICHT.md](docs/TESTBERICHT.md)**.

---

## Schnellstart

| System | Datei | Hinweis |
|---|---|---|
| Windows (x64) | `Gleisfieber.exe` | Doppelklick. Falls SmartScreen warnt: „Weitere Informationen“ → „Trotzdem ausführen“ (nicht signiert). |
| macOS (Apple Silicon & Intel) | `Gleisfieber.app` | Beim ersten Start **Rechtsklick → Öffnen** (nicht notariert). Alternativ im Terminal: `xattr -cr Gleisfieber.app` |

Projekt im Editor: **Godot 4.7.2** (Standard, nicht .NET) → *Importieren* → `project.godot` → **F5**. Keine Plugins, keine kostenpflichtigen Abhängigkeiten.

## Steuerung (Kurzfassung)

| Aktion | Tastatur | Controller |
|---|---|---|
| Laufen | WASD / Pfeiltasten | linker Stick |
| Aufheben · Ablegen · Tauschen (auf dem eigenen Feld) · Einladen · Gleise nehmen · Gleis legen · Lok löschen · Waggon benutzen · Kaufen | **Leertaste** (oder E) | A |
| Brücke bauen (Holz in der Hand, vor dem Wasser; über Lava mit Stein) | **Leertaste** | A |
| Tunnel bohren (Gleis in der Hand, am Streckenende vor dem Berg; kostet 2 Holz aus dem Lager) | **Leertaste** | A |
| Rolle (schnell nach vorn) | **Shift** | B |
| Werkzeug | automatisch beim Dagegenlaufen (Baum, Fels, Tier) | – |
| Zug sofort losschicken | Enter | Y |
| Zoom / Hupe / Rufe | Q / T / 1–4 | RB / LB / – |
| Schaf wegtreten | Leertaste | A |
| Schnellspeichern / Anleitung / Pause | F5 / F1 / Esc | – / Select / Start |

Alle Tasten lassen sich unter *Einstellungen → Tastenbelegung ändern* umlegen.

---

## Mit Freunden online spielen

Godot braucht niemand – nur das fertige Spiel:

1. **Spiel weitergeben:** die ZIP-Datei für das jeweilige System schicken (Windows: `Gleisfieber-Windows.zip`, Mac: `Gleisfieber-macOS.zip`), z. B. per WeTransfer, Google Drive oder USB-Stick. Entpacken, starten – fertig. Alle müssen **dieselbe Version** haben.
2. **Einer hostet:** Hauptmenü → *Online-Koop* → *Lobby erstellen*. Das Spiel zeigt einen **Code**.
3. **Die anderen treten bei:** *Online-Koop* → *Lobby beitreten* → Code eingeben.
4. **Im selben WLAN** klappt das sofort (die Lobby erscheint sogar automatisch in der Liste).
5. **Über das Internet** muss der Router des Hosts Verbindungen durchlassen:
   - Das Spiel versucht es automatisch (UPnP). FRITZ!Box: *Internet → Freigaben → Portfreigaben → Gerät auswählen → „Selbstständige Portfreigaben für dieses Gerät erlauben“*.
   - Klappt das nicht: Portfreigabe **UDP 24570** auf den Rechner des Hosts einrichten.
   - Ohne Router-Basteln: alle installieren das kostenlose **Tailscale** (oder ZeroTier), melden sich im selben Netz an und nutzen den Heimnetz-Code – das verhält sich wie ein gemeinsames WLAN.

Beim ersten Start fragen Windows bzw. macOS, ob das Spiel Verbindungen annehmen darf – bitte **Erlauben**.

---

## Was neu ist in 0.10.0

- **Tunnel:** Mit einem Gleis in der Hand am Streckenende auf einen Berg zeigen und Leertaste drücken – jedes Tunnelfeld kostet das Gleis + 2 Holz aus dem Materialwaggon, höchstens 4 Felder am Stück. Der Fels über dem Tunnel wird **durchsichtig** (man sieht den Zug darin), innen Stützbalken mit Laternen, an den Öffnungen gemauerte Portale, beim Bohren fliegen Brocken. Durch den Tunnel kann man laufen – außer wenn der Zug drin ist.
- **Neues Biom „Gebirge“** in Level 8 und 15: Ein Bergkamm sperrt die ganze Karte, ein Tunnel ist Pflicht. Im Finale gibt es einen schmalen Felsgrat. In den anderen Leveln ist ein Tunnel eine Abkürzung durch normale Berge (nicht durch den Vulkan).
- **Quests:** jedes Level eine zufällige Quest (oben links), geschafft = +1 Schraube. Zum Beispiel Schafe wegtreten, 9 auf einen Haufen stapeln, lange Geraden, viele Kurven, Bäume fällen – oder Verbote wie „nie rollen“, „kein Tier schlagen“, „die Lok darf nicht brennen“ und „lass die Lok 10 s brennen, erst dann löschen“.
- **Admin-Testwelt:** Wer mit einem Admin-Konto angemeldet ist, bekommt im Hauptmenü die „Testwelt“: Bahnhof mit 999 Schrauben, allen Waggons und Zugdesigns, freie Levelwahl, Optionen „Lok überhitzt nie“ und „Zug fährt erst auf Knopfdruck“. Zählt nicht für Statistik und Spielstände. (Im Code stehen nur Prüfsummen der Admin-Adressen, keine Klartext-Adressen.)
- **Bahnhof neu gestaltet:** große, kurze Schilder (Name + Preis), unten eine **Info-Karte** mit Beschreibung, Preis und Taste, am Zug die Übersicht **„Dein Zug“** mit Stufen und Ausbaupreisen. Meldungen haben jetzt einen dunklen Hintergrund und bleiben immer lesbar; beim Levelstart höchstens 3 Hinweise.
- Kartuschen „Flinke Schuhe“ und „Große Taschen“ entfernt – schneller laufen oder mehr tragen kann man nicht mehr kaufen.

## Was neu war in 0.9.1

- Der Zug wird **jedes Level deutlich schneller** (+12 % statt +7 % je Level, auf allen Schwierigkeiten). Die Lok heizt dabei nicht schneller auf als bisher.

## Was neu war in 0.9.0

- **20 Level, immer der Reihe nach:** Jede Fahrt beginnt bei Level 1. Am Bahnhof gibt es den normalen oder den schweren Weg zum nächsten Level.
- **Finale in Level 20:** längste Strecke, alle Gefahren auf einmal, Lichtstrahl über dem **Endbahnhof**, **Endspurt** kurz vor dem Ziel, großes **Feuerwerk**, Siegerbildschirm, goldener Zug und danach auf Wunsch **Endlos-Modus**.
- **Zugdesigns:** alle 3 geschafften Level ein neues, auswählbar in der **Lackiererei** (Depot und Bahnhöfe).
- **Nacht:** jede Minute 30 Sekunden stockdunkel, nur ~5 Felder Sicht, der Zug leuchtet.
- **Maulwürfe** (über Level 10) buddeln Hügel auf das 5. vorgebaute Gleis – mit der Spitzhacke weg, sonst entgleist der Zug.
- **Bremsschienen** (sehr selten): 3 Stück, darauf fährt der Zug langsamer.
- **Tiere** halten einen wieder auf (mit der Rolle kommt man vorbei); **Schafe wegtreten** mit der Leertaste, seltenes **goldenes Schaf** mit Schraube.
- **Hupe** (T) – Schafe erschrecken sich – und **Rufe** (1–4) als Sprechblasen, auch online.
- **Kamera:** Q zoomt in drei Stufen; Einstellung „Kamera folgt nur mir“ und Kamera-Abstand.
- **Bahnhof:** farbige **Preisschilder** über jedem Waggon (grün = genug Schrauben).
- **Konto:** nach dem Anmelden „Los geht’s – jetzt spielen!“.
- Wasser und Lava liegen nie direkt nebeneinander. Kartusche „Scharfe Klingen“ entfernt (kein schnelleres Abbauen).
- **Aufgeräumter Code:** Spielregeln in Module aufgeteilt (PlayerActions, WagonSim, Hazards, EnemyAI, HubLogic), Welt-Darstellung (WorldDecor, WorldFx), Menüs (PauseMenu, EndScreen), Netzwerk (NetDiscovery). Ungenutzter Code entfernt, Speicherleck bei der Hitzeanzeige behoben, weniger Arbeit pro Bild. Die Anleitung im Spiel wird direkt aus ANLEITUNG.md erzeugt.

---

## Was neu war in 0.8.0

- **Automatische Updates:** Das Spiel schaut beim Start auf GitHub nach einer neuen Version, lädt sie im Hintergrund (wenige MB) und benutzt sie nach einem Neustart. Neu herunterladen muss man ab 0.8 nur noch bei einem Engine-Wechsel.
- **Online-Spielstände:** Der Host speichert im Pausenmenü auf einem Online-Platz (oder F5); am Bahnhof automatisch. Später in der Lobby **„Spielstand laden …“** – Mitspieler werden am Namen wiedererkannt und bekommen Platz und Werkzeug zurück.
- **Jederzeit beitreten:** Der Beitritts-Code steht im Spiel klein oben rechts (und im Esc-Menü zum Kopieren).
- **2 Gleise Puffer** vor der Lok beim Levelstart.
- **Löschen und Einladen von allen Seiten** – auch vor der Lok und hinter dem letzten Waggon, Löschen auch schräg.
- **Figurenauswahl** als eigenes Fenster mit allen Figuren in 3D.
- **Vulkan:** zusätzlicher Teich direkt am Vulkan.
- **Steuerung:** schnelleres Anlaufen/Abbremsen, Figur rutscht an Baum- und Felsecken vorbei, ruckelfreie Darstellung auf 120/144-Hz-Bildschirmen. Tiere sperren einen nicht mehr ein – man läuft durch sie hindurch.

---

## Was neu war in 0.7.0

- **Vulkan ab Level 4:** großer, fester Vulkankegel; er spuckt alle paar Sekunden Lavabrocken, die zu festen Magmablöcken werden (nie direkt vors Gleis, der Weg bleibt immer offen).
- **Mehr Action:** freie Lichtungen auf jeder Karte, dort warten die Gegner. Wildschweine schon ab Level 3, **Spinnen** mit Netzen (2,5 s gefesselt), Waschbär-Diebe ab Level 6, schmale Bäche (1 Holz für die Brücke).
- **Explosionen** betäuben 5 Sekunden. **Eimer** füllt sich in 1,8 s.
- **Waggons:** höchstens 5 am Zug, teurer (auch die Ausbaustufen). Im Bahnhof mit der Leertaste **aufnehmen, tragen und an beliebiger Stelle einreihen** oder aufs **Abstellgleis** stellen; **E** baut aus.
- **Genau am Waggon:** Einladen nur am Materialwaggon, Interaktion nur mit dem Waggon, an dem man steht. **Glücksrad nur per Rolle (Shift)**. Über der Werkstatt dreht sich ein **Zahnrad mit Ladebalken**.
- **Tempo:** Der Zug wird jedes Level schneller (allein wie im Team), mit mehr Spielern etwas mehr.
- **Schwierigkeitsgrad** (Leicht / Mittel / Schwer) im Depot.
- **Sechs Spielfiguren** zur Auswahl im Hauptmenü.
- **Konto:** registrieren / anmelden mit E-Mail und Passwort, Spielstände und Rekorde werden online gesichert (auch nachträglich).
- **Replay** zeigt alle Level der Fahrt hintereinander.
- **Start:** Axt und Spitzhacke liegen direkt vor der Lok, der Startplatz ist kleiner und liegt jedes Mal woanders. **Zaun** rund um die Spielfläche.
- **Anzeige:** Fortschrittsleiste oben kleiner und durchsichtig (fast unsichtbar, wenn man oben am Rand ist); einzelne Anzeigen in den Einstellungen ausblendbar.
- Kurze **Ladebildschirme** auch vor dem Bahnhof und dem Depot. Karteneditor entfernt.

---

## Was neu war in 0.6.0

- **Brücken:** Holz in der Hand, vor ein Wasserfeld stellen, Leertaste – aus 1 Holz wird aufgeschüttete Wiese. Darauf kann man laufen und Gleise bauen. Über Lava geht das mit Stein. Der kleine Teich am Start bleibt (zum Löschen).
- **Fluss quer über die Karte:** auf der schweren Route immer, sonst ab Level 7 jedes zweite Level – ohne Brücke kommt der Zug nicht zum Bahnhof. Im Vulkan ist es ein Lavastrom.
- **Neue Gegner:** Wildschweine (ab Level 5) scharren mit den Hufen und rennen euch um. Waschbär-Diebe (ab Level 7) klauen Holz und Stein aus dem Materialwaggon – ein Treffer, und die Beute fällt herunter.
- **Steinschlag** (Canyon und später): Schatten am Boden, dann schlagen Felsbrocken ein. Werkzeuge werden nie eingemauert.
- **Mitnahme:** Alles, was am Ende neben dem Zug oder am Bahnhof liegt (Holz, Stein, Gleise, Werkzeuge, Dynamit), und was ihr tragt, liegt im nächsten Level direkt neben dem Zug und ist benutzbar. Meldung „Mitgenommen …“ im Bahnhof und „Mitgebracht …“ beim Levelstart.
- Meldungen brechen jetzt sauber um; der Ladebildschirm listet alle Gemeinheiten des nächsten Levels.

---

## Was neu war in 0.5.0

- **Gleise nur unter der Figur:** Gelegt wird genau auf dem Feld, auf dem man steht (grüne/rote Vorschau). Bis zu **8 Gleise** lassen sich stapeln – der Stapel in der Hand und am Boden zeigt, wie viele es ungefähr sind.
- **Holz und Stein stapeln sich sauber übereinander** (Zahl über Stapeln ab 2).
- **20 Sekunden** bis zur Abfahrt, **20 Sekunden** Brennzeit, bevor die Runde verloren ist.
- **9 Levels, 8 Biome**, jedes mit einer neuen Gemeinheit: Wiese → Canyon → Sumpf (*Matsch bremst*) → Schnee (*Eis, man rutscht*) → Nacht (*dunkel, Lichtkreise, leuchtender Zug*) → Wüste (*Sandsturm schiebt*) → Vulkan (*Lava, Lok heizt schneller*) → Labyrinth (*Berge überall, dunkel*). Danach mischen sich die Gemeinheiten.
- **Berge und Hindernisse senken sich**, wenn eine Figur dahinter steht – durchlaufen kann man trotzdem nicht.
- **Kamera:** ganze Insel samt unterem Rand sichtbar; mit mehreren Spielern zoomt sie heraus, damit alle im Bild bleiben.
- **Kartuschen** (wie in Unrailed 2) im Bahnhof: Flinke Schuhe, Große Taschen, Kühler Kopf, Scharfe Klingen, Turbo-Werkstatt, Schraubenfinder – bis zu 3 gleichzeitig.
- **Musik passt sich an:** eigener Stil je Biom, ruhig beim Bauen, treibend während der Fahrt, hektisch bei Gefahr (Feuer, Hitze, Gleisende nah).
- **Ladebildschirm** mit Zug, der über eine kleine Insel fährt, und dem Hinweis, was im nächsten Level neu ist.
- **Wetter & Licht:** Schnee, Glühwürmchen, Funken am Vulkan, Sandsturm mit Nebel.

---

## Was neu war in 0.4.0

- **Steuerung:** Leertaste hebt auf, legt ab, lädt ein, nimmt Gleise, baut und benutzt Waggons; Shift rollt. Aufheben geht nur auf dem Feld, auf dem die Figur steht. Einladen und Gleise nehmen nur per Taste (nicht mehr beim bloßen Berühren).
- **Gleise haben Vorrang:** Liegt Holz, Stein oder ein Werkzeug auf dem Bauplatz, rutscht es ein Feld zur Seite.
- **60 Sekunden** bis zur Abfahrt in Level 1 (später 54 s) – 30 s mehr als vorher.
- **Eine einzige Schraube pro Level**, ganz am Rand der Insel, dick eingepackt in Felsen und Bäume.
- **Glücksrad:** per Leertaste oder Rolle; Gewinne landen zwei Felder neben dem Zug mit „+3 Holz“-Anzeige und Meldung.
- **Neue Waggons** (nach dem Vorbild Unrailed 2): Sammelwaggon, Umwandler, Bremswaggon (ab Level 3), Geisterwaggon, Dynamitwaggon (ab Level 4), Bergbauwaggon (ab Level 5). Im Bahnhof höchstens vier Angebote.
- **Tastenbelegung** in den Einstellungen änderbar.

---

## Was in 0.3.0 dazukam

- **Levelkette:** Ein Level ist geschafft, sobald die letzte Schiene den Bahnhof berührt – dann rollt der Zug zügig hinein. Danach geht es in einen **begehbaren Bahnhof** mit Waggon-Podesten, Ausbau neben jedem Waggon, Wegweisern für die Route (normal / schwer mit mehr Schrauben) und dem Abfahrtssignal. Das nächste Level startet an genau diesem Bahnhof; Material, das in seiner Nähe liegt, und die Ladung im Zug kommen mit.
- **Einzelspieler startet im Depot** mit Zug und Levelauswahl (freigeschaltete Levels).
- **Jedes Level schneller und härter:** längere Strecken, mehr Tiere, Biome Wiese und Canyon im Wechsel.
- **Karte wie auf dem Referenzbild:** schwebende Insel, kleinere Felder, größere Karte, geschlossene Wald- und Felscluster, kantige Berge und Flüsse als feste Hindernisse.
- **Rolle** mit der Leertaste, Aufheben jetzt mit **E**.
- **Eimer:** am Wasser 3 Sekunden füllen, nur direkt am Zug mit E leeren. Bei 100 % Hitze brennt die Lok **12 Sekunden**, dann ist die Runde verloren.
- **Keine vorgebauten Gleise:** Werkstatt leer, vor der Lok liegt nur das Gleis, auf dem sie steht.
- **Materialwaggon** fasst am Anfang je 5 Holz und 5 Stein (+3 pro Ausbaustufe).
- **Glücksrad-Waggon** (Unrailed-2-„Slot Machine“): reinrollen → Rad dreht sich → nichts, Rohstoffe, fertige Gleise oder eine Explosion, die kurz betäubt. Bessere Chancen mit höherer Stufe und höherem Level.
- **Schätze:** goldene Schrauben liegen versteckt in den Clustern.
- **Tiere** (Schafe, Ziegen) laufen herum, blockieren Weg und Gleisbau, brauchen viele Schläge und lassen selten etwas fallen.
- **Ausbaukosten wie in Unrailed 2:** 3 / 4 / 6 / 12 Schrauben.
- **Speichern & Laden** (3 Plätze + Autosave am Bahnhof), **Statistik & Rekorde**, **Replay im Zeitraffer** nach einer Niederlage (2×–16×).
- **Zugtempo** automatisch nach Spielerzahl (allein langsamer) oder manuell.

---

## Projektstruktur

```
project.godot            Godot 4.7, Forward+ mit OpenGL-Rückfall; Autoloads Settings, InputSetup, Sfx, Music, Saves, Cloud, Net
scenes/                  main_menu.tscn, lobby.tscn, game.tscn (Aufbau im Code)
scripts/
  sim/                   Spiellogik – rein, headless testbar, netzwerkneutral
    gc.gd                Konstanten und Regeln
    run_data.gd          Fortschritt: Waggons, Stufen, Kosten, Biome, Routen, Glücksrad
    world_generator.gd   Seed-basierte Welten mit Clustern, Bergen, Flüssen, Schätzen, Tieren
    track_network.gd     Gleiskette, Platzierungsregeln, Kurven, Bahnhofsanschluss
    train_sim.gd         Zug, Tempo, Hitze, Brennen, Entgleisung, Einfahrt
    game_state.gd        Autoritativer Zustand: Aktion → Prüfung → Ereignisse (Level und Bahnhof)
    replay_recorder.gd   Aufzeichnung für das Zeitraffer-Replay
  net/                   Net (ENet-Host/Client, Lobby, Codes, LAN-Suche, UPnP), Lobby-Codes
  view/                  Insel, Gleise, Zug, Figuren, Tiere, Bahnhof, Effekte
  game/                  Spielszene, Steuerung, Kamera, Replay-Abspieler
  ui/                    Hauptmenü, Lobby, HUD, Anleitung, Einstellungen
  autoload/              Einstellungen, Tastenbelegung, Klangerzeugung, Spielstände
tests/
  run_tests.gd           685 Logikprüfungen (headless)
  playtest_driver.gd     Spieltest-Bot: steuert die echte Szene über simulierte Tastendrücke
tools/
  render_shot.sh         Bildschirmfotos ohne Grafikkarte
  net_test.sh            Online-Test mit 2–4 echten Prozessen (optional mit Latenz)
  net_test_drop.sh       Online-Test mit Verbindungsabbruch und Nachzügler
docs/TESTBERICHT.md      Ehrlicher Testbericht
```

## Architektur in Kürze

Alles, was über den Spielausgang entscheidet, liegt in `scripts/sim/` und ist frei von Szenen-Knoten. Jede Handlung läuft – auch im Einzelspieler – über denselben Weg:

```
Eingabe → Net.submit(Aktion) → Host: GameState.handle_action() prüft gegen den echten Zustand
       → Ereignisse (absolute Werte, idempotent) → apply_event() bei Host und allen Clients → Views
```

Online ist der Host autoritativ (ENet, UDP 24570). Ereignisse werden mit 20 Hz gebündelt; beim Beitreten, Levelwechsel und Bahnhof gibt es einen vollständigen Schnappschuss. Am Ende jedes Online-Tests vergleichen alle Teilnehmer eine Prüfsumme über den Zustand.

## Tests ausführen

```bash
godot --headless --path . --script res://tests/run_tests.gd                          # 685 Logikprüfungen
godot --headless --fixed-fps 60 --path . res://scenes/game.tscn -- --playtest          # 3 Gleise
godot --headless --fixed-fps 60 --path . res://scenes/game.tscn -- --playtest --levels=3   # 3 Level inkl. Bahnhof
godot --headless --fixed-fps 60 --path . res://scenes/game.tscn -- --playtest --race       # Wettlauf gegen den fahrenden Zug
tools/net_test.sh 3 15            # 3 Spieler online, 15 Gleise im Team
tools/net_test.sh 2 12 150        # mit 150 ms künstlicher Latenz
tools/net_test_drop.sh            # Abbruch und Wiedereinstieg
```
