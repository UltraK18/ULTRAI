# ULTRAI

Desktop aplikacija za Windows namijenjena AI radu koji se ne zaustavlja. Četiri moda u jednom prozoru — razgovor, izgradnja u stvarnom projektnom folderu, dizajniranje na platnu, generisanje slika i videa — uz zakazivanje, izvršavanje sa više agenata i vaš telefon kao drugi ekran.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Ovaj repozitorij služi **isključivo za distribuciju izdanja**. Izvorni kod ovdje nije objavljen.

---

## Preuzimanje

Windows 10 / 11 (x64). Zahtijeva WebView2 runtime, koji je već prisutan na većini Windows instalacija.

**[Preuzmite najnovije izdanje](https://github.com/UltraK18/ULTRAI/releases/latest)** — preuzmite `ULTRAI_x.y.z_x64_en-US.msi` i pokrenite ga.

Nakon toga aplikacija se sama brine o sebi: provjerava nove verzije pri pokretanju i periodično, obavještava vas kada je nova verzija dostupna i instalira je na licu mjesta.

## Četiri moda, jedan prozor

Svaki mod je namjenski dizajniran ekran sa vlastitim alatima i vlastitim agentima — ali jedna aplikacija, jedan skup postavki, jedno mjesto gdje živi vaša historija.

| Mode | Ekran | Šta tamo radite |
| :--- | :--- | :--- |
| **Chat** | Razgovor | Bilo koji provider i model, nivo napora razmišljanja po poruci, dubinsko istraživanje sa citatima, prilaganje fajlova i slika |
| **Code** | Pravi projektni folder | Stablo fajlova, razlike (diff) u panelu za pregled, terminal pored chata, upiti za dozvolu prije nego što bilo šta dotakne disk |
| **Design** | Platno uživo + agent za dizajn | Ekrani se renderuju pored chata dok se grade; gotov rad se prosljeđuje u Code kao stvarni fajlovi |
| **Studio** | Slobodno platno + chat | Generišite slike i video, postavljajte i raspoređujte ih, dodajte vlastite fajlove, nastavite iterirati na onome što već postoji |

Prebacivanje moda ništa ne restartuje — svaki mod čuva vlastite razgovore, a bočna traka prikazuje one koji pripadaju modu u kojem se trenutno nalazite.

## Interfejs je poenta

Većina alata u ovom prostoru su terminal ili web stranica u omotaču (wrapper). ULTRAI je desktop aplikacija koja je dizajnirana, a ne sastavljena.

- **Staklo koje je zaista staklo** — plutajuće površine pokreće mali rendering engine, ne blur filter.
  On peče (bake) normal mapu za rub i iz nje crta spekularne odsjaje, te pomjera ono što se nalazi
  iza površine tako da se ivice prelamaju. Kontrole poput prekidača i klizača idu i dalje — rješavaju
  Snellovo prelamanje pomoću indeksa prelamanja i debljine, tako da se klizač savija zajedno sa trakom
  ispod sebe. CSS frost efekat to ne može, i razlika se vidi na svakoj ivici.
- **Squircle uglovi** — paneli koriste superelipsu, a ne kružni luk, tako da kriva ulazi u ravnu ivicu
  bez ravnog dijela koji dobijete sa `border-radius`.
- **Dvije teme, obje namjerne** — svijetla i tamna tema izgrađene su na jednoj paleti u tonovima
  betona sa blagim hladnim nijansama, podešene tako da ništa ne bode oči ni na jednom kraju. Svaka
  površina je token, pa se cijela aplikacija mijenja zajedno umjesto da svaki ekran ide svojim putem.
- **Namjerna suzdržanost** — nigdje u proizvodu nema emojija, uskličnika ni bodrenja. Svaki panel
  nosi jednu jedinstvenu površinu; razdvajanje dolazi od rubnog svjetla i sjene, a ne od kutija
  nacrtanih unutar kutija.
- **Bešavni prozor** — naslovna traka od 32px u Windows 11 mjeri koja dijeli pozadinu sa aplikacijom,
  tako da se okvir ne doživljava kao zasebna traka iznad sadržaja.
- **Mobilni prikaz je drugačiji raspored, ne samo manji** — donji paneli (bottom sheets), kontrole
  pune širine i dodirno prilagođena površina za interakciju, određeni uređajem, a ne širinom prozora.

## Generisanje, sa pravim modelima

Studio nije jedna jedina tačka za generisanje slika. On bira iz kataloga za svaki zadatak i kaže vam koji je model koristio i zašto.

- **Video** — Veo 3.1 i Veo 3.0 (plus njihove brze varijante), Sora 2 i Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Slika** — GPT Image 2 i 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (i Flash Lite), Grok Imagine Image
- **Video na ulazu, video na izlazu** — proslijedite postojeći klip kao ulaz, ne samo tekstualni upit
- **Provjerava vlastiti rad** — izvlači kadrove iz onoga što je generisao, pregleda ih i odlučuje da li da pokuša ponovo
- **Dužina, format i kvalitet su vaš izbor** — ako tražite 30 sekundi, dobijate tačno 30 sekundi, u obliku koji ste tražili

Koji su vam modeli dostupni zavisi od naloga providera koje povežete (Vertex AI, OpenAI, xAI).

## ULTRA mod — mnogo agenata, jedan zadatak

Za posao koji je prevelik za jedan kontekst. ULTRA razbija zadatak na manje dijelove, izvršava ih preko agenata fazu po fazu, i osigurava da su rezultati **nezavisno provjereni prije spajanja** — kritičar i adversarijalne provjere, a ne isti agent koji ocjenjuje sam sebe. Možete pratiti izvršavanje i intervenisati u bilo kojem trenutku. Model i nivo napora razmišljanja postavljaju se po ulozi, tako da jeftini izvršilac i skupi provjerivač namjerno mogu biti različiti provideri.

## Drži svoje termine

Recite "svakog radnog dana u 9" ili "za dva sata" i to postaje stvaran zadatak, ne bilješka. Kada se aktivira, zadatak stiže kao potez (turn) u tom razgovoru i AI počinje raditi na njemu.

- Kalendar i lista prikazuju sve registrovano; sljedeće izvršavanje nalazi se pri dnu bočne trake
- Bila aplikacija zatvorena kada je nešto trebalo pokrenuti? Ona utvrdi šta je propušteno i objedini to u jedno nadoknađujuće izvršavanje
- `/loop` ponavlja zadatak onoliko krugova koliko postavite

## Ciljevi koje AI ne može sam proglasiti završenim

Postavite cilj za razgovor i nezavisna evaluacija odlučuje o završetku. Agent koji obavlja posao ne odlučuje sam da je gotov.

## Istraživanje koje kopa dublje, i pitanja prije posla

**Deep research** prvo planira uglove pristupa, zatim pretražuje i čita paralelno preko pod-agenata i citira ono što je pronašao. Svakodnevna pretraga je takođe neuobičajeno stroga: model je instruisan da pretražuje umjesto da nagađa, da koristi današnji datum umjesto godine ostale iz treninga, i da provjeri tvrdnje u sadašnjem vremenu prije nego što odgovori. Nalazi se prezentuju nepristrasno, sa izvorima direktno u tekstu.

**Deep interview** — kada zahtjev nije dovoljno precizno definisan, razgovor se pretvara u strukturisani intervju koji utvrdi šta zapravo želite prije nego što posao počne.

## Posao koji se izvršava dok vi radite nešto drugo

Dugotrajni zadaci ne drže prozor taocem.

- **Izvršavanje u pozadini** — proslijedite zadatak i on se izvršava izolovano, kao fork razgovora ili
  kao pod-agent, i može zatražiti dodatnu dozvolu usred izvršavanja ako naiđe na prepreku.
- **Monitor uživo** — traka pri dnu prikazuje sve što je trenutno u toku: vaše vlastite pozadinske
  zadatke, one pokrenute negdje drugdje, aktivne pozive pod-agenata, ULTRA izvršavanja, i svaku shell
  komandu koja traje već neko vrijeme. Kliknite na bilo koji od njih da ga pratite.
- **Forkujte razgovor** — granajte se iz bilo koje tačke da isprobate nešto bez gubitka originala, i
  skačite između grana putem indeksa poruka.

## Prosljeđivanje između modova

Posao ne ostaje zaglavljen u modu u kojem je započet. Design prosljeđuje gotove ekrane u Code kao
stvarne fajlove na disku. Code sesije razmjenjuju pitanja i rezultate jedna s drugom. Studio postavlja
ono što je agent proizveo direktno na platno. Svako prosljeđivanje pomjera stvarne fajlove ili stvarne
poteze, ne kopirani blok teksta.

## Radni prostor koji AI može koristiti bez diranja vaših fajlova

Chat mod dobija vlastiti privremeni prostor na disku. AI tamo može slobodno pisati, čitati, izvršavati
i mijenjati stvari — skice, skripte, međufajlove — bez traženja dozvole na svakom koraku i bez
zadiranja u vaše foldere. Nikada ne morate razmišljati gdje se taj prostor nalazi; jednostavno dobijete
rezultat, a vaši vlastiti direktoriji ostaju netaknuti osim ako ih sami ne naznačite.

## Sesije koje razgovaraju jedna s drugom

U Code modu jedna sesija može proslijediti pitanje ili rezultat drugoj — ona koja radi na backendu može pitati onu koja poznaje frontend. Poruke stižu kao stvaran potez u drugom razgovoru. Vi otvarate kanal; ništa se ne povezuje samo od sebe.

## Vaš telefon je drugi ekran

Uključite server i otvorite ULTRAI iz browsera na telefonu koji je na istoj mreži. Mobilni raspored je napravljen za dodir — donji paneli i kontrole pune širine — a ne smanjena desktop verzija. Razgovori, modeli i postavke su dijeljeni, tako da nastavljate tačno tamo gdje ste stali.

## Prilagodite je sebi

Sve dolje navedeno je obični fajl na vašem disku koji možete čitati, uređivati i verzionisati.

- **Agents** — `~/.ultrai/agents/*.md`. Frontmatter određuje sve: u kojim modovima se pojavljuje, koje alate smije koristiti, koje sekcije prompta dobija, koje funkcije (istraživanje, ciljevi, intervju) su mu dozvoljene. Uređujte iz Settings, a ugrađeni agenti se u bilo kojem trenutku mogu vratiti na originalno stanje.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Instrukcije za ponovnu upotrebu koje model može uvući, ili ih vi možete pozvati kao slash komandu. Svaku možete pojedinačno uključiti ili isključiti.
- **Prompt modules** — sistemski prompt se sastavlja iz kataloga, a frontmatter svakog agenta bira koje sekcije dobija. Ako ništa ne deklarišete, agentov prompt je bajt-identičan zadanom; uključite se (opt in) da promijenite način razmišljanja. Svaki mod dolazi sa vlastitim promptom napravljenim za tu vrstu posla, umjesto jednog prompta savijenog da odgovara svemu.
- **MCP servers** — deklarisani u `ultrai.jsonc`. Lokalni ili udaljeni, sa autentifikacijom gdje je potrebna, uključivi/isključivi po serveru.
- **Memory** — čuva se u tri kategorije (o vama, teme, oblasti), sažeci se ubacuju automatski, a detalji se dohvataju na zahtjev, uz periodično čišćenje koje spaja duplikate i kontradikcije. Samo u Chat modu, a svaki unos možete vidjeti i obrisati iz Settings.
- **Providers** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter i prilagođeni (custom) endpointi, sa vašim vlastitim ključevima.

## Vaši podaci ostaju na vašem računaru

Razgovori i postavke se čuvaju **isključivo na vašem računaru**. Ne postoji ULTRAI server — vaši razgovori idu isključivo AI provideru kojeg ste sami povezali, koristeći vlastiti ključ.

Ništa se ne prikuplja, i ne postoji telemetrija.

## Brzi početak

1. **Povežite providera** — dodajte svoj API ključ pod Settings → Providers.
2. **Odaberite model** — model i nivo napora razmišljanja nalaze se s desne strane trake za unos.
3. **Odaberite mod** — kartice pri vrhu bočne trake.
4. **Počnite raditi** — otvorite folder u Code modu; u ostalim modovima, jednostavno počnite razgovarati.
5. **Proslijedite nešto** — recite "sažmi mi dan svake večeri" i aplikacija će to sama preuzeti.

## Tehnički stek

Nativna Windows aplikacija izgrađena na Tauri 2. Interfejs je rađen u SolidJS; backend se izvršava kao jedna binarna datoteka spojena sa aplikacijom.

## Povratne informacije

Greške i zahtjeve za nove funkcije prijavite na [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licenca

ULTRAI je freeware. Besplatan za ličnu i komercijalnu upotrebu. Izvorni kod nije javno dostupan.

ULTRAI je nastao kao fork projekta [opencode](https://github.com/sst/opencode) i od tada je nadograđen
daleko iznad njega, ali i dalje sadrži opencode kod, koji je pod MIT licencom — Copyright (c) 2025
opencode. MIT licenca je u cijelosti citirana u napomenama koje dolaze uz aplikaciju.
