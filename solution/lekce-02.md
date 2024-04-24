## Pánské obleky

V tomto příkladu si vyzkoušíme týmovou spolupráci v Gitu. Vaším úkolem bude vytvořit webovou stránku pro e-shop s pánskými obleky. Stránka má vypadat přesně dle tohoto [grafického návrhu](../images/layout.png).

Pro účely všech následujících cvičení budeme pracovat ve dvoučlenných týmech. Jeden z týmu hraje roli Alice a druhý roli Barbory. Instrukce jsou vždy pro Alici nebo Barboru. Držte si kloubouky, začínáme:

Úkol pro **Alici**. Barbora čeká.

1. Alice vytvoří na svém GitHub účtu šablonu z repozitáře [cviceni-panske-obleky](https://github.com/Czechitas-podklady-WEB/cviceni-panske-obleky) obsahující výchozí soubory pro stránku s pánskými obleky.
1. Pozve Barboru do svého GitHub projektu jako spolupracovnici.
1. Naklonuje projekt do svého počítače a otevře složku `cviceni-panske-obleky` ve VS Code.
1. Seznámí se se strukturou projektu a otevře si stránku v prohlížeči.

Úkol pro **Barboru**, Alice čeká.

1. Jakmile Barbora obdrží pozvánku do projektu, naklonuje si tento projekt do svého počítače a ve VS Code otevře složku `cviceni-panske-obleky`.
1. Seznámí se se strukturou projektu a otevře si stránku v prohlížeči.

Na konci tohoto úkolu mají Alice i Barbora každá na svém počítači naklonovaný obsah repozitáře a mají projekt otevřený ve VS Code.

## Obrázky a styly

Úkol pro **Barboru**. Alice čeká.

1. Barbora vytvoří v projektu složku `img` a do ní vloží obrázky [bg.jpg](../images/bg.jpg) a [suit.jpg](../images/suit.jpg) pro hlavičku stránky.
1. Otevře soubor `style.css` a přidá do něj následující styl hlavičky těsně za třídu `.container`.
   ```css
   header {
     padding-top: 4rem;
     background-image: url(img/suit.jpg), url(img/bg.jpg);
     background-position: center, center;
     background-repeat: no-repeat, repeat-x;
     height: 360px;
   }
   ```
1. Pomocí `git add .` přidá do stage všechny změny a vyvoří commit se zprávou "Stylování hlavičky."
1. Pushne commit do vzdáleného repozitáře.
1. Na GitHubu zkontroluje, že se změny opravu zapsaly na server.

Úkol pro **Alici**, Barbora čeká.

1. Poté, co Barbora provedla commit, Alice si pullne změny z GitHub repozítáře k sobě do počítače.
1. Pomocí `git log` zkontroluje, že si opravdu stáhla Barbořin commit.
1. V projektu vytvoří složku `fonts` a vloží do ní font [Fashion Victim](../fashion-victim.woff2). Na začátek souboru `style.css` tento font vloží pomocí `@font-face`.
   ```css
   @font-face {
     font-family: 'Fashion Victim';
     src: url(fonts/fashion-victim.woff2) format('woff2');
   }
   ```
1. Dále do stylů přidá stylování nadpisu stránky hned za prvek `header`.

   ```css
   h1.site-title {
     font-family: 'Fashion Victim';
     font-size: 6rem;
     font-weight: normal;
     text-align: center;
   }

   h1.site-title span {
     margin: 0 2rem;
   }
   ```

1. Ověři si, že se stránka správně nastylovala a že nadpis nyní vypadá přesně podle zadání.
1. Přidá do stage všechny změny a provede commit se zprávou "Stylování nadpisu." Pushne commit do vzdáleného repozitáře.
1. Na GitHubu se přesvědčí, že její kód je opravdu na serveru.

Úkol pro **Barboru**, Alice čeká.

1. Poté, co Alice provedla commit, Barbora si pullne změny k sobě do počítače.
1. Pomocí `git log` zkontroluje, že obdržela Alicin commit.

Na konci tohoto cvičení jsou obě dámy opět synchronizované a obě mají projekt ve stejném stavu se správně nastylovanou havičkou i nadpisem stránky.

## Konflikt

V tuto chvíli se obě dámy nezávisle na sobě rozhodnou upravit stejnou část stránky.

Úkol pro **Barboru**. Alice čeká.

1. Barbora v souboru `index.html` přidá do elementu `.product__colors` následující HTML.
   ```html
   <p>Pomocí tlačítek vyberte barvu produktu</p>
   <div class="colors">
     <div class="color">
       <div class="color-box"></div>
       <p class="color__name">bílá</p>
     </div>
   </div>
   ```
1. Zatím neřeší stylování a změny rovnou commitne se zprávou "HTML pro výběr barvy."
1. Provede push na GitHub.

Úkol pro **Alici**, Barbora čeká.

1. Alice chce také vyrobit HTML pro výběr barvy. Nevšimne si však, že Barbora už pushnula úpravu stejné části kódu. Místo toho, aby si pullnula, vloží do elementu `.product__colors` svůj kód, který vypadá trochu jinak než ten, který vytvořila Barbora.
   ```html
   <p>Vyberte si barvu produktu</p>
   <div class="choose-colors">
     <div class="color-option">
       <div class="color-option__box"></div>
       <p class="color-option__name">bílá</p>
     </div>
   </div>
   ```
1. Provede commit svých změn se zprávou "Ukázka výběru barev."
1. Nyní se Alice pokusí provést push svých změn. Pushnutí však selže a Alice obdrží červenou zprávu `rejected`. Git nedovolí pushnout do repozitáře obsahující změny, které si Alice ještě nepullnula. Alice tedy musí nejdříve udělat pull.
1. Během pullování však nastane konflikt v souboru `index.html`.
   ```
   CONFLICT (content): Merge conflict in index.html
   ```
   Alice jej musí vyřešit. Kontaktuje Barboru a navzájem se domluví, jak konflikt vyřeší:
   - Buď přijmou změny, které provedla Alice (Accept Current Change),
   - nebo Alice svoje změny zahodí a přijme změny od Barbory (Accept Incoming Change),
   - nebo přijmou obě změny (Accept Both Changes) a nějakým způsobem je zkombinují dohromady.
     Pro pokračování projektu je jedno, kterou variantu si vyberete. Rozhodněte se dle svých preferencí.
1. Jakmile je konflikt vyřešen, Alice pomocí `git add` přidá změny v `index.html` a provede commit se zprávou "Vyřešen konflikt.".
1. Nakonec Alice pushne svoje změny do GitHub repozitáře.

Úkol pro **Barboru**.

1. Barbora si pullne nový commit, ve kterém je vyřešen konflikt. Tím se lokální repozitáře u Alice i Barbory dostanou opět do synchronizovaného stavu.

## Vlastní práce

Pokračujte dále v rolích Alice a Barbory. Společně si rozvhrněte práci na projektu a dotáhněte jej tak daleko, jak se vám samotným bude líbit. Nejlepší je, pokud jeden z týmu pracuje na HTML a stylech a druhý na JavaScriptu, abyse si navzájem nelezli do zelí a nevznikaly zbytečné konflikty.

Stránka by měla fungovat tak, že si uživatel může vybírat barvu košile pomocí tlačítek s barvami. Při kliknutí na příslušné tlačíko se obrázek košile přebarví na zvolenou barvu. Díky vlastnosti `style` na prvku `svg` můžete pomocí JavaScriptu měnit barvu košile. Vyzkoušejte si to.

Držte se pravidel pro spolupráce na jedné větvi. Vždy dělejte `pull` před tím, než uděláte `commit`.

Co všechno je možné na projektu udělat:

1. Dokončit HTML i CSS pro vybírání barev.
1. Přidat tlačítko pro objednávání.
1. Pomocí JavaScriptu zvýraznit barvu, kterou si uživatel vybral. Obarvit košili danou barvou.
1. Zařídit, aby šla vybrat pouze jedna barva.

Pokud pracujete v JavaScriptu, vyberte si techniky, které znáte a ve kterých se cítíte pohodlně.