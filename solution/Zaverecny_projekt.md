# Závěrečný projekt - Cafe Lora (první část)

## 1
Projekt Café Lóra nebudeme dělat úplně na zelené louce. Budeme vycházet z již připraveného základu, V tomto cvičení se seznámíme s tím, co všechno je pro nás připraveno a jakým způsobem budeme pracovat.

1. Základ celé stránky, kterou budete postupně tvořit najdete v repozitáři [cafelora](https://github.com/Czechitas-podklady-WEB/cafelora). Pomocí _Use this template_ si vytvořte kopii tohoto repozitáře na svém GitHubu a naklonujte si ji do svého počítače.
1. Pro všechny projekty používající JSX nebo React platí, že po jejich naklonování nebo aktualizaci z GitHubu je potřeba spustit `npm install`.
1. Základní strukturu a design cílové stránky v JSX a CSS spolu s veškerými obrázky najdete v připraveném repozitáři. Poděkujte grafikům a kodérům, kteří pro vás tento návrh připravili a vy se už můžete zabývat pouze programováním.
1. Seznamte se se zdrojovým kódem, který je pro vás v projektu připraven. Spusťte si web pomocí `npm run dev`. Prohlédněte si JSX a CSS obou stránek a vyzkoušejte si obě stránky zobrazit v prohlížeči.
1. Na stránkách najdete příklad nápojů a objednávky. Tato data samozřejmě budeme později stahovat z API, nyní jsou zde pouze jako ukázka.

## 2
Jako první budeme chtít rozsekat hlavní stránku index.jsx na následující komponenty:

- `Header` - hlavička stránky,
- `Banner` - uvítací obrázek,
- `Menu` - meníčko s nápoji,
- `Gallery` - obrázek kavárny a texty,
- `Contact` - kontakt a otvírací hodiny,
- `Footer` - patička.

1.  Ve složce `src` vytvořte složku `components` a v ní postupně vytvořte všechny výše zmíněné komponenty pro hlavní stránku. Rozsekejte JSX i CSS tak, aby každá komponenta měla vlastní styly i obrázky. Globální styly pro celou aplikaci najdete v souboru `global.css`, ten ponechte beze změny. Styly komponent hlavní stránky najdete v souboru `index.css`. Soubor `index.css` je strukturovaný tak, aby styly pro jednotlivé komponenty byly seskupené u sebe, nemusíte tak zoufale lovit styly po celém projektu. V souboru `order.css` jsou styly pro detail objednávky – ty zatím neřešte, detailem se budete zabývat až v druhé části projektu.

    Chceme dosáhnout toho, aby kód pro obsah hlavní stránky aplikace v `index.jsx` vypadal takto:

    ```jsx
    document.querySelector('#root').innerHTML = render(
      <div className="page">
        <Header />
        <main>
          <Banner />
          <Menu />
          <Gallery />
          <Contact />
        </main>
        <Footer />
      </div>
    );
    ```

1.  Vyzkoušejte, že máte hotovou stránku, která vypadá stejně jako stránka ze zadání s funkční navigací. Proveďte commit s hezky popisnou zprávou a pushněte do vzdáleného repozitáře.

## 3
Jako další úkol rozchodíme zatím nefunkční navigaci a zařídíme, aby se na úzkých displejích navigace zobrazovala po kliknutí na hamburger ikonku.

1. Nejdříve do těch komponent, které odpovídají odkazům v navigaci, přidejte attribut `id`. Atribut vložte přímo na `<section/>` uvnitř dané komponenty. Tím zajistíte, aby odkazy v navigaci po kliknutí přesunuly uživatele na správnou část stránky.
1. Zobrazování a skrývání navigačního menu uděláme tak, že budeme prvku `.rollout-nav` přidávat nebo odebírat třídu `nav-closed`. V hlavním `index.jsx` (ve složce `pages`) vyberte ikonku `.nav-btn` a připojte k ní posluchač události `click`. Tento posluchač bude přepínat třídu `nav-closed` na prvku `.rollout-nav`. Klikáním na ikonku tak můžeme zobrazovat nebo skrývat navigaci.
1. Navigaci budeme chtít schovat i po kliknutí na odkaz uvnitř navigace. Připojte tedy další posluchač události přímo na prvek `.rollout-nav`. V posluchači události zařiďte, aby se navigace při kliknutí na libovolnou její položku schovala (tj. prvku `.rollout-nav` přidáte třídu `nav-closed`, obdobně, jako v předchozím kroku při přepínání).
1. Jakmile je váš kód funkční, proveďte commit se zodpovědně napsanou zprávou a pushněte do vzdáleného repozitáře.

## 4
V komponentě `Menu` máme příklad tří napojů zatím jako natvrdo vytvořené JSX. Budeme chtít mít každý nápoj v menu jako komponentu. Připravujeme se tím na to, abychom později mohli seznam nápojů zobrazovat stažením dat z API.

Vytvoříme komponentu `Drink`, která zatím nebude mít funkční objednávací tlačítko a nebude ještě správně zobrazovat ingredience (layers). Obojí doplníme později.

1.  Ve složce `components` vytvořte komponentu `Drink` s `index.jsx` a `style.css`. Do `style.css` přesuňte styly související s komponentou.
1.  V `index.jsx` vytvořte komponentu `Drink` podle vzoru nápojů z `Menu`. Připravte komponentu, aby očekávala _props_ viz níže. Nebojte se použít destrukturování.

    ```jsx
    <Drink
      id={0}
      name="Romano"
      ordered={false}
      image="http://localhost:4000/assets/cups/romano.png"
      layers={[
        {
          color: '#fbdf5b',
          label: 'citrón',
        },
        {
          color: '#613916',
          label: 'espresso',
        },
      ]}
    />
    ```

1.  Uvnitř JSX komponenty použijte pouze 2 ze seznamu _props_: `name` a `image`. První bude sloužit jako název nápoje, druhá jako adresa obrázku (atribut `src`). Ostatní _props_ můžete zatím nechat nepoužité.
1.  Nyní máte komponentu připravenou. Vraťte se do komponenty `Menu`, smažte ukázkové příklady nápojů a místo nich použijte komponentu `Drink`. Zatím na stránce klidně zobrazte pouze jeden nápoj, ať se moc nenadřete. Předejte `Drink` _props_ podle příkladu výše, nebo si vymyslete vlastní data, ať můžete otestovat, že komponenta funguje. (Nevadí že předáte všechny _props_, i když komponenta zatím používá jenom `name` a `image`).
1.  Po předání _props_ by komponenta měla minimálně správně zobrazovat vámi zadané jméno přes `name` a případně i obrázek, pokud jste např. použily adresu obrázku, který máte uložený u sebe na počítači. Adresa obrázku v příkladu nahoře využívá lokální API, které zatím nemáme zprovozněné, takže se vám tento obrázek zobrazovat nebude.
1.  Tlačítko objednání zatím pouze zobrazte, funkčnost mu přidáme později.
1.  V této fázi si commitněte kód s užitečně napsanou commit zprávou a pushněte do vzdáleného repozitáře.

## 5
Abychom mohli vytvářet seznam ingrediencí podle dat, každá ingredience nápoje musí být také komponenta. Budeme postupovat obdobně jako u komponenty `Drink`.

1.  Ve složce `components` vytvořte komponentu `Layer`. Podívejte se do `Drink` na ukázkové JSX jednotlivých layers (ingrediencí) a podle něj vytvořte strukturu komponenty, která bude vracet JSX pro jednu ingredienci. `Layer` bude očekávat _props_ v následujícím tvaru, které na patřičných místech v JSX rovnou použijte.

    ```jsx
    <Layer color="#feeeca" label="mléčná pěna" />
    ```

1.  Do komponenty také přesuňte styly s ní související.

1.  Hotovou komponentu použijte v komponentě `Drink` a nahraďte tak předchozí ukázkové příklady layers. `Layer` předejte data pomocí _props_ a otestujte, že váš projekt funguje. Commitněte kód s výborně napsanou commit zprávou a pushněte do vzdáleného repozitáře.

# Závěrečný projekt - Cafe Lora (druhá část)

## 6
V tomto cvičení konečně zobrazíme celou nabídku nápojů, které si stáhneme z API.

1. Nejdříve si naklonujte repozitář [cafelora-api](https://github.com/Czechitas-podklady-WEB/cafelora-api), kde najdete připravená data pro `apidroid`. Otevřete si repozitář v novém okně VS Code a spusťte `npx apidroid@latest` (pozor na přidanou část `@latest` – to zajistí, aby se použila nejnovější verze `apidroid`, která je pro API Café Lóra potřeba).
1. Prohlédněte si data, která vrací endpoint `/api/drinks`.
1. Upravte hlavní stránku tak, aby stahovala seznam nápojů z API, zatím stačí do proměnné, kterou vypíšete do konzole.
1. Komponentu `Menu` upravte tak, aby přijímala _prop_ s názvem `drinks`. Skrz ni komponentě předejte stažený seznam nápojů a zobrazte uvnitř prvku `drinks-list` za využití komponenty `Drink`.
1. Díky datům z API můžeme komponentě `Drink` předat reálná data a zprovoznit tak obrázky a ingredience. Adresu obrázku z API předáte přes _prop_ `image`. Nezapomeňte, že z API vám přijde pouze relativní cesta souboru, např. `/assets/cups/romano.png`, které musí předcházet url adresa, kde běží váš backend server, např. `http://localhost:4000`. Pomocí interpolace řetězců složte správně URL adresu obrázku a použijte uvnitř `src`.
1. Ingredience zobrazíte za využití prop `layers` a komponenty `Layer`, která už také získá opravdová data.
1. Stránka by nyní měla zobrazovat všechny nápoje s obrázky i ingrediencemi. Commitněte se srozumitelnou zprávou a pushněte do vzdáleného repozitáře.

## 7
1.  Nejdříve si všimněte, že data pro jeden nápoj obsahují vlastnost `ordered`, která udává, zda je nápoj zrovna objednaný či nikoliv. Toto je zároveň _prop_ v komponentě `Drink`. Upravte tuto komponentu tak, aby v závislosti na hodnotě této _prop_ zobrazila na tlačíku text _Objednat_ nebo _Zrušit_.
1.  Na objednávací tlačítko také přidejte třídu `.order-btn--ordered` v případě, že nápoj je objednaný.
1.  Prop `id` předejte atributu `data-id`, který vložte na `<form>`.
1.  V hlavním souboru `index.jsx` pověste pomocí `querySelectorAll` posluchač události na každý objednávací formulář v nápojích. Zatím při kliknutí na tlačítko vypište do konzole `id` nápoje, abyste si ověřili, že váš posluchač události pracuje se správným prvkem pole. K `id` se dostanete pomocí vlastnosti `dataset.id`.
1.  Samotné objednání nápoje provedete pomocí `PATCH` požadavku na API endpoint `/api/drinks/:id`. `:id` zde představuje dynamickou část URL, kam vložíte `id` formuláře. Požadavek bude mít v těle JSON pole s objektem, tělo požadavku tedy bude vypadat takto:

    ```js
    [{ op: 'replace', path: '/ordered', value: true }];
    ```

    Proveďte tento požadavek pomocí `fetch` a zkontrolujte, že se vám v konzoli vypíše odpověď od API. Jakmile je váš kód funkční, proveďte refresh stránky, aby se vám zobrazila aktuální data.

1.  Vyzkoušejte si na stránce, že objednávání nápojů funguje.
1.  **Bonus**: Pokud vám toto cvičení přišlo jako pohodička, zkuste si zprovoznit zrušení objednávky. Stačí upravit vlastnost `value` v body požadavku, aby místo `true` posílala opak předchozího stavu nápoje. Přístup k `ordered` stavu nápoje máte díky datům z předchozího GET requestu. Budete muset v poli se všemi nápoji najít nápoj, který odpovídá `id` použitého formuláře.
1.  Commitněte váš kód se zodpovědně napsanou commit zprávou a pushněte do vzdáleného repozitáře.

## 8
Oživíme kostru stránky pro detail objednávky pomocí už existujících komponent. Komponenty pro jednotlivé položky objednávky vytvoříme v dalším cvičení.

1. Ve složce `src/pages` najdete soubor `order.html` i s JavaScriptem `order.jsx` a styly `order.css`.
1. Na stránce použijte komponenty `Header` a `Footer`. Komponentu `Header` bude potřeba upravit, protože na stránce s objednávkou se hlavička zobrazuje bez hlavního menu. Do komponenty `Header` tedy přidejte _prop_ s názvem `showMenu`. Pokud bude `showMenu` mít hodnotu `true`, komponenta `Header` zobrazí celé menu, jako doposud. Pokud bude `false`, zobrazí hlavičku pouze s odkazem na hlavní stránku, jak je navrženo v zadání projektu v souboru `order.jsx`.
1. Vyzkoušejte, že váš web funguje a že se lze přesouvat mezi oběma stránkami.
1. Proveďte _commit_ a _push_ vašich změn.

## 9
1.  Ve složce `src/components` vytvořte komponentu `Order` pro zobrazení obsahu objednávky. Tato komponenta bude mít jedinou _prop_ `items`, která bude očekávat pole objednaných nápojů. Toto pole bude obsahovat objekty s následující strukturou:
    ```js
    {
      id: 7,
      name: 'Romano',
      image: 'http://localhost:4000/assets/cups/romano.png',
    }
    ```
1.  Vytvořte také komponentu `OrderItem` s _props_ `name` a `image` představující jednu položku objednávky.
1.  Na stránce se detailem objednávky získáte jednotlivé položky z objednávky tak, že pošlete GET požadavek na API endpoint

    ```
    /api/drinks?filter=ordered:eq:true&select=id,name,image
    ```

    Tato URL adresa obsahuje speciální parametry, které ze seznamu nápojů vyfiltrují pouze ty, které jsou objednané a vrátí pouze jejich `id`, `name` a `image`. Pozor, že pokud nemáte zatím žádný nápoj objednaný, API endpoint vrátí prázdné pole.

1.  Pokud je objedávka prázdná, zobrazte příslušnou zprávu.
1.  Vyzkoušejte, že stránka s detailem objednávky správně zobrazuje obsah objednávky. Zkuste na hlavní stránce změnit objednané nápoje a zkontrolujte, že se na stránce s detailem objednávky správně aktualizuje obsah.
1.  Proveďte _commit_ a _push_ vašich změn.

Máte hotovo! Web _Café Lóra_ ožil pod vašima rukama.