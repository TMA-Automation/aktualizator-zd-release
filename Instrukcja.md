# Aktualizator ZD — instrukcja

Aplikacja czyta **oferty** i **potwierdzenia zamówień** (PDF) od dostawców i wpisuje
do arkusza ZD (eksport z enova):

- **ceny** — kolumny `Cena`, `NettoCy`, `Suma.VATCy`, `BruttoCy`,
- **terminy** — kolumna `Features.Prognozowana data dostawy`.

Rozpoznaje dokumenty: Festo (oferty i potwierdzenia), OMRON, SMC, MISUMI, AMTEK,
HARTING, TME, Sonepar, PF Electronic, eurobolt, PIKMET, Dźwignia, GPL, SCHUNK, Elesa+Ganter,
Alutec.
Dokumenty innych dostawców czyta w **trybie ogólnym** — wtedy wszystko, co znajdzie,
oznacza jako „do sprawdzenia”.

Do arkusza zawsze trafia **cena jednostkowa po rabacie** — także wtedy, gdy dokument liczy
wartość pozycji od ceny przed rabatem, a rabat odejmuje dopiero w podsumowaniu (np.
Elesa+Ganter). Jeśli w trybie ogólnym dokument wspomina o rabacie, a przy pozycjach nie
ma ceny po rabacie, pod listą dokumentów pojawia się ostrzeżenie — sprawdź wtedy ceny.

## W skrócie

1. Karta **Dokumenty** — dodaj PDF-y z ofertami i potwierdzeniami, a niżej wskaż arkusz ZD.
2. Kliknij **Wczytaj i porównaj**.
3. Karta **Podgląd zmian** — przejrzyj zmiany; pozycje wymagające uwagi są na górze.
4. Jeśli pojawi się pomarańczowy pasek — **Przejdź do konfliktów** i podejmij decyzje.
5. **Zapisz do Excela** — wskaż, gdzie i pod jaką nazwą zapisać wynik (domyślnie nowy plik
   obok oryginału).

Instrukcję otwiera odnośnik **Instrukcja** w prawym górnym rogu okna albo klawisz **F1**.

## 1. Dokumenty

- **Dodaj PDF-y…** — wybór plików; **Wskaż folder…** — wszystkie PDF-y z folderu;
  **Usuń zaznaczony** — usuwa dokument z listy (plik na dysku zostaje).
- Przy każdym dokumencie od razu widać, co aplikacja rozpoznała: dostawcę, typ (oferta /
  potwierdzenie), numer, datę, walutę i liczbę pozycji. Pomarańczowy wpis „nieznany — tryb
  ogólny” oznacza dostawcę bez profilu.
- **Ceny w dok.** — informacja, jakie ceny podaje dokument: `netto`, `brutto` albo
  `netto i brutto` (`—`, gdy dokument nie ma cen).
- **Wpisz do Excela** — kliknij w komórkę i wybierz z listy. Do wyboru jest tylko to, co jest
  w dokumencie: przy samym netto — tylko `netto` (`Cena`, `NettoCy`); przy samym brutto —
  tylko `brutto` (`Suma.VATCy`, `BruttoCy`); przy obu — także `oba` (wszystkie cztery
  kolumny, wprost z liczb dokumentu). Kolumny, których dokument nie dotyczy, zostają
  w arkuszu bez zmian.
- Zaznacz kilka dokumentów (Ctrl/Shift) i kliknij w komórkę jednego z nich — wybór dotyczy
  wszystkich zaznaczonych. Dokumenty bez potrzebnych cen są pomijane (komunikat w pasku
  stanu).
- **Podwójny klik** w dokument otwiera jego podgląd PDF.
- Pod tabelą pojawiają się ostrzeżenia zaznaczonego dokumentu, np. „brak możliwości
  wykonania”.
- **Arkusz z listą pozycji ZD** — przycisk **Wybierz…** wskazuje plik Excel (eksport ZD).

## 2. Podgląd zmian

Jeden wiersz na kod towaru.

- **✓** — które pozycje zapisać. **Zaznacz wszystkie** / **Odznacz wszystkie** działa na całą
  listę.
