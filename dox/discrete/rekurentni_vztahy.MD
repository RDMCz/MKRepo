# Rekurentní vztahy

## HLRV – homogenní lineární rekurentní vztahy

HLRV řešíme ve dvou krocích: __„HD“__. V kroku __H__ sestavíme obecné řešení HLRV a v kroku __D__ najdeme řešení vyhovující zadaným počátečním podmínkám.

* __H0.__ Rekurentně zadanou posloupnost přepíšeme na charakteristický polynom
  * Díváme se na členy 𝑎<sub>𝑛±𝑘</sub>. Člen s nejnižším dolním indexem odpovídá členu 𝑥⁰ v&nbsp;charakteristickém polynomu.<br>Jedná-li se např. o&nbsp;𝑎<sub>𝑛-1</sub>, pak 𝑎<sub>𝑛-1</sub> odpovídá 𝑥⁰, 𝑎<sub>𝑛</sub> odpovídá 𝑥¹, 𝑎<sub>𝑛+1</sub> odpovídá 𝑥² a tak dále.

* __H1.__ Najdeme kořeny charakteristického polynomu
  * U polynomu druhého stupně použijeme kvadratickou rovnici. Pokud máme vyšší stupeň polynomu a jedná se o školní příklad, pak můžeme zkusit kořen uhádnout: dosazujeme malá čísla, jestli to náhodou nevyjde, a po nalezení kořene polynom vydělíme (alternativně lze použít Hornerovo schéma). Nebo v tom může být schovaný nějaký vzoreček.

* __H2.__ Sestavíme obecné řešení
  * Máme-li pouze nenásobné a reálné kořeny 𝑟<sub>𝑖</sub>, pak je obecné řešení tvaru 𝑎<sub>𝑛</sub> = <i>α</i>𝑟₁<sup>𝑛</sup> + <i>β</i>𝑟₂<sup>𝑛</sup> + ⋯, kde <i>α</i>,<i>β</i>,… jsou libovolné konstanty.
  * Máme-li dvojnásobný kořen 𝑟, pak 𝑎<sub>𝑛</sub> = <i>α</i>𝑟<sup>𝑛</sup> + <i>β</i>𝑛𝑟<sup>𝑛</sup>. Máme-li trojnásobný kořen 𝑟, pak 𝑎<sub>𝑛</sub> = <i>α</i>𝑟<sup>𝑛</sup> + <i>β</i>𝑛𝑟<sup>𝑛</sup> + <i>γ</i>𝑛²𝑟<sup>𝑛</sup>. A tak dále.
  * Máme-li komplexně sdružené kořeny 𝑟 = 𝑎 ± 𝑏𝑖, pak 𝑎<sub>𝑛</sub> = <i>α</i>|𝑟|<sup>𝑛</sup>cos(𝑛<i>ϕ</i>) + <i>β</i>|𝑟|<sup>𝑛</sup>sin(𝑛<i>ϕ</i>), kde |𝑟|=√(𝑎²+𝑏²) ∧ <i>ϕ</i>=atan2(𝑏/𝑎)

* __D0.__ Pomocí počátečních podmínek dopočteme konstanty
  * Počáteční podmínky dosazujeme do obecného řešení. Dostaneme tolik rovnic, kolik je počátečních podmínek. Pomocí nich vypočteme hodnoty konstant <i>α</i>,<i>β</i>,…
  * Pro každou počáteční podmínku 𝑎<sub>𝑘</sub>=𝑐 vytvoříme rovnici tak, že za 𝑎<sub>𝑛</sub> dosadíme 𝑐 a za všechna 𝑛 dosadíme 𝑘.

* __D1.__ Do obecného řešení dosadíme vypočtené konstanty a máme výsledek

_Příklad:_ Najděte explicitní tvar posloupnosti dané vztahem 𝑎<sub>𝑛+2</sub> = 5𝑎<sub>𝑛+1</sub> - 6𝑎<sub>𝑛</sub> s počátečními podmínkami 𝑎₀=2 ∧ 𝑎₁=5.

* __H0.__ Přepíšeme na charakteristický polynom

𝑥² - 5𝑥 + 6 = 0

