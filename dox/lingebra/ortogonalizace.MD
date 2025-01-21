# Gramova-Schmidtova ortogonalizace

V lineárním obalu množiny vektorů<br>
&emsp;𝐺 = { 𝑔₁ = (1, 1, 1, 1), 𝑔₂ = (5, 1, -2, 0), 𝑔₃ = (1, 3, -1, 1) }<br>
vytvořte ortogonální množinu 𝐹.

* První vektor zařadíme rovnou, zatím tedy 𝐹 = { 𝑓₁ = (1, 1, 1, 1) }
* Další vektory musíme upravit následujícím způsobem:

![$$\tilde{f}_{n+1}=g\bigoplus_{i=1}^{n}\left(-\frac{\langle f_i|g\rangle}{||f_i||^2}\otimes f_i\right)$$](../../svg/lingebra/dox-lingebra-ortogonalizace-cd87b40629.svg)

* Vezmeme další vektor z 𝐺 a odečteme od něj určité násobky všech již ortogonálních vektorů z 𝐹
* Určitým násobkem je zlomek, kde:
  * V čitateli je skalární součin ortogonálního vektoru s vektorem, který chceme přidat ⟨𝑓<sub>𝑖</sub> | 𝑔⟩
  * Ve jmenovateli je norma na druhou ortogonálního vektoru
* Výsledný vektor přidáme do 𝐹, tyto kroky opakujeme, dokud nevyčerpáme 𝐺:

![$$\begin{align*}\tilde{f}_{n+1}&=(5,1,-2,0)-\frac{\langle(1,1,1,1)|(5,1,-2,0)\rangle}{||(1,1,1,1)||^2}\cdot(1,1,1,1)\\&=(5,1,-2,0)-\frac{4}{4}\cdot(1,1,1,1)\\&=(4,0,-3,-1)\end{align*}$$](../../svg/lingebra/dox-lingebra-ortogonalizace-f059064dcc.svg)

* Nyní 𝐹 = { 𝑓₁ = (1, 1, 1, 1), 𝑓₂ = (4, 0, -3, -1) }, zpracujeme poslední vektor z 𝐺:

![$$\begin{align*}\tilde{f}_{n+1}&=(1,3,-1,1)-\frac{\langle(1,1,1,1)|(1,3,-1,1)\rangle}{||(1,1,1,1)||^2}\cdot(1,1,1,1)-\frac{\langle(4,0,-3,-1)|(1,3,-1,1)\rangle}{||(4,0,-3,-1)||^2}\cdot(4,0,-3,-1)\\&=(1,3,-1,1)-\frac{4}{4}\cdot(1,1,1,1)-\frac{6}{26}\cdot(4,0,-3,-1)\\&=\left(-\frac{12}{13},2,-\frac{17}{13},\frac{3}{13}\right)\end{align*}$$](../../svg/lingebra/dox-lingebra-ortogonalizace-e0fa5cae86.svg)

<div align="left"><img alt="" src="..\svg\nSlwwhNE3f.svg"></div>

* 𝐹 = { 𝑓₁ = (1, 1, 1, 1), 𝑓₂ = (4, 0, -3, -1), 𝑓₃ = (-12/13, 2, -17/13, 3/13) }