- **Pewność**: ✔ — dane pewne (znany dostawca, kod zgodny); ⚠ — **do sprawdzenia** (kod
  z dopiskiem, kod znaleziony w opisie, nieznany dostawca, cena zmienia się o więcej niż 30 %).
  Pozycje ⚠ są **domyślnie odznaczone** — zaznacz je ręcznie, jeśli się zgadzają.
  Kod zapisany inaczej — bez myślników i spacji (`3SU10000AB100AA0` = `3SU1000-0AB10-0AA0`)
  albo z zerami wiodącymi (`0026101` = `26101`) — u znanego dostawcy jest pewny; szczegóły
  pokazują wtedy „Informacja: kod zapisany inaczej”. W trybie ogólnym zostaje ⚠.
- **Ilość dok. / ZD** — ilość z dokumentu i **suma** ilości ze wszystkich wierszy ZD z tym
  kodem, np. `59,863 / 59,863 m` dla profilu pociętego na 32 odcinki. Gdy sumy się nie
  zgadzają, na końcu jest `≠`, pozycja trafia do wymagających uwagi, a szczegóły podają
  różnicę. Ceną jednostkową z dokumentu zostają uzupełnione wszystkie te wiersze.
- **Cena było / jest / Różnica** — ▲ drożej, ▼ taniej, „nowa”, gdy w arkuszu było 0.
- **Data było / jest** — gdy oferta podaje czas realizacji („2-3 tygodnie”), data jest
  liczona od daty dokumentu i oznaczona „(z czasu real.)”. Potwierdzenie zamówienia ma
  pierwszeństwo przed ofertą.
- **Zmiana terminu** — 🙂 dostawa wcześniej niż w planie; 🙁 później, ale nie więcej niż
  próg (domyślnie 30 dni); 😞 później o więcej niż próg. Próg ustawia się za kołem ⚙.
- Pod tabelą są **szczegóły** zaznaczonego wiersza: dokument, strona, fragment z PDF i powód
  ewentualnego „do sprawdzenia”.
- **Podgląd PDF** — podwójny klik w wiersz (albo przycisk **Pokaż w PDF**) otwiera dokument
  na stronie tej pozycji, z czerwoną ramką wokół niej. Okno można zostawić otwarte obok
  (np. na drugim monitorze) — kolejna pozycja otworzy się w nim.
- **Kolejność i filtry** — pozycje wymagające uwagi (⚠, cena w konflikcie albo różna ilość)
  są na górze. Lista **Pokaż** zawęża tabelę do: wymagających uwagi, zmian cen, zmian dat,
  różnej ilości albo pozycji bez zmian; lista **Dokument** — do jednego pliku. **Szukaj** obejmuje kod, nazwy, ZD
  i nazwę dokumentu. Kliknięcie nagłówka sortuje po kolumnie.

## 3. Konflikty

- Karta pojawia się tylko wtedy, gdy aplikacja nie potrafi rozstrzygnąć czegoś sama;
  w nazwie karty widać liczbę otwartych, np. „Konflikty (1)”.
- Dopóki zostaje choć jeden nierozstrzygnięty, **zapis jest zablokowany** — na karcie
  „Podgląd zmian” widać wtedy pomarańczowy pasek z przyciskiem **Przejdź do konfliktów**.
- Przy opcjach z ceną przycisk **PDF** pokazuje tę pozycję w dokumencie.
- Gdy kod jest w kilku wierszach arkusza (różne BOM-y / złożenia), cenę można wybrać
  **osobno dla każdego wiersza** — opis wiersza podaje BOM, złożenie i ilość.

## 4. Zapis do Excela

- Po kliknięciu **Zapisz do Excela** aplikacja pyta, **gdzie i pod jaką nazwą** zapisać wynik.
  Podpowiada nowy plik obok oryginału: `<nazwa> — zaktualizowany RRRR-MM-DD_GGMM.xlsx` —
  wystarczy kliknąć „Zapisz”. Można też wybrać inny folder i wpisać własną nazwę.
