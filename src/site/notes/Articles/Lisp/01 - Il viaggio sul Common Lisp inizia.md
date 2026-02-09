---
{"dg-publish":true,"permalink":"/articles/lisp/01-il-viaggio-sul-common-lisp-inizia/"}
---

# Ambiente di sviluppo

In questa prima parte del viaggio andremo a configurare un **ambiente di sviluppo per Common Lisp**.

Praticamente tutti i linguaggi di programmazione offrono un supporto più o meno standard per creare un ambiente di sviluppo _ad hoc_ su qualunque editor si utilizzi. **Common Lisp no** — o meglio: non del tutto.

Storicamente, Common Lisp è supportato soprattutto da **ambienti di sviluppo dedicati** (come _LispWorks_, _Allegro CL_, _CLion + plugin_, ecc.) e da pochissimi editor general-purpose. Tra questi, **Emacs** è senza dubbio quello con l’integrazione migliore, grazie alla lunga tradizione Lisp e a strumenti maturi come **SLIME** e **Sly**.

In questa guida utilizzerò **Doom Emacs**, una “distribuzione” di Emacs moderna, modulare e orientata alla produttività.

> 📌 **Nota**: l’installazione di Doom Emacs non verrà trattata qui, poiché è spiegata in modo chiaro e aggiornato nella repository ufficiale:  
> [https://github.com/doomemacs/doomemacs](https://github.com/doomemacs/doomemacs)

---
## Perché Emacs (e perché Doom)

Emacs non è semplicemente un editor di testo: è un vero e proprio **ambiente di sviluppo estendibile**, e Common Lisp è uno dei linguaggi per cui Emacs offre l’esperienza migliore in assoluto.
Doom Emacs, in particolare, fornisce:
- una configurazione modulare (abiliti solo ciò che ti serve);
- performance migliori rispetto a una configurazione vanilla;
- integrazioni già pronte per LSP, REPL, Git, tree-sitter, ecc.
insomma ci da una grande mano per avere un jump-start davvero impareggiabile.

---

## Configurazione di Doom Emacs

La parte davvero importante è la **configurazione**. Per lavorare comodamente con Common Lisp dobbiamo abilitare alcuni moduli specifici modificando il file `init.el`.

Dopo ogni modifica a `init.el`, ricordati di eseguire:

```bash
doom sync
```

### Configurazione completa

Se non avete voglia di configurare Doom Emacs manualmente, potete copiare e incollare direttamente il mio `init.el` (riportato integralmente qui sotto). È una configurazione generale che uso quotidianamente e che include il supporto a Common Lisp.

> ⚠️ Non è necessario capire tutto subito: molte sezioni possono essere ignorate o modificate in seguito.

```lisp
;;; init.el -*- lexical-binding: t; -*-

;; This file controls what Doom modules are enabled and what order they load
;; in. Remember to run 'doom sync' after modifying it!

;; NOTE Press 'SPC h d h' (or 'C-h d h' for non-vim users) to access Doom's
;;      documentation. There you'll find a link to Doom's Module Index where all
;;      of our modules are listed, including what flags they support.

;; NOTE Move your cursor over a module's name (or its flags) and press 'K' (or
;;      'C-c c k' for non-vim users) to view its documentation. This works on
;;      flags as well (those symbols that start with a plus).
;;
;;      Alternatively, press 'gd' (or 'C-c c d') on a module to browse its
;;      directory (for easy access to its source code).

(doom! :input
       ;;bidi              ; (tfel ot) thgir etirw uoy gnipleh
       ;;chinese
       ;;japanese
       ;;layout            ; auie,ctsrnm is the superior home row

       :completion
       company           ; the ultimate code completion backend
       ;;(corfu +orderless)  ; complete with cap(f), cape and a flying feather!
       ;;helm              ; the *other* search engine for love and life
       ;;ido               ; the other *other* search engine...
       ;;ivy               ; a search engine for love and life
       vertico           ; the search engine of the future

       :ui
       ;;deft              ; notational velocity for Emacs
       doom              ; what makes DOOM look the way it does
       doom-dashboard    ; a nifty splash screen for Emacs
       ;;doom-quit         ; DOOM quit-message prompts when you quit Emacs
       ;;(emoji +unicode)  ; 🙂
       hl-todo           ; highlight TODO/FIXME/NOTE/DEPRECATED/HACK/REVIEW
       indent-guides     ; highlighted indent columns
       ligatures         ; ligatures and symbols to make your code pretty again
       ;;minimap           ; show a map of the code on the side
       modeline          ; snazzy, Atom-inspired modeline, plus API
       ;;nav-flash         ; blink cursor line after big motions
       ;;neotree           ; a project drawer, like NERDTree for vim
       ophints           ; highlight the region an operation acts on
       (popup +defaults)   ; tame sudden yet inevitable temporary windows
       ;;smooth-scroll     ; So smooth you won't believe it's not butter
       ;;tabs              ; a tab bar for Emacs
       ;;treemacs          ; a project drawer, like neotree but cooler
       unicode           ; extended unicode support for various languages
       (vc-gutter +pretty) ; vcs diff in the fringe
       vi-tilde-fringe   ; fringe tildes to mark beyond EOB
       window-select     ; visually switch windows
       workspaces        ; tab emulation, persistence & separate workspaces
       zen               ; distraction-free coding or writing

       :editor
       ;;(evil +everywhere); come to the dark side, we have cookies
       file-templates    ; auto-snippets for empty files
       fold              ; (nigh) universal code folding
       (format +onsave)  ; automated prettiness
       ;;god               ; run Emacs commands without modifier keys
       ;;lispy             ; vim for lisp, for people who don't like vim
       ;;multiple-cursors  ; editing in many places at once
       ;;objed             ; text object editing for the innocent
       parinfer          ; turn lisp into python, sort of
       ;;rotate-text       ; cycle region at point between text candidates
       snippets          ; my elves. They type so I don't have to
       (whitespace +guess +trim)  ; a butler for your whitespace
       word-wrap         ; soft wrapping with language-aware indent

       :emacs
       dired             ; making dired pretty [functional]
       electric          ; smarter, keyword-based electric-indent
       ;;eww               ; the internet is gross
       ;;ibuffer           ; interactive buffer management
       tramp             ; remote files at your arthritic fingertips
       undo              ; persistent, smarter undo for your inevitable mistakes
       vc                ; version-control and Emacs, sitting in a tree

       :term
       eshell            ; the elisp shell that works everywhere
       ;;shell             ; simple shell REPL for Emacs
       ;;term              ; basic terminal emulator for Emacs
       ;;vterm             ; the best terminal emulation in Emacs

       :checkers
       syntax              ; tasing you for every semicolon you forget
       ;;(spell +flyspell) ; tasing you for misspelling mispelling
       ;;grammar           ; tasing grammar mistake every you make

       :tools
       ;;ansible
       ;;biblio            ; Writes a PhD for you (citation needed)
       ;;collab            ; buffers with friends
       debugger          ; FIXME stepping through code, to help you add bugs
       ;;direnv
       ;;docker
       ;;editorconfig      ; let someone else argue about tabs vs spaces
       ;;ein               ; tame Jupyter notebooks with emacs
       (eval +overlay)     ; run code, run (also, repls)
       lookup              ; navigate your code and its documentation
       ;;llm               ; when I said you needed friends, I didn't mean...
       (lsp)      ; M-x vscode
       magit             ; a git porcelain for Emacs
       ;;make              ; run make tasks from Emacs
       ;;pass              ; password manager for nerds
       pdf               ; pdf enhancements
       ;;terraform         ; infrastructure as code
       tmux              ; an API for interacting with tmux
       tree-sitter       ; syntax and parsing, sitting in a tree...
       ;;upload            ; map local to remote projects via ssh/ftp

       :os
       (:if (featurep :system 'macos) macos)  ; improve compatibility with macOS
       ;;tty               ; improve the terminal Emacs experience

       :lang
       ;;ada               ; In strong typing we (blindly) trust
       ;;agda              ; types of types of types of types...
       ;;beancount         ; mind the GAAP
       (cc +lsp)         ; C > C++ == 1
       ;;clojure           ; java with a lisp
       common-lisp       ; if you've seen one lisp, you've seen them all
       ;;coq               ; proofs-as-programs
       ;;crystal           ; ruby at the speed of c
       ;;csharp            ; unity, .NET, and mono shenanigans
       ;;data              ; config/data formats
       ;;(dart +flutter)   ; paint ui and not much else
       ;;dhall
       ;;elixir            ; erlang done right
       ;;elm               ; care for a cup of TEA?
       emacs-lisp        ; drown in parentheses
       ;;erlang            ; an elegant language for a more civilized age
       ;;ess               ; emacs speaks statistics
       ;;factor
       ;;faust             ; dsp, but you get to keep your soul
       fortran           ; in FORTRAN, GOD is REAL (unless declared INTEGER)
       ;;fsharp            ; ML stands for Microsoft's Language
       ;;fstar             ; (dependent) types and (monadic) effects and Z3
       ;;gdscript          ; the language you waited for
       (go +lsp)         ; the hipster dialect
       ;;(graphql +lsp)    ; Give queries a REST
       (haskell +lsp)    ; a language that's lazier than I am
       ;;hy                ; readability of scheme w/ speed of python
       ;;idris             ; a language you can depend on
       json              ; At least it ain't XML
       ;;janet             ; Fun fact: Janet is me!
       (java +lsp)       ; the poster child for carpal tunnel syndrome
       ;;javascript        ; all(hope(abandon(ye(who(enter(here))))))
       julia             ; a better, faster MATLAB
       ;;kotlin            ; a better, slicker Java(Script)
       latex             ; writing papers in Emacs has never been so fun
       ;;lean              ; for folks with too much to prove
       ;;ledger            ; be audit you can be
       lua               ; one-based indices? one-based indices
       markdown          ; writing docs for people to ignore
       nim               ; python + lisp at the speed of c
       ;;nix               ; I hereby declare "nix geht mehr!"
       ;;ocaml             ; an objective camel
       org               ; organize your plain life in plain text
       ;;php               ; perl's insecure younger brother
       ;;plantuml          ; diagrams for confusing people more
       ;;graphviz          ; diagrams for confusing yourself even more
       ;;purescript        ; javascript, but functional
       ;;python            ; beautiful is better than ugly
       ;;qt                ; the 'cutest' gui framework ever
       ;;racket            ; a DSL for DSLs
       ;;raku              ; the artist formerly known as perl6
       ;;rest              ; Emacs as a REST client
       ;;rst               ; ReST in peace
       (ruby +rails)     ; 1.step {|i| p "Ruby is #{i.even? ? 'love' : 'life'}"}
       (rust +lsp)       ; Fe2O3.unwrap().unwrap().unwrap().unwrap()
       ;;scala             ; java, but good
       ;;(scheme +guile)   ; a fully conniving family of lisps
       sh                ; she sells {ba,z,fi}sh shells on the C xor
       ;;sml
       ;;solidity          ; do you need a blockchain? No.
       ;;swift             ; who asked for emoji variables?
       ;;terra             ; Earth and Moon in alignment for performance.
       ;;web               ; the tubes
       ;;yaml              ; JSON, but readable
       ;;zig               ; C, but simpler

       :email
       ;;(mu4e +org +gmail)
       ;;notmuch
       ;;(wanderlust +gmail)

       :app
       ;;calendar
       ;;emms
       ;;everywhere        ; *leave* Emacs!? You must be joking
       ;;irc               ; how neckbeards socialize
       ;;(rss +org)        ; emacs as an RSS reader

       :config
       ;;literate
       (default +bindings +smartparens))
```

---
### Moduli essenziali per Common Lisp

Se invece preferite una configurazione **minimale**, i moduli davvero indispensabili da “scommentare” (cioè rimuovere i `;;`) sono:
- `company` – completamento automatico
- `parinfer` – gestione intelligente delle parentesi Lisp
- `lsp` – supporto Language Server (non centrale per CL, ma utile)
- `common-lisp` – supporto al linguaggio
- `tree-sitter` – parsing e highlighting avanzato
Tutto il resto è **facoltativo** e dipende dalle vostre preferenze personali. In particolar modo ``evil``. Evil-mode implementa i keybind di Vim in Emacs. Vim ed Emacs sono editor modulari che hanno una grande quantita' di funzionalita' sia sul testo che al di fuori del testo in base a certe combinazioni di tasti o comandi. 

Se conoscete gia' i tasti di Neovim allora abilitate ``evil``, altrimenti usate quelli di Emacs, visto che io in questa serie di articoli faro' riferimento a quelli.
Emacs non e' un editor facile da usare, soprattutto se siete alle prime armi, per questo vi consiglio di leggere la guida integrata eseguendo il comando ``help-with-tutorial``. 

_Come si esegue un comando?_
Si entra nella **command mode** premendo quello che in notazione e' ``M-x``:
- M = Meta. Meta-key in Emacs e' il pulsante _Alt_
- x e' x...
poi basta scrivere il comando che serve per poterlo eseguire. Appare pure un menu sotto il cursore che ci aiuta a vedere tutti i comandi possibilmente inerenti mentre scriviamo.




---

---

👉 Questo articolo è pensato come **introduzione progressiva**: non serve sapere tutto subito. L’obiettivo è costruire, passo dopo passo, un ambiente di sviluppo solido e confortevole.

Nel prossimo articolo entreremo finalmente nel vivo del codice.