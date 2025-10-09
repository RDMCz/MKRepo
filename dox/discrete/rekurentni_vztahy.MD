# Rekurentní vztahy

> [!WARNING]  
> Tento postup pokrývá pouze případ, kdy se kromě _áček_ v zadání nachází pouze konstanta (30) a charakteristický mnohočlen nemá vícenásobné/komplexní kořeny. V těchto případech se postup liší. &ensp;TODO: zobecnit

Najděte 52. člen posloupnosti (𝑎<sub>𝑛</sub>)<sub>𝑛≥1</sub> definované tak, že:

𝑎₁ = 3 <br>
𝑎₂ = -2 <br>
𝑎<sub>𝑛</sub> = -5𝑎<sub>𝑛-1</sub> - 4𝑎<sub>𝑛-2</sub> + 30 &emsp; pro 𝑛 ≥ 3.

* `1a)` Přepíšeme do tvaru, aby nejnižší prvek měl index <sub>𝑛</sub>:

𝑎<sub>𝑛+2</sub> = -5𝑎<sub>𝑛+1</sub> - 4𝑎<sub>𝑛</sub> + 30

* `1b)` Převedeme všechna áčka na jednu stranu:

𝑎<sub>𝑛+2</sub> + 5𝑎<sub>𝑛+1</sub> + 4𝑎<sub>𝑛</sub> = 30

* `1c)` Převedeme na charakteristický mnohočlen (𝑎<sub>𝑛</sub> → _λ_<sup>𝑛</sup>, pak najít kořeny):

<i>λ</i>² + 5<i>λ</i>¹ + 4<i>λ</i>⁰ = 30 <br>
&emsp;<i>λ</i>² + 5<i>λ</i> + 4 = 30 <br>
(_λ_ + 4)(_λ_ + 1) = 30

* `1d)` Kořeny jsou __-4__ a __-1__, převedeme na „základní rekurentní tvar“:

𝑎<sub>𝑛</sub> = 𝑐₁ ⋅ (__-4__)<sup>𝑛</sup> + 𝑐₂ ⋅ (__-1__)<sup>𝑛</sup>

* `2)` Spočítáme partikulární řešení
* 𝑎<sub>𝑝</sub> se rovná nějaké 𝐴 krát to, co je na pravé straně

𝑎<sub>𝑝</sub> = 𝐴 ⋅ 30

* To dosadíme za každé 𝑎<sub>𝑛+𝑘</sub> do rovnice z `1b)`:

𝑎<sub>𝑛+2</sub> + 5𝑎<sub>𝑛+1</sub> + 4𝑎<sub>𝑛</sub> = 30

30𝐴 + 5 ⋅ 30𝐴 + 4 ⋅ 30𝐴 = 30 <br>
30𝐴 + 150𝐴 + 120𝐴 = 30 <br>
300𝐴 = 30 <br>
_A_ = 1/10

* Vyjde nám, kolik je _A_, a to dosadíme do původní partikulární rovnice:

𝑎<sub>𝑝</sub> = 1/10 ⋅ 30 = __3__

* `3)` Spočítáme konstanty
  * Dosadíme počáteční podmínky do rovnice z `1d)` a __přičteme partikulární řešení__
  * Dostaneme tolik rovnic, kolik je počátečních podmínek; vyřešíme:

𝑎<sub>𝑛</sub> = 𝑐₁ ⋅ (-4)<sup>𝑛</sup> + 𝑐₂ ⋅ (-1)<sup>𝑛</sup> __+ 𝑎<sub>𝑝</sub>__

𝑎<b>₁</b>: &ensp; 3 = 𝑐₁ ⋅ (-4)<b>¹</b> + 𝑐₂ ⋅ (-1)<b>¹</b> __+ 3__ <br>
𝑎<b>₂</b>:&ensp; -2 = 𝑐₁ ⋅ (-4)<b>²</b> + 𝑐₂ ⋅ (-1)<b>²</b> __+ 3__

0 = -4𝑐₁ - 1𝑐₂ <br>
-5 = 16𝑐₁ + 1𝑐₂

![$$\begin{pmatrix}-4&-1&|&0\\16&1&|&-5\end{pmatrix}\sim\dots\sim\begin{pmatrix}1&0&|&-\frac{5}{12}\\0&1&|&\frac{5}{3}\end{pmatrix}$$](../../svg/discrete/dox-discrete-rekurentni_vztahy-664bf74029.svg)

𝑐₁ = -5/12 <br>
𝑐₂ = 5/3

* `4)` Dosadíme do 𝑎<sub>𝑛</sub> = 𝑐₁ ⋅ (-4)<sup>𝑛</sup> + 𝑐₂ ⋅ (-1)<sup>𝑛</sup> + 𝑎<sub>𝑝</sub>:

𝑎<sub>𝑛</sub> = -5/12 ⋅ (-4)<sup>𝑛</sup> + 5/3 ⋅ (-1)<sup>𝑛</sup> + 3

* `5)` Vyjádříme 52. člen:

𝑎₅₂ = -5/12 ⋅ (-4)⁵² + 5/3 ⋅ (-1)⁵² + 3
