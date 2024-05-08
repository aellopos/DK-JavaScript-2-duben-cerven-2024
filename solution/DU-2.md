# Úkol 2
Vyzkoušíme si rozdělit běžnou stránku do několika komponent.

1. Vytvořte si repozitář ze šablony [cviceni-jogini](https://github.com/Czechitas-podklady-WEB/cviceni-jogini) se stránkou pro začínající jóga studio.
1. Vytvořte si nový projekt pomocí známého postupu.
1. V oddělené složce vytvořte komponentu `Header`, která vytvoří hlavičku stránky. Bude očekávat svoje `props` v následujícím formátu.

   ```js
   {
     title: 'Jogíni',
   }
   ```

1. V další složce vytvořte komponentu `Intro` vytvářející úvodní text podle následujích props.

   ```js
   {
     heading: 'Vítejte mezi Jogíny',
     text: `Naše lekce jsou zaměřeny na potřeby klientů, kteří mají odvahu zkusit
            něco nového. Cvičíme v pomalém tempu s podrobným slovním doprovodem.
            Postupně se seznámíte se základními principy jógy, jak přístupovat k
            sobě i ostatním. Krok za krokem objevíte a dostanete pod kontrolu
            svoje tělo, pocity a emoce.`,
   }
   ```

1. Stejným způsobem vytvořte komponentu `Pose`, která vytváří HTML pro úvodní obrázek. Komponenta očekává takovéto props.
   ```js
   {
     src: 'img/yoga-pose.jpg',
   }
   ```

Na konci tohoto úkolu by měl element `body` v souboru `index.html` vypadat klasicky takto.

```html
<body>
  <div id="root"></div>
</body>
```

Obsah stránky by měl být vytvořen zcela pomocí komponent.