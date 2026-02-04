---
{"dg-publish":true,"permalink":"/concepts/linguaggi-di-programmazione/regole-implicite-di-fortran/"}
---

- Regola **I-N**: i nomi delle variabili determinavano in modo _rigido_ il tipo di dato:
	- Tutte le variabili che iniziavano con I,J,K,L,M,N **erano automaticamente integer**
	- Tutto il resto rendeva la variabile un numero [[float\|float]]
- Nessuna dichiarazione: Non esisteva una sezione apposita per la dichiarazione di variabili, come non esisteva nemmeno un modo per dichiararle:
	- bastava usarle nel codice per dichiararle e sarebbe poi stato il compilatore ad assegnare loro il tipo di dato corretto.