- Oryginał zostaje nietknięty, a aplikacja dalej pracuje na zapisanym pliku (kolejne
  porównanie, np. z następną ofertą, buduje na nim).
- Wybranie **samego oryginału** zapisuje w miejscu — przed zapisem powstaje kopia zapasowa
  `<nazwa> — kopia RRRR-MM-DD_GGMM.xlsx`.
- **Anuluj** w oknie zapisu niczego nie zapisuje.
- Plik, który zapis zastępuje, musi być **zamknięty w Excelu** w chwili zapisu.

## Kiedy aplikacja pyta

| Sytuacja | Co znaczy |
|---|---|
| K1 — kod z dokumentu nie występuje w arkuszu | Potwierdzenie dotyczy innego zamówienia albo kod zapisano inaczej |
| K2 — kody arkusza nie występują w potwierdzeniach | Zwykle arkusz obejmuje więcej niż jedno zamówienie — normalne |
| K3 — niezgodna ilość | Liczba sztuk w potwierdzeniu nie zgadza się z sumą w arkuszu |
| K4 — kilka dat na jednej pozycji | Dostawa częściowa — wybierz, którą datę wpisać |
| K5 — różne daty w kilku potwierdzeniach | Wybierz właściwą |
| K6 — inna waluta | Dokument jest np. w EUR, a wiersz w PLN. Domyślnie cena jest pomijana; można wpisać ją w walucie dokumentu (zmieni się waluta wiersza) |
| K7 — dwie ceny jednego kodu w jednym dokumencie | Np. różne rabaty w dwóch sekcjach oferty — wybierz właściwą, także osobno dla każdego wiersza arkusza |
| K8 — różne ceny w kilku dokumentach | Domyślnie podpowiadana cena z najnowszego dokumentu |

## Ustawienia (⚙)

- **Źródło aktualizacji** — GitHub albo udział sieciowy (z repozytorium, ścieżką i nazwą
  pliku).
- **Domyślny folder roboczy** — folder, w którym otwierają się okna wyboru PDF-ów i arkusza.
- **Próg opóźnienia (dni)** — powyżej tylu dni opóźnienie jest oznaczane na czerwono (😞).

## Aktualizacje

Aplikacja sama sprawdza dostępność nowszej wersji i pokazuje żółty pasek z przyciskiem
„Pobierz i zainstaluj”. Przy braku dostępu do sieci lub repozytorium aplikacja milczy — to
normalne, nie jest błędem.

## Instalacja

1. Skopiuj `AktualizatorZD.exe` do **`C:\AktualizatorZD\`**.
2. Na pulpicie utwórz **skrót** do tego pliku.

**Nie uruchamiaj pliku z OneDrive, Pulpitu ani Dokumentów.** W firmie Pulpit i Dokumenty są
przekierowane do OneDrive, a aplikacja rozpakowuje się przy każdym starcie — OneDrive
potrafi zablokować ten proces i pojawia się błąd „Failed to load Python DLL” albo
„Permission denied”. Aplikacja sama ostrzega, gdy wykryje taką lokalizację.

## Gdy coś nie działa

- **„Failed to load Python DLL”** — plik uruchomiony z OneDrive (patrz wyżej) albo brak
  Microsoft Visual C++ 2015–2022 x64 (https://aka.ms/vs/17/release/vc_redist.x64.exe).
- **Ostrzeżenie SmartScreen** — „Więcej informacji → Uruchom mimo to”. Wraca po każdej
  aktualizacji, dopóki plik nie jest podpisany cyfrowo.
- **Plik pobrany z internetu jest zablokowany** — kliknij prawym na `.exe` → Właściwości →
  Odblokuj.
- **„Nie mogę zapisać pliku”** — plik docelowy jest otwarty w Excelu. Zamknij go i spróbuj
  ponownie; żadne dane nie zostają utracone.
- **„Nie rozpoznano żadnej pozycji”** — dokument nieznanego dostawcy, w którym nie ma
  żadnego kodu z arkusza, albo znany dostawca zmienił układ dokumentu. Zgłoś z załączonym
  PDF-em — dodanie profilu dostawcy to niewielka zmiana.
