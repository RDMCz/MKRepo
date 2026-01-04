# IEEE 754 převody

* Převody mezi soustavami a teorie ohledně IEEE 754 probrána zde: [SZRepo/BC/09](https://github.com/RDMCz/SZRepo/blob/main/BC/DX/09.MD)
* Číslo je uloženo jako 𝐴 = (-1)<sup>𝑆</sup> ⋅ 𝑀 ⋅ 2<sup>𝐸-_bias_</sup>
* Mantisa je vždy „_jedna celá něco_“, proto se jednička neukládá (je vždy stejná) a ukládá se pouze lomená část mantisy

alias|bitů||_sign_ 𝑆|_exponent_ 𝐸|_mantissa_ 𝑀||_bias_ = 2<sup>bitů(𝐸)-1</sup>-1
---|--:|---|--:|--:|--:|---|--:
`float`|32||1 bit|8 bitů|23 bitů||127
`double`|64||1 bit|11 bitů|52 bitů||1023

## Příklady

### Příklad I

Zobrazte ve 32 bitech číslo -258,125.

1. Podle originálního čísla určíme 𝑆 (0 kladné, 1 záporné)
   * `𝑆 = 1`

2. Převedeme absolutní hodnotu originálního čísla do binární soustavy
   * `258,125 → 100000010,001`

3. Posuneme čárku, aby byla napravo od _most significant jedničky_; pamatovat si: počet posunů, směr posunů, výsledné číslo
   * `100000010,001 → 1,00000010001`, `8 posunů vlevo`

4. 𝑀 je lomená část výsledného čísla
   * `𝑀 = 00000010001`

5. Spočteme 𝐸:
   * Pokud jsme posouvali vlevo (abs. hodnota originálního čísla je ≥ 1), pak 𝐸 = _bias_ + počet posunů
   * Pokud jsme posouvali vravo (abs. hodnota originálního čísla je < 1), pak 𝐸 = _bias_ - počet posunů
   * `𝐸 = 127 + 8 = 135 → 10000111`

6. Doplníme 𝑆𝐸𝑀 do 32 bitů (1 + 8 + 23), mantisu případně doplníme nulami __zprava__
   * `11000011100000010001000000000000`
   * `SEEEEEEEEMMMMMMMMMMMMMMMMMMMMMMM`

7. Převedeme na hexa
   * `C3811000`
   * Big endian: `C3 81 10 00`
   * Little endian: `00 10 81 C3`

### Příklad II

Převeďte číslo (42 91 40 00)<sub>16 (big endian)</sub> do dekadické soustavy dle IEEE 754.

1. Převedeme hexa na binary
   * `0x42914000 → 0100 0010 1001 0001 0100 000 000 (⇒ 32 bitů)`

2. 𝑆 je první bit
   * `𝑆 = 0 ⇒ Výsledné číslo je kladné`

3. Dalších 8 bitů je 𝐸; mantisu násobíme „hodnotou posunu“ 2<sup>𝐸-_bias_</sup>
   * `𝐸 = 10000101 = 133`, `„hodnota posunu“ = 2¹³³⁻¹²⁷ = 2⁶`

4. Mantisa je „_jedna celá zbylé bity_“
   * `𝑀 = 1,00100010100000000`

5. Vynásobíme mantisu „hodnotou posunu“
   * `1,00100010100000000 ⋅ 2⁶ = 1001000,10100000000`

6. Převedeme do dekadické soustavy
   * `1001000,101 = 72,625`

7. Nezapomenout na znaménko (pokud 𝑆 = 1)
