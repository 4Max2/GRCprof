L'objectif de ce TD est de créer le modèle, c'est à dire la base de données de notre projet.
Dans le langage symfony, une entity est une table.
Il est recommandé de lire en entier cette page avant de démarrer.
On rappelle que 
  
 1. les commandes doivent être tapées à la racine du projet.
 2. lors de la création d'une table, l'id (clé primaire est automatiquement créée)
 3. support officiel, à partir de la partie Creating an Entity Class : [ici](https://symfony.com/doc/current/doctrine.html#creating-an-entity-class)

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
3. Créer la table Projet
4. Créer la table EtatNote
5. créer la table Note

# Résultat souhaité avec le concepteur PhpMyAdmin
ce résultat est juste un visuel. En aucun cas, il faut utiliser PhpMyAdmin pour la cocneption. uniquement pour la visualisation. La conception se fait en ligne de commande via la commande **symfony console make:entity**.

![](http://51.222.75.212/ressources/phpR209.png)

Si vous avez terminé, vous pouvez commencer à créer des formulaires et modifier des données.

# Création d'un controller

Pour chaque entity (table) créée, il faut créer un controller.
La syntaxe d'un controller est Première lettre en majuscule suivi du mot Controller : exemple AdminController ou SecurityController

Afin de créer un controller, il faut se placer à la racine du projet et taper la commande : **symfony console make:controller**

Cette action va créer 
1. un fichier dans /src/controller (ce qui est le back)
1. un répertoire (qui porte le nom du controller) et un fichier index.html.twig à l’intérieur du répertoire /templates (ce qui est le front)

# Récupération de données de formulaires

## Dans le formulaire
Le formulaire, fichier *.html.twig dans répertoire template, doit être compris entre les lignes 
* `<form action="/connexion" method="POST">`
* `</form>`

les input type text doivent comporter des name=""

* `<input type="email" name="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">`
* `<input type="password" name="pwd"class="form-control" id="exampleInputPassword1" placeholder="Password">`

## Dans le controller (back-end)

En haut de la page de votre controller, il faut inclure les éléments suivants :
1. use Symfony\Component\HttpFoundation\Session\Session;
1. use Symfony\Component\HttpFoundation\Request;

Dans la fonction

`> public function connexion(Request $request, ManagerRegistry $doctrine): Response`
`>     {`

`> 		//Récupération variables de formulaire`

`> 		$email = $request->request->get('email');`

`> 		$pwd = $request->request->get('pwd');`
`> }`
