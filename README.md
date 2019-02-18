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

 ** 




comment creer un domaine, supprimer un domaine, lancer un domaine,  arrêter un domaine, lister les domaines
les aspects avances: la notion de domain, les pool de connexion, les utilisateurs, les realm pour les contexte d'application
