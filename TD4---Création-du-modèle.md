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