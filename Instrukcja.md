# Potwierdzenie zamówienia — instrukcja

Aplikacja przepisuje daty dostaw z PDF-ów potwierdzeń zamówień Festo do kolumny
`Features.Prognozowana data dostawy` w arkuszu z listą pozycji ZD.

## Instalacja

1. Skopiuj `PotwierdzenieZamowienia.exe` do **`C:\PotwierdzenieZamowienia\`**.
2. Na pulpicie utwórz **skrót** do tego pliku.

**Nie uruchamiaj pliku z OneDrive, Pulpitu ani Dokumentów.** W firmie Pulpit
i Dokumenty są przekierowane do OneDrive, a aplikacja rozpakowuje się przy każdym
starcie — OneDrive potrafi zablokować ten proces i pojawia się błąd
„Failed to load Python DLL" albo „Permission denied". Aplikacja sama ostrzega,
gdy wykryje taką lokalizację. Wspólny plik ustawień (w `%APPDATA%`) może
zostać na OneDrive — problem dotyczy wyłącznie samego pliku `.exe`.

## Praca z aplikacją

1. **Pliki** — dodaj jedno lub kilka potwierdzeń PDF i wskaż arkusz Excel.
   Jeśli w folderze roboczym jest dokładnie jeden plik `.xlsx`, aplikacja
   podpowie go automatycznie.
2. **Wczytaj i porównaj** — aplikacja czyta dokumenty i przygotowuje plan zmian.
3. **Podgląd zmian** — sprawdź, co zostanie wpisane. Zieleń oznacza wpis w pustą
   komórkę, kolor zwykły nadpisanie istniejącej daty, szary brak zmiany.
4. **Konflikty** — karta pojawia się tylko wtedy, gdy aplikacja nie potrafi
   rozstrzygnąć czegoś sama. Dopóki zostaje choć jeden nierozstrzygnięty,
   zapis jest zablokowany.
5. **Zapisz do Excela** — przed zapisem powstaje kopia zapasowa obok oryginału,
   nazwana `<nazwa> — kopia RRRR-MM-DD_GGMM.xlsx`.

Arkusz musi być **zamknięty w Excelu** w chwili zapisu.

## Kiedy aplikacja pyta

| Sytuacja | Co znaczy |
|---|---|
| Kod z PDF nie występuje w arkuszu | Potwierdzenie dotyczy innego zamówienia albo kod zapisano inaczej |
| Kody arkusza nie występują w PDF | Zwykle arkusz obejmuje więcej niż jedno zamówienie — normalne |
| Niezgodna ilość | Liczba sztuk w potwierdzeniu nie zgadza się z sumą w arkuszu |
| Kilka dat na jednej pozycji | Dostawa częściowa — wybierz, którą datę wpisać |
| Ten sam kod w dwóch potwierdzeniach | Różne daty w różnych zamówieniach — wybierz właściwą |

## Aktualizacje

Aplikacja sama sprawdza dostępność nowszej wersji i pokazuje żółty pasek
z przyciskiem „Pobierz i zainstaluj". Źródło aktualizacji (GitHub albo udział
sieciowy) ustawia się za kołem ⚙. Przy braku dostępu do sieci lub repozytorium
aplikacja milczy — to normalne, nie jest błędem.

Po kliknięciu „Pobierz i zainstaluj" aplikacja zamknie się i uruchomi ponownie
w nowej wersji.

## Gdy coś nie działa

- **„Failed to load Python DLL"** — plik uruchomiony z OneDrive (patrz wyżej) albo
  brak Microsoft Visual C++ 2015–2022 x64
  (https://aka.ms/vs/17/release/vc_redist.x64.exe).
- **Ostrzeżenie SmartScreen** — „Więcej informacji → Uruchom mimo to". Wraca po
  każdej aktualizacji, dopóki plik nie jest podpisany cyfrowo.
- **Plik pobrany z internetu jest zablokowany** — kliknij prawym na `.exe` →
  Właściwości → Odblokuj. Dotyczy też sytuacji, gdy firmowa polityka blokuje
  pliki `.exe` w folderze Pobrane — przenieś plik poza Pobrane.
- **„Nie mogę zapisać pliku"** — arkusz jest otwarty w Excelu. Zamknij go
  i spróbuj ponownie; żadne dane nie zostają utracone.
- **„Nie rozpoznano żadnej pozycji"** — to nie jest potwierdzenie Festo albo
  dostawca zmienił układ dokumentu. Zgłoś z załączonym PDF-em.
