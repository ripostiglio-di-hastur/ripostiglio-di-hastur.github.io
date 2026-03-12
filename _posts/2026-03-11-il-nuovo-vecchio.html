---
title: Rispolverare vecchi codici
description: Ho preso in mano roba vecchia e l'ho rispolverata
author: nex
date: 2026-03-11 11:33:00 +0800
categories: [Programming]
tags: [c,hacks,ai]
pin: true
math: true
mermaid: true
image:
  path: /assets/2026/2026-03-11.png
  alt: Una versione improved di catmem
---

# Rispolverare vecchi codici

Uno pensa: "ha appena fatto un post in cui dice che ha riaperto il blog, posterà nuovi contenuti, no?" e farebbe bene, ma analizzando le ragioni, credo di aver voluto fare il post precedente in un attimo di profonda nostalgia dei tempi andati. 

<br/>
D'altra parte sono qui a scrivere un altro articolo, quindi forse non era solo nostalgia? No? Sicuri?

<br/>
Non sono come quelli che fanno articoli lunghissimi, ricercatissimi e che effettivamente spendono parte del loro tempo a fare quello. Io scrivo, così di getto, perché ho voglia di lasciare quello che penso da qualche parte: in un ripostiglio.

## Catmem V2 or CKPTMINI (Checkpoint Mini)

Cosa ho rispolverato? Ho ripreso un vecchissimo progetto fatto un po' così a caso: catmem. Un programma contenuto che aveva lo scopo di ripristinare lo stato di un processo, salvando la sua memoria in una sorta di checkpoint. Quello che avrebbe dovuto fare, lo fa meglio, ma molto meglio, [CRIU](https://criu.org/Main_Page). 
<br/>
Però mi sono detto: "Boia com'era carina quell'idea, peccato poi mi sono fermato, e poi la vita mi ha travolto", ed ora sono qui perché ci ho riprovato.

