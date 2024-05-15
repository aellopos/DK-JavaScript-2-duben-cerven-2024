# Úkol 3

Vytvoříme jednoduchý web s několika stránkami zobrazující inzeráty na nemovitosti.

1. Na adrese https://apps.kodim.cz/daweb/trening-api/apis/realitka/dum01 najdete API endpoint, který vrací informace o jedné nemovitosti ke koupi. Prohlédněte si dobře strukturu dat, která API vrací.
1. V celku existují čtyři takové inzeráty, vždy končící `dum01`, `dum02`, `dum03` a `dum04`. Vyzkoušejte si, jak vypadají data pro všechny čtyři inzeráty.
1. Založte si nový Vite/JSX projekt pomocí `npm init kodim-app@latest cviceni-realitka jsx`.
1. Aplikace bude obsahovat celkem čtyři stránky – jednu pro každý inzerát, které budou sdílet stejný JavaScriptový soubor. Ve složce `pages` tedy založte čtyři soubory `dum01.html`, `dum02.html`, `dum03.html` a `dum04.html` a vložte do nich tentýž soubor `index.jsx`. Soubory budou mít všechny jeden hlavní element `div` s id `root` jak jsme zvyklí.
1. V této aplikaci nebudeme mít žádny `index.html`, takže všechny naše stránky budou na adrese `http://localhost:3000/dum01.html` atd.
1. Ve složce `src/components` vytvořte komponentu `Header`, která bude představovat hlavičku stránky s navigací. Hlavičku nastylujte a přidejte do ní odkazy na všechny čtyři stránky. Vložte hlavičku do obsahu stránky pomocí JSX v souboru `index.jsx`.
1. V tuto chvíli si vyzkoušejte, že vše funguje a že se všechny stránky zobrazují s hlavičkou a jde mezi nimi přepínat pomocí navigace.
1. Nyní bude potřeba si v JavaScriptu stáhnout data z toho inzerátu, na jaké stránce se zrovna nacházíme. V souboru `index.jsx` si pomocí `window.location.pathname` zjistěte, na jaké stránce zrovna uživatel je. Na základě toho sestavte správnou adresu pro `fetch` a stáhněte si data inzerátu z API. Výsledek si zatím pro kontrolu vypište do konzole.
1. Místo vypisování do konzole zobrazte inzerát na stránce.
1. Nakonec vytvořte komponentu `Estate` a přesuňte do ní kód zobrazující jeden inzerát. Sami rozhodněte, jaké přesně `props` bude komponenta potřebovat. Komponentu pak použijte ve funkci `render` v souboru `index.jsx`.
1. Nyní byste měli mít hotovou aplikaci, která zobrazuje inzeráty na nemovitosti a v hlavičce stránky je navigace, pomocí které se dá přepínat mezi jednotlivými nabídkami.