---
title: Optimiser les formulaires HTML5
seo-title: Optimizing HTML5 forms
description: Vous pouvez optimiser la taille de sortie des formulaires HTML5.
seo-description: You can optimize the output size of the HTML5 forms.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
exl-id: 8d2b5294-9763-4348-b927-706ebac90b95
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 24%

---

# Optimiser les formulaires HTML5 {#optimizing-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

HTML5 forms effectue le rendu des formulaires au format HTML5. La sortie générée peut être volumineuse en fonction de facteurs tels que la taille du formulaire et les images qu’il contient. Pour optimiser le transfert de données, l’approche recommandée consiste à compresser la réponse du HTML à l’aide du serveur web à partir duquel la requête est traitée. Cette approche réduit la taille de la réponse, le trafic réseau et le temps nécessaire pour diffuser les données entre le serveur et les ordinateurs clients.

Cet article décrit les étapes requises pour activer la compression sur le serveur web Apache 2.0 32 bits, avec JBoss.

*Remarque : Les instructions suivantes ne s’appliquent qu’au serveur web Apache 2.0 32 bits.*

Procurez-vous le logiciel du serveur web Apache correspondant à votre système d’exploitation :

* Pour Windows, téléchargez le serveur web Apache à partir du site Apache HTTP Server Project.
* Pour Solaris 64 bits, téléchargez le serveur web Apache à partir du site Web Sunfreeware for Solaris.
* Pour Linux, le serveur web Apache est préinstallé sur un système Linux.

Apache peut communiquer avec JBoss à l’aide du protocole HTTP ou AJP.

1. Ne commentez pas les configurations de module suivantes dans le fichier *APACHE_HOME/conf/httpd.conf*.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Pour Linux, le répertoire APACHE_HOME par défaut est /etc/httpd/.

1. Configurez le proxy sur le port 8080 de JBoss.

   Ajoutez la configuration suivante au fichier de configuration *APACHE_HOME/conf/httpd.conf*.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Lorsque vous utilisez un proxy, les modifications de configuration suivantes sont requises :
   > 
   >* Accès : *https://&lt;server>:&lt;port>/system/console/configMgr*
   * Modification de la configuration pour Apache Sling Referrer Filter
   * Dans le champ Allow Hosts (Autoriser les hôtes), ajoutez l’entrée pour le serveur proxy.


1. Activez la compression.

   Ajoutez la configuration suivante au fichier de configuration *APACHE_HOME/conf/httpd.conf*.

   ```java
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Pour accéder au serveur AEM, utilisez https://[Apache_server]:80.
