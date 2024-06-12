# Cvičení: Lokální API server
## Správce odkazů

Při brouzdání internetem by se jistě leckomu mohla hodit aplikace, která bude spravovat různé internetové odkazy, abychom je nemuseli mít v tisíci záložkách v prohlížeči, které se pak bojíme zavřít. Základ takové aplikací si vytvoříme v této úloze.

Postupujte dle následujících kroků. Naši aplikaci nazveme originálně _Správce odkazů_.

1. Nejdříve vytvořte lokální API server pro náš projekt. Založte si někde na disku složku `odkazy-api` a otevřete ji ve VS Code.
1. V této složce vytvořte složku `api` a v ní soubor `links.json` a vložte do něj pole několika odkazů, abychom měli do začátku nějaká data. Rozmyslete si, jak by měl objekt jednoho odkazu vypadat. Určitě budeme chtít evidovat

   - URL na kterou odkaz míří, např. `https://www.seznam.cz`,
   - název odkazu, např. `Seznam`,
   - popis odkazu, např. `Nejlepší český vyhledávač`.
   - typ odkazu, např. `web`, `youtube video` apod.

   Sami si rozmyslete, jak se budou jednotlivé vlastnosti jmenovat a jaké hodnoty budou mít. Vytvořte si alespoň dva objekty s různými hodnotami.

1. **Nezapomeňte**, že každá položka musí být číselné `id`.
1. Rozeběhněte si lokální server pomocí `npx apidroid`. Otevřete si v prohlížeči stránku [http://localhost:4000/api/links](http://localhost:4000/api/links) a ověřte, že se vám zobrazují data z vašeho souboru.
1. Založte si nový Vite/JSX projekt pomocí `npm init kodim-app@latest spravce-odkazu jsx`. Otevřete si složku projektu v novém okně VS Code.
1. Na začátku souboru `index.jsx` proveďte `fetch`, který načte data z vašeho lokálního API serveru. Výsledek uložte do proměnné `links`. Pomocí `console.log` ověřte, že se vám data načetla.
1. Zobrazte odkazy na stránce pomocí `map`.
1. Vytvořte komponentu `StoredLink`, která bude zobrazovat jeden odkaz. Sami si rozmyslete, jaké bude mít komponenta `props` a lehce ji nastylujte, aby stránka trošku vypadala.
1. Zapojte komponentu `StoredLink` do stránky.

# Cvičení: Search parametry
## E-shop

Vytvořte aplikaci, která bude simulovat nějaký malý e-shop. E-shop bude mít dvě stránky, na jedné bude seznam produktů a na druhé detail jednoho produktu. Na stránce s produkty bude možné vybrat jeden produkt a přejít na jeho detail.

Toto cvičení je zadáno schválně vágněji a obecněji než jsme zvyklí, abyste měli příležitost se sami zamyslet nad strukturou aplikace.

1. Rozmyslete si, jaké produkty váš e-shop bude nabízet.
1. Založte lokální API server. Vytvořte v něm jednu kolekci dat s vašimi produkty. Sami si rozmyslete, jaké vlastnosti budou produkty mít. Nebojte se do dat vložit např. odkazy na obrázek produktu, který můžete sehnat někde na internetu. Server rozeběhněte pomocí `npx apidroid` a ověřte, že se vám data zobrazují v prohlížeči.
1. Založte si novou Vite/JSX aplikaci. Na úvodní stránce vytvořte hlavní komponentu `HomePage`, která bude zobrazovat seznam produktů. Vytvořte komponentu `Product`, která bude zobrazovat jeden produkt. Zapojte komponentu do stránky.
1. Každý produkt nechť zobrazuje tlačítko, které vás přesune na stránku `detail.html`. Stránce předejte search parametr s id produktu.
1. Vytvořte stránku `detail.html` s vlastním JavaScriptem `detail.jsx`. Vytvořte hlavní komponentu `ProductPage`, která zatím bude zobrazovat například pouze nadpis _Detail produktu_. Zapojte komponentu do stránky.
1. Na začátku souboru načtěte data produktu z API serveru pomocí `fetch`. K tomu bude potřeba si přečíst id produktu ze search parametru. Výsledek uložte do proměnné `product`.
1. V komponentě `ProductPage` zobrazte detail produktu podle dat ze serveru.
1. Aplikaci lehce nastylujte, aby vypadala jako e-shop.
1. Vyzkoušejte, že vaše aplikace funguje.
