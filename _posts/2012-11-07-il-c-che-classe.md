---
title: "Il C...che classe..."
description: "Un tentativo mal riuscito di \"riprodurre\" le classi in C"
author: nex
date: 2012-11-07 20:54:03 +0100
categories: [Assembly, C, Hacks, Programming]
tags: [casual]
permalink: "/2012/11/07/il-c-che-classe/"
---

Un po' di giorni fa mi ero messo a bazzicare tra i miei sorgenti scritti e lasciati a marcire nei meandri del pc...

E cosa mi salta all'occhio? Un tentativo mal riuscito di "riprodurre" le classi in C.  
Come sia possibile dici? Eh, roba veramente assurda...

In pratica si tratta di codice automodificante che in run-time modifica una variabile all'interno di ogni funzione (facendone una copia) sostituendolo con l'indirizzo dell'istanza della classe.

Forse a dirsi è più difficile che a vedersi...

vector.c: https://sprunge.us/FEKd _(link non più disponibile)_

Probabilmente la parte più interessante è la 'function\_copy' che serve per "copiare" una funzione in un altra area di memoria, mettendo a posto gli offset delle call in modo da non creare errori; in questo modo si possono avviare più istanze di una sola classe.

Comunque questo è solo un gioco, un qualcosa di figo, non è assolutamente qualcosa di serio, anzi è sporco, brutto e fatto male, ma divertente. Mi son divertito a farlo funzionare ;)

Inoltre con l'aiuto del mio amico stoke, ho finalmente concluso lo shared object injector, che ora funziona quasi a meraviglia...

dlinj.c: [Gist](https://gist.github.com/interfector/ba125f4b23c25306fb3d)
