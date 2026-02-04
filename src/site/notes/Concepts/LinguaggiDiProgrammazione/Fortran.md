---
{"dg-publish":true,"permalink":"/concepts/linguaggi-di-programmazione/fortran/"}
---

# Storia
Ideato nel 1954 come _Fortran 0_, poi progettato effettivamente come _Fortran 1_ per il computer [[IBM 704\|IBM 704]].
> E' stato il primo linguaggio creato indipendentemente dalla macchina. I primi linguaggi come [[Concepts/LinguaggiDiProgrammazione/Il primo linguaggio mai creato - Plankalkul\|Plankalkul]], [[Short Code\|Short Code]] e [[Concepts/LinguaggiDiProgrammazione/Speedcoding\|Speedcoding]] erano tutti dipendenti dall'architettura della macchina
# Fortran 1
# [[Concepts/LinguaggiDiProgrammazione/Indipendenza dei linguaggi dalla macchina\|Indipendenza dei linguaggi dalla macchina]]
# Scelte progettuali
l'[[IBM 704\|IBM 704]] era un computer all'avanguardia per quei tempi (supportava [[registri\|registri]] indice e numeri in virgola mobile). Cio' porto all'idea di linguaggi [[Concepts/LinguaggiDiProgrammazione/Indipendenza dei linguaggi dalla macchina#Compilazione\|Compilati]] (come lo sara' poi il [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]]) piuttosto che [[Concepts/LinguaggiDiProgrammazione/Indipendenza dei linguaggi dalla macchina#Interpretazione\|Interpretati]].
# [[Concepts/LinguaggiDiProgrammazione/Caratteristiche fondamentali di Fortran\|Caratteristiche fondamentali di Fortran]]

## Perche' compilato e non interpretato
Perche' con l'hardware di quei tempi era impossibile nascondere il costo computazionale dell'interpretazione.
Tradotto in italiano:
> Il processo di traduzione da linguaggio di alto livello a [[Codice Macchina\|Codice Macchina]] sarebbe stato troppo lento e ne avrebbero sofferto le prestazioni del programma.
## [[Ambiente di sviluppo\|Ambiente di sviluppo]] e dominio applicativo
L'[[Ambiente di sviluppo\|Ambiente di sviluppo]] di [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]] era piuttosto scarno, come del resto era il panorama della programmazione negli anni '50
> Oltre a compilatori, [[linker\|linker]] e [[assembler\|assembler]] che almeno permettevano al programma di eseguire non c'era nient'altro:
- I computer erano piccoli e inaffidabili (e poco potenti).
	- Vedo che il [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]] ha tenuto conto di questa cosa qui: [[Concepts/LinguaggiDiProgrammazione/Caratteristiche fondamentali di Fortran\|Caratteristiche fondamentali di Fortran]], nella parte dove citiamo la mancanza di memorizzazione dinamica.
- Non esisteva ancora nessuna [[metodologia programmativa\|metodologia programmativa]] oppure nessun strumento di programmazione (Ex: IDE)
- I [[compilatore\|compilatori]] erano anch'essi molto basici, non c'era nessun tipo di ottimizzazione del programma al di fuori di quella fatta manualmente dal programmatore stesso, per questo motivo l'efficienza della macchina era la **preoccupazione piu' importante**.
[[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]] era un linguaggio molto incentrato su operazioni matematiche. Il suo dominio applicativo era quindi quello delle _applicazioni scientifiche_.

## Un esempio di [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]]
Proviamo a leggere questo esempio anche tenendo a mente le [[Concepts/LinguaggiDiProgrammazione/Regole implicite di Fortran\|Regole implicite di Fortran]]:
> IF (espressione) etichetta_negativa, etichetta_zero, etichetta_positiva      
```fortran
X = 15.0      
Y = 10.0       C     Per testare se X > Y, si calcola X-Y    
IF (X - Y) 10, 20, 30
10 PRINT 101      
   GO TO 40
20 PRINT 102     ! X = Y (X-Y zero)      
   GO TO 40  
30 PRINT 103    
40 CONTINUE
```

# L'evoluzione di Fortran
Fortran 1 non fu l'unica versione di [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]] mai creata, ce ne furono diverse:
- Fortran 95
- Fortran 2003 
	- supporto per OOP
	- puntatori a procedure
	- Interoperabilita' con C
- Fortran 2008
	- blocchi per scope locali
	- co-array
	- do-concurrent
con i loro relativi compilatori aggiornati e con qualche ottimizzazione

# Commenti finali su Fortran
Per quanto antico e primitivo, [[Concepts/LinguaggiDiProgrammazione/Fortran\|Fortran]] ha cambiato completamente il modo di utilizzare e programmare sui computer.