# Cvičení: Import/export
## Rádio

Vytvoříme web, kde na každé stránce zobrazíme detail jedné stanice rádia.

1. Založte si nový prázdný projekt jen se souborem `radio.js`.
1. V souboru založte datovou strukturu pro rádio. Každá stanice bude mít název, frekvenci, popis a odkaz. Např:
   ```js
   const radio = [
     {
       name: 'Evropa 2',
       frequency: '88.6 FM',
       description:
         'Evropa 2 je nejposlouchanější česká komerční rádio mezi mladými posluchači. Vysílá hudbu z žebříčků, kterou si sami vybírají posluchači a nejnovější hity.',
       link: '/evropa2.html',
     },
     {
       name: 'Frekvence 1',
       frequency: '102.1 FM',
       description:
         'Frekvence 1 je česká soukromá rozhlasová stanice, která vysílá od roku 1991. Vysílá hudbu z žebříčků, kterou si sami vybírají posluchači a nejnovější hity.',
       link: '/frekvence1.html',
     },
     {
       name: 'Radiožurnál',
       frequency: '92.6 FM',
       description:
         'Radiožurnál je česká rozhlasová stanice Českého rozhlasu. Vysílá hudbu z žebříčků, kterou si sami vybírají posluchači a nejnovější hity.',
       link: '/radiozurnal.html',
     },
   ];
   ```
1. Tuto datovou strukturu ze souboru `radio.js` správně exportujte.
1. Vytvořte stránku pro první stanici `evropa2.html` a na ni napojený soubor `evropa2.js`. V souboru `evropa2.js` importujte data ze souboru `radio.js` a pomocí JavaScriptu zobrazte na stráce stanici z nultého indexu pole. Použijte nějaké vhodné HTML elementy.
1. Nyní vytvoříme pro náš web navigaci. V `evropa2.html` vytvořte hlavičku `<header>`. V souboru `evropa2.js` vytvořte funkci `renderNavigation`, pomocí které vykreslíte do hlavičky stránky navigaci s odkazy na jednotlivé stanice. Použijte k tomu funkci `forEach`.
1. Vytvořte stránky pro zbylé dvě stanice. Pro každou vytvořte příslušný HTML soubor a soubor s JavaScriptem. V JavaScriptu vždy zobrazte na stránce příslušnou stanici. Stačí zkopírovat kód z první stránky a upravit index položky v poli.
1. Takto se nám samozřejmě bude kód pro zobrazení stanice opakovat na každé stránce znova. Vytvořte proto v souboru `radio.js` funkci `renderStation`, která bude mít jako parametr index stanice. Funkce vykreslí do stránky stanici, tak jako prve. Funkci tak nyní můžeme importovat do všech souborů s JavaScriptem a použít ji pro zobrazení stanice. Nesmíme však funkci zapomenout správně exportovat.
1. Všimněte si, že totéž můžeme provést s funkcí `renderNavigation`. Přesuňte tuto funkci do souboru `radio.js`. Správně ji exportujte a použijte ji na každé stránce pro vykreslení navigace.


# Cvičení: Zakládání Vite projektů
## Citát
Vyzkoušejte si založení vlastního Vite projektu s jednoduchou stránkou.

1. Založte nový Vite projekt s názvem _quotes_:
   ```sh
   npm init kodim-app@latest quotes jsx
   ```
1. Uvnitř projektu nastartujte vývojový server příkazem `npm run dev`.
1. Upravte soubor `index.html`. Uvnitř elementu `#root` vytvořte HTML pro stránku zobrazující nějaký známý citát. Upravte styly v souboru `index.css` a dejte stránce nějaký vzhled. Můžete se inspirovat třeba [zde](assets/quote.png). Vtipné citáty generované umělou inteligencí vám rád naservíruje [Inspirobot](https://inspirobot.me). Zajímavé nápadu bude mít jistě mít i [ChatGPT](https://chat.openai.com).
1. Ve složce `src/pages` vytvořte soubor `quotes.js` a vložte do něj pole s citáty. Vytvořte v něm funkci, která náhodně vybere jeden citát z pole a vrátí jej jako řetězec.
1. Samžte obsah souboru `index.jsx`, importujte v něm funkci pro výběr citátu a použijte ji pro zobrazení citátu na stránce.

## Oblíbené citáty
Pokračujte v projektu z předchozího cvičení.

1. V souboru `quotes.js` vytvořte funkci `moveToTop`, která obdrží index citátu a přesune jej na první místo v poli. Funkci exportujte, abyste ji mohli použít v `index.jsx`.
1. V souboru `index.jsx` vytvořte funkci `renderQuotes`. V té pomocí metody `forEach` projděte pole citátů a vypište je do stránky.
1. Pomocí `querySelectorAll` vyberte všechny citáty a pověste na ně posluchač události `click`. Když uživatel klikne na citát, zavolejte funkci `moveToTop` a poté `renderQuotes`. Tím by se měl vybraný citát přesunout na první místo na stránce.
1. Vyzkoušejte si, že takto můžete na stránce seřadit citáty podle oblíbenosti.