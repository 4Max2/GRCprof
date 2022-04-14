L'objectif de ce TD est de créer le modèle, c'est àd ire la abse de données de notre projet.
Dans le langage symfony, une entity est une table.
Vous retrouverez le modèle dans le power point page
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

# création d'un controller

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