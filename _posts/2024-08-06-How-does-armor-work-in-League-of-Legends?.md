![image](https://github.com/user-attachments/assets/3d85dd03-d9d4-49e8-bc39-25ac48ad4a29)---
title: "Come vengono calcolati i danni su League of legends"
date: 2024-08-06
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

![Armor function](/assets/armor_function.png armor_function.png)
*Funzione mitigazione danni f(x)*

# Il calcolo della riduzione dell'armatura
La penetrazione e la riduzione armatura segue il seguente ordine:

1) riduzione, flat
2) riduzione, percentuale
3) penetrazione, percentuale
4) penetrazione, flat


Fonti:
[Penetrazione armatura](https://leagueoflegends.fandom.com/wiki/Armor_penetration)
[Armatura](https://leagueoflegends.fandom.com/wiki/Armor)
