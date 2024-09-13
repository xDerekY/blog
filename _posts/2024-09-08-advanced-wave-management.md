---
title: "Wave management avanzato"
date: 2024-09-08
layout: post
---

Su League of Legends possono spawnare 3 tipi di wave:
- la wave senza cannone: 3 [unità melee](https://leagueoflegends.fandom.com/wiki/Melee_minion), 3 [unità ranged](https://leagueoflegends.fandom.com/wiki/Caster_minion)
- la wave con cannone: 1 [cannone](https://leagueoflegends.fandom.com/wiki/Siege_minion), 3 unità melee, 3 unità ranged
- la wave con superminions: 1 o 2 [super minions](https://leagueoflegends.fandom.com/wiki/Super_minion), 3 unità melee, 3 unità ranged

Ogni 90 secondi(3 wave) le wave che spawnano diventano più forti. Dal minuto 10 i minion ottengono progressivamente più velocità di movimento. Prima del minuto 14(e dopo la prima wave) le wave di minion si schiantano allo stesso tempo anche per le corsie più lunghe(le wave in top and in bot si schiantano allo stesso tempo della wave in mid). Nei primi 15 minuti la wave del cannone spawna ogni 3 wave, cioè alla terza wave.

### Aggro

L'aggro dei minion segue il seguente ordine di priorità:
- il campione nemico che attacca un campione alleato
- il minion che attacca un campione alleato
- il minion che attacca un minion alleato
- la torre che attacca un minion alleato
- campione nemico che attacca un minion alleato
- minion più vicino
- campione più vicino

### [Minion buffs](https://leagueoflegends.fandom.com/wiki/Minion_(League_of_Legends)#Buffs)

I minion ottengono dei buff in danni bonus e danni subiti ridotti che aumentano linearmente rispetto al prodotto tra il differenziale di livello medio e il differenziale di torri nella corsia. Tale meccanica incentiva a non perdere livelli, a distruggere le torri nemiche e a proteggere le torri alleate.


### Wave states

Lo stato di una wave può assumere 4 stati con i corrispettivi contrari:
- pushing:

![pushing]({{ "/assets/pushing.png" | relative_url }})
- accumulation:

![accumulation]({{ "/assets/accumulation.png" | relative_url }})
- freeze:

![freeze]({{ "/assets/freeze.png" | relative_url }})
- middle freeze:

![middle freeze]({{ "/assets/middle_freeze.png" | relative_url }})
