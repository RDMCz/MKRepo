# Vlastní čísla a vlastní vektory

## Způsoby výpočtu vlastních čísel a vlastních vektorů

### Klasika

* `Zadání` Určete vlastní čísla a jim odpovídající vlastní vektory matice:

```text
⎡-35  39⎤
⎢       ⎥
⎣-26  30⎦
```

#### Určení vlastních čísel

* `1` Odečteme od matice matici _λ_ · 𝐸 (jako 𝐸 chápeme jednotkovou matici), tím dostáváme matici 𝐹<sub>_λ_</sub>
* `2` Vypočítáme determinant matice 𝐹<sub>_λ_</sub>
* `3` Po úpravě výrazu dostáváme charakteristický polynom:

```text
    ⎡-35-λ   39 ⎤
det ⎢           ⎥ = (-35-λ)(30-λ)+39·26 = -1050+35λ-30λ+λ²+1014 = λ²+5λ-36
    ⎣ -26   30-λ⎦
```

* `4` Vypočítáme kořeny charakteristického polynomu:

![$$\begin{align*}\lambda^2+5\lambda-36&=0\\\sqrt{d}&=\sqrt{25+144}=\sqrt{169}=13\\\lambda_{1,2}&=\frac{-5\pm13}{2}=\begin{cases}-9\\+4\end{cases}\end{align*}$$](../../svg/lingebra/dox-lingebra-vlastni_vektory-49b52e743e.svg)

* `⇒` Vlastní čísla jsou __-9__ a __4__

#### Určení vlastních vektorů

* `1` Dosadíme vlastní číslo do matice 𝐹<sub>_λ_</sub>
* `2` Matici vyřešíme jako homogenní soustavu rovnic
* `3` Vyjde nekonečně mnoho řešení, proto zavedeme parametr 𝑥₂ = 𝑡 a dopočítáme 𝑥₁:

```text
                                                                𝑥₁ 𝑥₂              𝑥₂ = 𝑡
⎡-35-(-9)    39   ⎤   ⎡-26  39⎤   ⎡-26  39 ⎥ 0 ⎤   ⎡-2  3 ⎥ 0 ⎤   ⎡-2  3 ⎥ 0 ⎤   -2𝑥₁ + 3𝑡 = 0
⎢                 ⎥ = ⎢       ⎥ → ⎢        ⎥   ⎥ ~ ⎢      ⎥   ⎥ ~ ⎢      ⎥   ⎥        -2𝑥₁ = -3𝑡
⎣  -26     30-(-9)⎦   ⎣-26  39⎦   ⎣-26  39 ⎥ 0 ⎦   ⎣-2  3 ⎥ 0 ⎦   ⎣ 0  0 ⎥ 0 ⎦          𝑥₁ = (3/2)𝑡
```

* `⇒` Vlastní číslo __-9__ má vlastní vektory __𝑡 · (3/2; 1)__

```text
                                                                𝑥₁ 𝑥₂              𝑥₂ = 𝑡
      ⎡-35-4   39 ⎤   ⎡-39  39⎤   ⎡-39  39 ⎥ 0 ⎤   ⎡-1  1 ⎥ 0 ⎤   ⎡-1  1 ⎥ 0 ⎤   -1𝑥₁ + 1𝑡 = 0
      ⎢           ⎥ = ⎢       ⎥ → ⎢        ⎥   ⎥ ~ ⎢      ⎥   ⎥ ~ ⎢      ⎥   ⎥          𝑥₁ = 𝑡
      ⎣ -26   30-4⎦   ⎣-26  26⎦   ⎣-26  26 ⎥ 0 ⎦   ⎣-1  1 ⎥ 0 ⎦   ⎣ 0  0 ⎥ 0 ⎦
```

* `⇒` Vlastní číslo __4__ má vlastní vektory ___t_ · (1; 1)__

### Rychlejší způsob určení vlastních čísel pro matice 2×2

![$$\begin{align*}\lambda_{1,2}&=m\pm\sqrt{m^2-p}\\m&:\text{prumer hlavni diagonaly matice}\\p&:\text{determinant matice}\\m&=\frac{-35+30}{2}=-\frac{5}{2}\\p&=(-35\cdot30)-(39\cdot(-26))=36\\\lambda_{1,2}&=-\frac{5}{2}\pm\sqrt{\frac{25}{4}+\frac{144}{4}}\\&=-\frac{5}{2}\pm\sqrt{\frac{169}{4}}\\&=-\frac{5}{2}\pm\frac{13}{2}\\&=\frac{-5\pm13}{2}=\begin{cases}-9\\+4\end{cases}\end{align*}$$](../../svg/lingebra/dox-lingebra-vlastni_vektory-a2a6a862bb.svg)

## Příklady

```py
# Vygenerování náhodného příkladu pro výpočet vlastních čísel a vektorů (Python + SymPy):
values = [-2, -1, 1, 2]
mx_v = sp.Matrix([[1, random.choice(values)], [0, 1]]) * sp.Matrix([[1, 0], [random.choice(values), 1]])
mx = mx_v * sp.Matrix([[random.randint(-10, 10), 0], [0, random.randint(-10, 10)]]) * mx_v.inv()
print(f"Určete vlastní čísla a jim odpovídající vlastní vektory matice:\n{sp.pretty(mx)}\n")
eigenvecs = "".join(f"  Vlastní číslo: {tup[0]}\nVlastní vektory: {[list(x) for x in tup[2]]}\n\n" for tup in mx.eigenvects())
print(eigenvecs)
```
