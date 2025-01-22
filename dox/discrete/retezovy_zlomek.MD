# Bézoutova rovnost, Diofantická rovnice, Řetězový zlomek

## Bézoutova rovnost

Bézoutova rovnost nám říká, že pro libovolná 𝑎,𝑏 ∈ ℕ⁺ platí: NSD(𝑎,𝑏) = min{𝑎𝑥 + 𝑏𝑦 > 0 ⁞ 𝑥,𝑦 ∈ ℤ}. Česky? NSD(𝑎,𝑏) je roven nejmenšímu kladnému číslu, které lze vyjádřit jako 𝑎𝑥 + 𝑏𝑦. Jinými slovy neexistuje kladné číslo vyjádřitelné jako 𝑎𝑥 + 𝑏𝑦, které by bylo menší než NSD(𝑎,𝑏). Příklad:

Největšího společného dělitele čísel 𝑎 = 3 420 a 𝑏 = 23 490 vyjádřete ve tvaru Bézoutovy rovnosti.<br>Řešení:

```text
NSD(3420,23490) = 3 420 ⋅ 𝑥 + 23 490 ⋅ 𝑦

23 490
 3 420  6       ╔═══╦═══════╦═══╦═══╦═══╦═══╦═══╦═══╗   ╔═══╦═══════╦═══╦═══╦════╦════╦═════╦═════╗
 2 790  1       ║ q ║       ║ 6 ║ 1 ║ 6 ║ 1 ║ 1 ║ 2 ║   ║ q ║       ║ 6 ║ 1 ║  6 ║  1 ║   1 ║   2 ║
   450  6       ╠═══╬═══╦═══╬═══╬═══╬═══╬═══╬═══╬═══╣   ╠═══╬═══╦═══╬═══╬═══╬════╬════╬═════╬═════╣
   270  1       ║ Q ║ 1 ║ 0 ║   ║   ║   ║   ║   ║   ║ → ║ Q ║ 1 ║ 0 ║ 1 ║ 1 ║  7 ║  8 ║  15 ║  38 ║ =  3 420 / 90
   180  1       ╠═══╬═══╬═══╬═══╬═══╬═══╬═══╬═══╬═══╣   ╠═══╬═══╬═══╬═══╬═══╬════╬════╬═════╬═════╣
  → 90  2       ║ P ║ 0 ║ 1 ║   ║   ║   ║   ║   ║   ║   ║ P ║ 0 ║ 1 ║ 6 ║ 7 ║ 48 ║ 55 ║ 103 ║ 261 ║ = 23 490 / 90
     0          ╚═══╩═══╩═══╩═══╩═══╩═══╩═══╩═══╩═══╝   ╚═══╩═══╩═══╩═══╩═══╩════╩════╩═════╩═════╝
                                                                                         ↑
90 ?= 3 420 ⋅ (+/- 103) + 23 490 ⋅ (+/- 15)
90 == 3 420 ⋅ ( -  103) + 23 490 ⋅ ( +  15)
```

Postup:

* Bézoutova rovnost je ve tvaru NSD(𝑎,𝑏) = 𝑎𝑥 + 𝑏𝑦
  * Již víme, že platí NSD(𝑎,𝑏) = min{𝑎𝑥 + 𝑏𝑦 > 0} kde 𝑥,𝑦 ∈ ℤ
  * 𝑎 a 𝑏 známe ze zadání, NSD spočítat umíme, jak na 𝑥 a 𝑦 ?
