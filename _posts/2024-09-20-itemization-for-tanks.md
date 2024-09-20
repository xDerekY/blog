---
title: "Itemizzazione per tank"
date: 2024-09-20
layout: post
---

Per semplicità verranno considerati solo i danni fisici, gli stessi calcoli si applicano a quelli magici.

# Armatura/resistenza magica e danni effettivi

Su league of legends esiste il concetto di armatura, i danni fisici non vengono subiti in quantità nominale ma vengono mitigati in base all'armatura posseduta secondo l'equazione:

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

Dividendo la salute massima per il DPS effettivo si può calcolare quanto tempo il tank può restare in fight:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{\text{DPS effettivo}}
$$

Sostituendo il termine del DPS effettivo esplicitando il fattore di mitigazione e il DPS nominale si ottiene:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{f(\text{armatura}) \cdot \text{DPS nominale}}
$$

Fissando il termine legato al DPS nominale, studiamo il fattore $$ \frac{\text{salute massima}}{f(\text{armatura})} $$ sotto il punto di vista dell'itemizzazione:

$$
g(a,h) = \frac{\text{salute attuale} + h}{f(\text{armatura attuale} + a)}
$$

Siccome il termine $\text{armatura attuale} + a$ è sempre positivo, possiamo semplificare la formula: 

$$
g(a,h) = \frac{\text{salute attuale} + h}{\frac{100}{100 + \text{armatura attuale} + a}} = (\text{salute attuale} + h)(1 + \frac{\text{armatura attuale} + a}{100})
$$
