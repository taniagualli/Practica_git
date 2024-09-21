# Practica_git

## 1. ¿Qué comando utilizaste en el paso 11? ¿Por qué?

Comando: git reset --hard HEAD~1
Porque este comando deshace el último commit y cualquier cambio en el working directory.

## 2. ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

Comando: git reflog y luego git reset --hard <commit-id>
Utilizamos reflog para encontrar el commit eliminado y luego lo restauramos con git reset.

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reflog
0030c7a (HEAD -> styled, main) HEAD@{0}: reset: moving to HEAD~1
d439df6 HEAD@{1}: commit: Aplicar estilo en markdown al poema
0030c7a (HEAD -> styled, main) HEAD@{2}: checkout: moving from main to styled
0030c7a (HEAD -> styled, main) HEAD@{3}: commit: Añadir el archivo git-nuestro.md
84d1fc4 (origin/main, origin/HEAD) HEAD@{4}: clone: from https://github.com/taniagualli/Practica_git.git
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reset --hard d439df6

## 3. El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

No causó ningún conflicto, porque el cambio del archivo git-nuestro.md está solo en la rama styled.

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git merge main
Already up to date.


## 4. El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

Si causó conflicto porque el archivo git-nuestro.md está en las dos ramas: styled y htmlify

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git merge htmlify
Auto-merging git-nuestro.md
CONFLICT (content): Merge conflict in git-nuestro.md
Automatic merge failed; fix conflicts and then commit the result.

Se resolvió:

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git branch
  htmlify
  main
* styled
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git add git-nuestro.md 
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git commit -m "Contenido de la rama “styled"
[styled e351e95] Contenido de la rama “styled
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git merge htmlify
Already up to date.

## 5. El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

No causó conflicto porque el archivo git-nuestro.md no estaba  en main como en el caso anterior.

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git merge styled
Updating 0030c7a..e351e95
Fast-forward
 git-nuestro.md | 32 ++++++++++++++++++++++----------
 1 file changed, 22 insertions(+), 10 deletions(-)


## 6. ¿Qué comando o comandos utilizaste en el paso 25?

Comando: git log --graph  --all

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git log --graph  --all
* commit e67fcc768707cb0f46d1a7a95f6d683c45004be2 (title)
| Author: Tania Gualli <31165833+taniagdn@users.noreply.github.com>
| Date:   Fri Sep 20 23:18:07 2024 -0500
| 
|     Añadir título al archivo
|   
*   commit e351e95cfa68576e5747d4370cfa7bb887053e0b (HEAD -> main, styled)
|\  Merge: d439df6 2975364
| | Author: Tania Gualli <31165833+taniagdn@users.noreply.github.com>
| | Date:   Fri Sep 20 23:06:28 2024 -0500
| | 
| |     Contenido de la rama “styled
| | 
| * commit 2975364dbcfbc8a7c377dfaf763c3b8b42acee2d (htmlify)
| | Author: Tania Gualli <31165833+taniagdn@users.noreply.github.com>
| | Date:   Fri Sep 20 22:55:24 2024 -0500
| | 
| |     Convertir git-nuestro.md a formato HTML
| | 
* | commit d439df607659e320d67fd1d5e92f777f86e3e981
|/  Author: Tania Gualli <31165833+taniagdn@users.noreply.github.com>
|   Date:   Fri Sep 20 22:44:25 2024 -0500
|   
|       Aplicar estilo en markdown al poema
| 
* commit 0030c7aedec12d549ce32c3ef0911d89b06cd302
| Author: Tania Gualli <31165833+taniagdn@users.noreply.github.com>
| Date:   Fri Sep 20 22:41:18 2024 -0500
| 
|     Añadir el archivo git-nuestro.md
| 
* commit 84d1fc4fed114e4c163d376e4c747e14092725d8 (origin/main, origin/HEAD)
  Author: taniagualli <tania.gualli@estrategos.mobi>
  Date:   Sun Sep 15 16:33:50 2024 -0500
  
      Initial commit


