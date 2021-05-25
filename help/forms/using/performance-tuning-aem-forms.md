---
title: Réglage des performances du serveur AEM Forms
seo-title: Réglage des performances du serveur AEM Forms
description: Pour qu’AEM Forms s’exécute de manière optimale, vous pouvez affiner les paramètres du cache et les paramètres JVM. En outre, l’utilisation d’un serveur Web peut améliorer les performances du déploiement d’AEM Forms.
seo-description: Pour qu’AEM Forms s’exécute de manière optimale, vous pouvez affiner les paramètres du cache et les paramètres JVM. En outre, l’utilisation d’un serveur Web peut améliorer les performances du déploiement d’AEM Forms.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Administrator
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 79%

---

# Réglage des performances du serveur AEM Forms {#performance-tuning-of-aem-forms-server}

Cet article explique les stratégies et les recommandations que vous pouvez implémenter pour réduire les ralentissements et optimiser les performances du déploiement d’AEM Forms.

## Paramètres du cache {#cache-settings}

Vous pouvez configurer et contrôler la stratégie de mise en cache d’AEM Forms à l’aide du composant **Mobile Forms Configurations** de la console d’administration Web d’AEM à l’adresse :

* (AEM Forms on OSGi) `https://[server]:[port]/system/console/configMgr`
* (AEM Forms on JEE) `https://[server]:[port]/lc/system/console/configMgr`

Les options disponibles pour la mise en cache sont les suivantes :

* **Aucune** : Impose de ne mettre en cache aucun artefact. En pratique, ceci ralentit les performances et nécessite une disponibilité importante de la mémoire en raison de l’absence de cache.
* **Conservatrice** : Indique de ne mettre en cache que les artefacts intermédiaires générés avant le rendu du formulaire, tels qu’un modèle contenant des fragments et des images en ligne.
* **Agressive** : Impose de mettre en cache presque tout ce qui peut être mis en cache, y compris le contenu HTML rendu, outre tous les artefacts du niveau de mise en cache Conservatrice. Ceci permet d’obtenir de meilleures performances mais utilise davantage de mémoire pour le stockage des artefacts mis en cache. La stratégie de mise en cache Agressive permet d’obtenir des performances constantes dans la rapidité du rendu d’un formulaire car le contenu rendu est mis en cache.

Les paramètres de cache par défaut d’AEM Forms peuvent ne pas suffire pour obtenir des performances optimales. Par conséquent, il est recommandé d’utiliser les paramètres suivants :

* **Stratégie de cache** : Agressive
* **Taille du cache** (nombre de formulaires) : Selon les besoins
* **Taille d’objet maximale** : Selon les besoins

![Configuration de Mobile Forms](assets/snap.png)

>[!NOTE]
>
>Si vous utilisez le répartiteur AEM pour mettre en cache des formulaires adaptatifs, il met également en cache les formulaires adaptatifs contenant des formulaires avec des données préremplies. Si ces formulaires sont diffusés à partir du cache du répartiteur AEM, il se peut que des données préremplies ou obsolètes soient diffusées aux utilisateurs. Par conséquent, utilisez le répartiteur AEM pour mettre en cache des formulaires adaptatifs qui n’utilisent pas de données pré-renseignées. De plus, un cache de répartiteur n’invalide pas automatiquement les fragments mis en cache. Par conséquent, ne l’utilisez pas pour mettre en cache des fragments de formulaire. Pour de tels formulaires et fragments, utilisez le [Cache de formulaires adaptatifs](/help/forms/using/configure-adaptive-forms-cache.md).

## Paramètres JVM    {#jvm-parameters}

