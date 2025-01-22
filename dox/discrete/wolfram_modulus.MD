# Modulární aritmetika ve WolframAlpha

Zde je na konkrétních vstupech ukázáno, jak programu WolframAlpha (případně Mathematica) říct, aby počítal v určitém modulu. Obecně tak lze učinit volitelným parametrem `Modulus`, kde např. `Modulus -> 5` znamená, že má Wolfram počítat v soustavě ℤ₅.

* __Kongruence__:
  * `768x = -1240 (mod 412)`
  * Netřeba používat symbol „≡“, nezapomenout na klíčové slovo `mod`

* __Soustava kongruencí__ (ne/zobecněná čínská věta o zbytku):
  * `x=3 (mod 15) and x=6 (mod 9) and x=7 (mod 8)`
  * Jednotlivé kongrunce oddělíme klíčovým slovem `and`

* __Soustavy rovnic v ℤ<sub>𝑛</sub>__:
  * `Solve[4x + 2y + z == 1 && 2x + y == 4 && x + y + z == 1, {x, y, z}, Modulus -> 5]`
  * Parametry: seznam rovnic oddělených `&&` (pozor na dvojité rovná se), seznam řešených proměnných, Modulus
  * Funguje jen v Mathematica, ne ve WolframAlpha ¯\\\_(ツ)\_/¯

* __Inverzní matice v ℤ<sub>𝑛</sub>__:
  * `MatrixForm[Inverse[{{15, 2, 12}, {0, 2, 3}, {0, 1, 1}}, Modulus -> 26]]`
  * Prvky matice jsou zadávány po řádcích

* __Dělení polynomů v ℤ<sub>𝑛</sub>[𝑥]__:
  * `PolynomialQuotientRemainder[x^4 + x^2 + x + 1, x + 1, x, Modulus -> 2]`
  * Parametry: co dělit, čím dělit, pro jakou proměnnou, Modulus

* __Rozklad na ireducibilní polynomy v ℤ<sub>𝑛</sub>[𝑥]__:
  * `FactorList[x^6 + 1, Modulus -> 5]`

* __NSD polynomů v ℤ<sub>𝑛</sub>[𝑥]__:
  * `PolynomialGCD[4x^6 + 6x^5 + 6x^4 + 4x^3 + 4x^2 + 3, 5x^6 + x^5 + 4x^3 + 2x^2 + 3x + 1, Modulus -> 7]`
  * Domněnka: Pokud jsou polynomy nesoudělné, pak Mathmematica vrací 1 a WolframAlpha nevrací nic (případně chybu)

* __NSN polynomů v ℤ<sub>𝑛</sub>[𝑥]__:
  * `Expand[PolynomialLCM[3x^6 + x^5 + 2x^4 + x^2 + 4x + 2, 4x^5 + 3x^3 + 3x^2 + 4x + 3, Modulus -> 5], Modulus -> 5]`
  * Pozor, nemusí vracet polynom v monickém tvaru

* __Počítání v tělese s nosičem ℤ<sub>𝑝</sub>[𝑥]/𝑞(𝑥)__:
  * `PolynomialMod[(4x^2 + 3x + 2)(4x + 3), x^3 + 2 x + 1, Modulus -> 5]`
  * Parametry: co chceme spočítat, 𝑞(𝑥), Modulus 𝑝

Poznámka: Mathematice vadí `**` jako mocnina a je tedy nutné používat `^`, ve WolframAlpha je to jedno.
