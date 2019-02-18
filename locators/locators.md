# Locators

Locators pozwalają nam znaleźć dany element na stronie. W zależności od frameworku możemy używać różnych rodzajów locatorów, natomiast 2 typy są najbardziej popularne:

1. xPath
2. CSS selectors

## xPath

- ciężkie do pisania i rozumienia przez człowieka, natomiast można je automatycznie generować za pomocą narzędzi developerskich google chrome lub firefox.
- często są używane do przeszukiwania dokumentów XML, dlatego poniekąd warto wiedzieć jak działają.

[Materiały](https://developer.mozilla.org/pl/docs/Web/XPath)

## CSS selectors

- pochodzą bezpośrednio z CSS, co oznacza, że każdy frontend developer je bardzo dobrze zna. Łatwe, przejrzyste, za pomocą narzędzie developerskich google chrome lub firefox lub IE można je łatwo generować, debugować i optymalizować.

Zasady:

```css

nazwa
/* wyszukiwanie po nazwie html tag */

.nazwa
/* wyszukiwanie po klasie html (<tag class="nazwa"></tag>) */

#nazwa
/* wyszukiwanie po identyfikatorze tagu html (<tag id="nazwa"></tag>) */

*[data="nazwa"]
/* wyszukiwanie po atrybucie, często do aplikacji dodaje się tag data-bdd, w celu zabezpieczenia selektorów przed zmianą html */

```

Selektory CSS można zagnieżdzać i łączyć ze sobą. Co powoduje, że istnieje ich hierarchia. Główną zasadą jest to, że zwycięża najbardziej dokładny, specyficzny selektor.

## Waga selectora (od najmniej ważnego)

1. Nazwa taga
2. Klasa taga
3. ID taga
4. Klauzula !important, podnośi ważność dowolnego selektora
5. Inline selektor
6. Js selector
7. Asynchronous Js selector

## Generowanie CSS selektorów

1. Otwórz aplikację w przeglądarce
2. Otwórz narzędzia developerskie
3. Zaznacz interesujący cię tag w zakładce Elements
4. Na tagu prawy przycisk myszy (menu)
5. Copy selector -> Css Selector

## Testowanie CSS selektorów

1. Otwórz aplikację w przeglądarce
2. Otwórz narzędzia developerskie
3. Otwórz zakładkę elements w narzędziach developerskich
4. Ctrl+F (wyszukiwanie)
5. Wklej swój selektor lub zacznij pisać
6. Narzędzia developerskie podświetlą wszystkie pasujące dopasowania

## Ćwiczenie selektorów CSS

[Dinner selector](https://flukeout.github.io/)

## Materiały o selektorach

[CSS](https://www.w3schools.com/cssref/css_selectors.asp)
