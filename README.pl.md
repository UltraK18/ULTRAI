# ULTRAI

Aplikacja desktopowa dla Windows do pracy z AI, która nie przestaje działać. Cztery tryby w jednym oknie — rozmowa, tworzenie w prawdziwym folderze projektu, projektowanie na płótnie, generowanie obrazów i wideo — a do tego harmonogramy, uruchomienia wieloagentowe i telefon jako drugi ekran.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> To repozytorium służy wyłącznie do **dystrybucji wydań**. Kod źródłowy nie jest tu publikowany.

---

## Pobieranie

Windows 10 / 11 (x64). Wymaga środowiska WebView2, które jest już obecne w większości instalacji Windows.

**[Pobierz najnowsze wydanie](https://github.com/UltraK18/ULTRAI/releases/latest)** — pobierz plik `ULTRAI_x.y.z_x64_en-US.msi` i uruchom go.

Później aplikacja radzi sobie sama: sprawdza dostępność nowych wersji przy uruchomieniu i okresowo, informuje, gdy jest dostępna nowa wersja, i instaluje ją na miejscu.

## Cztery tryby, jedno okno

Każdy tryb to ekran zaprojektowany do konkretnego celu, z własnymi narzędziami i własnymi agentami — ale jedna aplikacja, jeden zestaw ustawień, jedno miejsce, w którym żyje twoja historia.

| Mode | Ekran | Co tam robisz |
| :--- | :--- | :--- |
| **Chat** | Rozmowa | Dowolny dostawca i model, poziom wysiłku rozumowania dla każdej wiadomości, dogłębne badania z cytowaniami, pliki i obrazy na wejściu |
| **Code** | Prawdziwy folder projektu | Drzewo plików, różnice (diffy) w panelu przeglądu, terminal obok czatu, prośby o uprawnienia zanim cokolwiek dotknie dysku |
| **Design** | Płótno na żywo + agent projektowy | Ekrany renderują się obok czatu w miarę powstawania; gotowa praca trafia do Code jako prawdziwe pliki |
| **Studio** | Swobodne płótno + czat | Generuj obrazy i wideo, umieszczaj je i przestawiaj, dodawaj własne pliki, iteruj dalej nad tym, co już jest |

Przełączenie trybu niczego nie restartuje — każdy tryb zachowuje własne rozmowy, a pasek boczny pokazuje te, które należą do miejsca, w którym aktualnie jesteś.

## Interfejs jest sednem

Większość narzędzi w tej dziedzinie to terminal albo strona internetowa w opakowaniu. ULTRAI to aplikacja desktopowa, która została zaprojektowana, a nie złożona z gotowych elementów.

- **Szkło, które naprawdę jest szkłem** — pływające powierzchnie działają na małym silniku renderującym, a nie filtrze rozmycia. Wypieka mapę normalnych dla ramki i na jej podstawie rysuje odbicia lustrzane, a także przesuwa to, co znajduje się za powierzchnią, tak by krawędzie załamywały światło. Kontrolki takie jak przełącznik czy suwak idą dalej i rozwiązują załamanie zgodnie z prawem Snella, uwzględniając współczynnik załamania i grubość, dzięki czemu uchwyt wygina leżący pod nim tor. Mgiełka CSS tego nie potrafi, a różnica widoczna jest na każdej krawędzi.
- **Narożniki typu squircle** — panele wykorzystują superelipsę, a nie łuk kołowy, dzięki czemu krzywizna wchodzi w prostą krawędź bez płaskiego odcinka, jaki daje `border-radius`.
- **Dwa motywy, oba przemyślane** — jasny i ciemny zbudowane są na jednej palecie w tonacji betonu z lekkim chłodnym odcieniem, dostrojonej tak, by nic nie raziło na żadnym z krańców. Każda powierzchnia to token, więc cała aplikacja zmienia się spójnie, zamiast dryfować ekran po ekranie.
- **Celowy umiar** — żadnych emoji w całym produkcie, żadnych wykrzykników, żadnego dopingowania. Każdy panel ma jedną powierzchnię; rozdzielenie osiągane jest przez światło konturowe i cień, a nie przez ramki rysowane wewnątrz ramek.
- **Bezszwowe okno** — pasek tytułu o wysokości 32px w formacie Windows 11, który dzieli tło z resztą aplikacji, dzięki czemu obudowa nie wygląda jak osobny pasek nad treścią.
- **Mobile to inny układ, nie mniejsza wersja tego samego** — arkusze dolne, kontrolki na pełną szerokość i obszary dotykowe o odpowiednim rozmiarze, dobierane na podstawie urządzenia, a nie szerokości okna.

## Generowanie na prawdziwych modelach

Studio to nie jeden punkt końcowy do obrazów. Dla każdego zadania wybiera z katalogu i informuje, którego modelu użył i dlaczego.

- **Wideo** — Veo 3.1 i Veo 3.0 (oraz ich szybkie warianty), Sora 2 i Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Obraz** — GPT Image 2 i 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (oraz Flash Lite), Grok Imagine Image
- **Wideo na wejściu, wideo na wyjściu** — jako dane wejściowe możesz podać istniejący klip, nie tylko prompt
- **Sprawdza własną pracę** — wyciąga klatki z tego, co wygenerował, ogląda je i decyduje, czy spróbować ponownie
- **Długość, proporcje i jakość zależą od ciebie** — poprosisz o 30 sekund, dostaniesz 30 sekund, w kształcie, o jaki poprosiłeś

To, które modele są dla ciebie dostępne, zależy od kont dostawców, które podłączysz (Vertex AI, OpenAI, xAI).

## Tryb ULTRA — wielu agentów, jedno zadanie

Do pracy zbyt dużej dla jednego kontekstu. ULTRA dzieli zadanie na mniejsze taski, uruchamia je na agentach faza po fazie, a wyniki są **niezależnie weryfikowane przed scaleniem** — krytyk i kontrole adwersarialne, nie ten sam agent oceniający sam siebie. Możesz obserwować przebieg i włączyć się w dowolnym momencie. Model i poziom wysiłku rozumowania ustawiane są osobno dla każdej roli, więc tani wykonawca i drogi weryfikator mogą celowo pochodzić od różnych dostawców.

## Dotrzymuje terminów

Powiedz „każdego dnia roboczego o 9” albo „za dwie godziny”, a stanie się to prawdziwym zadaniem, nie notatką. Gdy nadejdzie czas, zadanie pojawia się jako kolejna wiadomość w tej rozmowie i AI zaczyna nad nim pracować.

- Kalendarz i lista pokazują wszystko, co zostało zarejestrowane; najbliższe uruchomienie widać na dole paska bocznego
- Aplikacja była zamknięta, gdy coś miało się odbyć? Program ustala, co przegapił, i łączy to w jedno zbiorcze uruchomienie nadrabiające zaległości
- `/loop` powtarza zadanie przez tyle rund, ile ustawisz

## Cele, których AI nie może samo uznać za ukończone

Ustaw cel dla rozmowy, a niezależna ocena będzie warunkiem jego ukończenia. Agent wykonujący pracę nie decyduje sam, że skończył.

## Badania, które drążą, i pytania przed rozpoczęciem pracy

**Dogłębne badania** planują kąty podejścia, po czym wyszukują i czytają równolegle na wielu subagentach oraz cytują to, co znalazły. Zwykłe wyszukiwanie też jest nietypowo rygorystyczne: model ma nakaz szukać zamiast zgadywać, używać dzisiejszej daty zamiast roku zapamiętanego z treningu i weryfikować twierdzenia w czasie teraźniejszym przed udzieleniem odpowiedzi. Wyniki przedstawiane są bezstronnie, ze źródłami wplecionymi w tekst.

**Dogłębny wywiad** — gdy prośba jest niedoprecyzowana, zamienia rozmowę w ustrukturyzowany wywiad i ustala, czego naprawdę potrzebujesz, zanim zacznie się jakakolwiek praca.

## Praca, która toczy się, gdy robisz coś innego

Długie zadania nie biorą okna jako zakładnika.

- **Uruchomienia w tle** — przekaż zadanie, a wykona się w izolacji, jako rozgałęzienie (fork) rozmowy albo jako subagent, i może poprosić o dodatkowe uprawnienia w trakcie, jeśli napotka ścianę.
- **Monitor na żywo** — pasek na dole pokazuje jednocześnie wszystko, co jest w toku: twoje własne zadania w tle, te uruchomione gdzie indziej, działające wywołania subagentów, uruchomienia ULTRA oraz każde polecenie powłoki, które trwa już jakiś czas. Kliknij, by przejść do dowolnego z nich.
- **Rozgałęź rozmowę** — odgałęź się w dowolnym punkcie, by coś wypróbować bez utraty oryginału, i przeskakuj między gałęziami z poziomu indeksu wiadomości.

## Przekazywanie pracy między trybami

Praca nie zostaje uwięziona w trybie, w którym się zaczęła. Design przekazuje gotowe ekrany do Code jako prawdziwe pliki na dysku. Sesje Code przekazują sobie nawzajem pytania i wyniki. Studio umieszcza to, co wytworzył agent, wprost na płótnie. Każde przekazanie przenosi rzeczywiste pliki albo rzeczywiste wiadomości, a nie skopiowany fragment tekstu.

## Przestrzeń robocza, z której AI korzysta bez dotykania twoich plików

Tryb Chat ma własną przestrzeń roboczą na dysku. AI może tam swobodnie pisać, czytać, uruchamiać i poprawiać rzeczy — szkice, skrypty, pliki pośrednie — bez pytania cię o zgodę na każdym kroku i bez sięgania do twoich folderów. Nigdy nie musisz się zastanawiać, gdzie to jest; po prostu dostajesz wynik, a twoje własne katalogi pozostają nietknięte, chyba że sam na nie wskażesz.

## Sesje, które rozmawiają ze sobą

W trybie Code jedna sesja może przekazać pytanie lub wynik innej — ta pracująca nad backendem może zapytać tę, która zna frontend. Wiadomości docierają jako prawdziwa wiadomość w drugiej rozmowie. To ty otwierasz kanał; nic nie łączy się samo.

## Twój telefon jako drugi ekran

Włącz serwer i otwórz ULTRAI z przeglądarki telefonu w tej samej sieci. Układ mobilny jest zaprojektowany pod dotyk — arkusze dolne i kontrolki na pełną szerokość — a nie zmniejszoną wersję desktopu. Rozmowy, modele i ustawienia są współdzielone, więc kontynuujesz dokładnie tam, gdzie skończyłeś.

## Dostosuj do siebie

Wszystko poniżej to zwykłe pliki na twoim dysku, które możesz czytać, edytować i wersjonować.

- **Agenci** — `~/.ultrai/agents/*.md`. Frontmatter decyduje o wszystkim: w jakich trybach się pojawia, z jakich narzędzi może korzystać, jakie sekcje promptu otrzymuje, jakie funkcje (badania, cele, wywiad) są mu dozwolone. Edytuj z poziomu Ustawień, a wbudowanych agentów w każdej chwili można przywrócić do stanu oryginalnego.
- **Umiejętności (Skills)** — `~/.ultrai/skills/*/SKILL.md`. Wielokrotnego użytku instrukcje, które model może dociągnąć samodzielnie albo które ty możesz wywołać jako polecenie ze slashem. Każdą można włączyć lub wyłączyć osobno.
- **Moduły promptu** — prompt systemowy jest składany z katalogu, a frontmatter każdego agenta wybiera, które sekcje otrzymuje. Nic nie deklarujesz — prompt agenta jest identyczny co do bajtu z domyślnym; włączasz moduły, by zmienić sposób myślenia agenta. Każdy tryb ma własny prompt zbudowany pod ten rodzaj pracy, zamiast jednego promptu naginanego do wszystkiego.
- **Serwery MCP** — deklarowane w `ultrai.jsonc`. Lokalne lub zdalne, z uwierzytelnianiem tam, gdzie potrzebne, przełączane osobno dla każdego serwera.
- **Pamięć** — przechowywana w trzech kategoriach (o tobie, tematy, obszary), streszczenia są wstrzykiwane, a szczegóły pobierane na żądanie, z okresowym porządkowaniem, które scala duplikaty i sprzeczności. Dostępna tylko w trybie Chat; każdy wpis możesz zobaczyć i usunąć w Ustawieniach.
- **Dostawcy** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter oraz własne endpointy, z twoimi własnymi kluczami.

## Twoje dane pozostają na twoim komputerze

Rozmowy i ustawienia są przechowywane **wyłącznie na twoim komputerze**. Nie ma serwera ULTRAI — twoje rozmowy trafiają wyłącznie do dostawcy AI, którego sam podłączyłeś, przy użyciu twojego własnego klucza.

Nic nie jest zbierane i nie ma żadnej telemetrii.

## Szybki start

1. **Podłącz dostawcę** — dodaj swój klucz API w Ustawienia → Dostawcy.
2. **Wybierz model** — model i poziom wysiłku rozumowania znajdują się po prawej stronie paska wprowadzania.
3. **Wybierz tryb** — zakładki u góry paska bocznego.
4. **Zacznij pracę** — otwórz folder w trybie Code; w pozostałych trybach po prostu zacznij rozmawiać.
5. **Zleć zadanie** — powiedz „podsumowuj mój dzień każdego wieczoru”, a program przejmie to samodzielnie.

## Stos technologiczny

Natywna aplikacja Windows zbudowana na Tauri 2. Interfejs jest w SolidJS; backend działa jako pojedynczy plik binarny dołączony do aplikacji.

## Opinie

Zgłoszenia błędów i propozycje funkcji trafiają do [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licencja

ULTRAI jest freeware. Darmowe do użytku osobistego i komercyjnego. Kod źródłowy nie jest publicznie dostępny.

ULTRAI zaczęło się jako fork [opencode](https://github.com/sst/opencode) i zostało odbudowane daleko poza jego pierwotny zakres, ale wciąż zawiera kod opencode, który jest objęty licencją MIT — Copyright (c) 2025 opencode.
Pełna treść licencji MIT jest zacytowana w informacjach prawnych dołączonych do aplikacji.
