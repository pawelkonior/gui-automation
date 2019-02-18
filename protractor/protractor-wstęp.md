# Protractor

[Protractor strona główna](https://www.protractortest.org/#/)

Protractor to framework stworzony do obsługi aplikacji Angularowych, natomiast istnieje możliwość używania go również z innymi bibliotekami frontendowymi. Do działania niezbędny jest Selenium oraz Webdrivery do poszczególnych przeglądarek.

[Selenium](https://www.seleniumhq.org/)
[ChromeDriver](http://chromedriver.chromium.org)
[FFDriver](https://github.com/mozilla/geckodriver/releases)
[IEDriver](https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver)

## Instalacja

W nowych wersjach Angulara, Protractor jest dodawany automatycznie wraz z tworzeniem nowego projektu. Pozostaje tylko użyć. Aby go usunąć należy przejść do katalogu package.json i skasować wszystkie zależności, a następnie użyć komendy

```bash
npm i
# lub
yarn install

```

## Konfiguracja:

```javascript
// conf.js
exports.config = {
  framework: "jasmine",
  seleniumAddress: "http://localhost:4444/wd/hub",
  specs: ["spec.js"],
  multiCapabilities: [
    {
      browserName: "firefox"
    },
    {
      browserName: "chrome"
    }
  ]
};
```

## Użycie:

```bash
webdriver-manager update
webdriver-manager start
# nowe okno terminala
protractor conf.js

```

## Przykładowy kod

```javascript
describe("Protractor Demo App", function() {
  it("should add one and two", function() {
    browser.get("http://juliemr.github.io/protractor-demo/");
    // Uwaga używanie locatorów angularowych jest już niewspierane w nowych wersjach Angular
    element(by.model("first")).sendKeys(1);
    element(by.model("second")).sendKeys(2);

    element(by.id("gobutton")).click();

    expect(element(by.binding("latest")).getText()).toEqual("5"); // This is wrong!
  });
});
```

## Działanie protractor

Protractor to test runner, używa wyrażeń regularnych do wyszukiwania plików, w których znajdują się testy.

Testy powinny mieć następującą hierachie:

1. Plik - test suite
2. it() - test case
3. beforeAll/beforeEach - fixture
4. Wiele plików - test plan
5. Wybrane testy kluczowe dla działania aplikacja - smoke test

---

Budowa testu (metoda zwana 3A)

1. Arrange
2. Act
3. Assert