* __H1.__ Najdeme kořeny charakteristického polynomu

√(𝑑) = √(25 - 24) = 1<br>
𝑥<sub>1,2</sub> = (5 ± 1) / 2 = { 3, 2 }

* __H2.__ Sestavíme obecné řešení

𝑎<sub>𝑛</sub> = <i>α</i>3<sup>𝑛</sup> + <i>β</i>2<sup>𝑛</sup>

* __D0.__ Pomocí počátečních podmínek dopočteme konstanty

𝑎₀=2 &ensp;⇝&ensp; 2 = <i>α</i>3⁰ + <i>β</i>2⁰ &ensp;→&ensp; 2 = <i>α</i> + <i>β</i><br>
𝑎₁=5 &ensp;⇝&ensp; 5 = <i>α</i>3¹ + <i>β</i>2¹ &ensp;→&ensp; 5 = 3<i>α</i> + 2<i>β</i><br>
První rovnici vynásobíme třemi a odečteme od ní druhou. Vyjde nám <i>β</i>=1, což po dosazení do první rovnice umožňuje dopočítat <i>α</i>=1.

* __D1.__ Dosadíme konstanty a máme výsledek

𝑎<sub>𝑛</sub> = 3<sup>𝑛</sup> + 2<sup>𝑛</sup>

Ve Wolfram Mathematica lze příklad vypočítat příkazem

```mathematica
RSolve[{a[n+2]==5a[n+1]-6a[n], a[0]==2, a[1]==5}, a[n], n]
```

## NLRV – nehomogenní lineární rekurentní vztahy

Obecné řešení NLRV má tvar 𝑎<sub>𝑛</sub> = 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> + 𝑎<sub>𝑛</sub><sup>(𝑃)</sup>. NLRV řešíme ve třech krocích __„HPD“__: V kroku __H__ sestavíme obecné řešení 𝑎<sub>𝑛</sub><sup>(𝐻)</sup>, v kroku __P__ sestavíme partikulární řešení 𝑎<sub>𝑛</sub><sup>(𝑃)</sup> a v kroku __D__ najdeme řešení vyhovující zadaným počátečním podmínkám. Tento postup počítá se zadáním, kdy nalevo od rovnítka jsou všechny členy s nějakým 𝑎<sub>𝑛±𝑘</sub> a napravo je zbytek. Tyto zbylé členy chápeme jako „pravou stranu“.

* Krok __H__ je stejný jako při řešení HLRV. Při přepisování na charakteristický polynom ignorujeme pravou stranu zadání, resp. si ji představujeme jako nulovou. Krok končí sestavením obecného řešení zde označovaného jako 𝑎<sub>𝑛</sub><sup>(𝐻)</sup>. Konstanty v tomto obecném řešení, které označujeme <i>α</i>,<i>β</i>,…, nazveme jako „homogenní konstanty“, aby se nepletly s druhým typem konstant, které se objeví posléze.

* V kroku __P__ nejprve z pravé strany zadání odvodíme tzv. zkušební řešení. Ze zkušebního řešení pak dopočítáme partikulární řešení 𝑎<sub>𝑛</sub><sup>(𝑃)</sup>.

