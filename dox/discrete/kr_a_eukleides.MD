# Kanonické rozklady a Eukleidův algoritmus

* KR = kanonický rozklad
  * Číslo zapsané ve tvaru součinu prvočísel
* NSD = největší společný dělitel
  * Největší číslo, které dělí všechna vstupní čísla beze zbytku
  * WolframAlpha: `gcd()`
* NSN = nejmenší společný násobek
  * Nejmenší číslo, které je beze zbytku dělitelné všemi vstupními čísly
  * WolframAlpha: `lcm()`

## Číslo → KR

```text
𝑎 = 15 287 571 = 3² ⋅ 13² ⋅ 19 ⋅ 23²
𝑏 = 15 923 349 = 3² ⋅ 13² ⋅ 19² ⋅ 29
𝑐 =  2 880 267 = 3 ⋅ 13³ ⋅ 19 ⋅ 23
```

* Bruteforce na kalkulačce (hodí se mít tabulku prvočísel):
  * Do kalkulačky předepíšeme `15287571 ÷ ()`; závorky jsou důležité, od teď vše píšeme do nich
  * Číslo postupně zkoušíme dělit prvočísly (2, 3, 5, 7, ...), dokud nenajdeme nějaké, které ho dělí beze zbytku
  * Pokud je výsledek dělení beze zbytku, zkusíme ještě mociny prvočísla (𝑝², 𝑝³, ...)
  * Necháme největší mocninu daného 𝑝, která dělí číslo beze zbytku; nyní máme `15287571 ÷ (3²)`
  * Zapíšeme krát a zkoušíme další prvočísla, opět necháváme takové, aby celý výraz vycházel beze zbytku a abychom měli největší možnou mocninu
    * `15287571 ÷ (3² × 5)`&emsp;nelze, zkoušíme další prvočíslo
    * `15287571 ÷ (3² × 7)`&emsp;taky nic
    * `15287571 ÷ (3² × 11)`&emsp;stále nic
    * `15287571 ÷ (3² × 13)`&emsp;nález, zkusíme druhou mocninu
    * `15287571 ÷ (3² × 13²)`&emsp;zkusíme třetí mocninu...
    * `15287571 ÷ (3² × 13³)`&emsp;to už nelze, necháváme 13² a zkoušíme dále
    * `15287571 ÷ (3² × 13² × 17)`
    * ...
  * Skončíme, jakmile je výsledek 1: `15287571 ÷ (3² × 13² × 19 × 23²)`
  * Na Casiu po tlačítku „=“ mačkat šipku doleva, to nás hodí na konec řádku
    * Některá novější Casia už mají funkci kanonického rozkladu zabudovanou (FACT)

### KR → NSD/NSN

```text
𝑎 = 15 287 571 = 3² ⋅ 13² ⋅ 19  ⋅ 23² 
𝑏 = 15 923 349 = 3² ⋅ 13² ⋅ 19²       ⋅ 29
𝑐 =  2 880 267 = 3  ⋅ 13³ ⋅ 19  ⋅ 23
——————————————————————————————————————————————————————————
    NSD(𝑎,𝑏,𝑐) = 3  ⋅ 13² ⋅ 19            =           9 633
    NSN(𝑎,𝑏,𝑐) = 3² ⋅ 13³ ⋅ 19² ⋅ 23² ⋅ 29 = 109 504 871 073
```

* NSD – vynásobit čísla, která se vyskytují ve všech rozkladech, a u každého použít nejmenší mocninu, ve které se vyskytuje
* NSN – vynásobit čísla, která se vyskytují alespoň v jednom z rozkladů, a u každého použít největší mocninu, ve které se vyskytuje

### KR → Počet dělitelů

Určete počet všech společných dělitelů čísel 𝑎,𝑏,𝑐.

```text
τ(NSD(𝑎,𝑏,𝑐)) = τ(9633) = 2 ⋅ 3 ⋅ 2 = 12
```

* Počet společných dělitelů více čísel je roven počtu dělitelů jejich NSD
* Funkce τ(𝑥) vrací počet dělitelů čísla 𝑥 a počítá se jako Π(𝑚+1), kde 𝑚 jsou mocniny prvočíselného rozkladu
* Tedy `9 633 = 3 ⋅ 13² ⋅ 19` → mocniny jsou 1, 2 a 1 → `Π(𝑚+1) = (1+1)(2+1)(1+1) = (2)(3)(2) = 12`
* WolframAlpha: `DivisorSigma0(9633)`

