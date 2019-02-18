# Jakie podejście użyć?

## Protractor

1. Zalety
   - tworzony przez twórców Angular
   - obsługa Angular digest loop
   - synchronizacja z component life cycle w Angular
   - wolno się rozwija (nie trzeba się uczyć dużo)
2. Wady
   - dokumentacja często nieaktualna
   - opóżnienia w implementacji nowości
   - wolno się rozwija (niektóre rzeczy trzeba hackować)

## Testcafe

1. Zalety
   - javascript
   - możliwość obsługi bez selenium
   - bez selenium nie obsługuje wszystkich przeglądarek
   - przyszłość dla E2E i testów funkcjonalnych
2. Wady
   - nie wszystkie przeglądarki

## Selenium

1. Zalety
   - java
   - najnowsze zmiany od razu
   - wszystkie platformy, dla których jest webdriver
   - integracja z appium (przeglądarki mobilne)
2. Wady
   - java (długa składnia, testerzy muszą znać technologie frontendowe i backendowe)
