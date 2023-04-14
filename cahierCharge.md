Cahier des charges configurateur en ligne:

1.  Objectifs

*   Développer un configurateur de PC en ligne qui permet aux clients de choisir les composants de leur ordinateur sur mesure.
*   Assurer que chaque composant sélectionné par le client est compatible avec les autres composants du PC.



2.  Fonctionnalités

*   Un formulaire de configuration où les clients peuvent choisir les composants de leur PC, tels que le processeur, la carte graphique, la carte mère, la mémoire vive, le disque dur, l'alimentation, etc.
*   Un système de vérification de compatibilité pour éviter que les clients choisissent des composants incompatibles les uns avec les autres.
*   Un système de suggestion de composants compatibles en fonction des choix déjà effectués par le client.
*   Un système de recommandation de configuration en fonction de l'utilisation prévue du PC, par exemple, une configuration gaming, une configuration bureautique, une configuration pour les professionnels de la création de contenu, etc.
*   Une interface utilisateur conviviale qui facilite la navigation, la sélection de composants et la visualisation de la configuration finale.



3.  Architecture technique

*   Un front-end dynamique basé sur ReactJS pour créer une expérience utilisateur moderne et réactive.
*   Une base de données pour stocker les informations sur les composants et les configurations de PC basé sur PostGres SQL.
*   Des APIs pour communiquer avec les bases de données et les différents services tiers, tels que le système de vérification de compatibilité basé sur NestJS.
*   Un système de gestion des utilisateurs pour permettre aux clients de créer des comptes, de gérer leurs informations de facturation et d'expédition, et de consulter l'historique de leurs commandes.






1.  Table "Utilisateurs" (users) :

*   ID (serial, clé primaire)
*   Nom (varchar)
*   Prénom (varchar)
*   Email (varchar)
*   Mot de passe (varchar)

2.  Table "Commandes" (pré-orders) :

*   ID (serial, clé primaire)
*   ID de l'utilisateur (int, clé étrangère vers la table "Utilisateurs")
*   Order_date (date)
*   Prix total (number)
*   Components_ID (int, clé étrangère vers la table "components")

3.  Table "Composants" (components) :

*   ID (serial, clé primaire)
*   Name (varchar)
*   Prix (decimal)
*   Description (varchar)
*   Types_Id (int, clé étrangère vers la table "Types")

4. Table "Types" :

*  ID (serial, clé primaire)
*  name (varchar)


Les relations:

*   Un utilisateur peut passer plusieurs commandes, mais une commande ne peut être passée que par un seul utilisateur. Relation 1:N entre la table "Utilisateurs" et la table "Commandes".
*   Une commande peut contenir plusieurs composants, et un composant peut appartenir à plusieurs commandes. Relation M:M entre la table "Commandes" et la table "Composants".
*  Un composant peu avoir un seul type (proc, carte graphique, ram etc), et un type peu appartenir à plusieurs composants. Relation 1:M  entre la table "types" et "composants"



MVP : connexion, enregistrement/modif/supp de sa configuration