Pour des performances optimales, il est recommandé d’utiliser les arguments `init` JVM suivants pour configurer les `Java heap` et `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>Les paramètres recommandés concernent Windows 2008 R2 8 Core et Oracle HotSpot 1.7 (64 bits) JDK et doivent être augmentés ou réduits selon votre configuration système.

## Utilisation d’un serveur Web {#using-a-web-server}

Les formulaires adaptatifs et les formulaires HTML5 sont rendus au format HTML5. Le résultat peut être volumineux en fonction de facteurs comme la taille du formulaire et les images qu’il contient. Pour optimiser le transfert des données, l’approche recommandée consiste à compresser la réponse HTML à l’aide du serveur Web à partir duquel la demande est traitée. Cette approche réduit la taille de la réponse, le trafic réseau et le temps nécessaire pour diffuser les données entre les machines client et serveur.

Par exemple, suivez les étapes ci-dessous pour activer la compression sur Apache Web Server 2.0 32 bits avec JBoss :

>[!NOTE]
>
>Les instructions suivantes ne s’appliquent à aucun autre serveur que le serveur web Apache 2.0 32 bits. Pour obtenir des instructions spécifiques à un autre serveur, reportez-vous à la documentation correspondante.

Les étapes suivantes présentent les modifications à effectuer pour activer la compression avec le serveur Web Apache.

**Procurez-vous le logiciel du serveur Web Apache correspondant à votre système d’exploitation**

* Windows : Téléchargez le serveur Web Apache à partir du site Apache HTTP Server Project.
* Solaris 64 bits : Téléchargez le serveur Web Apache à partir du site Web Sunfreeware for Solaris.
* Linux : Le serveur Web Apache est préinstallé sur un système Linux.

Apache peut communiquer avec CRX via le protocole HTTP. Les configurations concernent l’optimisation via HTTP.

1. Supprimez les commentaires des configurations de module suivantes dans le fichier `APACHE_HOME/conf/httpd.conf`.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Pour Linux, la valeur par défaut `APACHE_HOME` est `/etc/httpd/`.

1. Configurez le proxy sur le port 4502 de crx.

   Ajoutez la configuration suivante dans le fichier de configuration `APACHE_HOME/conf/httpd.conf`.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Activez la compression. Ajoutez la configuration suivante dans le fichier de configuration `APACHE_HOME/conf/httpd.conf`.

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

   Pour accéder au serveur crx, utilisez `https://[server]:80`, où `server` est le nom du serveur sur lequel le serveur Apache est exécuté.

## À l’aide d’un antivirus sur un serveur exécutant AEM Forms {#using-an-antivirus-on-server-running-aem-forms}

Les performances peuvent être lentes sur les serveurs exécutant un logiciel antivirus. Un logiciel antivirus (analyse à l’accès) toujours actif analyse tous les fichiers d’un système. Il peut ralentir le serveur et les performances d’AEM Forms sont affectées.

Pour améliorer les performances, vous pouvez configurer le logiciel antivirus pour exclure les fichiers et dossiers AEM Forms suivants de l’analyse permanente (à l’accès) :

* Répertoire d’installation d’AEM. S’il n’est pas possible d’exclure le répertoire complet, excluez les fichiers suivants :

   * [AEM répertoire d’installation]\crx-repository\temp
   * [AEM répertoire d’installation]\crx-repository\repository
   * [AEM répertoire d’installation]\crx-repository\launchpad

* Répertoire temporaire du serveur d’applications. L’emplacement par défaut est :

   * (Jboss) [AEM répertoire d’installation]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(AEM Forms on JEE uniquement)** Répertoire de stockage global de documents (GDS). L’emplacement par défaut est :

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLo gic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(AEM Forms on JEE uniquement)** Journaux du serveur et répertoire temporaire AEM Forms. L’emplacement par défaut est :

   * Journaux du serveur - `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * Répertoire temporaire - [Répertoire d’installation AEM Forms]\temp

>[!NOTE]
>
>* Si vous utilisez un autre emplacement pour le répertoire de stockage global de documents et le répertoire temporaire, ouvrez l’interface utilisateur d’administration à l’adresse `https://[server]:[port]/adminui)`, accédez à **Accueil > Paramètres > Paramètres de Core System > Configurations de base** pour confirmer l’emplacement utilisé.

* Si le serveur AEM Forms est lent, même après avoir exclu les répertoires suggérés, excluez également le fichier exécutable Java (java.exe).


