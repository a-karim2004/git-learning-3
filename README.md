# 🧠 Git Learning – Exercices 1, 2 et 3

Ce dépôt contient un ensemble d’exercices pratiques pour apprendre à manipuler Git et GitHub exclusivement depuis le terminal.

---

## 🚀 Exercice 1 – First Repo & Simple Commit

**Objectifs :**
- Créer un dépôt GitHub et le cloner localement.
- Créer un fichier, le modifier et suivre l’historique avec des commits.

**Étapes principales :**
```bash
# Créer le dépôt sur GitHub (git-learning-1)
git clone https://github.com/a-karim2004/git-learning-1.git
cd git-learning-1

# Créer un fichier README.md
echo "Mon premier projet Git" > README.md

# Ajouter et committer
git add README.md
git commit -m "Ajout du fichier README.md avec un premier texte"
git push origin main

# Modifier le fichier
echo "Nom : Karim - Mac N° 12" >> README.md

# Commit et push final
git add README.md
git commit -m "Ajout de mon nom et numéro de Mac dans le README"
git push origin main



Exercice 2 – Branching & Merging

Objectifs :

Créer et gérer des branches.

Utiliser GitHub CLI pour créer un repo, pousser une branche et effectuer un merge via Pull Request.





# Créer le dépôt depuis le terminal
gh repo create git-learning-2 --public --clone
cd git-learning-2

# Créer et basculer sur la branche myself
git checkout -b myself

# Créer un fichier about.txt

# Commit et push
git add about.txt
git commit -m "Ajout de about.txt avec mes informations"
git push origin myself

# Créer la branche main et la relier
git checkout --orphan main
echo "# git-learning-2" > README.md
git add README.md
git commit -m "Initial commit avec README"
git push origin main
git checkout myself
git rebase main
git push origin myself --force

# Créer et merger la Pull Request
gh pr create --base main --head myself --title "Ajout de about.txt" --body "Création du fichier about.txt avec mes infos personnelles"
gh pr merge --merge



Exercice 3 – Gestion des Conflits

Objectifs :

Comprendre et résoudre un conflit de fusion manuellement.




# Créer le dépôt
gh repo create git-learning-3 --public --clone
cd git-learning-3

# Sur la branche main
echo "Ligne écrite depuis la branche main" > notes.txt
git add notes.txt
git commit -m "Ajout de notes.txt depuis la branche main"
git branch -M main
git push origin main

# Créer et basculer sur conflict-test
git checkout -b conflict-test
echo "Ligne écrite depuis la branche conflict-test" > notes.txt
git add notes.txt
git commit -m "Modification de notes.txt depuis la branche conflict-test"
git push origin conflict-test

# Retour sur main
git checkout main
echo "Ligne écrite depuis la branche main pour la seconde fois" > notes.txt
git add notes.txt
git commit -m "Seconde modification de notes.txt sur la branche main"
git push origin main

# Essayer de merger -> Conflit attendu
git merge conflict-test
# Résolution manuelle dans notes.txt
# Garder les deux lignes, supprimer les marqueurs <<<<<<<, =======, >>>>>>>
git add notes.txt
git commit -m "Résolution du conflit entre main et conflict-test"
git push origin main

**EN RESUMÉ**

# 1️ Le Branching (Création de branches)

Définition :
Le branching consiste à créer une branche parallèle dans ton projet.
C’est comme une copie indépendante de ton code actuel sur laquelle tu peux travailler sans impacter la version principale (main).


# 2 Le Merging (Fusion des branches)

 Définition :
Le merging permet de fusionner le travail effectué sur une branche (ex: my-feature) dans une autre ex(main)


# 3 La Gestion des Conflits (Conflict Resolution)

Définition :
Un conflit arrive quand deux branches modifient la même partie d’un fichier différemment.
Git ne sait pas laquelle des deux versions garder.
