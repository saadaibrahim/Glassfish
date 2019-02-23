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
Dans le panneau de gauche, accédez à Ressources - JDBC - Pools de connexions JDBC.  
Cliquez sur Nouveau et entrez les valeurs suivantes: 
 1. Pool Name: testpool 
 2. Resource Type: javax.sql.DataSource 
 3. Nom de la classe de la source de données:  oracle.jdbc.pool.OracleDataSource
 4. Ajouter les propriétés suivantes: DatabaseName, User, Password, URL, PortNumber, serverName.
      jdbc:oracle:thin:@localhost:1521:sample
 5. Créer une source de données: Ressources ; clic sur Ressources JDBC ; clic sous Nouveau.  
 Nom JNDI : jdbc/sample     
 Nom du pool : Sample     

# Glassfish Realms
Un realm est un domaine de sécurité défini pour un serveur Web ou un serveur d'applications.  
Un domaine contient une collection d'utilisateurs, qui peuvent ou non être affectés à un groupe.  
La gestion des utilisateurs sur le serveur GlassFish est décrite dans la section Gestion des utilisateurs et des groupes sur le serveur GlassFish. 
 **Utilisateur** 
    Un utilisateur est une personne définie dans le serveur GlassFish. Dans une application Web, un utilisateur peut être associé à un ensemble de rôles lui donnant le droit d'accéder à toutes les ressources par ces rôles. Les utilisateurs peuvent être associés à un groupe.
    
 **Groupe**
    Un groupe sur le serveur GlassFish est une catégorie d'utilisateurs classés par caractéristiques communes, telles que le titre du poste ou le profil du client. Par exemple, la plupart des clients d’une application de commerce électronique peuvent appartenir au groupe CLIENT, mais les gros utilisateurs appartiennent au groupe PRÉFÉRÉ.  
    
 **Role**
    Un groupe sur le serveur GlassFish est différent d'un rôle. Un groupe est désigné pour l'ensemble du serveur GlassFish, tandis qu'un rôle est associé uniquement à une application spécifique du serveur GlassFish.   
Un rôle est un nom pour l'autorisation d'accéder à un ensemble particulier de ressources dans une application. Un rôle peut être comparé à une clé pouvant ouvrir un verrou. 

Les principaux realms sont:
1. file:  enregistre les informations dans un fichier. Il s'agit du domaine par défaut lors de la première installation du serveur GlassFish.   
    - Accéder à la console à l'adresse http://localhost:4848        
    - Ouvrez l'entrée "Configurations > server-config > Sécurité > Domaines" et cliquez sur "file"          
    - Une page "Modifier le domaine" s'affiche. Cliquez sur "Gérer les utilisateurs". Dans la nouvelle page, cliquez sur le       bouton "Nouveau".      
    - Créez les utilisateurs.       
2. jdbc:  enregistre les informations dans une base de données.    
    - Il faut commencer par créer les tables relationnelles qui vont conserver les informations sur les utilisateurs.      
    - Dans NetBeans, onglet Services > Databases, clic droit sur l'entrée Java DB et "Create Database" pour créer une nouvelle base de données "sample".         
      Une nouvelle entrée "jdbc:oracle:thin:@localhost:1521:sample" a dû être créée.       
    - Créez les tables dans le schéma associé à l'utilisateur: clic droit sur le nom du schéma et "Execute Command" et copiez la commande SQL qui crée les tables en les séparant par un ";".              
3. ldap:  les informations sont dans un annuaire LDAP.  

 

