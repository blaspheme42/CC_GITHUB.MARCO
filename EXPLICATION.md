# Explication

## Objectif

On viens expliquer ici les étapes du CC Git

## Contexte

- **Projet / sujet : Musée des inventions absurdes
- **Environnement : Git
- **Date des tests : 14/10
- **Testeur :*MARCO BENJAMIN


 67aeb4f (HEAD -> main, tag: depart-cc) Fournir le site fonctionnel des ateliers
 id original de commit

## Tableau de suivi des tests

| Étape/version testée | Action                                                                                                                                                                                      | Résultat attendu                                                                              | Résultat constaté     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------- |
| Étape 1.1            | Création de branche pour la modification de style de la page<br>859044d (feature/cssv2)                                                                                                     | LE style de la page est modifé et correspond bien à l'attente du sujet                        | OK                    |
| Étape 1.2            | Création de branche pour la modification du app.js qui permet d'afficher la confirmation de reservation<br>4dc6678 (feature/appjsv2)                                                        | Le site fait bien apparaitre la confirmation lors du clique                                   | OK                    |
| Étape 2              | Merge des branches sur le main                                                                                                                                                              | les modifications sont bien effectives sur le main, aucun bug detecté                         | KO ( voir étapes 2.1) |
| Étape 2.1            | L'affichage de la confirmation de reservation n'apparait pas, création d'un hotfix pour regler le problème (modification du style.css pour changer la font-color)<br>aa7af80 (hotfix/appjs) | La confirmation de reservation apparait correctement, et aucun nouveau probleme n'est visible | OK                    |
| Étape 3              | création d'une branche feature/atelier, modification de app.js pour afficher l'atelier à coté de la confirmation de reservation<br>8b8084d (HEAD -> main, feature/atelier)                  | L'affichage de l'atelier fonctionne                                                           | OK                    |
TEST DE MAIN : 
1. Ouverture ou actualisation : compteur à zéro, confirmation masquée.  OK
2. Première réservation : compteur à un, confirmation lisible avec le nom de l'atelier et une place. OK
3. Trois réservations au total : compteur et confirmation indiquent trois places. OK
4. Recommencer : compteur à zéro, confirmation masquée. OK 
5. Nouvelle réservation après remise à zéro : compteur à un et confirmation de nouveau visible. OK
6. Affichage à 390 px : textes et boutons lisibles, aucun défilement horizontal. OK


Obtenu avec : git log --all --graph --oneline
* 8b8084d (HEAD -> main, feature/atelier) permet l'affichage de l'atelier
* aa7af80 (hotfix/appjs) Correction color-font de la confirmation appjs
*   354925c Merge branch 'feature/cssv2'
|\  
| * 859044d (feature/cssv2) Modif. couleurs background et font
* | 4dc6678 (feature/appjsv2) Affichage de la confirmation
|/  
* 67aeb4f (tag: depart-cc) Fournir le site fonctionnel des ateliers

## QUESTION PERSONNEL

**Base et branches :** quel commit est le point de départ commun de A et B ?

67aeb4f est l'id duquel sont partis les branches A et B

Indiquez aussi les commits de main depuis lesquels hotfix et la quatrième branche ont été créées.
le hotfix viens de  354925c et la quatrième branche viens de aa7af80



**Fusion et fonctionnement :** pourquoi une fusion Git réussie ne garantit-elle pas que le site fonctionne correctement ?

Une fusion réussi signifie que le merge des projet c'est bien passé, cependant, cela ne signifie pas qu'il n'y a pas de problème, comme vu dans le CC, sans vérification humaine, on ne peux pas voir un problème de couleur qui se superpose.


**Commit et publication :** après un commit local, qu'est-ce qui reste à faire pour que ce changement soit visible sur GitHub ?

Un commit prépare la modification à l'envoi, l'envoi n'est déclenché que par la commande git push (avec des attribut si c'est la première fois)
Par exemple, pour ce projet, je vais : 

git remote add origin https://github.com/blaspheme42/CC_GITHUB.MARCO.git
git remote -v (verification)
git push -u origin main
git push -u origin feature/appjsv2
git push -u origin feature/cssv2
git push -u origin feature/atelier
git push -u origin hotfix/appjs


sur github, sur le dépot, sous le bouton <>code, on trouve le bouton commit, qui nous liste tout les commit, comme le 8b8084d, affiché : 1 parent [aa7af80](https://github.com/blaspheme42/CC_GITHUB.MARCO/commit/aa7af80151c871b2a62b4661ccd83ce52e164063) commit 8b8084d


