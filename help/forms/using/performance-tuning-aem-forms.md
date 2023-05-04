---
title: Réglage des performances du serveur AEM Forms
seo-title: Performance tuning of AEM Forms server
description: Pour qu’AEM Forms s’exécute de manière optimale, vous pouvez affiner les paramètres de cache et les paramètres JVM. En outre, l’utilisation d’un serveur web peut améliorer les performances du déploiement d’AEM Forms.
seo-description: For AEM Forms to perform optimally, you can fine-tune the cache settings and JVM parameters. Also, using a web server can enhance the performance of AEM Forms deployment.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Admin
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 29%

---

# Réglage des performances du serveur AEM Forms {#performance-tuning-of-aem-forms-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cet article décrit les stratégies et les bonnes pratiques que vous pouvez implémenter pour réduire les goulets d’étranglement et optimiser les performances de votre déploiement AEM Forms.

## Paramètres du cache {#cache-settings}

Vous pouvez configurer et contrôler la stratégie de mise en cache d’AEM Forms à l’aide du **Configurations de Mobile Forms** dans la console de configuration web d’AEM à l’adresse :

* (AEM Forms on OSGi) `https://[server]:[port]/system/console/configMgr`
* (AEM Forms on JEE) `https://[server]:[port]/lc/system/console/configMgr`

Les options disponibles pour la mise en cache sont les suivantes :

* **Aucun**: Impose de ne mettre en cache aucun artefact. En pratique, cela ralentit les performances et nécessite une disponibilité élevée de la mémoire en raison de l’absence de cache.
* **Conservatrice**: Indique de ne mettre en cache que les artefacts intermédiaires générés avant le rendu du formulaire, tels qu’un modèle contenant des fragments et des images en ligne.
* **Agressive**: Impose de mettre en cache pratiquement tout ce qui peut être mis en cache, y compris le contenu du HTML rendu en plus de tous les artefacts du niveau de mise en cache Conservatrice. Cela se traduit par de meilleures performances, mais consomme également plus de mémoire pour le stockage des artefacts mis en cache. Une stratégie de mise en cache agressive signifie que vous obtiendrez des performances constantes lors du rendu d’un formulaire, car le contenu rendu est mis en cache.

Les paramètres de cache par défaut d’AEM Forms peuvent ne pas suffire pour obtenir des performances optimales. Il est donc recommandé d’utiliser les paramètres suivants :

* **Stratégie de cache**: Agressive
* **Taille du cache** (nombre de formulaires) : Selon les besoins
* **Taille d’objet maximale** : Selon les besoins

![Configuration de Mobile Forms](assets/snap.png)

>[!NOTE]
>
>Si vous utilisez AEM Dispatcher pour mettre en cache des formulaires adaptatifs, il met également en cache les formulaires adaptatifs qui contiennent des formulaires avec des données préremplies. Si de tels formulaires sont diffusés à partir du cache AEM Dispatcher, cela peut entraîner la diffusion de données préremplies ou obsolètes aux utilisateurs. Ainsi, utilisez AEM Dispatcher pour mettre en cache les formulaires adaptatifs qui n’utilisent pas de données préremplies. De plus, un cache de Dispatcher n’invalide pas automatiquement les fragments mis en cache. Ainsi, ne l’utilisez pas pour mettre en cache des fragments de formulaire. Pour ces formulaires et fragments, utilisez [Cache de formulaires adaptatifs](/help/forms/using/configure-adaptive-forms-cache.md).

## Paramètres JVM  {#jvm-parameters}

