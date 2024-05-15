# Cvičení: Volání API
## Východ a západ slunce

Vytvořme webovou stránku, která bude zobrazovat čas, kdy dnes vyšlo a kdy zapadá slunce. V tomto cvičení ještě nebudeme používat JSX a komponenty, abychom se mohli soustředit na práci s API.

1. Založte si nový klasický HTML/CSS/JS projekt, tedy bez JSX, Vite apod.

   ```shell
   npm init kodim-app@latest cviceni-vychod-zapad html-css-js
   ```

1. Otevřete si ve VS Code vytvořenou složku `cviceni-vychod-zapad`.
1. V souboru `index.js` pomocí funkce `fetch` a klíčovécho slova `await` získejte data z API na adrese
   ```
   https://api.sunrise-sunset.org/json?lat=50&lng=14.5
   ```
   Výsledný JSON zatím pouze vypište do konzole a prohlédněte si jeho strukturu.
1. Místo do konzole vypište někam do stránky čas východu a západu slunce. Obsah stránky sestavte postaru, tedy jako řetězec s použitím vlastnosti `innerHTML`.

## Generátor hesel

Vyrobte stránku, která pomůže uživateli vygenerovat opravdu silné a neprůstřelné heslo. Použijte k tomu veřejné API na [psswrd.net](https://www.psswrd.net/api/v1/password/?length=17) na generování hesel. Zároveň už projekt vytvořte pomocí Vite a JSX.

1. Založte si nový projekt příkazem

   ```shell
   npm init kodim-app@latest cviceni-generator-hesel jsx
   ```

1. Otevřete si ve VS Code vytvořenou složku `cviceni-generator-hesel`.
1. Prohlédněte si URL endpointu pro generování hesla a vyzkoušejte si jej „na sucho“ v prohlížeči. Zkuste vygenerovat hesla různých délek a prohlédněte si, jak vypadá struktura dat, která API vrací.
1. V hlavním `index.jsx` promažte JSX ve funkci `render`. Nechte na stránce pouze prvek `.container` a nadpis `h1`.
1. Před voláním funkce `render` vytvořte proměnnou `data`, do které si pomocí volání `fetch` na tréninkové API uložíte vygenerované heslo délky 12.
1. Upravte JSX ve funkci `render` tak, aby zobrazila uživateli vygenerované heslo s nějakým vhodným textem pro uživatele.

### Bonus

1. Vytvořte pro zobrazení heslo komponentu `StrongPassword`, která bude mít dvě `props` s názvem `password` a `length`. Tuto komponentu pak použijte ve funkci `render`.
1. Nezapomeňte pro komponentu vytvořit vlastní složku ve složce `src/components` a správně ji importujte.

# Cvičení: Lokální API a komponenty

## Workshop

Vyzkoušejte si práci s lokálními daty, která už vypadají o kousek realističtěji.

1. Repozitář [cviceni-workshop-api](https://github.com/Czechitas-podklady-WEB/cviceni-workshop-api) obsahuje data pro lokální API, které poskytuje informace o smyšleném IT workshopu. Naklonujte si tento repozitář a spusťte lokální API server pomocí `npx apidroid@latest`.
1. Data o workshopu najdete na API endpointu `/api/workshops/0`. Vyzkoušejte si jej v prohlížeči a prohlédněte si strukturu dat.
1. Nechte API spuštěné a vytvořte nový projekt pomocí `npm init kodim-app@latest cviceni-workshop jsx`. V tomto projektu si v hlavním `index.jsx` stáhněte data pomocí `fetch` a zatím si je pro kontrolu vypište do konzole.
1. Pomocí JSX zobrazte na stránce nějaké základní informace o workshopu. Nemusíte zobrazovat vše, vyberte si pouze to, co vás zajímá. Zobrazte však alespoň název workshopu, jméno instruktora a místo konání workshopu.

## Workshop - komponenty

Pokračujte v předchozím cvičení. V tomto cvičení vytvoříme komponenty pro zobrazení informací o workshopu.

1. Už známým postupem vytvořte komponentu `WorkshopIntro`, která bude zobrazovat informace o workshopu. Tato komponenta bude mít zatím dvě `props` s názvem `title` a `description`. Komponenta bude zobrazovat název workshopu a jeho popis. Komponentu mějte v oddělené složce, správně ji importujte a použijte ve funkci `render`.
1. Vytvořte další dvě komponenty `Venue` a `Instructor`, které budou zobrazovat informace o místě konání a instruktorovi. Dejte těmto komponentám takové `props` jaké uznáte za vhodné, abyste zobrazili takové informace, jaké chcete.
1. Data o celém workshopu jsou relativně obsáhlá, můžete si z nich vybrat další informace, které vás zajímají a zobrazit je na stránce. Dejte také stránce nějakou hezkou strukturu a styly.