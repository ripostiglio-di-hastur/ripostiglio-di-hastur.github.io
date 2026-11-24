---
title: "La dura vita del blogger (LOL)"
description: "E dopo tanto tempo torniamo a scrivere"
author: nex
date: 2012-06-12 17:03:35 +0200
categories: [Personal, Programming, Scheme]
tags: [casual]
permalink: "/2012/06/12/la-dura-vita-del-blogger-lol/"
---

"E dopo tanto tempo torniamo a scrivere..." (cit.)

Ormai scrivo troppo spesso questa frase ma tuttavia è la realtà, non sono fatto per tenere un blog XD (chi non l'aveva capito?)

Beh che dire? Ho finito la scuola, tutto bene, nulla di così speciale...

Quest'estate avevo intenzione di imparare a suonare il violino(non ci spero) e a utilizzare After Effects(mooolto meglio!)

Inoltre volevo partecipare a dei corsi di orientamento all'università dato che sono molto indeciso...

Ora che è arrivata l'estate finalmente potrò portare avanti qualche progetto serio con Beagleboard, Arduino and so on...

Di recente ho creato un disegnatore di funzioni in Scheme che utilizza un wrapper delle SDL scritto in C ( LOL ):

plot.ss: https://sprunge.us/ESXB _(link non più disponibile)_

sdl.c: https://sprunge.us/XTPK _(link non più disponibile)_

L'utilizzo è semplice, dopo aver caricato lo script con load, basta utilizzare la funzione plot nel seguente modo:

```scheme
(plot (list sin exp tan log))
```

E in modo analogo potrete usare funzioni scritte da voi ;)

Quest'estate mi piaceva riempire anche la categoria Filosofia se mi viene in mente qualcosa :D  
P.S.

Ecco qui tutto il pacchetto, il wrapper delle SDL, il plotter (anche uno 3D, o almeno i primi test) e varie cosuccie matematiche...

https://sprunge.us/FeUG _(link non più disponibile)_

Basta che lo salvate e poi date un "base64 -d file > file.tar.gz" e avrete il vostro archivio :D Enjoy ...
