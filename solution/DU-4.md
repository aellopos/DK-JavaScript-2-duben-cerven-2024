# Úkol 4

Rozdělte již naprogramovanou větší komponentu na vícero menších komponent.

1. Založte nový JSX projekt pomocí
   ```shell
   npm init kodim-app@latest rezervace jsx
   ```
1. Vytvořte složku pro komponentu `BookingSummary` a zkopírujte do ní následující kód:
   ```jsx
   export const BookingSummary = () => {
     return (
       <div className="summary">
         <h2>Booking Summary</h2>
         <div className="summary__head">
           <img
             className="summary__photo"
             src="https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?w=960"
           />
           <div className="summary__head-property">
             <h3 className="summary__name">Hotel Lefsní Zátiší</h3>
             <div className="summary__adress">Malohradské skály 347/21</div>
             <div className="summary__city">Malohradská ves</div>
             <div className="summary__rating">4.65</div>
           </div>
           <div className="summary__head-room">
             <h3 className="summary__name">Pokoj 2</h3>
             <div className="summary__room-type">
               Dvoulůžkový s dětskou přistýlkou
             </div>
             <div className="summary__room-price">1 800 Kč / noc</div>
           </div>
         </div>
         <div className="summary__detail">
           <h3>Detail rezervace</h3>
           <div className="summary__number">Ćíslo: 459787-745</div>
           <div className="summary__dates">Pobyt: 13.6.2023 - 17.6.2026</div>
           <div className="summary__guests">Hosté: 2 dospělí, 1 dítě</div>
           <div className="summary__services">Stravovávní: žádné</div>
           <div className="summary__room-total">7 200 Kč</div>
           <div className="summary__check-in">Check-in: 13.6.2023 do 18:00</div>
           <div className="summary__check-out">
             Check-out: 17.6.2026 do 10:00
           </div>
         </div>
         <div className="summary__services">
           <h3>Doplňkové služby</h3>
           <div className="summary__service">Parkování: 200 Kč / noc</div>
           <div className="summary__service">Snídaně: 150 Kč / noc</div>
           <div className="summary__service">Wellness: Zdarma</div>
           <div className="summary__service">
             Wifi: Zdarma na všech pokojích
           </div>
         </div>
         <div className="summary__cancal">
           <h3>Storno podmínky</h3>
           <div className="summary__cancel-text">
             <p>
               Pokud zrušíte rezervaci do 14 dní před příjezdem, nebude Vám
               účtována žádná částka.
             </p>
             <p>
               Pokud zrušíte rezervaci později nebo nedorazíte vůbec, bude Vám
               účtována částka za první noc pobytu.
             </p>
           </div>
         </div>
       </div>
     );
   };
   ```
1. Zobrazte komponentu na stránce. Lehce ji nastylujte, aby se zobrazovala hezky. Můžete požádat aby to za vás udělal ChatGPT, abyste se nemuseli příliš trápit.
1. Rozhodněte, jak rozdělit komponentu na více menších komponente. Navrhujeme vytvořit alespoň 4 různé komponenty, ze kterých pak poskládáte výslednou komponentu `BookingSummary`. Dejte komponentám smysluplná jména a vymyslete, jaké mají mít `props`.

### Bonus

1. Zkuste vymyslet strukturu JavaScriptového objektu, který bude obsahovat data pro komponentu `BookingSummary` a zařiďte, aby komponenta zobrazovala tato data.
1. Jelikož ještě neumíme vytvořit vlastní API, zatím si pouze představuje, že tato data stahujete z nějakého serveru. Můžete této představe pomoct tak, že data vytvoříte na tom místě, kde byste jinak volali funkci `fetch`.