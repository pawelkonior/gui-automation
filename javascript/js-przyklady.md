# Przykłady kodu

## Przykład 1

```javascript
function foo() {
  Promise.resolve().then(console.log(1));

  setTimeout(() => console.log(2), 0);

  Promise.resolve().then(console.log(3));

  console.log(4);
}

foo();

console.log(5);
```

1. Kod, który nie jest w całości JS:
   - Promise - API, które w połowie jest wykonywane po stronie silnika JS, a w połowie po stronie hosta (przeglądarka, nodejs)
   - console.log - API narzędzi developerskim, tak na prawdę to funkcjonalność terminala
   - setTimeout - funkcjonalności hosta, Timer
2. Kolejność wykonywania kodu jest zależna od jego typu
   1. Pierwsze kod synchroniczny
   2. Następnie kody asynchroniczny:
      1. Pierwsze kod promise based
      2. Następnie wszystkie callbacki

## Przykład 2

```javascript

function \*gen(){
console.log(1)
let a = 10
yield a
console.log(2)
let b = yield a
console.log(3)
yield b
console.log(4)
}

const g = gen()
g.next()
g.next()
g.next(5)
g.next()

```

1. Przykład generatora zaimplementowanego w js
2. Przykład pokazujący możliwość przekazania danych wewnątrz generatora
3. Generatory są zamrażane, co znaczy że mogą być lazy evaluated, do momentu, kiedy nie poprosimy o kolejne dane, żadne kalkulacje nie są wykonywane, co daje dużą optymalizację wydajności
4. Generatory świetnie nadają się do pracy ze streamami danych (Reactive programming, Event Driven Development, Dependency Injection, Subscriber/Observer pattern)

## Przykład 3

```javascript

function \*data(){
const data = yield fetch(url)
console.log(data)
}

const g = data()
const futureData = g.next()
futureData.value.then(response => g.next(response))

```

```javascript
async function data() {
  const data = await fetch(url);
  console.log(data);
}
```

1. Implementacja synchronicznego zapisu kodu asynchronicznego za pomocą generatora
2. Automatyzacja zapisu za pomocą async/await, oraz wytłumaczenie dlaczego await zawsze musi być przed obiektem typu promise
