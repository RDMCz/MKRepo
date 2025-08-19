# Algoritmus Apriori

## Generování množin

Mějme transakční data, např. položky v nákupech:

```text
I1, I2, I5
I2, I4
I2, I3
I1, I2, I4
I1, I3
I2, I3
I1, I3
I1, I2, I3, I5
I1, I2, I3
```

Spočítáme výskyty jednotlivých položek (jednoprvkových množin):

```text
{I1}    6
{I2}    7
{I3}    6
{I4}    2
{I5}    2
```

Vyřadíme záznamy, které nesplňují minimální support.<br>
Náš minimmální support jsou 2 výskyty, proto se tabulka nezmění:

```text
{I1}    6
{I2}    7
{I3}    6
{I4}    2
{I5}    2
```

Vytvoříme dvoupoložkové množiny a spočítáme jejich výskyty:

Každý s každým, nezáleží na pořadí: {I1, I2}, {I1, I3}, {I1, I4}, {I1, I5}, {I2, I3}, {I2, I4}, {I2, I5}, {I3, I4}, {I3, I5}, {I4, I5}

U vytvořených množin je potřeba zkontrolovat, zdali jsou všechny jejich podmnožiny také frekventované. U&nbsp;dvouprvkových množin jsou podmnožiny pouze jednoprvkové, a ty jsou vždy frekventované (dvojice tvoříme z&nbsp;prvků splňujících minimální support).

```text
{I1, I2}    4   (ve 4 nákupech se objevilo jak I1, tak I2)
{I1, I3}    4
{I1, I4}    1
{I1, I5}    2
{I2, I3}    4
{I2, I4}    2
{I2, I5}    2
{I3, I4}    0
{I3, I5}    1
{I4, I5}    0
```

Odebereme dvojice nesplňující minimální support:

```text
{I1, I2}    4
{I1, I3}    4
{I1, I5}    2
{I2, I3}    4
{I2, I4}    2
{I2, I5}    2
```

Vytvoříme třípoložkové množiny a spočítáme jejich výskyty:

Trojice tvoříme pouze z dvojic se stejnou levou stranou: {𝑥, 𝑦} & {𝑥, 𝑧} → {𝑥, 𝑦, 𝑧}<br>
⇒ {I1, I2, I3}, {I1, I2, I5}, {I1, I3, I5}, {I2, I3, I4}, {I2, I3, I5}, {I2, I4, I5}

U vytvořených množin je potřeba zkontrolovat, zdali jsou všechny jejich podmnožiny také frekventované. U&nbsp;tříprvkových jsou to jednoprvkové (vždy frekventované) a dvouprvkové (je potřeba všechny zkontrolovat, např.: pro {𝑥, 𝑦, 𝑧} zkontrolovat {𝑥, 𝑦}, {𝑥, 𝑧}, {𝑦, 𝑧}).

* Takto vyřadíme:
  * {I1, I3, I5} &emsp; ...protože {I3, I5} není frekventovaná
  * {I2, I3, I4} &emsp; ...protože {I3, I4} není frekventovaná
  * {I2, I3, I5} &emsp; ...protože {I3, I5} není frekventovaná
  * {I2, I4, I5} &emsp; ...protože {I4, I5} není frekventovaná

Z toho, co zbylo, odebereme trojice nesplňující minimální support (v tomto případě nic neodebíráme):

```text
{I1, I2, I3}    2
{I1, I2, I5}    2
```

Vytvoříme čtyřpoložkové množiny a spočítáme jejich výskyty:

{I1, I2, I3, I5}

Zkontrolovat frekventovanost podmnožin → {I2, I3, I5} a další nejsou frekventované → zahazujeme poslední množinu → končíme.

Výsledek je 𝐿 = { {I1}, {I2}, {I3}, {I4}, {I5}, {I1, I2}, {I1, I3}, {I1, I5}, {I2, I3}, {I2, I4}, {I2, I5}, {I1, I2, I3}, {I1, I2, I5} }

## Generování asociačních pravidel

Pravidla tvoříme z množin z 𝐿 ve formě ( 𝑠 → 𝑙 ∖ 𝑠 ), tato pravidla musí splňovat zadaný minimální confidence, např. 70 %. Ten se počítá jako počet výskytů 𝑙 lomeno počet výskytů 𝑠.

Vezměme například 𝑙 = {I1, I2, I5}

* I1 → I2 ∧ I5
  * 𝑠 = {I1}
  * 𝑙 ∖ 𝑠 = {I2, I5}
  * Počet výskytů 𝑙 je 2 (čitatel je vždy stejný)
  * Počet výskytů 𝑠 je 6
  * Confidence = 2/6 ~ 33 % ⇒ Pravidlo nepřijato
* I2 → I1 ∧ I5
  * 2/7 ~ 29 % ⇒ Ne
* I5 → I1 ∧ I2
  * 2/2 = 100 % ⇒ __Ano__
* I1 ∧ I2 → I5
  * 𝑠 = {I1, I2}
  * 𝑙 ∖ 𝑠 = {I5}
  * Počet výskytů 𝑠 je 4
  * Confidence = 2/4 = 50 % ⇒ Ne
* I1 ∧ I5 → I2
  * 2/2 = 100 % ⇒ __Ano__
* I2 ∧ I5 → I1
  * 2/2 = 100 % ⇒ __Ano__

Z {I1, I2, I5} jsme získali 3 pravidla. Tohle musíme provést pro všechny víceprvkové množiny z 𝐿.
