#Marche à suivre - Utilisation de l'API Google AdWords

####Rédigée le 8 Juin 2016

###Préalable

Avant de pouvoir continuer, il faut posséder un AdWords Manager Account.

Si ce n'est pas le cas, suivre ce lien : https://www.google.com/adwords/manager-accounts/

###Manager Test Account

Ensuite, il vous faut créer un compte maître de test (https://adwords.google.com/um/Welcome/Home?sf=mt#ta).

Une fois le compte créer, et la connexion effectuée à ce dernier, vous devez voir un bandeau rouge en haut à gauche indiquant que ce compte est bel et bien un compte de test.

Sur la page d'accueil du compte, cliquez sur le bouton rouge pour ajouter un compte (qui sera un compte fils du Manager Test Account). Pour les besoins futurs du test, vous pouvez aussi lui ajouter une ou deux campagnes.

###Google API Console

Pour continuer, il va falloir se connecter à la google API Console et créer un nouveau projet. Donnez lui un nom et un type (à reglé sur "Autre").

Ensuite, rendez vous sur la configuration du projet et cliquez sur le bouton "Créer des identifiants" et sélectionnez "ID Client OAuth". Choisir "Autre" pour le type de l'application et "Créer".

Le gestionnaire fait sortir deux codes qu'il faudra conserver par la suite.

###API et librairies

Une des dernières étapes consiste à choisir une librairie pour le développement (PHP sera traité ici).

Se rendre sur le Github de la librairie afin de la télécharger (https://github.com/googleads/googleads-php-lib).

Une fois le projet téléchargé, partez à la recherche du fichier **auth.ini** et renseigner les valeurs.

- developerToken = Jeton de développement accessbile par l'engrenage en haut à gauche du compte MCC de production.
- userAgent = Nom de l'application
- clientCustomerId = ID client présent en dessous du nom de compte dans Manager Account, celui du compte à observer.
- client_id = Code obtenu après la création du projet dans Google API Console
- client_secret = Code obtenu après la création du projet dans Google API Console
- refresh_token = Détails ci-dessous

###Obtention du refresh_token

Le refresh token est obtenu après exécution d'un script présent dans la librairie PHP. Il suffit de se rendre dans le dossier suivant : examples\AdWords\Auth et de lancer le script GetRefreshToken.php par la ligne de commande (il faut au préalable avoir renseigné toutes les informations dans le **auth.ini**).

La commande, une fois lancée, doit faire ressortir une URL qui demande validation dans le navigateur. Si tout se passe pour le mieux, un code est prompt par le navigateur, code qu'il faut alors rentrer dans la console afin de valider la request. La ligne de commande fait alors ressortir le refresh token, qu'il faut entrer dans le **auth.ini**.

###Test de l'API

Une fois les étapes précédentes effectuées, il ne reste plus qu'à tester la connexion à l'API. Pour se faire, il suffit d'ouvrir une fenêtre de commande et de naviguer vers le répertoire suivant : examples\AdWords\v201605\BasicOperations

Exécuter le script GetCampaigns.php et observer le résultat. Il doit normalement prompt la liste des campagnes présentes sur le compte de test ou alors qu'aucune campagne est présente.

Tout autre résultat est assimilé à une erreur, dont la signification peut être trouvée ici : https://developers.google.com/adwords/api/docs/common-errors

####Bon courage !
