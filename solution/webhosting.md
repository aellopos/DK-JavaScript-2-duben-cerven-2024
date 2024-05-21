# Webhosting

Zatím jsme všechny aplikace zkoušeli jen u sebe na počítači.
V prohlížeči píšeme do adresního řádku `localhost`, což označuje tento (místní) počítač – ten počítač, na kterém adresu napíšu.
Kdybyste se chtěli svými stránkami pochlubit a někomu poslali odkaz na `localhost`, pokusí se prohlížeč připojit na jeho lokální počítač – kde ale vaše aplikace neběží.

My ale chceme vytvářet www stránky, kde to „www“ je zkratka z „World Wide Web“, tedy celosvětová síť.
Potřebujeme tedy, aby naše webové stránky byly dostupné z celého světa, ne jen z našeho počítače.

Zpřístupnit náš počítač celému světu by bylo technicky obtížné a nepohodlné – asi byste nechtěli, aby váš notebook musel pořád běžet a být připojený k internetu, protože co kdyby se někdo chtěl podívat na váš web.
Řešením je umístit naše webové stránky u někoho, kdo má trvale běžící server, který je trvale připojený do internetu (a má spolehlivější a rychlejší připojení k internetu, než my; má také zálohované napájení elektrickým proudem).
Dotyčný (a jeho server) bude náš web _hostovat_, proto se té službě říká **webhosting**.

Než se pustíme do toho, jaký webhosting vybrat a jak s ním pracovat, musíme udělat odbočku k tomu, jakému typu webhostingu se vyhnout.
Webhosting je totiž už hodně stará záležitost, pochází ještě z doby, kdy se webové stránky psaly bez JavaScriptu a často i bez CSS, žádný React neexistoval, a webové aplikace se psaly nejčastěji v PHP.
Pokud se dnes řekne _webhosting_ obvykle se tím myslí tento starý typ webhostingu.
A tomu my se chceme vyhnout, protože poskytuje služby, které nechceme (třeba právě PHP), ale museli bychom za ně platit.
Naopak tento typ hostingu neposkytuje služby, které nám usnadní práci – třeba spolupráci s Gitem a GitHubem.
Pokud tedy narazíte na webhosting jako Wedos, Active24, Savana nebo jiný webhosting, který se bude chlubit tím, které verze PHP podporuje, vyhněte se mu.
Nemusí být špatný pro PHP, ale není to nic pro naše aplikace.
Zprovoznit je na tomto typu hostingu by sice šlo, ale bylo by to zbytečně pracné.