Il codice sorgente di catmem lo trovate: [qui](https://gist.github.com/interfector/4d0c855ae9799bb68783)
<br/><br/>
Mentre il codice di ckptmini lo trovate: [quo](https://github.com/interfector/ckptmini) (e qua? :D)

### Vibe coding

Lo so, lo so. Qualcuno mi odierà, qualcuno dirà "ma come? la parte pià divertente è programmare!!!!1!!ONE!1!" e io sono anche d'accordo, ma sinceramente non ho più lo sbatti di fare le stronzate come facevo dieci anni fa, quando non c'avevo da pensare a nient'altro (e avevo meno hobby). <br/>
Quindi 'vibe-coding', in che senso? Ho preso 'opencode', modello gratuito e gli ho dato in pasto il codice di catmem, istruzioni inizialmente generiche e poi sempre più precise e ho guardato cosa veniva fuori.
<br/><br/>

C'è da dire che nel mezzo è passata tanta merda e tanti problemi gli ho dovuti correggere a mano, ma sono piacevolmente colpito. Un altro codice che ho dato in pasto a 'opencode' è questo [qui](https://gist.github.com/interfector/0fd830ea799b2f5f7c96), uno shared object injection scritto decenni fa quando c'era ancora **"__libc_dlopen_mode"** e **dlopen** non era ancora in libc. Vabbé, integrato [facile](#Loadare_shared_objects) in un progetto del genere.

### Le funzioni

La funzione principale è quella di fare il `restore` del processo, copiando in memoria il dump effettuato dal comando `save`. Questa è una copia brutale delle memory map, non tenendo conto degli indirizzi e quello che succede se è presente l'ASLR. 
Funziona per programmi piccoli e di poco conto? Sì, soprattutto se usato per ripristinare un processo ancora in esercuzione, visto che gli indirizzi saranno gli stessi. 
Talvolta funziona anche con l'ASLR attivo per via del fatto che i programmi piccoli, sfruttando poca memoria, troveranno gli indirizzi da ripristinare non ancora allocati e quindi ptrace con `MAP_FIXED` può ricostruire il layout originale del programma.

La funzione `inject_shellcode`, sempre carina. Allo shellcode viene aggiunta una '*int3*' (0xCC) per dire al programma principale che lo shellcode è stato eseguito e che quindi può ripristinare i registri e riportare l'esecuzione a dove dovrebbe essere.

Un'altro funzione che avrei dovuto implementare dall'inizio ma che non ho fatto e che forse avrei dovuto chiamare in altro modo è la funzione `upload`. Non fa molto, lancia '*mmap*' e copia dei bytes in quell'indirizzo. Utile in qualche caso, come creare un'intera nuova memory map, o un piccolo spazio di memoria, avrei potuto usarla per refactorare il codice? Forse sì, ma non mi sembrava il caso.

Insieme alla precedente, la funzione `call` è una delle mie preferite, perché ci permette di eseguire codice, in generale una funzione, passando degli argomenti. L'injection è strutturato in modo da creare una pocket con una singola istruzione '*int3*' (ormai famosa!) che sarà il return address della call, a quel punto finita la call (che si spera non finisca in un SIGSEGV), il programma ritorna a quell'indirizzo e triggera un **SIGTRAP**, allora il programma principale ripristina l'esecuzione.

L'ultima funzione, usata magari in concomitanza con la precedente, è `resolve`, questa insieme alla futura `load_so`, trova l'indirizzo di un simbolo tramite **dlsym** e trovando poi l'indirizzo di base della **libc** nel processo target, si calcola l'indirizzo del simbolo dentro il processo target. Vuoi usare `printf` per stampare qualcosa? Lo puoi fare! Vuoi usare una qualsiasi funzione per fare qualcosa? Puoi!

### Loadare shared objects

Qui riprendo un vecchio programma che avevo scritto quando ancora c'era **"__libc_dlopen_mode"** e che trovate [qui](https://gist.github.com/interfector/0fd830ea799b2f5f7c96). In generale però l'idea è la stessa: si calcola l'indirizzo della dlopen del processo target e si chiama tramite "call" con i giusti argomenti, et voilà, shared object caricato.

### Parasite load

Come funziona? Prendiamo spunto da CRIU, ma facciamo le cose più semplici, niente socket strani per la comunicazione, solo la classica *'int3'* che ferma il processo di copia di una regione e passa a quella successiva. That's it! Noi scriviamo i dati delle regioni in una memoria scratch e il parasite copia quella memoria dall'interno sugli indirizzi giusti. E' sicuramente una pesata senza senso, lo so. <br/><br/>

Forse, avrei potuto fare in maniera diversa e quindi mi chiedo quale sia il metodo migliore. <br/>
Magari bastava usare un ciclo di mprotect e `process_vm_writev` senza nessun parasite, senza unmapping e senza croba strana. Chiaramente il parasite ha il pregio di poter fare più cose, e implementandolo un pochino meglio posso manipolare maggiormente il processo target, però è chiaramente più difficile. <br/>
Ora che ci penso, potrei usare `process_vm_writev` per la funzione principale di restore...

## In fin dei conti

Eh, direi carino come progetto ricreativo, utile? Non proprio. Mi sono stupito di quanto l'AI possa fare per idioti come me? SI! E devo dire che in fin dei conti, la cosa che mi è piaciuta è poter visualizzare un'idea ed arrivarci passo passo, anche se non scrivi codice ma vedendolo, commentandolo, dando dritte e aggiustando dove puoi aggiustare. 
E' stato a tratti un casino, perché cancellava codice, riscriveva, poi si perdeva di nuovo e cancellava tutto il file per riscriverlo... senza git sicuramente avrei fatto del casino. 
<br/><br/>
Ma... mi è piaciuto. E ora, vediamo se riesce a scrivere una [TUI](https://github.com/interfector/ckptmini-tui)