* __P0.__ Podle pravé strany zadání odvodíme zkušební řešení – nejprve jej navrhneme, a poté zkontrolujeme
  * Návrh zkušebního řešení volíme podle tabulky:
    * V levém sloupci platí: 𝑟 ∈ ℝ, 𝑡 ∈ ℕ, 𝑛 je „index“ posloupnosti
    * Velká písmena v pravém sloupci nazveme jako „partikulární konstanty“

    Člen pravé strany|Člen zkušebního řešení
    ---|---
    𝑟|𝐴
    𝑛<sup>𝑡</sup>|𝐴<sub>𝑡</sub>𝑛<sup>𝑡</sup> + 𝐴<sub>𝑡-1</sub>𝑛<sup>𝑡-1</sup> + ⋯ + 𝐴₀
    𝑟<sup>𝑛</sup>|𝐴𝑟<sup>𝑛</sup>
    cos(<i>ϕ</i>𝑛) nebo sin(<i>ϕ</i>𝑛)|𝐴cos(<i>ϕ</i>𝑛) + 𝐵sin(<i>ϕ</i>𝑛)
    𝑟<sup>𝑛</sup>𝑛<sup>𝑡</sup>|𝑟<sup>𝑛</sup>(𝐴<sub>𝑡</sub>𝑛<sup>𝑡</sup> + 𝐴<sub>𝑡-1</sub>𝑛<sup>𝑡-1</sup> + ⋯ + 𝐴₀)
    𝑟<sup>𝑛</sup>cos(<i>ϕ</i>𝑛) nebo 𝑟<sup>𝑛</sup>sin(<i>ϕ</i>𝑛)|𝑟<sup>𝑛</sup>( 𝐴cos(<i>ϕ</i>𝑛) + 𝐵sin(<i>ϕ</i>𝑛) )

  * Nacházi-li se naše pravá strana v levém sloupci tabulky, pak je přislušná hodnota pravého sloupce návrhem na zkušební řešení. Je-li naše pravá strana lineární kombinací hodnot z levého sloupce, pak je návrhem příslušná lineární kombinace hodnot z pravého sloupce.
  * Nakonec je potřeba zkontrolovat, zdali některý ze sčítanců návrhu zkušebního řešení není řešením HLRV. Jinými slovy, zdali neexistuje způsob jak nastavit „homogenní konstanty“, aby se 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> rovnalo některému z členů našeho návrhu. Pokud ano, musíme náš celý návrh vynásobit 𝑛-kem a zkusit znovu. Náš návrh násobíme 𝑛-kem do té doby, než žádný člen návrhu (po roznásobení) neřeší HLRV.

* __P1.__ Dosadíme zkušební řešení do zadání a spočteme „partikulární konstanty“
  * Dosazujeme stylem, že všechny členy 𝑎<sub>𝑛±𝑘</sub> nahradíme za zkušební řešení, ale v každém zkušebním řešení nahradíme 𝑛 za dolní index konkrétního nahrazovaného členu (obsah dolního indexu mějme v závorce).
  * Například pokud je zkušební řešení 𝐴𝑛, pak do dvojčlenu 2𝑎<sub>𝑛+1</sub> - 3𝑎<sub>𝑛</sub> dosadíme následovně: 2𝐴(𝑛+1) - 3𝐴𝑛.
  * (Dosazujeme pouze za členy 𝑎<sub>𝑛±𝑘</sub>, pravou stranu zadání opisujeme)

* __P2.__ Dosadíme spočtené „partikulární konstanty“ do zkušebního řešení a sestavíme 𝑎<sub>𝑛</sub> = 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> + 𝑎<sub>𝑛</sub><sup>(𝑃)</sup>

* __D0.__ Pomocí počátečních podmínek dopočteme „homogenní konstanty“, stejně jako při řešení HLRV, zde ale počítáme i s přičteným partikulárním řešením

* __D1.__ Dosadíme vypočtené „homogenní konstanty“ a máme výsledek

_Příklad:_ Najděte explicitní tvar posloupnosti dané vztahem 𝑎<sub>𝑛+2</sub> - 4𝑎<sub>𝑛+1</sub> + 4𝑎<sub>𝑛</sub> = 2<sup>𝑛</sup> s počátečními podmínkami 𝑎₀=0 ∧ 𝑎₁=0.

* __H0.__ Přepíšeme na charakteristický polynom

𝑥² - 4𝑥 + 4 = 0

* __H1.__ Najdeme kořeny charakteristického polynomu

√(𝑑) = √(16 - 16) = 0<br>
𝑥<sub>1,2</sub> = (4 ± 0) / 2 = { 2, 2 }

* __H2.__ Sestavíme obecné řešení

𝑎<sub>𝑛</sub><sup>(𝐻)</sup> = <i>α</i>2<sup>𝑛</sup> + <i>β</i>𝑛2<sup>𝑛</sup>

* __P0.__ Podle pravé strany zadání odvodíme zkušební řešení

Pravá strana je 2<sup>𝑛</sup>, proto navrhujeme 𝐴2<sup>𝑛</sup>. Následuje kontrola:

