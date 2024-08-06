---
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

![Armor function](/assets/armor_function.png)

*Funzione mitigazione danni f(x)*

Si può osservare dal grafico che la massima pendenza è quando l'armatura è 0 e la pendenza diminuisce man mano che l'armatura aumenta, ciò significa che meno armatura hai più è vantaggioso aumentare l'armatura.
Inoltre nel punto 0 la pendenza è -1, ossia per ogni punto di armatura acquisita si ha una equivalente mitigazione percentuale dei danni. A 100 di armatura i danni fisici subiti sono dimezzati.

## Penetrazione armatura percentuale o lethality?

![Armor pen efficiency](/assets/flat_vs_percentage_pen.png)

Nel primo grafico vengono disegnate 2 ulteriori funzioni:

- la funzione blu è f(x-20)/f(x)
- la funzione verde è f(x*(100-20)/100)/f(x) = f(0.8x)/f(x)

Si può notare dal grafico che l'aumento dei danni a parità di lethality o penetrazione percentuale è la stessa nel punto in cui l'armatura è uguale a 100. Quando il nemico ha più di 100 di armatura è più vantaggiosa la penetrazione armatura percentuale.
Nel grafico sottostante vediamo cosa succede quando utilizziamo un approccio ibrido:

![Hybrid pen efficiency](/assets/hybrid_pen.png)

Notiamo che nella fascia 50-100 dove si trovano la maggior parte dei campioni che non comprano oggetti di armatura aumentiamo i danni di circa 15% solamente aumentando la lethality a 20(che è circa equivalente a comprare un oggetto con lethality).

# Il calcolo della riduzione dell'armatura
La penetrazione e la riduzione armatura segue il seguente ordine:

1) riduzione, flat
2) riduzione, percentuale
3) penetrazione, percentuale
4) penetrazione, flat


Fonti:
[Penetrazione armatura](https://leagueoflegends.fandom.com/wiki/Armor_penetration)
[Armatura](https://leagueoflegends.fandom.com/wiki/Armor)