## 7. El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

Si, porque el archivo no estaba en main.

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git merge title
Updating e351e95..e67fcc7
Fast-forward
 git-nuestro.md | 1 +
 1 file changed, 1 insertion(+)

## 8. ¿Qué comando o comandos utilizaste en el paso 27?

Comando: git reset --merge

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reset --merge
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reflog
e67fcc7 (HEAD -> main, title) HEAD@{0}: reset: moving to HEAD
e67fcc7 (HEAD -> main, title) HEAD@{1}: merge title: Fast-forward
e351e95 (styled) HEAD@{2}: checkout: moving from main to main
e351e95 (styled) HEAD@{3}: checkout: moving from title to main
e67fcc7 (HEAD -> main, title) HEAD@{4}: commit: Añadir título al archivo
e351e95 (styled) HEAD@{5}: checkout: moving from main to title
e351e95 (styled) HEAD@{6}: merge styled: Fast-forward
0030c7a HEAD@{7}: checkout: moving from styled to main
e351e95 (styled) HEAD@{8}: commit (merge): Contenido de la rama “styled
d439df6 HEAD@{9}: checkout: moving from htmlify to styled
2975364 (htmlify) HEAD@{10}: commit: Convertir git-nuestro.md a formato HTML
0030c7a HEAD@{11}: checkout: moving from main to htmlify
0030c7a HEAD@{12}: checkout: moving from styled to main
d439df6 HEAD@{13}: reset: moving to d439df6
0030c7a HEAD@{14}: reset: moving to HEAD~1
d439df6 HEAD@{15}: commit: Aplicar estilo en markdown al poema
0030c7a HEAD@{16}: checkout: moving from main to styled
0030c7a HEAD@{17}: commit: Añadir el archivo git-nuestro.md
84d1fc4 (origin/main, origin/HEAD) HEAD@{18}: clone: from https://github.com/taniagualli/Practica_git.git

## 9. ¿Qué comando o comandos utilizaste en el paso 28?

Comando: git checkout -- git-nuestro.md

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git checkout -- git-nuestro.md
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reflog
e67fcc7 (HEAD -> main, title) HEAD@{0}: reset: moving to HEAD
e67fcc7 (HEAD -> main, title) HEAD@{1}: merge title: Fast-forward
e351e95 (styled) HEAD@{2}: checkout: moving from main to main
e351e95 (styled) HEAD@{3}: checkout: moving from title to main
e67fcc7 (HEAD -> main, title) HEAD@{4}: commit: Añadir título al archivo
e351e95 (styled) HEAD@{5}: checkout: moving from main to title
e351e95 (styled) HEAD@{6}: merge styled: Fast-forward
0030c7a HEAD@{7}: checkout: moving from styled to main
e351e95 (styled) HEAD@{8}: commit (merge): Contenido de la rama “styled
d439df6 HEAD@{9}: checkout: moving from htmlify to styled
2975364 (htmlify) HEAD@{10}: commit: Convertir git-nuestro.md a formato HTML
0030c7a HEAD@{11}: checkout: moving from main to htmlify
0030c7a HEAD@{12}: checkout: moving from styled to main
d439df6 HEAD@{13}: reset: moving to d439df6
0030c7a HEAD@{14}: reset: moving to HEAD~1
d439df6 HEAD@{15}: commit: Aplicar estilo en markdown al poema
0030c7a HEAD@{16}: checkout: moving from main to styled
0030c7a HEAD@{17}: commit: Añadir el archivo git-nuestro.md
84d1fc4 (origin/main, origin/HEAD) HEAD@{18}: clone: from https://github.com/taniagualli/Practica_git.git


## 10. ¿Qué comando o comandos utilizaste en el paso 29?

Comando: git branch -D title

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git branch -D title
Deleted branch title (was e67fcc7).


## 11. ¿Qué comando o comandos utilizaste en el paso 30?

