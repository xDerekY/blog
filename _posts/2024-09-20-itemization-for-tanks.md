---
title: "Itemizzazione per tank"
date: 2024-09-20
layout: post
---

# Armatura/resistenza magica e danni effettivi

Su league of legends esiste il concetto di armatura e di resistenza magica, i danni non vengono subiti in quantità nominale ma vengono mitigati in base all'armatura e alla resistenza magica posseduta secondo l'equazione:

$$
f(x) = 
\begin{cases} 
    \frac{100}{100+armor}, & \text{if } armor \geq 0 \\
    2-\frac{100}{100+|armor|}, & \text{if } x < 0 
\end{cases}
$$

$$
\text{danni subiti} = f(\text{armatura}) \cdot \text{danni nominali}
$$

Pertanto dividendo ambo i membri per l'unità di tempo si ottiene:

$$
\text{DPS effettivo} = f(\text{armatura}) \cdot \text{DPS nominale}
$$

Considerando anche la resistenza magica e l'additività dei danni:

$$
\text{DPS totale effettivo} = f(\text{armatura}) \cdot \text{DPS fisico nominale} + f(\text{resistenza magica}) \cdot \text{DPS magico nominale}
$$

Trascurando la rigenerazione salute, dividendo la salute massima per il DPS effettivo si può calcolare quanto tempo il tank può restare in fight:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{\text{DPS totale effettivo}}
$$

Sostituendo il termine del DPS totale effettivo esplicitando i fattori di mitigazione e i DPS nominali si ottiene:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{f(\text{armatura}) \cdot \text{DPS fisico nominale} + f(\text{resistenza magica}) \cdot \text{DPS magico nominale}}
$$

Studiandolo dal punto di vista dell'itemizzazione:

$$
g(h,a,r) = \frac{\text{salute attuale} + h}{f(\text{armatura attuale}+a) \cdot \text{DPS fisico nominale} + f(\text{resistenza magica attuale} + r) \cdot \text{DPS magico nominale}}
$$

Siccome il termine $$\text{armatura attuale}+a$$ e il termine $$\text{resistenza magica attuale}+r$$ sono sempre positivi:

$$
g(h,a,r) = \frac{\text{salute attuale} + h}{\frac{100}{100+\text{armatura attuale}+a} \cdot \text{DPS fisico nominale} + \frac{100}{100+\text{resistenza magica attuale}+r} \cdot \text{DPS magico nominale}}
$$

Si possono considerare 2 casi:
- il DPS fisico è equiparabile a quello magico
- uno dei due DPS è preponderante

# Danni prevalentemente fisici

Studiamo prima il caso in cui uno dei due DPS è preponderante, ad esempio quello fisico, allora possiamo studiare la funzione semplificata:

$$
g(h,a) = \frac{\text{salute attuale} + h}{\frac{100}{100+\text{armatura attuale}+a} \cdot \text{DPS fisico nominale}}
$$

Siccome il DPS fisico nominale non dipende dalle statistiche difensive del nostro campione, ma dalle statistiche offensive dei campioni nemici possiamo considerarlo costante:

$$
salute effettiva = g(h,a) = \frac{\text{salute attuale} + h}{\frac{100}{100+\text{armatura attuale}+a}} = (\text{salute attuale} + h)(1+\frac{\text{armatura attuale}+a}{100})
$$

Prendendo come esempio Blitzcrank e confrontando la Warmog non completata(+150+350+200 salute ~ +700 salute) pari a  e il Locket(+200 salute, 30 armatura, 30 resistenza magica) come first item al livello 7 con già l'oggetto da support che dà 200 di salute:

$$
g(Warmog non completata) = (1128 + 200 + +150+350+200)(1 + \frac{60+0}{100}) = 3245
$$
$$
g(Warmog 2000 gold) = (1128 + 200 +150+150+200)(1 + \frac{60+0}{100}) = 2925
$$
$$
g(Locket) = (1128 + 200 + 200)(1 + \frac{60+30}{100}) = 2903
$$
$$
g(Locket con attiva) = (1128 + 200 + 200 + 280)(1 + \frac{60+30}{100}) = 3435
$$

È evidente che il build path della Warmog è migliore di quello del Locket, e che il Locket rende più tankosi solo con l'utilizzo dell'attiva. È anche vero che l'attiva della Warmog è molto più forte del Locket se si riesce a sfruttarla. Questo non considerando le altre diverse statistiche che i due oggetti portano come ability haste e rigenerazione salute.

# Danni misti equiparabili

Studiamo prima il caso in cui i due DPS sono confrontabili, allora possiamo studiare la funzione semplificata:

$$
g(h,a,r) = \frac{\text{salute attuale} + h}{(\frac{100}{100+\text{armatura attuale}+a} + \frac{100}{100+\text{resistenza magica attuale}+r}) \cdot \text{DPS nominale}}
$$

Siccome il DPS nominale non dipende dalle statistiche difensive del nostro campione, ma dalle statistiche offensive dei campioni nemici possiamo considerarlo costante:

$$
g(h,a,r) = \frac{\text{salute attuale} + h}{\frac{100}{100+\text{armatura attuale}+a} + \frac{100}{100+\text{resistenza magica attuale}+r}} = \frac{(\text{salute attuale} + h)(100+\text{armatura attuale}+a)(100+\text{resistenza magica attuale}+r)}{100(200+\text{armatura attuale}+a+\text{resistenza magica attuale}+r)}
$$

$$
g(Warmog non completata) = \frac{(1128 + 200 +700)(100 + 60 + 0)(100 + 42 + 0)}{100(200 + 60 + 0 + 42 + 0)} = 1525
$$

$$
g(Warmog 2000 gold) = \frac{(1128 + 200 +150+150+200)(100 + 60 + 0)(100 + 42 + 0)}{100(200 + 60 + 0 + 42 + 0)} = 1375
$$

$$
g(Locket) = \frac{(1128 + 200 + 200)(100 + 60 + 30)(100 + 42 + 30)}{100(200 + 60 + 30 + 42 + 30)} = 1379
$$

$$
g(Locket con attiva) = \frac{(1128 + 200 + 200 + 280)(100 + 60 + 30)(100 + 42 + 30)}{100(200 + 60 + 30 + 42 + 30)} = 1632
$$

Come prima l'attiva del Locket dà un sacco di value all'item.
