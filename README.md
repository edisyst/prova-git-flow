# Git Flow
```
git flow support start <version.x> <base>
git flow hotfix start <version.h> support/<version.x>
git flow hotfix finish <version.h>
git flow feature start <name> support/<version.x>
git flow feature finish <name>
git flow release start <version.r> support/<version.x>
git flow release finish <version.r>
```


### Feature
```
git flow init
git flow feature start prima_feature
```

Faccio le mie modifiche
```
git add .
git commit -m "Modifiche sulla Prima Feature"
git flow feature finish prima_feature
git log --graph --date=short 
```
// MAGARI POSSO CREARE UN ALIAS glog AL POSTO DI git log --graph --date=short




### Release
```
git flow release start 1.0
```

Faccio i test e gli eventuali fix
```
git add .
git commit -m "Fix sulla Prima Release"
git flow release finish 1.0
```
Mi obbliga a inserire un messaggio, potrebbe aprirmi l'editor di default (vim o Notepad++)



### Hotfix
```
git log --graph --date=short
git flow hotfix start 1.0.1
```

Faccio il fix
```
git add .
git commit -m "Primo Hotfix sulla Release 1.0"
git flow hotfix finish 1.0.1
```
Mi obbliga a inserire un messaggio, potrebbe aprirmi l'editor di default (vim o Notepad++)



# TAG
```
git branch
git tag
```
Posso creare un tag nuovo velocemente
```
git tag v1.2
git log
```

Modifico un file per esempio
```
git status
git add .
git commit -m "Modifica per il tag 1.2"
git log
```

```
git checkout -b branch-da-vecchio-tag 1.1
```

```
git push --tags
```
(altrimenti non pusha anche i tag)


https://git.logikum.hu/flow/support
Per il support serve un commit hash di partenza.
Supponiamo di essere alla stable 10.4 ma di voler fare un support per la 9.0
```
git flow support start support/9.0 12345
git branch support/6.0 12345 => in git normale sarebbe così
```



# stash
```
git stash
```
Saved working directory and index state WIP on master: ddaf625 Modifica per il tag 1.2 (ho il track per recuperare la modifica messa in stash)

```
git stash pop
```
Recupera l'ultima modifica che avevo messo su stash

```
git stash list // mi dà la lista
git stash pop stash@{0} // và ad uno stash preciso
git stash show stash@{0} -p // mi descrive il diff con lo stash
git stash drop stash@{0} // elimina quello stash
git stash push -m "stash con un messaggio"
```



# cherry-pick
Serve per copiare un commit di un branch in un altro branch (es. risolvo un bug su un branch e lo voglio portare su develop). Rompe la history però
```
git checkout -b feature-nuova
```
//Faccio le modifiche
```
git add .
git commit -m "commit su feature-nuova da cherripickare su develop"
git log
git checkout develop
git cherry-pick bf2cc9e
```
SE DA' CONFLITTO NON POSSO ABBANDONARE develop: DEVO CORREGGERE IL CONFLITTO E FARE: git add .
```
git commit -m "risolto conflittto col cherry-pick"
git log
```
Posso cherry-pickare anche diversi commit insieme
```
git cherry-pick bf2cc9e a657a1a 4ddb2b3
```



```
git config user.name "Gino"
```
Modifica localmente solo il file .git/config di questo progetto, non il parametro globale


```
git diff README.md
```
// ho già impostato perchè esca bellino installando Git Bash

















