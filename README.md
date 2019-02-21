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

 *Créer un domaine:     
La sous-commande create-domain crée un domaine avec un utilisateur administratif unique spécifié par l'option de l'utilitaire asadmin --user. 
Si l'option --user n'est pas spécifiée et que l'option --nopassword est définie sur true, 
l'utilisateur administratif par défaut, admin, est utilisé.
> create-domain --adminport 4848 domain1

 *Supprimer un domaine:   
Utilisez la sous-commande delete-domain pour supprimer un existant domaine existant. Seul l'utilisateur root ou l'utilisateur du système d'exploitation autorisé à administrer le domaine peut exécuter cette sous-commande.
> delete-domain --domaindir ..\domains domain1

*Lancer un domaine: 
>asadmin start-domain domain1 

*Arrêter un domaine:  
>asadmin stop-domain domain1


comment ,   lancer un domaine  lister les domaines
les aspects avances: la notion de domain, les pool de connexion, les utilisateurs, les realm pour les contexte d'application