### KR → Součet dělitelů

Určete součet všech společných dělitelů čísel 𝑎,𝑏,𝑐.

![$$\mathrm{S(NSD}(a,b,c))=\mathrm{S}(9633)=\frac{3^2-1}{3-1}⋅\frac{13^3-1}{13-1}⋅\frac{19^2-1}{19-1}=4⋅183⋅20=14640$$](../../svg/discrete/dox-discrete-kr_a_eukleides-060b03ec63.svg)

* Součet společných dělitelů více čísel je roven součtu dělitelů jejich NSD
* Funkce S(𝑥) vrací počet dělitelů čísla 𝑥 a počítá se jako Π((𝑝<sup>𝑚+1</sup>-1)/(𝑝-1)), kde 𝑝 jsou čísla prvočíselného rozkladu a 𝑚 jsou jejich mocniny
* WolframAlpha: `DivisorSigma1(9633)`

### KR → výpis všech dělitelů

Vypište všechny dělitele čísel 𝑎,𝑏,𝑐 vzestupně.

```text
9633 = 19¹ ⋅ 13² ⋅ 3¹ → [1 2 1]

[0 0 0] → 19⁰ ⋅ 13⁰ ⋅ 3⁰ =    1
[0 0 1] → 19⁰ ⋅ 13⁰ ⋅ 3¹ =    3
[0 1 0] → 19⁰ ⋅ 13¹ ⋅ 3⁰ =   13
[0 1 1] → 19⁰ ⋅ 13¹ ⋅ 3¹ =   39
[0 2 0] → 19⁰ ⋅ 13² ⋅ 3⁰ =  169
[0 2 1] → 19⁰ ⋅ 13² ⋅ 3¹ =  507
[1 0 0] → 19¹ ⋅ 13⁰ ⋅ 3⁰ =   19
[1 0 1] → 19¹ ⋅ 13⁰ ⋅ 3¹ =   57
[1 1 0] → 19¹ ⋅ 13¹ ⋅ 3⁰ =  247
[1 1 1] → 19¹ ⋅ 13¹ ⋅ 3¹ =  741
[1 2 0] → 19¹ ⋅ 13² ⋅ 3⁰ = 3211
[1 2 1] → 19¹ ⋅ 13² ⋅ 3¹ = 9633

1, 3, 13, 19, 39, 57, 169, 247, 507, 741, 3211, 9633
```

* Pro společné dělitele více čísel opět využijeme rozklad jejich NSD
* (Nezbývá než spočítat všechny kombinace mocnin prvočísel z rozkladu v rozsahu 0–𝑚)
* (Prvočísla si lépe seřadit sestupně, výsledek je pak „seřazenější“)

## Eukleidův algoritmus

Pro 𝑎 = 42 237, 𝑏 = 305 045, 𝑐 = 183 027 určete NSD(𝑎,𝑏,𝑐).

* Platí:
  * NSD(𝑎,𝑏,𝑐) = NSD(NSD(𝑎,𝑏),𝑐)

```text
NSD(𝑎,𝑏):       NSD(NSD(𝑎,𝑏),𝑐):
305 045         183 027
 42 237           4 693 ←
  9 386               0
  4 693 ←
      0

NSD(𝑎,𝑏,𝑐) = 4 693
```

* Napíšeme dvě čísla pod sebe (větší nahoru) a vydělíme je, zbytek po dělení napíšeme na další řádek; opakujeme pro spodní dvě čísla, dokud nedostaneme zbytek 0; poslední nenulový zbytek je NSD

### NSD → NSN

* Platí:
  * NSN(𝑎,𝑏) = (𝑎 ⋅ 𝑏) / __NSD__(𝑎,𝑏)
  * NSN(𝑎,𝑏,𝑐) = NSN(NSN(𝑎,𝑏),𝑐)

```text
     NSN(𝑎,𝑏,𝑐) → NSN(42237,305045,183027) = ?

       NSN(𝑎,𝑏) → NSN(42237,305045) = (42237 ⋅ 305045) / 4693 = 2745405

NSN(NSN(𝑎,𝑏),𝑐) → ? = NSN(2745405,183027)

2 745 405
  183 027 ←     ⇒    NSD(2745405,183027) = 183027
        0       ⇒ ? = (2745405 * 183027) / 183027 = 2745405

NSN(𝑎,𝑏,𝑐) = 2745405
```