My budeme hledat služby, které ještě nemají svůj ustálený název – někdy se jim říká třeba cloud hosting, serverless deployment platform nebo třeba [Jamstack](https://jamstack.org) deployment.
Nejznámějšími zástupci těchto služeb jsou:

- [Netlify](https://www.netlify.com)
- [Vercel](https://vercel.com/) (dříve se jmenoval Zeit.co, kdybyste na to někde narazily)

Zařadit sem lze i [GitHub Pages](https://pages.github.com) (které mají svá specifika a hodí se zejména v případě, kdy  potřebujete web pro prezentaci svého projektu hostovaného na GitHubu nebo ke sdílení životopisu) nebo [Cloudflare Pages](https://pages.cloudflare.com).
Pokud si budete vybírat hosting pro svůj projekt, doporučujeme volit mezi Netlify a Vercelem.
Obě služby jsou hodně podobné, fungují na podobných principech.
My si ukážeme práci s Netlify, ale velmi podobný postup použijete i s Vercelem, jenom obrazovky vypadají trochu jinak.

Firma provozující Vercel je zároveň autorem Reactového frameworku [Next.js](https://nextjs.org).
Takže pokud máte projekt založený na Next.js, je Vercel jasná volba.
Ne že by Next.js nešel provozovat jinde, ale s Vercelem je to nejsnazší.

A jak je to s cenou?
Bude pro vás někdo jen tak platit provoz serveru, abyste na něm mohly mít zdarma své stránky?
Ano, bude 😀
Netlify i Vercel jsou placené služby, ale obě mají základní variantu zdarma, která je dostatečná pro soukromé nebo hobby projekty.

## Vytvoření účtu a přihlášení

Obě dvě služby – Netlify i Vercel – fungují tak, že propojíte službu se svým GitHub účtem, řeknete, který repozitář chcete jako web zveřejnit, doplníte pár informací o tom, jak se s vaším projektem má zacházet – a Netlify nebo Vercel si stáhne zdrojové kódy, _zbuildí_ aplikaci, tj. převede ji do tvaru, v jakém se dá zveřejnit na webu, a nakonec ji nahraje na nějaký server a web zveřejní.

Začneme tedy vytvořením účtu / přihlášením.
Obě služby podporují přihlášení prostřednictvím dalších služeb – doporučuji přihlásit se pomocí GitHubu.
Stejně budete chtít Netlify nebo Vercelu zpřístupnit projekty na svém GitHub účtu, když se přes GitHub přihlásíte, bude to jednodušší.
Po přihlášení a propojení Netlify/Vercelu s GitHubem budete muset udělit Netlify/Vercelu přístup k vašim repozitářům na GitHubu.
Provede vás tím průvodce, který vás přesměruje na GitHub, kde dostanete na výběr – buď Netlify/Vercelu zpřístupnit všechny své repozitáře (i ty budoucí), nebo vybrat, ke kterým přesně má mít Netlify/Vercel přístup.
Své rozhodnutí můžete kdykoli později změnit.
Pokud nemáte na svém GitHub účtu vyloženě nějaký tajný výzkum, klidně povolte přístup ke všem repozitářům.
Zjednodušíte si tak přidávání budoucích projektů.

Když jste povolily Netlify/Vercelu přístup ke svým repozitářům na GitHubu, Netlify/Vercel si načte jejich seznam a nabídne vám, ze kterého repozitáře chcete nasadit web.
Pod jedním účtem můžete mít zveřejněno i více webů z různých repozitářů.
Vyberte si ten, který chcete nyní zveřejnit, a dokončete nastavení v průvodci, který vás provede konfigurací toho, aby bylo možné váš repozitář publikovat na webu.
Nejdůležitější je konfigurace deploye – tedy postupu, jak ze zdrojového repozitáře _vyrobit_ výsledný web.

## Deploy nebo-li zveřejnění projektu

Jak už bylo řečeno v lekci o bundlování, dnešní weby se prohlížeči neposkytují v tom tvaru, jak je napsaný zdrojový kód.
Námi napsaný zdrojový kód prochází tzv. buildem (sestavením), kdy se vezmou HTML soubory, CSS, skripty, a zmenší se a zabalí do balíčků, aby se s nimi prohlížeči lépe pracovalo.
V případě šablonovacích systémů (např. námi používané Reactové JSX) je to dokonce nutné, protože tento kód není určen pro běh v prohlížeči a musíme jej nejprve přeložit do standardního JavaScriptu.
Podobně se upraví třeba i obrázky – mohou se zkomprimovat, aby zabíraly menší objem a rychleji se stáhly, případně se i přizpůsobí pro různě velká zařízení.
Pro nás teď ale není podstatné, co vše se při buildu dělá – to zařídil někdo, kdo pro nás napsal `vite.config.js` nebo jiný předpis buildu.
Pro nás je teď důležité, že celý proces buildu spustíme jedním příkazem:

```shell
npm run build
```

Příkaz sestaví web do výsledné podoby, v jaké má být vystaven na webovém serveru, a jak si z něj bude prohlížeč stahovat jednotlivé soubory.
Výsledek umístí do adresáře `dist`, který vznikl ve vašem projektu.
V jiných projektech (s jinou konfigurací Vite) se cílový adresář může jmenovat třeba `build`, v našich projektech vytvořených pomocí `npm init kodim-app@latest` se vždy bude jmenovat `dist`.
Mimochodem, tento adresář nepatří do gitu, nebude na GitHubu (o to se zase stará konfigurace v souboru `.gitignore`).

Kdybyste přece jen použily PHP hosting, nyní nahrajete obsah adresáře `dist` na server ručně (nejspíš pomocí FTP nebo SFTP).
Cloud hostingy se ale o tohle postarají automaticky – naklonují si repozitář, spustí build a výsledný adresář zveřejní na svém serveru.
Jenom jim musíte pomoci s tím, kterým příkazem se build spouští (v našem případě `npm run build`) a kde bude výsledný web (u nás `dist`). 

To je vše, Netlify i Vercel vám po úspěšném buildu napíšou, na jakou doménu váš web nasadily.
Bude to doména ve tvaru `*.netlify.app` nebo `*.vercel.app`, takže třeba `jumping-squirrel-7586.netlify.app`.
Jméno na místě hvězdičky si můžete zvolit, jaké chcete – pokud už není zabrané.
Domény pod doménou `netlify.app` nebo `vercel.app` (tzv. domény třetího řádu) máte zdarma.

Pokud byste chtěli profesionálně vypadající web, měl by mít vlastní doménu.
I to je s Netlify i Vercelem možné.
Nejprve si musíte svou doménu koupit (jde to i přes Netlify nebo Vercel, ale nedoporučuju to, je to zbytečně drahé).
Pak už jen podle instrukcí nasměrujete koupenou doménu na Netlify nebo Vercel, a váš web bude dostupný na vaší krásné doméně.

A jak zařídit, aby se na váš web promítly změny nebo opravy, které uděláte ve svém zdrojovém kódu?
To je na cloudových hostinzích to nejlepší.
Prostě své změny pushnete do větve `main` na GitHubu, tak, jak jste zvyklé.
A to je vše!
Netlify nebo vercel zjistí, že došlo ke změně, zbuildují novou verzi aplikace a když se to podaří, nasadí ji na web.
Takže pushnete, počkáte pár desítek vteřin, než proběhne build, a máte zveřejněnou novou verzi webu.
Někdy to není tak snadné a build skončí nějakou chybou.
V tom případě se nemusíte bát, vystavena je pořád předchozí verze webu.
Doporučuji spustit build lokálně pomocí `npm run build` – pravděpodobně vám spadne na stejnou chybu, na jaké spadl na cloudovém hostingu.
Až chybu opravíte, pushnete změnu, Netlify nebo Vercel se o změně dozví, čapne nové zdrojové kódy, _zbuildí_ je – a pokud se podařilo chybu opravit a build projde bez chyby, máte za pár desítek sekund zveřejněnou novou verzi webu.

Netlify i Vercel toho umí daleko víc, ale pro zveřejnění soukromého projektu tohle stačí.

## Na co si dát pozor

### Velikost písmen v názvech souborů

Nejčastější problém při nasazení nového projektu na Netlify nebo Vercel je ve velikostech písmen v názvech souborů.
Windows ani macOS moc nerozlišují velikost písmen v názvech souborů a složek (každý trochu jiným způsobem).
Takže třeba soubor `fotka.jpg` a `Fotka.jpg` pro ně bude to samé.
Nebo-li když budete mít na disku soubor `Fotka.jpg` a v kódu na něj odkážete jako na `fotka.jpg`, bude vám to na vašem počítači nebo Macu fungovat.
Netlify i Vercel ale běží na Linuxu a Linux velikost písmen v názvech souborů rozlišuje.
Takže ve výše uvedeném případě vám bude tvrdit, že žádný soubor `fotka.jpg` neexistuje – a je mu úplně jedno, že existuje soubor `Fotka.jpg`.

Pokud tedy nasazujete projekt na Netlify nebo Vercel, musíte mít v kódu názvy souborů a složek přesně tak, jak jsou na disku.
Pokud je název na disku správně a v kódu špatně, jednoduše název v kódu opravte.
Pokud je správně název v kódu a na disku je špatně – pak hodně štěstí.
Tím, že Windows a MacOS nerozlišují velikost písmen, nejde rozumně přejmenovat `Fotka.jpg` na `fotka.jpg` (_vždyť je to přece to samé_) a ještě tak, aby si té změny všiml Git.
Řešení, které není zrovna sofistikované, ale pro menší množství souborů či složek funguje – přejmenujte soubor na úplně jiný název, třeba z `Fotka.jpg` udělejte `xfotka.jpg`, změnu commitněte, a pak soubor přejmenujte zpět ale už se správným názvem, např. `fotka.jpg`.

### Složka `public`

Soubory, které nejsou nikde importované v javascriptovém kódu nebo jejich název musí zůstat přesně stejný (např. `robots.txt`, `favicon.ico`, `.well-known/` atp.), můžeme umístit do speciálního adresáře `public` v kořenové složce projektu. Obsah tohoto adresáře pak bude dostupný během vývoje a po nasazení v kořeni webu. Na tyto soubory se můžeme v kódu odkazovat relativně pomocí URL adres začínajících `/`, ale nelze je importovat jako cesty v JavaScriptu.
