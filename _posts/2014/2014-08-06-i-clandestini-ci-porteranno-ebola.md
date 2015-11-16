---
layout: page
sidebar: right
title:  "I clandestini ci portano Ebola!!11!!! Ma anche no."
subheadline:  "La matematica parla chiaro."
teaser: "Noti gruppi neo fascisti italiani sfruttano la paura del diverso per guadagnare consensi, millantando possibili arrivi di malattie esotiche. Epidemia in arrivo?"
categories:
    - "attualità"
tags:
    - fascisti
    - ebola
    - immigrazione
    - clandestini
    - malattie
image:
    title: 2014/clandestini-ebola.jpg
    thumb: 2014/clandestini-ebola.jpg
    homepage: 2014/clandestini-ebola.jpg
    caption: Arrivano i clandestini!
    caption_url: http://danilopianini.org/
header:
    image_fullwidth: "2014/clandestini-ebola.jpg"
    caption: Il manifesto dei neofascisti
    caption_url: http://danilopianini.org/
---

Sono rimasto sconvolto da un manifesto di Forza Nuova, che fa leva sul timore di una diffusione dell'epidemia di Ebola in corso per alimentare l'odio xenofobico verso i clandestini. Siccome la matematica non è un fosso, ho pensato di buttare giù due conti e vedere quanto questi giovanotti sono andati vicini alla realtà.

Purtroppo non sono un epidemiologo, per cui farò alcune assunzioni un po' grezze. Diciamo che considero 4-5 ordini di grandezza nell'errore finale della probabilità come accettabili - quando vedrete il risultato capirete perché. In ogni caso, avrei piacere se qualche epidemiologo mi lasciasse approfondimenti nei commenti, in particolare sono curioso circa la distribuzione probabilistica del tempo di insorgenza dei sintomi dal momento del contagio.

Ebola ha un periodo di incubazione di 2-21 giorni. È praticamente impossibile viaggiare senza un mezzo rapido dalle zone soggette al [focolaio attuale](http://en.wikipedia.org/wiki/2014_West_Africa_Ebola_outbreak) alle coste sicule in quel tempo: l'epidemia non è in Nord Africa. Occorrerebbe una traversata del Sahara a malattia già contratta, e a quel punto comunque la si diffonderebbe a macchia sul barcone. Il malato suddetto mostrerebbe i sintomi PRIMA dello sbarco, e non solo: se si suppone una [distribuzione di Poisson](http://en.wikipedia.org/wiki/Poisson_distribution) di media 9 giorni (ed è enormemente abbondante) per l'apparizione dei sintomi e una durata di 5 giorni, la probabilità che un singolo manifesti i sintomi è:

![Poisson](http://www.sciweavers.org/tex2img.php?eq=P%28x%3C9%29%20%3D%20%20%5Csum_%7Bi%3D0%7D%5E5%20%7B9%5Ei%20%C2%B7%20%5Cfrac%7Be%5E%7B-9%7D%7D%7Bi%21%7D%7D%20%5Csimeq%7B%7D%20%200.20678083982%20%5Csimeq%7B%7D%2020%5C%25&bc=White&fc=Black&im=png&fs=12&ff=arev&edit=0)

tradotto, in un barcone di 200 immigranti la probabilità che NESSUNO mostri i sintomi di Ebola è:

![Reverse](http://www.sciweavers.org/tex2img.php?eq=%281%20-%20P%28x%3C9%29%29%5E%7B200%7D%20%3D%207.5620441e%5E%7B-21%7D%20%7E%3D%200.000000000000000007%5C%25&bc=White&fc=Black&im=png&fs=12&ff=arev&edit=0)

Per farte un confronto, le probabilità di essere colpito da due fulmini entro un'ora è circa:
![Prob](http://www.sciweavers.org/tex2img.php?eq=226%20%5Ccdot%7B%7D%20e%7B-21%7D&bc=White&fc=Black&im=png&fs=12&ff=arev&edit=0)
Ossia circa due ordini di grandezza più grande (calcolato a partire da P=1/3000 su 80 anni di vita). È circa 50 volte meno probabile che ebola sbarchi in Sicilia non individuato rispetto al rischio di essere colpiti da due fulmini in un'ora. Io comincerei a consigliare alla gente di stare chiusa in casa e montare parafulmini ovunque: il rischio è alto. Faccio anche notare che sono stato conservativo, perché ho supposto che la traversata del deserto avvenga in tempo zero e che il contagio avvenga **dopo** l'imbarco senza che vi fosse alcuna traccia prima della partenza.

Se i soggetti che scrivono simili scempiaggini andassero a fare un ripassino di matematica invece di giocare al fascista moderno, la società ne trarrebbe grande beneficio.
