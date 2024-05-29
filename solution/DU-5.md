# Úkol 5

Pokračujte v projektu _Česká města_ z předchozího příkladu.

1. Ve složce `src` vašeho projektu si vytvořte prázdný soubor `cz-cities.js`.
1. Do tohoto souboru zkopírujte obsah souboru [cz-cities.js](https://github.com/Czechitas-podklady-WEB/cviceni-cz-cities/blob/main/cz-cities.js) z GitHubu. Soubor obsahuje seznam všech českých měst aktuální k 1. lednu 2020.
1. Smažte pole `cities` ve vašem `index.jsx` a místo něj si imporujte pole `cities` ze souboru `cz-cities.js`. V tuto chvíli by měl váš projekt fungovat jako v přechozím příkladu, pouze na stránce uvidíte mnohem více měst než před tím.
1. Upravte komponentu `City` tak, aby zobrazovala také okres, do kterého dané město patří.
1. U každého města je odkaz na fotografii z daného města. Do vaší komponenty `City` přidejte element `img` a zobrazte u každého města také jeho obrázek. Opět si můžete malinko pohrát se styly, aby stránka vypadala hezky.