# ULTRAI

Eine Windows-Desktop-App für KI-Arbeit, die nicht stehen bleibt. Vier Modi in einem Fenster — sprechen, in einem echten Projektordner entwickeln, auf einer Leinwand gestalten, Bilder und Videos generieren — dazu Terminplanung, Multi-Agent-Läufe und das eigene Smartphone als zweiter Bildschirm.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Dieses Repository dient **ausschließlich der Release-Distribution**. Der Quellcode wird hier nicht veröffentlicht.

---

## Download

Windows 10 / 11 (x64). Erfordert die WebView2-Runtime, die auf den meisten Windows-Installationen bereits vorhanden ist.

**[Die aktuelle Version herunterladen](https://github.com/UltraK18/ULTRAI/releases/latest)** — `ULTRAI_x.y.z_x64_en-US.msi` herunterladen und ausführen.

Danach kümmert sich die App selbst darum: Sie prüft beim Start und danach in regelmäßigen Abständen auf neue Versionen, informiert Sie, wenn eine verfügbar ist, und installiert sie an Ort und Stelle.

## Vier Modi, ein Fenster

Jeder Modus ist ein eigens dafür gebauter Bildschirm mit eigenen Werkzeugen und eigenen Agenten — aber eine App, eine Reihe von Einstellungen, ein Ort, an dem Ihr Verlauf lebt.

| Modus | Der Bildschirm | Was Sie dort tun |
| :--- | :--- | :--- |
| **Chat** | Unterhaltung | Beliebiger Provider und beliebiges Modell, Reasoning-Effort pro Nachricht, Deep Research mit Quellenangaben, Dateien und Bilder als Eingabe |
| **Code** | Ein echter Projektordner | Dateibaum, Diffs in einem Review-Panel, ein Terminal neben dem Chat, Berechtigungsabfragen bevor irgendetwas auf die Festplatte geschrieben wird |
| **Design** | Live-Leinwand + Designer-Agent | Bildschirme werden neben dem Chat gerendert, während sie entstehen; fertige Arbeit wird als echte Dateien an Code übergeben |
| **Studio** | Freie Leinwand + Chat | Bilder und Videos generieren, platzieren und neu anordnen, eigene Dateien einfügen, iterativ am Vorhandenen weiterarbeiten |

Der Wechsel des Modus startet nichts neu — jeder Modus behält seine eigenen Unterhaltungen, und die Seitenleiste zeigt die, die zum aktuellen Bereich gehören.

## Die Oberfläche ist der Punkt

Die meisten Tools in diesem Bereich sind ein Terminal oder eine Webseite in einem Wrapper. ULTRAI ist eine Desktop-App, die gestaltet wurde, nicht zusammengesetzt.

- **Glas, das wirklich Glas ist** — schwebende Flächen laufen über eine kleine Rendering-Engine, keinen Weichzeichnungsfilter. Sie backt eine Normal Map für die Fassung und zeichnet daraus Spekular-Highlights, und sie verschiebt das, was hinter der Fläche liegt, sodass Kanten sich brechen. Bedienelemente wie der Toggle und der Slider gehen weiter und lösen die Snelliussche Brechung mit einem Brechungsindex und einer Dicke, sodass der Griff die Spur darunter verbiegt. Ein CSS-Frost kann das nicht, und der Unterschied zeigt sich an jeder Kante.
- **Squircle-Ecken** — Panels verwenden eine Superellipse statt eines Kreisbogens, sodass die Kurve ohne die flache Stelle, die `border-radius` erzeugt, in die gerade Kante übergeht.
- **Zwei Themes, beide bewusst gestaltet** — Hell und Dunkel bauen auf einer betontonigen Palette mit einem leichten kühlen Einschlag auf, abgestimmt, damit an keinem Ende etwas blendet. Jede Fläche ist ein Token, sodass sich die gesamte App gemeinsam bewegt, statt pro Bildschirm auseinanderzudriften.
- **Zurückhaltung mit Absicht** — keine Emojis irgendwo im Produkt, keine Ausrufezeichen, kein Anfeuern. Panels tragen jeweils eine einzige Fläche; Trennung entsteht durch Rim Light und Schatten statt durch Boxen innerhalb von Boxen.
- **Nahtloses Fenster** — eine 32px hohe Titelleiste im Windows-11-Maß, die den Hintergrund der App teilt, sodass das Chrome nicht als separater Streifen über dem Inhalt wirkt.
- **Mobil ist ein anderes Layout, kein kleineres** — Bottom Sheets, Bedienelemente in voller Breite und touchgerechte Trefferflächen, entschieden anhand des Geräts statt der Fensterbreite.

## Generierung mit echten Modellen

Studio ist kein einzelner Bild-Endpunkt. Es wählt pro Auftrag aus einem Katalog aus und teilt Ihnen mit, welches Modell es verwendet hat und warum.

- **Video** — Veo 3.1 und Veo 3.0 (plus deren Fast-Varianten), Sora 2 und Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Bild** — GPT Image 2 und 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (und Flash Lite), Grok Imagine Image
- **Video rein, Video raus** — einen vorhandenen Clip als Eingabe übergeben, nicht nur einen Prompt
- **Es prüft die eigene Arbeit** — zieht Frames aus dem Generierten zurück, betrachtet sie und entscheidet, ob ein erneuter Versuch nötig ist
- **Länge, Seitenverhältnis und Qualität bestimmen Sie** — wurden 30 Sekunden angefragt, werden auch 30 Sekunden gebaut, in der Form, die Sie angefragt haben

Welche Modelle Sie erreichen können, hängt von den Provider-Konten ab, die Sie verbinden (Vertex AI, OpenAI, xAI).

## ULTRA-Modus — viele Agenten, eine Aufgabe

Für Arbeit, die für einen einzelnen Kontext zu groß ist. ULTRA zerlegt die Aufgabe in Tasks, führt sie phasenweise über mehrere Agenten aus und lässt die Ergebnisse **unabhängig verifizieren, bevor sie zusammengeführt werden** — ein Kritiker und adversariale Prüfungen, nicht derselbe Agent, der sich selbst bewertet. Sie beobachten den Lauf und können jederzeit eingreifen. Modell und Reasoning-Effort werden pro Rolle festgelegt, sodass ein günstiger Worker und ein teurer Verifizierer bewusst unterschiedliche Provider sein können.

## Es hält seine Termine ein

Sagen Sie „jeden Wochentag um 9 Uhr" oder „in zwei Stunden", und daraus wird ein echter Job, keine Notiz. Wenn er auslöst, kommt die Aufgabe als Turn in dieser Unterhaltung an, und die KI beginnt daran zu arbeiten.

- Ein Kalender und eine Liste zeigen alles Registrierte; der nächste Lauf steht unten in der Seitenleiste
- War die App geschlossen, als etwas fällig war? Sie ermittelt, was sie verpasst hat, und fasst es in einem Nachhollauf zusammen
- `/loop` wiederholt eine Aufgabe für so viele Runden, wie Sie festlegen

## Ziele, die die KI nicht selbst für erledigt erklären kann

Legen Sie ein Ziel für eine Unterhaltung fest, und eine unabhängige Bewertung entscheidet über den Abschluss. Der Agent, der die Arbeit ausführt, entscheidet nicht selbst, dass sie fertig ist.

## Recherche, die gräbt, und Fragen vor der Arbeit

**Deep Research** plant die Blickwinkel und sucht und liest dann parallel über mehrere Sub-Agenten hinweg und zitiert, was sie gefunden hat. Auch die alltägliche Suche ist ungewöhnlich streng: Das Modell wird angewiesen zu suchen statt zu raten, das heutige Datum zu verwenden statt eines aus dem Training mitgeschleppten Jahres, und Aussagen im Präsens vor der Antwort zu verifizieren. Befunde werden ausgewogen präsentiert, mit Quellen im Text.

**Deep Interview** — wenn eine Anfrage unterspezifiziert ist, verwandelt es die Unterhaltung in ein strukturiertes Interview und klärt, was Sie tatsächlich wollen, bevor die Arbeit beginnt.

## Arbeit, die läuft, während Sie etwas anderes tun

Lange Jobs halten das Fenster nicht als Geisel.

- **Hintergrundläufe** — eine Aufgabe abgeben, und sie läuft isoliert, als Fork der Unterhaltung oder als Sub-Agent, und kann mitten im Lauf um weitere Berechtigung bitten, wenn sie an eine Grenze stößt.
- **Ein Live-Monitor** — eine Leiste unten zeigt alles gleichzeitig Laufende: Ihre eigenen Hintergrundaufgaben, anderswo gestartete, laufende Sub-Agent-Aufrufe, ULTRA-Läufe und jeden Shell-Befehl, der schon eine Weile läuft. Klicken Sie sich zu dem durch, das Sie beobachten möchten.
- **Eine Unterhaltung forken** — von jedem beliebigen Punkt abzweigen, um etwas auszuprobieren, ohne das Original zu verlieren, und zwischen Zweigen über den Nachrichtenindex wechseln.

## Übergabe zwischen Modi

Arbeit bleibt nicht in dem Modus stecken, in dem sie begonnen hat. Design übergibt fertige Bildschirme als echte Dateien auf der Festplatte an Code. Code-Sitzungen geben Fragen und Ergebnisse gegenseitig weiter. Studio platziert, was ein Agent erzeugt hat, direkt auf die Leinwand. Jede Übergabe bewegt echte Dateien oder echte Turns, keinen kopierten Textblock.

## Ein Arbeitsbereich, den die KI nutzen kann, ohne Ihre Dateien anzufassen

Der Chat-Modus erhält einen eigenen Arbeitsbereich auf der Festplatte. Die KI kann dort frei schreiben, lesen, ausführen und überarbeiten — Entwürfe, Skripte, Zwischendateien — ohne bei jedem Schritt um Erlaubnis zu fragen und ohne in Ihre Ordner hineinzugreifen. Sie müssen nie darüber nachdenken, wo das liegt; Sie bekommen einfach das Ergebnis, und Ihre eigenen Verzeichnisse bleiben unangetastet, solange Sie nicht selbst darauf verweisen.

## Sitzungen, die miteinander sprechen

Im Code-Modus kann eine Sitzung eine Frage oder ein Ergebnis an eine andere weitergeben — die Sitzung, die am Backend arbeitet, kann die fragen, die sich mit dem Frontend auskennt. Nachrichten kommen als echter Turn in der anderen Unterhaltung an. Sie öffnen den Kanal; nichts verbindet sich von selbst.

## Ihr Smartphone ist ein zweiter Bildschirm

Server einschalten und ULTRAI aus dem Browser eines Smartphones im selben Netzwerk öffnen. Das mobile Layout ist für Touch gebaut — Bottom Sheets und Bedienelemente in voller Breite — kein geschrumpfter Desktop. Unterhaltungen, Modelle und Einstellungen werden geteilt, sodass Sie genau dort weitermachen, wo Sie aufgehört haben.

## Machen Sie es zu Ihrem

Alles Folgende ist eine einfache Datei auf Ihrer Festplatte, die Sie lesen, bearbeiten und versionieren können.

- **Agents** — `~/.ultrai/agents/*.md`. Das Frontmatter entscheidet über alles: in welchen Modi der Agent erscheint, welche Tools er nutzen darf, welche Prompt-Abschnitte er erhält, welche Funktionen (Recherche, Ziele, Interview) ihm erlaubt sind. Bearbeitung über Settings, und eingebaute Agenten können jederzeit auf ihren Originalzustand zurückgesetzt werden.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Wiederverwendbare Anweisungen, die das Modell heranziehen kann oder die Sie als Slash-Befehl aufrufen können. Jede einzeln ein- oder ausschaltbar.
- **Prompt-Module** — der System-Prompt wird aus einem Katalog zusammengesetzt, und das Frontmatter jedes Agenten wählt aus, welche Abschnitte er erhält. Wird nichts deklariert, ist der Prompt des Agenten byteidentisch mit dem Standard; per Opt-in lässt sich verändern, wie er denkt. Jeder Modus bringt seinen eigenen, für diese Art von Arbeit gebauten Prompt mit, statt eines einzigen Prompts, der für alles zurechtgebogen wird.
- **MCP-Server** — deklariert in `ultrai.jsonc`. Lokal oder remote, mit Auth wo nötig, pro Server umschaltbar.
- **Memory** — geführt in drei Kategorien (über Sie, Themen, Bereiche), Zusammenfassungen werden eingespeist und Details bei Bedarf abgerufen, mit einem periodischen Aufräumdurchgang, der Duplikate und Widersprüche zusammenführt. Nur im Chat-Modus, und Sie können jeden Eintrag in Settings einsehen und löschen.
- **Provider** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter und benutzerdefinierte Endpunkte, mit Ihren eigenen Schlüsseln.

## Ihre Daten bleiben auf Ihrem PC

Unterhaltungen und Einstellungen werden **ausschließlich auf Ihrem Rechner** gespeichert. Es gibt keinen ULTRAI-Server — Ihre Unterhaltungen gehen nur an den KI-Provider, den Sie selbst verbunden haben, mit Ihrem eigenen Schlüssel.

Es wird nichts erfasst, und es gibt keine Telemetrie.

## Schnellstart

1. **Provider verbinden** — Ihren API-Schlüssel unter Settings → Providers hinzufügen.
2. **Modell wählen** — Modell und Reasoning-Effort befinden sich rechts in der Eingabeleiste.
3. **Modus wählen** — die Tabs oben in der Seitenleiste.
4. **Loslegen** — im Code-Modus einen Ordner öffnen; in den anderen Modi einfach anfangen zu schreiben.
5. **Etwas abgeben** — sagen Sie „fasse jeden Abend meinen Tag zusammen", und die App übernimmt das eigenständig.

## Tech-Stack

Eine native Windows-App auf Basis von Tauri 2. Die Oberfläche ist SolidJS; das Backend läuft als einzelne Binärdatei, die mit der App gebündelt ist.

## Feedback

Fehlerberichte und Funktionswünsche gehören zu den [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Lizenz

ULTRAI ist Freeware. Kostenlos für private und kommerzielle Nutzung. Der Quellcode ist nicht öffentlich verfügbar.

ULTRAI begann als Fork von [opencode](https://github.com/sst/opencode) und wurde weit darüber hinaus neu aufgebaut, enthält aber weiterhin Code von opencode, der MIT-lizenziert ist — Copyright (c) 2025 opencode. Die MIT-Lizenz ist vollständig in den mit der App ausgelieferten Hinweisen zitiert.
