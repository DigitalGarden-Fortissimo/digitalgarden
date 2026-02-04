---
{"dg-publish":true,"permalink":"/concepts/linguaggi-di-programmazione/caratteristiche-fondamentali-di-fortran/"}
---

- **mancato bisogno di [[Concepts/LinguaggiDiProgrammazione/memorizzazione dinamica\|memorizzazione dinamica]]**. Consentire soltanto [[Concepts/LinguaggiDiProgrammazione/memorizzazione statica\|memorizzazione statica]] rendeva la gestione dei dati in memoria semplice e veloce.
	- Il linguaggio ha scelto di negare la possibilita' di variabili locali in chiamate di funzioni. La conseguenza logica di questa scelta e' la mancanza di [[ricorsione\|ricorsione]].
	- Le subroutine esistono ma non avevano variabili locali, usano le variabili globali. 
- Possedeva una buona gestione di [[array\|array]] e cicli di conteggio
	- Il ciclo di conteggio era un do-while
- **Nessuna** gestione di stringa, aritmetica decimale o input/output potente
- Gli identificatori avevano al massimo _6 caratteri_
- **Caratteristico IF a tre vie** 
- **Nessuna dichiarazione di tipi di dato utente**.
	- Struct, oggetti e/o typedef non esistevano
- Una volta compilato, il codice era piuttosto veloce