# Úkol 6

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
