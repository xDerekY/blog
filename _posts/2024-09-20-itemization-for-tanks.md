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

Dividendo la salute massima per il DPS effettivo si può calcolare quanto tempo il tank può restare in fight:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{\text{DPS totale effettivo}}
$$

Sostituendo il termine del DPS totale effettivo esplicitando i fattori di mitigazione e i DPS nominali si ottiene:

$$
t = \text{secondi in fight} = \frac{\text{salute massima}}{f(\text{armatura}) \cdot \text{DPS fisico nominale} + f(\text{resistenza magica}) \cdot \text{DPS magico nominale}}
$$