Pour des performances optimales, il est conseillé d’utiliser les arguments `init` JVM suivants pour configurer le `Java heap` et `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Les paramètres recommandés sont ceux de Windows 2008 R2 8 Core et Oracle HotSpot 1.7 (64 bits) JDK et doivent être adaptés en fonction de la configuration de votre système.

## Utiliser un serveur web {#using-a-web-server}

Les formulaires adaptatifs et les formulaires HTML5 sont rendus au format HTML5. La sortie générée peut être volumineuse en fonction de facteurs tels que la taille du formulaire et les images qu’il contient. Pour optimiser le transfert de données, l’approche recommandée consiste à compresser la réponse du HTML à l’aide du serveur web à partir duquel la requête est traitée. Cette approche réduit la taille de la réponse, le trafic réseau et le temps nécessaire pour diffuser les données entre les ordinateurs serveur et client.

Par exemple, procédez comme suit pour activer la compression sur Apache Web Server 2.0 32 bits avec JBoss :

>[!NOTE]
>
>Les instructions suivantes ne s’appliquent qu’à Apache Web Server 2.0 32 bits. Pour obtenir des instructions spécifiques à un autre serveur, reportez-vous à la documentation correspondante.

Les étapes suivantes présentent les modifications requises pour activer la compression avec le serveur web Apache.

**Procurez-vous le logiciel du serveur web Apache correspondant à votre système d’exploitation**

* Windows : téléchargez le serveur web Apache à partir du site Apache HTTP Server Project.
* Solaris 64 bits : téléchargez le serveur web Apache à partir du site web Sunfreeware for Solaris.
* Linux : le serveur web Apache est préinstallé sur un système Linux.

Apache peut communiquer avec CRX à l’aide du protocole HTTP. Les configurations sont destinées à l’optimisation via HTTP.

1. Supprimez les commentaires des configurations de modules suivantes dans le fichier `APACHE_HOME/conf/httpd.conf`.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Pour Linux, le répertoire `APACHE_HOME` par défaut est `/etc/httpd/`.

1. Configurez le proxy sur le port 4502 de crx.

   Ajoutez la configuration suivante dans le fichier de configuration `APACHE_HOME/conf/httpd.conf`.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Activez la compression. Ajoutez la configuration suivante au fichier de configuration `APACHE_HOME/conf/httpd.conf`.

   **Pour les formulaires HTML5**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Pour les formulaires adaptatifs**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Pour accéder au serveur CRX, utilisez `https://[server]:80`, où `server` est le nom du serveur sur lequel s’exécute le serveur Apache.

## Utiliser un antivirus sur un serveur exécutant AEM Forms {#using-an-antivirus-on-server-running-aem-forms}

Les performances des serveurs exécutant un logiciel antivirus peuvent être ralenties. Un logiciel antivirus (analyse à l’accès) toujours actif analyse tous les fichiers d’un système. Cela peut ralentir le serveur et affecter les performances d’AEM Forms.

Pour améliorer les performances, vous pouvez diriger le logiciel antivirus afin d’exclure les fichiers et dossiers AEM Forms suivants de l’analyse toujours active (à l’accès) :

* AEM Répertoire d&#39;installation. S’il n’est pas possible d’exclure un répertoire complet, excluez ce qui suit :

   * [Répertoire d’installation d’AEM]\crx-repository\temp
   * [Répertoire d’installation d’AEM]\crx-repository\repository
   * [Répertoire d’installation d’AEM]\crx-repository\launchpad

* Répertoire temporaire du serveur d’applications. L’emplacement par défaut est :

   * (JBoss) [Répertoire d’installation d’AEM]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(AEM Forms on JEE uniquement)** Répertoire de stockage global de documents. L’emplacement par défaut est :

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLo gic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(AEM Forms on JEE uniquement)** Journaux du serveur et répertoire temporaire AEM Forms. L’emplacement par défaut est :

   * Journaux du serveur - `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * Répertoire temporaire - [Répertoire d’installation d’AEM Forms]\temp

>[!NOTE]
>
>* Si vous utilisez un autre emplacement pour le répertoire de stockage global de documents et le répertoire temporaire, ouvrez l’interface utilisateur d’administration à l’adresse `https://[server]:[port]/adminui)`, accédez à **Accueil > Paramètres > Paramètres de Core System > Configurations de base** pour confirmer l’emplacement utilisé.
* Si le serveur AEM Forms est lent, même après l’exclusion des répertoires suggérés, excluez également le fichier exécutable Java (java.exe).
>

