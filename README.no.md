# ULTRAI

En Windows-skrivebordsapp for AI-arbeid som ikke stopper opp. Fire moduser i ett vindu — snakk, bygg i en ekte prosjektmappe, design på et lerret, generer bilder og video — pluss planlegging, kjøringer med flere agenter og telefonen som en ekstra skjerm.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Dette depotet er kun for **utgivelsesdistribusjon**. Kildekoden publiseres ikke her.

---

## Nedlasting

Windows 10/11 (x64). Krever WebView2-runtime, som allerede finnes på de fleste Windows-installasjoner.

**[Last ned nyeste utgivelse](https://github.com/UltraK18/ULTRAI/releases/latest)** — hent `ULTRAI_x.y.z_x64_en-US.msi` og kjør den.

Etter det tar appen seg av resten: den sjekker etter nye versjoner ved oppstart og med jevne mellomrom, varsler når en er tilgjengelig, og installerer den direkte.

## Fire moduser, ett vindu

Hver modus er en skjerm bygget for sitt formål, med egne verktøy og egne agenter — men det er én app, ett sett innstillinger, ett sted historikken din bor.

| Mode | The screen | What you do there |
| :--- | :--- | :--- |
| **Chat** | Samtale | Alle leverandører og modeller, resonneringsinnsats per melding, dyptgående research med kildehenvisninger, filer og bilder som input |
| **Code** | En ekte prosjektmappe | Filtre, differ i et gjennomgangspanel, en terminal ved siden av chatten, tillatelsesspørsmål før noe rører disken |
| **Design** | Livelerret + designeragent | Skjermer rendres ved siden av chatten mens de bygges; ferdig arbeid overleveres til Code som ekte filer |
| **Studio** | Fritt lerret + chat | Generer bilder og video, plasser og omorganiser dem, dra inn egne filer, og fortsett å bygge videre på det som er der |

Å bytte modus starter ikke noe på nytt — hver modus har sine egne samtaler, og sidepanelet viser bare dem som hører til der du er.

## Grensesnittet er selve poenget

De fleste verktøy på dette området er enten en terminal eller en nettside pakket inn i et skall. ULTRAI er en skrivebordsapp som er designet, ikke satt sammen.

- **Glass som faktisk er glass** — flytende flater kjører en liten rendringsmotor, ikke et blur-filter.
  Den baker et normalkart for kanten og tegner spekulære høylys ut fra det, og forskyver det som ligger
  bak flaten slik at kantene brytes. Kontroller som bryteren og glidebryteren går enda lenger og løser
  Snells brytningslov med en brytningsindeks og en tykkelse, slik at håndtaket bøyer sporet under seg.
  Dette klarer ikke en CSS-frost, og forskjellen synes langs hver eneste kant.
- **Squircle-hjørner** — panelene bruker en superellipse, ikke en sirkelbue, slik at kurven møter den
  rette kanten uten den flate overgangen `border-radius` gir.
- **To temaer, begge gjennomtenkte** — lys og mørk er bygget på én betongtonet palett med et svakt
  kjølig skjær, justert slik at ingenting er skarpt i noen av endene. Hver flate er et token, så hele
  appen beveger seg samlet i stedet for å drive fra hverandre per skjerm.
- **Bevisst tilbakeholdenhet** — ingen emoji noe sted i produktet, ingen utropstegn, ingen heiarop.
  Hvert panel har én flate; skillet skapes av kantlys og skygge, ikke av bokser tegnet inne i bokser.
- **Sømløst vindu** — en tittellinje på 32px i Windows 11-mål som deler bakgrunn med appen, slik at
  rammen ikke leses som en egen stripe over innholdet.
- **Mobil er et annet oppsett, ikke et mindre ett** — bunnark, kontroller i full bredde og trykkflater
  tilpasset fingeren, avgjort av enheten og ikke av vindusbredden.

## Generering, med ekte modeller

Studio er ikke ett enkelt bilde-endepunkt. Den velger fra en katalog for hver jobb og forteller deg hvilken modell den brukte og hvorfor.

- **Video** — Veo 3.1 og Veo 3.0 (pluss deres raske varianter), Sora 2 og Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Bilde** — GPT Image 2 og 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (og Flash Lite), Grok Imagine Image
- **Video inn, video ut** — gi den en eksisterende klipp som utgangspunkt, ikke bare en prompt
- **Den sjekker sitt eget arbeid** — henter bilder ut av det den nettopp genererte, ser på dem, og avgjør om den skal prøve på nytt
- **Lengde, bildeformat og kvalitet er dine valg** — ber du om 30 sekunder, er det 30 sekunder som blir bygget, i formatet du ba om

Hvilke modeller du når, avhenger av hvilke leverandørkontoer du kobler til (Vertex AI, OpenAI, xAI).

## ULTRA-modus — mange agenter, én oppgave

For arbeid som er for stort for én kontekst. ULTRA deler jobben opp i oppgaver, kjører dem gjennom flere agenter fase for fase, og lar resultatene bli **uavhengig verifisert før de slås sammen** — en kritiker og adversarielle sjekker, ikke samme agent som vurderer sitt eget arbeid. Du følger kjøringen og kan gripe inn når som helst. Modell og resonneringsinnsats settes per rolle, slik at en billig arbeider og en dyr verifikator bevisst kan være forskjellige leverandører.

## Den holder avtalene sine

Si «hver hverdag klokken 9» eller «om to timer», og det blir en ekte jobb, ikke et notat. Når tiden er inne, kommer oppgaven inn som en tur i samtalen, og AI-en begynner å jobbe med den.

- En kalender og en liste viser alt som er registrert; neste kjøring ligger nederst i sidepanelet
- Var appen lukket når noe skulle skje? Den regner ut hva som ble oversett og samler det i én innhentingskjøring
- `/loop` gjentar en oppgave så mange runder du velger

## Mål som AI-en ikke kan erklære fullført selv

Sett et mål for en samtale, og en uavhengig evaluering avgjør om det er fullført. Agenten som utfører arbeidet, får ikke selv bestemme at det er ferdig.

## Research som graver, og spørsmål før arbeidet starter

**Dyptgående research** planlegger vinklingene først, søker og leser deretter parallelt gjennom underagenter, og siterer det den finner. Vanlig søk er også uvanlig strengt: modellen får beskjed om å søke fremfor å gjette, å bruke dagens dato i stedet for et årstall hengende igjen fra treningen, og å verifisere påstander i nåtid før den svarer. Funn presenteres balansert, med kilder rett i teksten.

**Dybdeintervju** — når en forespørsel er for vagt formulert, gjør den samtalen om til et strukturert intervju og fastslår hva du faktisk vil ha, før noe arbeid starter.

## Arbeid som fortsetter mens du gjør noe annet

Lange jobber holder ikke vinduet som gissel.

- **Bakgrunnskjøringer** — gi fra deg en oppgave, og den kjører isolert, enten som en forgrening av
  samtalen eller som en underagent, og kan be om mer tillatelse underveis hvis den støter på en hindring.
- **En sanntidsmonitor** — en linje nederst viser alt som er i gang samtidig: dine egne bakgrunnsoppgaver,
  andre som er startet et annet sted, kjørende underagent-kall, ULTRA-kjøringer og eventuelle
  skallkommandoer som har holdt på en stund. Klikk deg inn på den du vil følge med på.
- **Forgren en samtale** — grei ut fra hvilket som helst punkt for å prøve noe uten å miste originalen,
  og hopp mellom grener fra meldingsindeksen.

## Overlevering mellom moduser

Arbeid blir ikke sittende fast i modusen det startet i. Design overleverer ferdige skjermer til Code som ekte filer på disk. Code-sesjoner sender spørsmål og resultater til hverandre. Studio plasserer det en agent har produsert, rett på lerretet. Hver overlevering flytter faktiske filer eller faktiske turer, ikke en kopiert tekstblokk.

## Et arbeidsområde AI-en kan bruke uten å røre filene dine

Chat-modus får sitt eget skisseområde på disk. AI-en kan skrive, lese, kjøre og redigere ting der fritt — utkast, skript, mellomliggende filer — uten å be om tillatelse for hvert steg, og uten å strekke seg inn i mappene dine. Du trenger aldri å tenke på hvor det er; du får bare resultatet, og dine egne mapper forblir urørt med mindre du selv peker på dem.

## Sesjoner som snakker sammen

I Code-modus kan én sesjon gi et spørsmål eller et resultat videre til en annen — den som jobber med backend, kan spørre den som kan frontend. Meldinger kommer inn som en ekte tur i den andre samtalen. Du åpner kanalen selv; ingenting kobler seg til av seg selv.

## Telefonen din er en ekstra skjerm

Slå på serveren og åpne ULTRAI fra en telefonnettleser på samme nettverk. Mobiloppsettet er bygget for touch — bunnark og kontroller i full bredde — ikke et nedskalert skrivebordsoppsett. Samtaler, modeller og innstillinger deles, slik at du fortsetter nøyaktig der du slapp.

## Gjør den til din egen

Alt under er en vanlig fil på disken din, som du kan lese, redigere og versjonere.

- **Agenter** — `~/.ultrai/agents/*.md`. Frontmatter avgjør alt: hvilke moduser agenten dukker opp i, hvilke verktøy den kan bruke, hvilke promptseksjoner den får, og hvilke funksjoner (research, mål, intervju) den har tilgang til. Rediger fra Innstillinger, og innebygde agenter kan tilbakestilles til originalen når som helst.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Gjenbrukbare instruksjoner modellen kan trekke inn selv, eller som du kan kalle opp som en skråstrek-kommando. Slå hver enkelt av eller på.
- **Promptmoduler** — systempromptet settes sammen fra en katalog, og hver agents frontmatter velger hvilke seksjoner den får. Erklærer du ingenting, er agentens prompt byte-for-byte identisk med standarden; velger du å slå på moduler, endrer det hvordan den tenker. Hver modus leveres med sitt eget prompt bygget for akkurat den typen arbeid, i stedet for ett prompt bøyd til å passe alt.
- **MCP-servere** — deklareres i `ultrai.jsonc`. Lokale eller eksterne, med autentisering der det trengs, og kan slås av og på per server.
- **Hukommelse** — holdes i tre bøtter (om deg, temaer, områder), der sammendrag settes inn og detaljer hentes ved behov, med en periodisk opprydding som slår sammen duplikater og motsigelser. Kun i chat-modus, og du kan se og slette hver eneste oppføring fra Innstillinger.
- **Leverandører** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter og egendefinerte endepunkter, med dine egne nøkler.

## Dataene dine blir på din PC

Samtaler og innstillinger lagres **kun på din egen maskin**. Det finnes ingen ULTRAI-server — samtalene dine går bare til AI-leverandøren du selv har koblet til, med din egen nøkkel.

Ingenting samles inn, og det finnes ingen telemetri.

## Kom i gang

1. **Koble til en leverandør** — legg til API-nøkkelen din under Innstillinger → Leverandører.
2. **Velg en modell** — modell og resonneringsinnsats finner du til høyre for inntastingsfeltet.
3. **Velg en modus** — fanene øverst i sidepanelet.
4. **Begynn å jobbe** — åpne en mappe i Code-modus; i de andre modusene er det bare å begynne å skrive.
5. **Gi fra deg noe** — si «oppsummer dagen min hver kveld», så tar den seg av det selv.

## Tech Stack

En nativ Windows-app bygget på Tauri 2. Grensesnittet er SolidJS; backend kjører som en enkelt binærfil pakket sammen med appen.

## Tilbakemeldinger

Feil og funksjonsønsker meldes inn under [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Lisens

ULTRAI er freeware. Gratis for privat og kommersiell bruk. Kildekoden er ikke offentlig tilgjengelig.

ULTRAI startet som en fork av [opencode](https://github.com/sst/opencode) og har siden blitt bygget godt
utover det, men inneholder fortsatt opencode-kode, som er MIT-lisensiert — Copyright (c) 2025 opencode.
MIT-lisensen er gjengitt i sin helhet i lisensvarslene som følger med appen.
