# Cvičení: Zkracování a map
## Zkracovací jednohubky

aložte si obyčejnou stránku s JavaScriptem, bez Vite i bez JSX. Můžete použít následující kód (šablona `html-css-js` nepoužívá Vite ani JSX):

```shell
npm init kodim-app@latest cviceni-zkracovaci-jednohubky html-css-js
```

Následující funkce přepište do zkráceného zápisu. Vlastními slovy popište, k čemu nejspíše funkce slouží.

1.  ```js
    const isEmail = (str) => {
      return str.includes('@');
    };
    ```
1.  ```js
    const roll = () => {
      return Math.floor(Math.random() * 6) + 1;
    };
    ```
1.  ```js
    const getNumber = (id) => {
      return Number(document.querySelector(`#${id}`).value);
    };
    ```
1.  ```js
    const weather = (temperature) => {
      if (temperature > 16) {
        return 'teplo';
      }

      return 'zima';
    };
    ```

    **Nápověda:** Použijte ternární operátor.

## Opakování map

Založte si obyčejnou stránku s JavaScriptem, bez Vite i bez JSX:

```shell
npm init kodim-app@latest cviceni-opakovani-map html-css-js
```

Do souboru `index.js` si zkopírujte následující pole.

```js
const weekdays = [
  'pondělí',
  'úterý',
  'středa',
  'čtvrtek',
  'pátek',
  'sobota',
  'neděle',
];
const months = [
  {
    name: 'leden',
    days: 31,
  },
  {
    name: 'únor',
    days: 28,
  },
  {
    name: 'březen',
    days: 31,
  },
  {
    name: 'duben',
    days: 30,
  },
  {
    name: 'květen',
    days: 31,
  },
  {
    name: 'červen',
    days: 30,
  },
  {
    name: 'červenec',
    days: 31,
  },
  {
    name: 'srpen',
    days: 31,
  },
  {
    name: 'září',
    days: 30,
  },
  {
    name: 'říjen',
    days: 31,
  },
  {
    name: 'listopad',
    days: 30,
  },
  {
    name: 'prosinec',
    days: 31,
  },
];
```

Všechny body níže vyřešte pomocí metody `map`. Tam, kde je to možné, použijte zkrácený zápis funkcí. Výsledky vypisujte do konzole pomocí `console.log`.

1. Z pole `weekdays` vyrobte pole obsahující všechny názvy dnů napsané VELKÝMI PÍSMENY.
1. Z pole `weekdays` vyrobte pole obsahující pouze první dvě písmena každého dne, tedy
   ```js
   ['po', 'út', 'st' /* atd. */];
   ```
1. Z pole `months` vyrobte pole obsahující pouze počty dní v každém měsíci.
1. Z pole `months` vyrobte pole obsahující pro každý měsíc datum jeho prvního dne v roce 2020, tedy
   ```js
   ['1. leden 2020', '1. únor 2020' /* atd. */];
   ```

# Cvičení: Zobrazování seznamů
## Česká města

1. Založte si Vite/JSX projekt:

```shell
npm init kodim-app@latest cviceni-ceska-mesta jsx
```

1. Do souboru `index.jsx` vložte mimo komponentu pole s názvy deseti největších českých měst.
   ```js
   const cities = [
     'Praha',
     'Brno',
     'Ostrava',
     'Plzeň',
     'Liberec',
     'Olomouc',
     'České Budějovice',
     'Hradec Králové',
     'Ústí nad Labem',
     'Pardubice',
   ];
   ```
1. Z pole `cities` pomocí funkce `map` vyrobte pole JSX elementů. Každý JSX element nechť má následující strukturu.
   ```js
   <div className="city">Název města</div>
   ```
   Výsledné pole uložte do proměnné `cityElements`.
1. Použijte pole `cityElements` uvnitř komponenty JSX a zobrazte jej tak na vaší stránce.
1. Zbavte se proměnné `cityElements` a funkci `map` použijte přímo uvnitř komponenty JSX.
1. V konzoli si JSX bude stěžovat, že chybí `key` prop. Máme však štěstí, jména měst jsou unikátní. Můžeme tak na náš `div` přidat prop `key` a do něj poslat přímo název města.

## Česká města 2
Pokračujte v projektu z předchozího příkladu.

1.  Do pole `cities` si uložte obsáhlejší data o českých městech.
    ```js
    const cities = [
      {
        name: 'Praha',
        population: 1324277,
        area: 496.21,
      },
      {
        name: 'Brno',
        population: 381346,
        area: 230.18,
      },
      {
        name: 'Ostrava',
        population: 287968,
        area: 214.23,
      },
      {
        name: 'Plzeň',
        population: 174842,
        area: 137.67,
      },
      {
        name: 'Liberec',
        population: 104802,
        area: 106.09,
      },
      {
        name: 'Olomouc',
        population: 100663,
        area: 103.33,
      },
      {
        name: 'České Budějovice',
        population: 94463,
        area: 55.6,
      },
      {
        name: 'Hradec Králové',
        population: 92939,
        area: 105.69,
      },
      {
        name: 'Ústí nad Labem',
        population: 92716,
        area: 93.97,
      },
      {
        name: 'Pardubice',
        population: 91727,
        area: 82.66,
      },
    ];
    ```
1.  Upravte kód vaší aplikace tak, aby u každého města zobrazoval kromě názvu také počet obyvatel a rozlohu v kilometrech.
1.  Jako `key` prop opět použijte název města.
1.  Vytvořte komponentu `City`, jejímž úkolem bude zobrazovat jedno město. Tato komponenta bude mít props `name`, `population` a `area`. Použijte komponentu k zobrazení každého města ze seznamu.
1.  Pro komponentu `City` vytvořte vlastní složku a komponentu malinko nastylujte, aby vypadala hezky.