<i>α</i>=𝐴 ∧ <i>β</i>=0 &ensp;⇒&ensp; 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> = 𝐴2<sup>𝑛</sup> &ensp;⇒&ensp; návrh musíme vynásobit 𝑛-kem &ensp;⇒&ensp; nový návrh 𝐴2<sup>𝑛</sup>𝑛<br>
<i>α</i>=0 ∧ <i>β</i>=𝐴 &ensp;⇒&ensp; 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> = 𝐴𝑛2<sup>𝑛</sup> &ensp;⇒&ensp; návrh musíme vynásobit 𝑛-kem &ensp;⇒&ensp; nový návrh 𝐴2<sup>𝑛</sup>𝑛²<br>
Homogenní konstanty již nelze nastavit tak, aby 𝑎<sub>𝑛</sub><sup>(𝐻)</sup>=_člen\_návrhu_, zkušební řešení je tedy __𝐴2<sup>𝑛</sup>𝑛²__.

* __P1.__ Dosadíme zkušební řešení do zadání a spočteme partikulární konstanty (v tomto případě pouze konstantu 𝐴)

𝐴2<sup>𝑛+2</sup>(𝑛+2)² - 4𝐴2<sup>𝑛+1</sup>(𝑛+1)² + 4𝐴2<sup>𝑛</sup>𝑛² = 2<sup>𝑛</sup> &emsp;&emsp;&emsp;&emsp;&emsp; // rovnici vydělíme 2<sup>𝑛</sup><br>
𝐴4(𝑛+2)² - 4𝐴2(𝑛+1)² + 4𝐴𝑛² = 1 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; // roznásobíme jednotlivé členy<br>
𝐴4(𝑛²+4𝑛+4) - 𝐴8(𝑛²+2𝑛+1) + 4𝐴𝑛² = 1<br>
𝐴4𝑛² + 𝐴16𝑛 + 𝐴16 - 𝐴8𝑛² - 𝐴16𝑛 - 𝐴8 + 4𝐴𝑛² = 1 &emsp;&ensp; // členy s 𝑛 a 𝑛² se požerou<br>
𝐴8 = 1<br>
𝐴 = 1/8 = 2⁻³

* __P2.__ Dosadíme spočtené partikulární konstanty do zkušebního řešení a sestavíme 𝑎<sub>𝑛</sub>

𝑎<sub>𝑛</sub><sup>(𝑃)</sup> = 2⁻³2<sup>𝑛</sup>𝑛² = 2<sup>𝑛-3</sup>𝑛²<br>
𝑎<sub>𝑛</sub> = 𝑎<sub>𝑛</sub><sup>(𝐻)</sup> + 𝑎<sub>𝑛</sub><sup>(𝑃)</sup> = <i>α</i>2<sup>𝑛</sup> + <i>β</i>𝑛2<sup>𝑛</sup> + 2<sup>𝑛-3</sup>𝑛²

* __D0.__ Pomocí počátečních podmínek dopočteme homogenní konstanty

𝑎₀=0 &ensp;⇝&ensp; 0 = <i>α</i>2<sup>0</sup> + <i>β</i>0 ⋅ 2<sup>0</sup> + 2<sup>0-3</sup>0² &ensp;→&ensp; 0 = <i>α</i><br>
𝑎₁=0 &ensp;⇝&ensp; 0 = <i>α</i>2<sup>1</sup> + <i>β</i>1 ⋅ 2<sup>1</sup> + 2<sup>1-3</sup>1² &ensp;→&ensp; 0 = 2<i>α</i> + 2<i>β</i> + 2⁻²<br>
Dosazením první rovnice do druhé dostáváme 0 = 2<i>β</i> + 2⁻² &ensp;→&ensp; <i>β</i> = -(1/8) = -2⁻³

* __D1.__ Dosadíme homogenní konstanty a máme výsledek

𝑎<sub>𝑛</sub> = -2⁻³𝑛2<sup>𝑛</sup> + 2<sup>𝑛-3</sup>𝑛² = 2<sup>𝑛-3</sup>𝑛(𝑛 - 1)

Ve Wolfram Mathematica lze příklad vypočítat příkazem

```mathematica
RSolve[{a[n+2]-4a[n+1]+4a[n]==2^n, a[0]==0, a[1]==0}, a[n], n]
```

