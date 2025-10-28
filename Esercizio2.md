# Esercizio di risoluzione di un merge conflict

**Il tempo massimo in laboratorio per questo esercizio è di _20 minuti_.
Se superato, sospendere l'esercizio e riprenderlo per ultimo!**

Si visiti https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.
Questo repository contiene due branch: `master` e `feature`

Per ognuna delle seguenti istruzioni, si annoti l'output ottenuto.
Prima di eseguire ogni operazione sul worktree o sul repository,
si verifichi lo stato del repository con `git status`.

1. Si cloni localmente il repository
git clone https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git
Cloning into 'OOP-git-merge-conflict-test'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 12 (delta 1), reused 1 (delta 1), pack-reused 8 (from 1)
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (2/2), done.

git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

3. Ci si assicuri di avere localmente entrambi i branch remoti
>git log --oneline --graph --all
* bed943f (origin/feature) Print author information
| * 8e0f29c (HEAD -> master, origin/master, origin/HEAD) Change HelloWorld to print the number of available processors
|/
* d956df6 Create .gitignore
* 700ee0b Create HelloWorld

4. Si faccia il merge di `feature` dentro `master`, ossia: si posizioni la `HEAD` su `master`
   e da qui si esegua il merge di `feature`
   git merge origin/feature
Auto-merging HelloWorld.java
CONFLICT (content): Merge conflict in HelloWorld.java
Automatic merge failed; fix conflicts and then commit the result.

6. Si noti che viene generato un **merge conflict**!
git status
On branch master
Your branch is up to date with 'origin/master'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   HelloWorld.java

no changes added to commit (use "git add" and/or "git commit -a")

7. Si risolva il merge conflict come segue:
   - Il programma Java risultante deve stampare sia il numero di processori disponibili
     (funzionalità presente su `master`)
     che il nome dell'autore del file
     (funzionalità presente su `feature`)

     git commit
U       HelloWorld.java
error: Committing is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.

C:\Users\jacop\Documents\università\PSS\pss-lab04\OOP-git-merge-conflict-test>git add HelloWorld.java

C:\Users\jacop\Documents\università\PSS\pss-lab04\OOP-git-merge-conflict-test>git commit
[master ba92647] Merge remote-tracking branch 'origin/feature'

C:\Users\jacop\Documents\università\PSS\pss-lab04\OOP-git-merge-conflict-test>git log --oneline --graph --all
*   ba92647 (HEAD -> master) Merge remote-tracking branch 'origin/feature'
|\
| * bed943f (origin/feature) Print author information
* | 8e0f29c (origin/master, origin/HEAD) Change HelloWorld to print the number of available processors
|/
* d956df6 Create .gitignore
* 700ee0b Create HelloWorld

8. Si crei un nuovo repository nel proprio github personale

9. Si aggiunga il nuovo repository creato come **remote** e si elenchino i remote
   git remote add remote https://github.com/JacopoFoschi2/2025-10-28-PSS.git

C:\Users\jacop\Documents\università\PSS\pss-lab04\OOP-git-merge-conflict-test>git remote -v
origin  https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git (fetch)
origin  https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git (push)
remote  https://github.com/JacopoFoschi2/2025-10-28-PSS.git (fetch)
remote  https://github.com/JacopoFoschi2/2025-10-28-PSS.git (push)

10. Si faccia push del branch `master` sul proprio repository
git push remote
Enumerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 4 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (15/15), 1.57 KiB | 537.00 KiB/s, done.
Total 15 (delta 4), reused 10 (delta 2), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (4/4), done.
To https://github.com/JacopoFoschi2/2025-10-28-PSS.git
 * [new branch]      master -> master

11. Si setti il branch remoto `master` del nuovo repository come *upstream* per il proprio branch `master` locale
git checkout -b remote/master
Switched to a new branch 'remote/master'

git status
On branch remote/master
nothing to commit, working tree clean