* S čísly provedeme [Eukleidův algoritmus](./kr_a_eukleides.MD#eukleidův-algoritmus), ale zaznamenáváme si i celou část
* Vytvoříme tabulku přibližných zlomků:

```text
╔═══╦═══════╗
║ q ║       ║
╠═══╬═══╦═══╣
║ Q ║ 1 ║ 0 ║
╠═══╬═══╬═══╣
║ P ║ 0 ║ 1 ║
╚═══╩═══╩═══╝
```

* Pro každou celou část z Eukleidova algoritmu přidáme sloupec; hodnota se nachází vždy v prvním řádku
* Dopočítáme druhý a třetí řádek podle vztahů:
  * 𝑃<sub>𝑖</sub> = 𝑞<sub>𝑖</sub> ⋅ 𝑃<sub>𝑖-1</sub> + 𝑃<sub>𝑖-2</sub>
  * 𝑄<sub>𝑖</sub> = 𝑞<sub>𝑖</sub> ⋅ 𝑄<sub>𝑖-1</sub> + 𝑄<sub>𝑖-2</sub>
* Poslední sloupec slouží jako jakási kontrola a navíc podle něj zjistíme, který řádek „náleží“ kterému z čísel 𝑎,𝑏
* Absolutní hodnoty čísel 𝑥,𝑦 se ale nachází v předposledním sloupci
  * Číslo 𝑥 se nachází v řádku, kde je poslední sloupec roven 𝑏/NSD a vice versa („křížové pravidlo“ ☺)
  * Tedy `3 420 ⇝ 103` a `23 490 ⇝ 15`
* Nyní zbývá uhádnout znaménka čísel 𝑥,𝑦 (zkoušíme všechny 4 možnosti, jedna z nich se bude rovnat NSD)

## Diofantická rovnice

Diofantická rovnice je celočíselná rovnice tvaru `𝑎𝑥 + 𝑏𝑦 = 𝑐`. Příklad:

Nalezněte všechna celočíselná řešení rovnice 69𝑥 - 123𝑦 = -33

* __1.__ Spočteme NSD koeficientů levé strany pomocí Eukleidova algoritmu (včetně celých částí)
  * `NSD(𝑎,𝑏)` → `NSD(69,123)`

```text
123
 69 1
 54 1
 15 3
  9 1
  6 1
→ 3 2
  0
```

* __2.__ Zkontrolujeme řešitelnost: spočtené NSD musí dělit pravou stranu
  * `NSD(𝑎,𝑏)|𝑐` → `3|33`
  * 3 dělí 33, rovnice má řešení

* __3.__ Vyplníme tabulku přibližných zlomků:

```text
╔═══╦═══════╦═══╦═══╦═══╦═══╦════╦════╗
║ q ║       ║ 1 ║ 1 ║ 3 ║ 1 ║  1 ║  2 ║
╠═══╬═══╦═══╬═══╬═══╬═══╬═══╬════╬════╣
║ Q ║ 1 ║ 0 ║ 1 ║ 1 ║ 4 ║ 5 ║  9 ║ 23 ║ =  69 / 3
╠═══╬═══╬═══╬═══╬═══╬═══╬═══╬════╬════╣
║ P ║ 0 ║ 1 ║ 1 ║ 2 ║ 7 ║ 9 ║ 16 ║ 41 ║ = 123 / 3
╚═══╩═══╩═══╩═══╩═══╩═══╩═══╩════╩════╝
                               ↑
```

* __4.__ Vytvoříme Bézoutovu rovnost, kde levá strana je ze zadání a pravá strana je NSD(𝑎,𝑏)
  * `69𝑥 - 123𝑦 = 3`
  * Využijeme předposlední sloupec a „křížové pravidlo“:
    * `69 ⇝ 16` a `123 ⇝ 9`
    * ⇒ `69(+/-16) - 123(+/-9) = 3`
  * Uhádneme znaménka: `69(-16) - 123(-9) = 3`

* __5.__ Vynásobíme Bézoutovu rovnost tak, aby pravá strana odpovídala zadání
  * Pravá strana je nyní 3 a má být -33, násobíme tedy -11
  * Na levé straně násobíme 𝑥 a 𝑦, aby koeficienty 𝑎 a 𝑏 zůstaly shodné se zadáním
  * `69(-16 ⋅ -11) - 123(-9 ⋅ -11) = 3 ⋅ -11` → `69(176) - 123(99) = -33`
  * Máme partikulární řešení `𝑥 = 176` a `𝑦 = 99`

* __6.__ Určíme homogenní řešení („křížové pravidlo 2“ ☺)
  * Pro 𝑥 je to koeficient 𝑦 děleno NSD(𝑎,𝑏) → `𝑏/NSD(𝑎,𝑏)` → `123/3 = 41`
  * Pro 𝑦 je to koeficient 𝑥 děleno NSD(𝑎,𝑏) → `𝑎/NSD(𝑎,𝑏)` → `69/3 = 23`

* __7.__ Určíme znaménka homogenního řešení
  * Pokud sgn(𝑎) = sgn(𝑏), pak musí být jedno znaménko kladné a jedno záporné
  * Pokud sgn(𝑎) ≠ sgn(𝑏), pak musí být obě znaménka stejná
  * sgn(69) ≠ sgn(-123) → stejná znaménka

* __8.__ Výsledek je spojením partikulárního řešení a celočíselných násobků homogenního řešení:

```text
𝑥 = 176 + 41𝑘
𝑦 =  99 + 23𝑘

𝑘 ∈ ℤ
```

## Přibližné zlomky / rozvoj v řetězový zlomek

Mějme zlomek 5322/3400. Pro vytvoření řetězového zlomku nám stačí celé části Eukleidova algoritmu:

```text
5 322
3 400   1
1 922   1
1 478   1
  444   3
  146  24
    6   3
    2
    0
```

Řetězový zlomek pak vypadá následovně:

![$$1+\cfrac{1}{1+\cfrac{1}{1+\cfrac{1}{3+\cfrac{1}{3+\cfrac{1}{24+\cfrac{1}{3}}}}}}$$](../../svg/discrete/dox-discrete-retezovy_zlomek-c9f2a7c8dd.svg)

Pro získání hodnot přibližných zlomků potřebujeme tabulku:

```text
╔═══╦═══════╦═══╦═══╦═══╦════╦════╦═════╦══════╗
║ q ║       ║ 1 ║ 1 ║ 1 ║  3 ║  3 ║  24 ║    3 ║
╠═══╬═══╦═══╬═══╬═══╬═══╬════╬════╬═════╬══════╣
║ Q ║ 1 ║ 0 ║ 1 ║ 1 ║ 2 ║  7 ║ 23 ║ 559 ║ 1700 ║ = 3 400 / 2
╠═══╬═══╬═══╬═══╬═══╬═══╬════╬════╬═════╬══════╣
║ P ║ 0 ║ 1 ║ 1 ║ 2 ║ 3 ║ 11 ║ 36 ║ 875 ║ 2661 ║ = 5 322 / 2
╚═══╩═══╩═══╩═══╩═══╩═══╩════╩════╩═════╩══════╝
```

Hodnoty jednotlivých přibližných zlomků jsou 𝑃/𝑄 (1, 2, 3/2, 11/7, 36/23, 875/559, 2661/1700).

Přibližné zlomky jsou nejlepší aproximace reálných čísel pomocí racionálních čísel, jejichž jmenovatel je nejvýše roven 𝑄.
