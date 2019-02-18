# Execution model

Execution model to sposób w jaki kod JS będzie wykonywany, zrozumienie go jest niezbędne do poprawnego przewidywania co się stanie i kiedy w naszej aplikacji.

## Elementy

1. Silnik JS
2. Scope
3. Host
4. Event Loop
5. CallStack
6. Memory - C.E.V.E (context execution variable environment)
7. Global/Local execution context
8. Microtask queue (job queue)
9. Callback queue

## Silnik JS

- w zależności, gdzie nasz kod zostanie uruchomiony to różny silnik może zostać użyty, co komplikuje przewidywanie zachowania naszego kodu. Js to język interpretowany z just in time compilation, to oznacza, że na milisekundy przed uruchomieniem nasz kod jest poddawany analizie i optymalizacji.

## Scope

- funkcjonalność powiązana z C.E.V.E, która ma za zadanie dostarczanie do silnika danych istniejących w danych zasięgach. Temat się komplikuje, bo w Js mamy zasięg funkcyjny i blokowy. Funkcyjny to każda para klamerek funkcji (e.g function f(){}), blokowy to dowolna para klamerek.

## Host

- środowisko uruchomienia aplikacji, w związku z tym, że js nie posiada wielu funkcjonalności jak np. Timer, XmlHttpRequest, to host dostarcza tych funkcjonalności.

## Event Loop

- nieskończona pętla oparta na 4 warunkach. Po stronie callstack sprawdza czy nie ma nić na global context oraz czy cały global context jest wykonany. Kolejne warunki to czy microtask queue jest puste, a następnie czy callback queue jest puste.

## Callstack

- wskaźnik interpretera, informuje silnik, gdzie obecnie się znajduje.

## Memory

- pamięć RAM, w której trzymane są wszystkie referencje i wartości w aktualnie wykonywanym programie, które nie zostały usunięte przez garbage collector.

## Global Execution Context

- aktualnie wykonywany kod przez silnik js.

## Microtask queue

- kolejka, struktura danych FIFO, trafiają tutaj wszystkie promise based obiekty

## Callback queue

- kolejka, struktura danych FIFO, trafiają tutaj wszystkie callbacki
