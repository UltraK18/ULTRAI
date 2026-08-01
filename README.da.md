# ULTRAI

En Windows-desktopapp til AI-arbejde, der bliver ved. Fire tilstande i ét vindue — tal, byg i en rigtig projektmappe, design på et lærred, generér billeder og video — samt planlægning, kørsler med flere agenter og din telefon som en ekstra skærm.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Dette repository er kun til **udgivelsesdistribution**. Kildekoden er ikke offentliggjort her.

---

## Download

Windows 10/11 (x64). Kræver WebView2-runtime, som allerede findes i de fleste Windows-installationer.

**[Download den seneste udgivelse](https://github.com/UltraK18/ULTRAI/releases/latest)** — hent `ULTRAI_x.y.z_x64_en-US.msi`, og kør den.

Derefter klarer appen sig selv: den tjekker for nye versioner ved opstart og løbende, gør opmærksom på det, når en er tilgængelig, og installerer den på stedet.

## Fire tilstande, ét vindue

Hver tilstand er en formålsbygget skærm med sine egne værktøjer og sine egne agenter — men én app, ét sæt indstillinger, ét sted hvor din historik ligger.

| Tilstand | Skærmen | Hvad du gør der |
| :--- | :--- | :--- |
| **Chat** | Samtale | Enhver udbyder og model, ræsoneringsindsats pr. besked, deep research med kildehenvisninger, filer og billeder ind |
| **Code** | En rigtig projektmappe | Filtræ, diffs i et review-panel, en terminal ved siden af chatten, tilladelsesprompter før noget rører disken |
| **Design** | Live lærred + designer-agent | Skærme renderes ved siden af chatten, mens de bygges; det færdige arbejde overdrages til Code som rigtige filer |
| **Studio** | Frit lærred + chat | Generér billeder og video, placér og omarrangér dem, træk dine egne filer ind, bliv ved med at videreudvikle det, der allerede er der |

Skift af tilstand genstarter ikke noget — hver tilstand har sine egne samtaler, og sidebjælken viser dem, der hører til der, hvor du er.

## Interfacet er selve pointen

De fleste værktøjer i dette felt er enten en terminal eller en webside i en wrapper. ULTRAI er en
desktopapp, der er designet, ikke samlet.

- **Glas, der rent faktisk er glas** — svævende flader kører en lille renderingsmotor, ikke et
  blurfilter. Den bager et normal map til kanten og tegner spekulære highlights ud fra det, og
  forskyder det, der ligger bag fladen, så kanterne bryder lyset. Kontroller som kontakten og
  skyderen går et skridt videre og løser Snells brydningslov med et brydningsindeks og en tykkelse,
  så håndtaget bøjer sporet under sig. Det kan en CSS-frost ikke, og forskellen ses på hver eneste kant.
- **Squircle-hjørner** — paneler bruger en superellipse i stedet for en cirkelbue, så kurven glider
  ind i den lige kant uden den flade overgang, man får med `border-radius`.
- **To temaer, begge gennemtænkte** — lys og mørk er bygget på én betontonet palet med et svagt
  køligt skær, afstemt så intet skærer i øjnene i nogen af retningerne. Enhver flade er et token, så
  hele appen bevæger sig samlet i stedet for at glide fra hinanden skærm for skærm.
- **Bevidst tilbageholdenhed** — ingen emoji noget sted i produktet, ingen udråbstegn, ingen
  heppekor-tone. Hvert panel har én enkelt flade; adskillelse kommer fra kantlys og skygge frem for
  kasser tegnet inde i kasser.
- **Sømløst vindue** — en 32px titelbjælke i Windows 11-formatet, der deler baggrund med appen, så
  rammen ikke opleves som en separat stribe over indholdet.
- **Mobil er et andet layout, ikke et mindre** — bundark, kontroller i fuld bredde og et
  touch-tilpasset klikområde, afgjort af enheden frem for vinduets bredde.

## Generering, med rigtige modeller

Studio er ikke ét enkelt billed-endpoint. Den vælger fra et katalog for hver opgave og fortæller dig, hvilken model den brugte, og hvorfor.

- **Video** — Veo 3.1 og Veo 3.0 (plus deres fast-varianter), Sora 2 og Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Billede** — GPT Image 2 og 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (og Flash Lite), Grok Imagine Image
- **Video ind, video ud** — giv den et eksisterende klip som input, ikke kun en prompt
- **Den tjekker selv sit eget arbejde** — trækker billeder ud af det, den har genereret, ser på dem og afgør, om der skal genforsøges
- **Længde, billedformat og kvalitet er dine valg** — bad du om 30 sekunder, er det 30 sekunder, der bliver bygget, i det format du bad om

Hvilke modeller du kan nå, afhænger af de udbyderkonti, du forbinder (Vertex AI, OpenAI, xAI).

## ULTRA-tilstand — mange agenter, én opgave

Til arbejde, der er for stort til én kontekst. ULTRA bryder opgaven ned i tasks, kører dem på tværs af agenter fase for fase, og lader resultaterne **verificere uafhængigt, før de flettes sammen** — en kritiker og modstridende kontroller, ikke den samme agent der bedømmer sit eget arbejde. Du følger kørslen og kan gribe ind når som helst. Model og ræsoneringsindsats sættes pr. rolle, så en billig worker og en dyr verifikator bevidst kan være forskellige udbydere.

## Den holder sine aftaler

Sig "hver hverdag kl. 9" eller "om to timer", og det bliver til en rigtig opgave, ikke en note. Når tiden er inde, ankommer opgaven som en tur i den samtale, og AI'en går i gang med den.

- En kalender og en liste viser alt, hvad der er registreret; den næste kørsel ligger nederst i sidebjælken
- Var appen lukket, da noget skulle køre? Den regner ud, hvad den gik glip af, og samler det i én indhentningskørsel
- `/loop` gentager en opgave så mange runder, som du angiver

## Mål, som AI'en ikke selv kan erklære færdige

Sæt et mål for en samtale, og en uafhængig evaluering afgør, om det er fuldført. Den agent, der udfører arbejdet, bestemmer ikke selv, hvornår det er færdigt.

## Research, der graver, og spørgsmål før arbejdet

**Deep research** lægger vinklerne først og søger og læser derefter parallelt på tværs af sub-agenter og henviser til det, den finder. Almindelig søgning er også usædvanligt streng: modellen er instrueret i at søge frem for at gætte, i at bruge dagens dato i stedet for et årstal hængt fast fra træningen, og i at verificere nutidige påstande, før den svarer. Resultater præsenteres afbalanceret, med kilder angivet direkte i teksten.

**Deep interview** — når en forespørgsel er underspecificeret, gør den samtalen til et struktureret interview og fastlægger, hvad du egentlig vil have, før noget arbejde går i gang.

## Arbejde, der kører, mens du gør noget andet

Lange opgaver holder ikke vinduet som gidsel.

- **Baggrundskørsler** — overdrag en opgave, og den kører isoleret, enten som en fork af samtalen
  eller som en sub-agent, og kan bede om flere tilladelser undervejs, hvis den støder på en mur.
- **En live-monitor** — en bjælke i bunden viser alt, hvad der er i gang på én gang: dine egne
  baggrundsopgaver, dem startet andre steder, kørende sub-agent-kald, ULTRA-kørsler og enhver
  shell-kommando, der har kørt et stykke tid. Klik ind på den, du vil følge.
- **Fork en samtale** — forgren fra et hvilket som helst punkt for at prøve noget uden at miste
  originalen, og hop mellem grene fra beskedindekset.

## Overdragelse mellem tilstande

Arbejde sidder ikke fast i den tilstand, det startede i. Design overdrager færdige skærme til Code
som rigtige filer på disken. Code-sessioner sender spørgsmål og resultater til hinanden. Studio
placerer det, en agent har produceret, direkte på lærredet. Hver overdragelse flytter faktiske filer
eller faktiske ture, ikke en kopieret tekstblok.

## Et arbejdsrum, AI'en kan bruge uden at røre dine filer

Chat-tilstand får sit eget scratch-space på disken. AI'en kan skrive, læse, køre og revidere ting der
frit — udkast, scripts, mellemliggende filer — uden at spørge om tilladelse ved hvert skridt og uden
at række ind i dine mapper. Du behøver aldrig tænke på, hvor det ligger; du får bare resultatet, og
dine egne mapper forbliver urørte, medmindre du selv peger på dem.

## Sessioner, der taler sammen

I Code-tilstand kan én session sende et spørgsmål eller et resultat videre til en anden — den, der arbejder på backend, kan spørge den, der kender frontend. Beskeder ankommer som en rigtig tur i den anden samtale. Du åbner kanalen; intet forbinder sig selv.

## Din telefon er en ekstra skærm

Tænd serveren, og åbn ULTRAI fra en telefonbrowser på samme netværk. Mobil-layoutet er bygget til touch — bundark og kontroller i fuld bredde — ikke en formindsket desktop. Samtaler, modeller og indstillinger deles, så du fortsætter præcis, hvor du slap.

## Gør den til din egen

Alt nedenfor er en almindelig fil på din disk, som du kan læse, redigere og versionere.

- **Agenter** — `~/.ultrai/agents/*.md`. Frontmatter afgør alt: hvilke tilstande den optræder i, hvilke værktøjer den må bruge, hvilke promptafsnit den får, hvilke funktioner (research, mål, interview) den har adgang til. Rediger fra Indstillinger, og indbyggede agenter kan til enhver tid gendannes til deres oprindelige form.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Genbrugelige instruktioner, som modellen kan trække ind, eller som du selv kan kalde som en slash-kommando. Slå hver enkelt til eller fra.
- **Promptmoduler** — systemprompten samles fra et katalog, og hver agents frontmatter vælger, hvilke afsnit den får. Erklærer du intet, er agentens prompt byte-identisk med standarden; tilvælg for at ændre måden, den tænker på. Hver tilstand leverer sin egen prompt, bygget til netop den slags arbejde, i stedet for én prompt bøjet til at passe til alt.
- **MCP-servere** — deklareres i `ultrai.jsonc`. Lokale eller eksterne, med godkendelse hvor nødvendigt, kan slås til pr. server.
- **Hukommelse** — opbevares i tre kategorier (om dig, emner, områder), hvor resuméer indsprøjtes, og detaljer hentes ved behov, med en periodisk oprydning, der samler dubletter og modsigelser. Kun i Chat-tilstand, og du kan se og slette hver eneste post fra Indstillinger.
- **Udbydere** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter og brugerdefinerede endpoints, med dine egne nøgler.

## Dine data bliver på din pc

Samtaler og indstillinger gemmes **kun på din egen maskine**. Der findes ingen ULTRAI-server — dine samtaler går kun til den AI-udbyder, du selv har forbundet, med din egen nøgle.

Der indsamles intet, og der er ingen telemetri.

## Kom hurtigt i gang

1. **Forbind en udbyder** — tilføj din API-nøgle under Indstillinger → Udbydere.
2. **Vælg en model** — model og ræsoneringsindsats findes til højre for inputfeltet.
3. **Vælg en tilstand** — fanerne øverst i sidebjælken.
4. **Gå i gang** — åbn en mappe i Code-tilstand; i de andre tilstande skal du bare begynde at skrive.
5. **Overdrag en opgave** — sig "opsummer min dag hver aften", og den tager over af sig selv.

## Teknologistak

En native Windows-app bygget på Tauri 2. Brugerfladen er SolidJS; backenden kører som en enkelt binær fil, der leveres sammen med appen.

## Feedback

Fejl og funktionsønsker sendes til [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licens

ULTRAI er freeware. Gratis til privat og kommerciel brug. Kildekoden er ikke offentligt tilgængelig.

ULTRAI begyndte som en fork af [opencode](https://github.com/sst/opencode) og er siden blevet
genopbygget langt ud over det, men indeholder stadig opencode-kode, som er MIT-licenseret —
Copyright (c) 2025 opencode. MIT-licensen er gengivet i fuld ordlyd i de meddelelser, der følger med
appen.