Comando: git merge title

## 12. ¿Qué comando o comandos usaste en el paso 32?

Comandos: 
git reflog
git checkout 0030c7a

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reflog
e67fcc7 (HEAD -> main) HEAD@{0}: checkout: moving from main to main
e67fcc7 (HEAD -> main) HEAD@{1}: reset: moving to HEAD
e67fcc7 (HEAD -> main) HEAD@{2}: merge title: Fast-forward
e351e95 HEAD@{3}: checkout: moving from main to main
e351e95 HEAD@{4}: checkout: moving from title to main
e67fcc7 (HEAD -> main) HEAD@{5}: commit: Añadir título al archivo
e351e95 HEAD@{6}: checkout: moving from main to title
e351e95 HEAD@{7}: merge styled: Fast-forward
0030c7a HEAD@{8}: checkout: moving from styled to main
e351e95 HEAD@{9}: commit (merge): Contenido de la rama “styled
d439df6 HEAD@{10}: checkout: moving from htmlify to styled
2975364 HEAD@{11}: commit: Convertir git-nuestro.md a formato HTML
0030c7a HEAD@{12}: checkout: moving from main to htmlify
0030c7a HEAD@{13}: checkout: moving from styled to main
d439df6 HEAD@{14}: reset: moving to d439df6
0030c7a HEAD@{15}: reset: moving to HEAD~1
d439df6 HEAD@{16}: commit: Aplicar estilo en markdown al poema
0030c7a HEAD@{17}: checkout: moving from main to styled
0030c7a HEAD@{18}: commit: Añadir el archivo git-nuestro.md
84d1fc4 (origin/main, origin/HEAD) HEAD@{19}: clone: from https://github.com/taniagualli/Practica_git.git
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git checkout 0030c7a
Note: switching to '0030c7a'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 0030c7a Añadir el archivo git-nuestro.md


## 13. ¿Qué comando o comandos usaste en el punto 33?

Comando:
git reflog
git checkout e67fcc7

(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git reflog
0030c7a (HEAD) HEAD@{0}: checkout: moving from main to 0030c7a
e67fcc7 (main) HEAD@{1}: checkout: moving from main to main
e67fcc7 (main) HEAD@{2}: reset: moving to HEAD
e67fcc7 (main) HEAD@{3}: merge title: Fast-forward
e351e95 HEAD@{4}: checkout: moving from main to main
e351e95 HEAD@{5}: checkout: moving from title to main
e67fcc7 (main) HEAD@{6}: commit: Añadir título al archivo
e351e95 HEAD@{7}: checkout: moving from main to title
e351e95 HEAD@{8}: merge styled: Fast-forward
0030c7a (HEAD) HEAD@{9}: checkout: moving from styled to main
e351e95 HEAD@{10}: commit (merge): Contenido de la rama “styled
d439df6 HEAD@{11}: checkout: moving from htmlify to styled
2975364 HEAD@{12}: commit: Convertir git-nuestro.md a formato HTML
0030c7a (HEAD) HEAD@{13}: checkout: moving from main to htmlify
0030c7a (HEAD) HEAD@{14}: checkout: moving from styled to main
d439df6 HEAD@{15}: reset: moving to d439df6
0030c7a (HEAD) HEAD@{16}: reset: moving to HEAD~1
d439df6 HEAD@{17}: commit: Aplicar estilo en markdown al poema
0030c7a (HEAD) HEAD@{18}: checkout: moving from main to styled
0030c7a (HEAD) HEAD@{19}: commit: Añadir el archivo git-nuestro.md
84d1fc4 (origin/main, origin/HEAD) HEAD@{20}: clone: from https://github.com/taniagualli/Practica_git.git
(base) MacBook-Pro-de-TaniaG:Practica_git taniagualli$ git checkout e67fcc7
Previous HEAD position was 0030c7a Añadir el archivo git-nuestro.md
HEAD is now at e67fcc7 Añadir título al archivo
