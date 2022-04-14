Une entity est une table.
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