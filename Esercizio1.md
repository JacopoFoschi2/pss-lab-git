# Esercizio con Git, in locale

Per ogni passo,
si annoti in questo file il comando utilizzato ed il suo output,
per confrontarlo con le soluzioni.

### Si crei una nuova directory
mkdir esercizio1
cd esercizio1

### Si inizializzi un repository Git dentro la cartella suddetta.
git init
Initialized empty Git repository in C:/Users/jacop/Documents/università/PSS/pss-lab04/pss-lab-git/esercizio1/.git/

### Si osservi lo stato del repository
git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

### Si scriva un file `HelloWorld.java` contenente un `main` con una stampa a video e si osservi il contenuto del repository
dir
 Il volume nell'unità C non ha etichetta.
 Numero di serie del volume: EC72-7B58

 Directory di C:\Users\jacop\Documenti\università\PSS\pss-lab04\pss-lab-git\esercizio1

28/10/2025  09:39    <DIR>          .
28/10/2025  09:39    <DIR>          ..
28/10/2025  09:40                55 HelloWorld.java
               1 File             55 byte
               2 Directory  19,259,068,416 byte disponibili

### Si aggiunga `HelloWorld.java` allo stage, e si osservi lo stato del repository
git add HelloWorld.java
warning: in the working copy of 'HelloWorld.java', LF will be replaced by CRLF the next time Git touches it

### Si crei il primo commit, con messaggio ragionevole. Se necessario, si configuri nome utente ed email di git usando i dati dell'account istituzionale.
git commit -m "added class HelloWorld.java"
[master (root-commit) 8a0b707] added class HelloWorld.java
 1 file changed, 3 insertions(+)
 create mode 100644 HelloWorld.java

### Si compili il file Java e si verifichi lo stato del repository


### Si noti che c'è un file rigenerabile (`HelloWorld.class`). Si costruisca una lista di file ignorati che ignori tutti i file con estensione `.class`

### Si osservi lo stato del repository
git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   HelloWorld.java

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

### Si crei un nuovo commit che tracci il la ignore list, aggiungendo allo stage i file necessari. Si osservi sempre lo stato del repository dopo l'esecuzione di un comando
git commit -m "added .gitignore file to ignore binaries"
[master 195c621] added .gitignore file to ignore binaries
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore

git status
On branch master
nothing to commit, working tree clean

### Si gestiscano i caratteri di fine linea in modo appropriato, creando un file `.gitattributes`
git commit -m "added .gitattributes file to handle EOL conflicts"
[master 5785f19] added .gitattributes file to handle EOL conflicts
 1 file changed, 8 insertions(+)
 create mode 100644 .gitattributes
 
### Si osservi la storia del repository usando `git log --all --graph`
git log --all --graph
* commit 5785f193f13c9ba81df73f7526a7e6187f09a37b (HEAD -> master)
| Author: Jacopo Foschi <jacopo.foschi2@studio.unibo.it>
| Date:   Tue Oct 28 10:02:32 2025 +0100
|
|     added .gitattributes file to handle EOL conflicts
|
* commit 195c621f1c623a6c58ee263413795a58332ee170
| Author: Jacopo Foschi <jacopo.foschi2@studio.unibo.it>
| Date:   Tue Oct 28 09:56:25 2025 +0100
|
|     added .gitignore file to ignore binaries
|
* commit 7585eb048f13426a8e16545f188423792367192c
| Author: Jacopo Foschi <jacopo.foschi2@studio.unibo.it>
| Date:   Tue Oct 28 09:55:12 2025 +0100
|
|     fixed missing semicolon
|
* commit 8a0b707c1832ac77fbd3e89417521f5b6afddd47
  Author: Jacopo Foschi <jacopo.foschi2@studio.unibo.it>
  Date:   Tue Oct 28 09:47:21 2025 +0100

      added class HelloWorld.java

### Da questo punto in poi, prima e dopo ogni comando, ci si assicuri di osservare lo stato del repository con `git status`

### Si crei un file Mistake.java, con contenuto arbitrario, lo si aggiunga al tracker, e si faccia un commit
git commit -m "added class Mistake.java"
[master 63a51e1] added class Mistake.java
 1 file changed, 3 insertions(+)
 create mode 100644 Mistake.java

 git status
On branch master
nothing to commit, working tree clean

### Si rinomini `Mistake.java` in `ToDelete.java`, e si faccia un commit che registra la modifica
git commit -m "renamed Mistake.java to ToDelete.java"
[master 2a6f946] renamed Mistake.java to ToDelete.java
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename Mistake.java => ToDelete.java (100%)

C:\Users\jacop\Documents\università\PSS\pss-lab04\esercizio1>git status
On branch master
nothing to commit, working tree clean

### Si elimini `ToDelete.java` e si registri la modifica in un commit
>git add ToDelete.java

C:\Users\jacop\Documents\università\PSS\pss-lab04\esercizio1>git commit -m "deleted class ToDelete.java"
[master b8852e8] deleted class ToDelete.java
 1 file changed, 3 deletions(-)
 delete mode 100644 ToDelete.java

C:\Users\jacop\Documents\università\PSS\pss-lab04\esercizio1>git status
On branch master
nothing to commit, working tree clean

### Si osservi la storia del repository e si identifichi il commit dove è stato creato `Mistake.java`. Per una visione compatta, si usi l'opzione `--oneline`
>git log --oneline
b8852e8 (HEAD -> master) deleted class ToDelete.java
2a6f946 renamed Mistake.java to ToDelete.java
63a51e1 added class Mistake.java
5785f19 added .gitattributes file to handle EOL conflicts
195c621 added .gitignore file to ignore binaries
7585eb0 fixed missing semicolon
8a0b707 added class HelloWorld.java

### Si ripristini Mistake.java dal commit identificato al passo precedente

### Si rimuova il file ripristinato e si ripulisca lo stage

### Si torni al commit precedente a quello in cui `Mistake.java` è stato creato. Si utilizzi la storia del repository se utile.
git checkout 63a51e1
Note: switching to '63a51e1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 63a51e1 added class Mistake.java

### Si crei un nuovo branch di nome `experiment` e si agganci la `HEAD` al nuovo branch
git checkout -b experiment
Switched to a new branch 'experiment'

### Si crei un file README.md con contenuto a piacere, e si faccia un commit che lo includa
git commit -m "added README.md file"
[experiment 030376b] added README.md file
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

### Si torni sul branch master e si elenchino i branch disponibili
git log --graph --all --oneline
* 030376b (experiment) added README.md file
| * b8852e8 (HEAD -> master) deleted class ToDelete.java
| * 2a6f946 renamed Mistake.java to ToDelete.java
|/
* 63a51e1 added class Mistake.java
* 5785f19 added .gitattributes file to handle EOL conflicts
* 195c621 added .gitignore file to ignore binaries
* 7585eb0 fixed missing semicolon
* 8a0b707 added class HelloWorld.java

### Si unisca il branch experiment al branch master (si faccia un merge in cui experiment viene messo dentro master, e non viceversa)
git merge experiment
Merge made by the 'ort' strategy.
 README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

### Si osservi la storia del repository
git log --graph --all --oneline
*   0970980 (HEAD -> master) Merge branch 'experiment'
|\
| * 030376b (experiment) added README.md file
* | b8852e8 deleted class ToDelete.java
* | 2a6f946 renamed Mistake.java to ToDelete.java
|/
* 63a51e1 added class Mistake.java
* 5785f19 added .gitattributes file to handle EOL conflicts
* 195c621 added .gitignore file to ignore binaries
* 7585eb0 fixed missing semicolon
* 8a0b707 added class HelloWorld.java