## Soustavy rekurencí

V této sekci uvažujeme soustavu dvou homogenních rekurencí druhého řádu.

_Příklad:_ Najděte explicitní tvar posloupností daných vztahy 𝑥<sub>𝑛+1</sub> = 3𝑥<sub>𝑛</sub> ∧ 𝑦<sub>𝑛+1</sub> = 𝑥<sub>𝑛</sub> + 2𝑦<sub>𝑛</sub> s počátečními podmínkami 𝑥₀=1 ∧ 𝑦₀=0.

* __S0.__ Ze zadání vytvoříme matici konstant 𝒜 a vektor počátečních podmínek x̰₀

```text
A = ⎡3  0⎤,     ⎡𝑥₀⎤ = ⎡1⎤
    ⎣1  2⎦      ⎣𝑦₀⎦   ⎣0⎦
```

* __S1.__ Vypočteme vlastní čísla a vlastní vektory matice 𝒜 (viz [rychlejší způsob určení vlastních čísel a vektorů pro matice 2×2](../lingebra/vlastni_vektory.MD#rychlej%C5%A1%C3%AD-zp%C5%AFsob-ur%C4%8Den%C3%AD-vlastn%C3%ADch-%C4%8D%C3%ADsel-pro-matice-22)), vyjde nám:

Vlastní číslo 3 s vlastním vektorem (1;1)<br>
Vlastní číslo 2 s vlastním vektorem (0;1)

* __S2.__ Pomocí počátečních podmínek a vlastních vektorů spočítáme konstanty `x̰₀ = Σ konstanta ⋅ vl.vektor`

```text
⎡1⎤ = α ⎡1⎤ + β ⎡0⎤
⎣0⎦     ⎣1⎦     ⎣1⎦

1 = α
0 = α + β  →  β = -α
              β = -1
```

* __S3.__ Sestavíme řešení tvaru `Σ konstanta ⋅ vl.čísloⁿ ⋅ vl.vektor`

```text
⎡𝑥ₙ⎤ = (1)(3ⁿ)⎡1⎤ + (-1)(2ⁿ)⎡0⎤
⎣𝑦ₙ⎦          ⎣1⎦           ⎣1⎦
```

𝑥<sub>𝑛</sub> = 3<sup>𝑛</sup><br>
𝑦<sub>𝑛</sub> = 3<sup>𝑛</sup> - 2<sup>𝑛</sup>

Ve Wolfram Mathematica lze příklad vypočítat příkazem

```mathematica
RSolve[{x[n+1]==3x[n], y[n+1]==x[n]+2y[n], x[0]==1, y[0]==0}, {x, y}, n]
```

## Vytvořující funkce

### Katalog

Posloupnost|Obyčejná VřF
---|:-:
𝑎<sub>𝑛</sub> = 1|![$$\frac{1}{1-x}$$](../../svg/discrete/GF_katalog_0.svg)
𝑎<sub>𝑛</sub> = 𝑟<sup>𝑛</sup>|![$$\frac{1}{1-rx}$$](../../svg/discrete/GF_katalog_1.svg)
𝑎<sub>𝑛</sub> = 𝑛|![$$\frac{x}{1-x^2}$$](../../svg/discrete/GF_katalog_2.svg)
𝑎<sub>𝑛</sub> = 𝑛 + 1|![$$\frac{x}{(1-x)^2}$$](../../svg/discrete/GF_katalog_3.svg)
𝑎<sub>𝑛</sub> = 𝑛²|![$$\frac{x(1+x)}{(1-x)^3}$$](../../svg/discrete/GF_katalog_4.svg)
𝑎<sub>𝑛</sub> = (-1)<sup>𝑛</sup>|![$$\frac{1}{1+x}$$](../../svg/discrete/GF_katalog_5.svg)
𝑎<sub>𝑛</sub> = 𝑛(-1)<sup>𝑛</sup>|![$$-\frac{x}{(1+x)^2}$$](../../svg/discrete/GF_katalog_6.svg)

### Obyčejná vytvořující funkce

__Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛</sub>𝑥<sup>𝑛</sup>__

_Příklad:_ Pomocí obyčejné vytvořující funkce najděte explicitní tvar posloupnosti dané vztahem 𝑎<sub>𝑛+1</sub> = 𝑎<sub>𝑛</sub> + 2<sup>𝑛</sup> s počáteční podmínkou 𝑎₀=0.

* __V0.__ Upravíme zadání do správného tvaru (členy s 𝑎<sub>𝑛±𝑘</sub> vlevo, zbytek vpravo)

𝑎<sub>𝑛+1</sub> - 𝑎<sub>𝑛</sub> = 2<sup>𝑛</sup>

* __V1.__ Vynásobíme rovnici nejvyšší možnou mocninou 𝑥<sup>𝑛±𝑘</sup> (podle dolních indexů v zadání) a sumujeme každý člen přes 𝑛=0..∞

Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛+1</sub>𝑥<sup>𝑛+1</sup> - Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛</sub>𝑥<sup>𝑛+1</sup> = Σ<sub>𝑛≥0</sub>2<sup>𝑛</sup>𝑥<sup>𝑛+1</sup>

* __V2.__ V každém členu srovnáme horní index 𝑥 s dolním indexem 𝑎 (vytkneme potřebnou mocninu 𝑥 ze sumy); napravo chceme 𝑥<sup>𝑛</sup>

Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛+1</sub>𝑥<sup>𝑛+1</sup> - 𝑥 ⋅ Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛</sub>𝑥<sup>𝑛</sup> = 𝑥 ⋅ Σ<sub>𝑛≥0</sub>2<sup>𝑛</sup>𝑥<sup>𝑛</sup>

* __V3.__ Převedeme členy na vytvořující funkce podle vztahu 𝐹 = Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛</sub>𝑥<sup>𝑛</sup>; pravou stranu podle katalogu
  * Pokud nějaký člen „začíná sumovat později“, je potřeba od daného 𝐹 odečíst prvních 𝑘 prvků sumy:
    * Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛+𝑘</sub>𝑥<sup>𝑛+𝑘</sup> = 𝐹 - 𝑎₀ - 𝑎₁𝑥 - 𝑎₂𝑥³ - ⋯ - 𝑎<sub>𝑘-1</sub>𝑥<sup>𝑘-1</sup>

(𝐹 - 𝑎₀) - 𝑥𝐹 = 𝑥 ⋅ 1/(1 - 2𝑥)

* __V4.__ Dosadíme počáteční podmínky a vyjádříme 𝐹 tak, aby šlo pomocí katalogu převést na výsledek

```text
(𝐹 - 0) - 𝑥𝐹 = 𝑥 ⋅ 1/(1 - 2𝑥)
    𝐹(1 - 𝑥) = 𝑥/(1 - 2𝑥)
           𝐹 = 𝑥/((1 - 2𝑥)(1 - 𝑥))
           𝐹 = 1/(1 - 2𝑥) - 1/(1 - 𝑥)
```

V poslední úpravě byl proveden [rozklad na parciální zlomky](../misc/rozklad_parcialni_zlomky.MD).

* __V5.__ Pomocí katalogu převedeme na výsledek

```text
𝐹 = 1/(1 - 2𝑥) - 1/(1 - 𝑥)
𝑎ₙ = 2ⁿ         - 1
```

𝑎<sub>𝑛</sub> = 2<sup>𝑛</sup> - 1

Ve Wolfram Mathematica lze příklad vypočítat příkazem

```mathematica
RSolve[{a[n+1]==a[n]+2^n, a[0]==0}, a[n], n]
```

_Poznámka:_ Pozor na znaménka / pořadí členů: `1/(1 - 2𝑥) ⇝ 2ⁿ` ∧ `1/(2𝑥 - 1) = -1/(1 - 2𝑥) ⇝ -2ⁿ`

### Soustava rekurencí pomocí vytvořujících funkcí

Zavedeme 𝐹 = Σ<sub>𝑛≥0</sub>𝑎<sub>𝑛</sub>𝑥<sup>𝑛</sup> ∧ 𝐺 = Σ<sub>𝑛≥0</sub>𝑏<sub>𝑛</sub>𝑥<sup>𝑛</sup> a použijeme dosazovací metodu.

//TODO
