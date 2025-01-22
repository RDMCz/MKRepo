# Eulerova funkce a Eulerova věta

## Eulerova funkce

* Eulerova funkce ϕ(𝑥) vrací počet čísel v řadě 1 až 𝑥, která jsou nesoudělná s 𝑥
* Počítá se jako Π(𝑝<sup>𝑚</sup> - 𝑝<sup>𝑚-1</sup>), kde 𝑝 jsou čísla prvočíselného rozkladu a 𝑚 jsou jejich mocniny
* (Pro prvočísla je ϕ(𝑝) = 𝑝-1)

Nalezněte hodnotu Eulerovy funkce pro číslo 221559.

```text
221 559 = 3 ⋅ 13² ⋅ 19 ⋅ 23

ϕ(221559) = (3¹ - 3⁰) ⋅ (13² - 13¹) ⋅ (19¹ - 19⁰) ⋅ (23¹ - 23⁰) = 123 552

WolframAlpha: `EulerPhi(221559)`
```

## Eulerova věta

Eulerova věta nám říká, že pro __nesoudělná__ čísla 𝑎,𝑚 platí: __𝑎<sup>ϕ(𝑚)</sup> ≡ 1 (𝑚)__

### Eulerova věta – Zjednodušení výrazu

Určete zbytek po dělení čísla 11<sup>5 080 324</sup> číslem 7 514 640.

* Potřebujeme zjistit hodnotu 11<sup>5 080 324</sup> modulo 7 514 640
* Výraz je potřeba nějak zjednodušit
* Díky Eulerově větě můžeme najít číslo 11<sup>?</sup> ≡ 1 (7 514 640)
* Pokud bude mocnina nižší než ta v zadání, budeme moci výraz zjednodušit s využitím 𝑎<sup>𝑟+𝑠</sup> = 𝑎<sup>𝑟</sup>𝑎<sup>𝑠</sup>

```text
11 je prvočíslo a nedělí 7 514 640 ⇒ čísla jsou nesoudělná, podmínka je splněna

KR: 7 514 640 = 2⁴ ⋅ 3³ ⋅ 5 ⋅ 7² ⋅ 71

 ϕ(7 514 640) = (2⁴ - 2³)(3³ - 3²)(5 - 1)(7² - 7)(71 - 1) = 1 693 440

⇒ 11¹⁶⁹³⁴⁴⁰ ≡ 1 (7 514 640)

11⁵⁰⁸⁰³²⁴ = 11¹⁶⁹³⁴⁴⁰ ⋅ 11¹⁶⁹³⁴⁴⁰ ⋅ 11¹⁶⁹³⁴⁴⁰ ⋅ 11⁴
          ≡  1        ⋅  1        ⋅  1        ⋅ 11⁴ (7 514 640)
          
          = 11⁴ = 14 641
```

### Eulerova věta – Kongruence 1. stupně

Vyřešte kongruenci 7𝑥 ≡ 3 (90) s využitím Eulerovy funkce.

* Díky Eulerově větě můžeme najít číslo 7<sup>?</sup> ≡ 1 (90)
* Pokud číslem 7<sup>?-1</sup> vynásobíme obě strany kongruence, pak vlevo dostaneme 7<sup>?</sup>, z toho se modulací stane 1, tedy samotné 𝑥

```text
NSD(7, 90) = 1, podmínka je splněna

KR: 90 = 2 ⋅ 3² ⋅ 5

 ϕ(90) = (2 - 1)(9 - 3)(5 - 1) = 24

⇒ 7²⁴ ≡ 1 (90)

      7𝑥 ≡ 3      (90)
7𝑥 ⋅ 7²³ ≡ 3 ⋅ 7²³ (90)
    7²⁴𝑥 ≡ 3 ⋅ 7²³ (90)

       𝑥 ≡ 3 ⋅ 7²³ (90)
```

Jak na 7²³ modulo 90?

```text
23 = 16 + 4 + 2 + 1
7²³ = 7¹⁶ ⋅ 7⁴ ⋅ 7² ⋅ 7¹

mod 90:
7¹  = 7
7²  = 49
7⁴  = 49² = 2401 ≡ 61
7⁸  = 61² = 3721 ≡ 31
7¹⁶ = 31² =  961 ≡ 61

7²³ = 61 ⋅ 61 ⋅ 49 ⋅ 7 = 1 276 303 ≡ 13

𝑥 ≡ 3 ⋅ 13
𝑥 ≡ 39
```
