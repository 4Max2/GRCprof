# Mise en place de la base de données

en ligne de commande : mysql -p puis entrer le mot de passe root. Vous entrer dans le terminal Maria DB Entrer la commande suivante en modifiant les éléments suivants

GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY ‘123’; flush privileges ;
Le 123 représnete le mot de passe.

# Création du projet symfony

symfony new nom_projet --full.
Vous devez modifier le nom_projet

# Lien avec la BD

Modification du fichier .env (à la racine) :

DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name"
Vous devez modifier le db_user, db_password et le db_name

symfony console doctrine:database:create

# Démarrer le serveur
symfony serve -d

# Test démarrage du serveur

Dans le navigateur de votre choix, taper dans la barre d'adresse 

@IP:n° de port fourni par symfony

