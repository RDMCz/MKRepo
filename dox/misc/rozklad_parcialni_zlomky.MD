# Rozklad na parciální zlomky

Jsme ve situaci, kdy máme zlomek se součinem polynomů ve jmenovateli. Zlomek chceme převést na součet zlomků, které mají jednodušší jmenovatele. Tento algoritmus využíváme např. při integraci nebo řešení rekurentních vztahů pomocí vytvořujících funkcí.

Prvním krokem je určení počtu výsledných parciálních zlomků a jejich jmenovatelů. Čitatele budou zatím obsahovat konstanty, které později dopočteme.

Platí:

![$$\begin{align*}&\frac{\cdots}{(x+a)^k}=\frac{A_1}{x+a}+\cdots+\frac{A_k}{(x+a)^k}\\\\&\frac{\cdots}{(x^2+ax+b)^k}=\frac{A_1x+B_1}{x^2+ax+b}+\cdots+\frac{A_kx+B_k}{(x^2+ax+b)^k}\end{align*}$$](../../svg/misc/rozklad_parcialni_zlomky-4a43f16528.svg)

Máme-li ve jmenovateli 𝑘-tou mocninu polynomu prvního stupně, pak budeme mít 𝑘 parciálních zlomků, v jejichž jmenovatelích se postupně zvyšuje mocnina původního polynomu od 1 do 𝑘. V čitatelích jsou konstanty, které budou dopočítány.

Máme-li ve jmenovateli polynom druhého stupně, postup je stejný až na tvar čitatelů, který je v tomto případě 𝐴𝑥 + 𝐵.

Máme-li ve jmenovateli součin více polynomů (nebo jejich mocnin), pak výsledný součet obsahuje parciální zlomky pro každý polynom zvlášť. Např.:

![$$\frac{\cdots}{(x+1)^2(x^2+3x+2)^2}=\frac{A}{x+1}+\frac{B}{(x+1)^2}+\frac{Cx+D}{x^2+3x+2}+\frac{Ex+F}{(x^2+3x+2)^2}$$](../../svg/misc/rozklad_parcialni_zlomky-faded0e2af.svg)

Jak dopočítat konstanty? Rovnici, která nám vyšla, celou vynásobíme původním jmenovatelem. Poté roznásobíme pravou stranu a odvodíme soustavu rovnic.

## Příklad

![$$\begin{align*}\frac{x^2+x+1}{(1+x)^2(1-2x)}&=\frac{A}{1+x}+\frac{B}{(1+x)^2}+\frac{C}{1-2x}\\\\x^2+x+1&=A(1+x)(1-2x)+B(1-2x)+C(1+x)^2\\x^2+x+1&=A(1-x-2x^2)+B(1-2x)+C(1+2x+x^2)\\x^2+x+1&=A-Ax-2Ax^2+B-2Bx+C+2Cx+Cx^2\\\\1&=-2A+C\\1&=-A-2B+2C\\1&=A+B+C\\\\&\begin{pmatrix}-2&0&1&|&1\\-1&-2&2&|&1\\1&1&1&|&1\\\end{pmatrix}\sim\cdots\sim\begin{pmatrix}9&0&0&|&-1\\0&3&0&|&1\\0&0&9&|&7\\\end{pmatrix}\\\\\frac{x^2+x+1}{(1+x)^2(1-2x)}&=\frac{-\frac{1}{9}}{1+x}+\frac{\frac{1}{3}}{(1+x)^2}+\frac{\frac{7}{9}}{1-2x}\end{align*}$$](../../svg/misc/rozklad_parcialni_zlomky-de2dee3094.svg)

Jak odvodit soustavu rovnic? Na levé straně máme tři členy – budou tři rovnice. Koeficient u členu 𝑥² je 1, a první rovnice proto bude `1 = koeficienty u členů s 𝑥² na pravé straně`. A tak dále.

Tip: Narazíme-li ve jmenovateli na 𝑥², můžeme na něj pohlížet jako na (𝑥 - 0)².

## Rozklad na parciální zlomky pro vytvořující funkce

Při převodu obyčejné vytvořující funkce na explicitní tvar posloupnosti se nám hodí mít zlomky ve tvaru 1/(1-𝑟𝑥). Máme-li zlomek s polynomem druhého stupně ve jmenovateli a zkusíme z něj pomocí kvadratické rovnice a rozkladu na parciální zlomky udělat součet dvou jednodušších zlomků, nemusí nám nutně vyjít zlomky ve výše uvedeném tvaru. Můžeme ale zvolit obecnější postup, kterým si tento tvar zajistíme:

![$$\begin{align*}\frac{\cdots}{ax^2+bx+c}&=\frac{A}{1-\alpha x}+\frac{B}{1-\beta x}\\\\^*\!\implies ax^2+bx+c&=(1-\alpha x)(1-\beta x)=\\&=\alpha\beta\cdot x^2+(-\alpha-\beta)\cdot x+1\\\\^{**}\!\implies\cdots&=A(1-\beta x)+B(1-\alpha x)=\\&=(A+B)+(-A\beta-B\alpha)\cdot x\end{align*}$$](../../svg/misc/rozklad_parcialni_zlomky-93ce2d5602.svg)

Výsledné dva zlomky chceme ve tvaru 𝐴/(1-<i>α</i>𝑥)+𝐵/(1-<i>β</i>𝑥), a proto se musí součin jejich jmenovatelů rovnat původnímu jmenovateli. Podle původního jmenovatele tedy vypočítáme konkrétní hodnoty pro <i>α</i> a <i>β</i>. Poté už můžeme vypočítat samotné 𝐴 a 𝐵.

_Příklad:_

![$$\begin{align*}\frac{1-x}{1-2x-x^2}&=\frac{A}{1-\alpha x}+\frac{B}{1-\beta x}\\\\^*\!\implies 1-2x-x^2&=\alpha\beta\cdot x^2+(-\alpha-\beta)\cdot x+1\\-2&=-\alpha-\beta\\-1&=\alpha\beta\end{align*}$$](../../svg/misc/rozklad_parcialni_zlomky-99e4f719c4.svg)

Z první rovnice odvodíme <i>β</i>=2-<i>α</i> a to dosadíme do druhé. Vyjde nám <i>α</i>=1±√(2), vybereme si jedno řešení (<i>α</i>=1+√(2)) a dopočítáme <i>β</i> = 2-<i>α</i> = 2-1-√(2) = 1-√(2).

![$$\begin{align*}^{**}\!\implies 1-x&=(A+B)+(-A\beta-B\alpha)\cdot x\\1&=A+B\\-1&=-A\beta-B\alpha\end{align*}$$](../../svg/misc/rozklad_parcialni_zlomky-d21fce44de.svg)

Z první rovnice odvodíme 𝐵=1-𝐴 a to dosadíme do druhé. Vyjde nám 𝐴=(1-<i>α</i>)/(<i>β</i>-<i>α</i>), po dosazení alfy a bety nám vyjde 𝐴=1/2. Dopočítáme 𝐵 = 1-𝐴 = 1-1/2 = 1/2 a máme hotovo.

![math](../../svg/misc/rozklad_parcialni_zlomky-cc7f1e7a56.svg)

Tuto vytvořující funkci můžeme pak snadno převést na explicitní tvar posloupnosti 𝑎<sub>𝑛</sub> = 1/2 ⋅ ((1 + √(2))<sup>𝑛</sup> + (1 - √(2))<sup>𝑛</sup>).
