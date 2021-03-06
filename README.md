# aurelia-spring-app
Application starter basée sur Aurelia JS et Spring MVC en CORS

# Ce starter contient
* Une configuration complète de Spring security stateless CORS
* Inclusion de Bootstrap CSS + un menu vertical pour la navigation
* Une configuration complète de Spring Data avec inclusion de QueryDSL + des fonctions utilitaires pour la pagination
* Une configuration complète pour gérer le multi-tenant (proposé: schéma/database => à décommenter)
* une gestion des utilisateurs type RBAC (utilisateurs/groupes/permissions) couplée à Spring security avec les écrans d'administration associés
* Fonctionnalité de reset et changement de password avec envoi de mail (+ utilisation de velocity)
* Une page 'about' générée via un goal maven pour lister rapidement l'ensemble des dépendances du projet
* Packaging de l'application (externalisation des properties et templates de mails) + bundle aurelia


# Pré-requis
Java7 et MySQL (bdd utilisée par défaut)

# Installation
Suivre les _readme_ des 2 projets

# Screenshot
![Image of Yaktocat](http://lagrede.alwaysdata.net/aurelia-spring-app/aurelia-spring-app-screenshot.png)



# Déploiement 
Bundle de l'application aurelia
```bash
gulp build
```
```bash
aurelia bundle
```

Exemple de configuration apache
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName monserveur.ddns.net

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    LogLevel warn

    #ServerPath /app
    DocumentRoot /var/www/aurelia

     ProxyPass /spring-server http://localhost:8080/spring-server

     ProxyRequests Off
     ProxyPreservehost on
     
     <Proxy>
         Order Allow,Deny
         Allow from all
     </Proxy>

</VirtualHost>
```
