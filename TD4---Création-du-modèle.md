L'objectif de ce TD est de créer le modèle, c'est à dire la base de données de notre projet.
Dans le langage symfony, une entity est une table.
Il est recommandé de lire en entier cette page avant de démarrer.
Voici le modèle à créer :

![r209](http://51.222.75.212/ressources/modeleR209.png)
# Création d'une entité et identification des champs et des types
Commande pour créer une entity : symfony console make:entity

Ensuite rentrer le nom de la table (sans espace avec une majuscule au début).

Puis rentrer le nom des property (champs) et répondez aux questions de types, de longueur éventuelle et de null.

Une fois que tous les champs sont nommés, appuyer sur entrée.
Le mot Success apparait.

# Migration vers la base de données

Pour appliquer ces modifications tapez les commandes suivantes 
* symfony console make:migration
* symfony console doctrine:migrations:migrate

# Point de vigilance
Dans les tables suivantes vous devrez créer des relations.
* Table Note : deux relations une vers la table Projet et une vers la table EtatNote
* table Projet : deux relations une vers etatProjet et une vers user

Lorsque vous avez entré le nom de votre propriété (clé étrangère), vous allez être invité à entrer le Type Field. Par défaut le choix est à string, il faut écrire relation. Puis écrire le nom de la class (Entity) à laquelle le champ sera relié.

Pour ces relations le format est **ManytoOne**

# Ordre de création des tables
Vous devez créer les entity dans l'ordre suivant. Lors de l'authentification la table user a été créée.
1. Terminer la table User
2. Créer la table EtatProjet
3. créer la table Projet
4. Créer la table EtatNote
5. créer la table Note
