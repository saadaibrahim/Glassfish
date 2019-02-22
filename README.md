# GlassFish
GlassFish est un serveur d'applications compatible Java EE. C'est l'implémentation de référence Java EE développé par Oracle-Sun. 
Glassfish est un server Web comme "Tomcat" et "Weblogic". Il permet de déployer des applications web écrites sur Java. 
Glassfish a deux versions: une gratuite avec code source ouvert et une autre commerciale.

# Audience
Ce tutoriel est destiné aux programmeurs qui sont destinés à développer et déployer des applications Java EE 7.

# Prérequis  
L'EDI Netbeans 8.0 [Netbeans Website](http://www.netbeans.org/)  
Pour installer le serveur Glassfish, installez simplement l'EDI Netbeans avec tous les composants.


# La notion de domaine de Glassfish
Un domaine est une notion très générale, qui ressemble à un espace de travail.
Glassfish peut gérer de nombreux domaines, et toutes les applications doivent etre déployer à l'intérieur d'un domaine.
Un domaine admet:
 1. Un répertoire: $GLASSFISH_HOME/glassish/domains
 2. Un nom et un port pour l'administrateur: admin, 4848, ...etc
 3. Un port pour déployer l'application: 8080, 8081, ...etc.

 * Créer un domaine:     
La sous-commande create-domain crée un domaine avec un utilisateur administratif unique spécifié par l'option de l'utilitaire asadmin --user. 
Si l'option --user n'est pas spécifiée et que l'option --nopassword est définie sur true, 
l'utilisateur administratif par défaut, admin, est utilisé.
> create-domain --adminport 4848 domain1

 * Supprimer un domaine:   
Utilisez la sous-commande delete-domain pour supprimer un existant domaine existant. Seul l'utilisateur root ou l'utilisateur du système d'exploitation autorisé à administrer le domaine peut exécuter cette sous-commande.
> delete-domain --domaindir ..\domains domain1

* Lancer un domaine: 
>asadmin start-domain domain1 

* Arrêter un domaine:  
>asadmin stop-domain domain1

# Les Pool de connexions 
Un pool de connexions est un stocker de connexions de base de données pouvant être utilisées pour se connecter à une base de données.
Au lieu de créer une nouvelle connexion chaque fois que nécessaire, un pool de connexions est créé au démarrage de votre serveur d'applications.
Ces connexions peuvent ensuite être utilisées et réutilisées. Lorsqu'une nouvelle connexion est requise, le pool recherche une connexion disponible. S'il en existe un, il est renvoyé au demandeur. Si l'une d'entre elles n'est pas disponible, une nouvelle connexion est établie en fonction du nombre de connexions déjà présentes dans le pool. 
Une fois la connexion établie, elle est renvoyée au pool de connexions pour être utilisée par le demandeur suivant.

 * Créer un pool de connexion:  
Une fois le serveur démarré, vous pouvez accéder à la console à l'adresse http://localhost:4848  
Dans le panneau de gauche, accédez à Ressources - Pools de connexions JDBC-JDBC.  
Cliquez sur Nouveau et entrez les valeurs suivantes: 
 1. Pool Name: testpool 
 2. Resource Type: javax.sql.DataSource 
 3. Driver Vendor: MySql  
Cliquez sur Next, puis sur Finish à l'écran suivant, en acceptant les valeurs par défaut. 

# Glassfish Realms 

