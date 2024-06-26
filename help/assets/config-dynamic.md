---
title: Configuration de Dynamic Media - mode hybride
seo-title: Configuring Dynamic Media - Hybrid mode
description: Découvrez comment configurer Dynamic Media en mode hybride.
seo-description: Learn how to configure Dynamic Media - Hybrid mode.
uuid: de88f68f-4697-4ff0-8008-3ae6a4684a84
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 821eb27e-67c9-4589-9196-30dacb84fa59
exl-id: 1e122f97-ac37-44f5-a1cd-bf53ffda6f5b
feature: Configuration,Hybrid Mode
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '7816'
ht-degree: 37%

---

# Configuration de Dynamic Media - mode hybride {#configuring-dynamic-media-hybrid-mode}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dynamic Media : l’option hybride doit être activée et configurée pour être utilisée. Selon l’utilisation que vous souhaitez en faire, Dynamic Media prend en charge [plusieurs configurations](#supported-dynamic-media-configurations).

>[!NOTE]
>
>Si vous envisagez de configurer et d’exécuter Dynamic Media en mode d’exécution Scene7, reportez-vous à la section [Configuration de Dynamic Media - mode Scene7](config-dms7.md).
>
>Si vous envisagez de configurer et d’exécuter Dynamic Media en mode d’exécution hybride, suivez les instructions de cette page.

En savoir plus sur l’utilisation des [vidéos](video.md) dans Dynamic Media.

Si Adobe Experience Manager est configuré dans des environnements différents, tels que le développement, l’évaluation et la production, vous devez configurer Dynamic Media Cloud Services pour chacun de ces environnements.

Si vous rencontrez des problèmes avec votre configuration Dynamic Media, les fichiers journaux spécifiques à Dynamic Media constituent un emplacement important à rechercher. Ils sont installés automatiquement lorsque vous activez Dynamic Media :

* `s7access.log`
* `ImageServing.log`

Ils sont documentés dans [Surveillance et maintenance de votre instance AEM](/help/sites-deploying/monitoring-and-maintaining.md).

La diffusion de contenus et la publication hybride est une fonctionnalité clé lorsque vous ajoutez Dynamic Media à Adobe Experience Manager. La publication hybride vous permet de diffuser des ressources Dynamic Media, telles que des images, des visionneuses et des vidéos, à partir du cloud plutôt que depuis les noeuds de publication AEM.

D’autres contenus, tels que les visionneuses Dynamic Media, les pages du site et le contenu statique, continueront à être diffusés à partir des noeuds de publication AEM.

Si vous utilisez déjà Dynamic Media, il vous est demandé d’utiliser la publication hybride comme méthode de diffusion pour tout le contenu Dynamic Media.

## Architecture de publication hybride des vidéos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-506.png)

## Architecture de publication hybride pour les images {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## Configurations Dynamic Media prises en charge {#supported-dynamic-media-configurations}

Les tâches de configuration qui suivent font référence aux termes suivants :

| **Terme** | **Dynamic Media activé** | **Description** |
|---|---|---|
| AEM noeud Auteur | Coche blanche dans un cercle vert | Nœud auteur que vous déployez sur On-Premise ou via les Managed Services. |
| AEM noeud de publication | « X » blanc dans un carré rouge. | Nœud de publication que vous déployez sur On-Premise ou via les Managed Services. |
| Noeud de publication Image Service | Coche blanche dans un cercle vert. | Nœud de publication que vous exécutez dans les data centers gérés par Adobe. Renvoie à l’URL du service d’images. |

Vous pouvez choisir de mettre en oeuvre Dynamic Media uniquement pour les images, uniquement pour les vidéos ou pour les images et les vidéos. Pour déterminer les étapes de configuration de Dynamic Media pour votre scénario spécifique, reportez-vous au tableau suivant.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Scénario</strong></td> 
   <td><strong>Fonctionnement</strong></td> 
   <td><strong>Étapes de configuration</strong></td> 
  </tr> 
  <tr> 
   <td>Diffuser UNIQUEMENT des images en production</td> 
   <td>Les images sont diffusées via des serveurs dans les centres de données d’Adobe du monde entier, puis mises en cache par un réseau de diffusion de contenu pour une portée globale et des performances évolutives.</td> 
   <td> 
    <ol> 
     <li>Sur l’AEM <strong>author</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a>.</li> 
     <li>Configuration de l’imagerie dans <a href="#configuring-dynamic-media-cloud-services">Cloud Services Dynamic Media</a>.</li> 
     <li><a href="#configuring-image-replication">Configurer la réplication de l’image</a>.</li> 
     <li><a href="#replicating-catalog-settings">Répliquer les paramètres du catalogue</a>.</li> 
     <li><a href="#replicating-viewer-presets">Répliquer les paramètres prédéfinis de la visionneuse</a>.</li> 
     <li><a href="#using-default-asset-filters-for-replication">Utiliser des filtres de ressource par défaut pour la réplication</a>.</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Configurer les paramètres du serveur d’images Dynamic Media</a>.</li> 
     <li><a href="#delivering-assets">Livrer les ressources</a>.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Diffuser UNIQUEMENT des images en préproduction (développement, QE, évaluation, etc.)</td> 
   <td>Les images sont diffusées via le noeud de publication AEM. Dans ce scénario, puisque le trafic est minimal, il n’est pas nécessaire de diffuser des images vers le centre de données d’Adobe. Un autre avantage est que cela permet un aperçu sécurisé du contenu avant le lancement de la production.</td> 
   <td> 
    <ol> 
     <li>Sur l’AEM <strong>author</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a>.</li> 
     <li>Sur AEM <strong>publier</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a>.</li> 
     <li><a href="#replicating-viewer-presets">Répliquer les paramètres prédéfinis de la visionneuse</a>.</li> 
     <li>Configuration <a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">filtre de ressources pour les images hors production</a>.</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Configurez les paramètres du serveur d’images Dynamic Media.</a></li> 
     <li><a href="#delivering-assets">Livrez les ressources.</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Diffuser UNIQUEMENT de la vidéo dans n’importe quel environnement (production, développement, QE, évaluation, etc.)</td> 
   <td>Les vidéos sont diffusées et mises en cache par un réseau de diffusion de contenu pour des performances évolutives et une portée globale. L’image d’affiche vidéo (miniature de la vidéo affichée avant le début de la lecture) sera diffusée par l’instance de publication AEM.</td> 
   <td> 
    <ol> 
     <li>Sur l’AEM <strong>author</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a>.</li> 
     <li>Sur l’AEM <strong>publier</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a> (l’instance de publication diffuse l’image d’affiche vidéo et fournit des métadonnées pour la lecture vidéo).</li> 
     <li>Configuration d’une vidéo dans <a href="#configuring-dynamic-media-cloud-services">Cloud Services Dynamic Media.</a></li> 
     <li><a href="#replicating-viewer-presets">Répliquer les paramètres prédéfinis de la visionneuse</a>.</li> 
     <li>Configuration <a href="#setting-up-asset-filters-for-video-only-deployments">filtre de ressources pour la vidéo uniquement</a>.</li> 
     <li><a href="#delivering-assets">Livrez les ressources.</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Diffuser À LA FOIS des images et des vidéos en production</td> 
   <td><p>Les vidéos sont diffusées et mises en cache par un réseau de diffusion de contenu pour des performances évolutives et une portée globale. Les images et les images d’affiche vidéo sont diffusées via les serveurs des centres de données d’Adobe dans le monde entier, puis mises en cache par un réseau de diffusion de contenu pour une portée globale et des performances évolutives.</p> <p>Reportez-vous aux sections précédentes pour configurer une image ou une vidéo en préproduction. </p> </td> 
   <td> 
    <ol> 
     <li>Sur l’AEM <strong>author</strong> noeud, <a href="#enabling-dynamic-media">activer Dynamic Media</a>.</li> 
     <li>Configuration d’une vidéo dans <a href="#configuring-dynamic-media-cloud-services">Cloud Services Dynamic Media.</a></li> 
     <li>Configuration de l’imagerie dans <a href="#configuring-dynamic-media-cloud-services">Cloud Services Dynamic Media.</a></li> 
     <li><a href="#configuring-image-replication">Configurer la réplication de l’image</a>.</li> 
     <li><a href="#replicating-catalog-settings">Répliquer les paramètres du catalogue</a>.</li> 
     <li><a href="#replicating-viewer-presets">Répliquer les paramètres prédéfinis de la visionneuse</a>.</li> 
     <li><a href="#using-default-asset-filters-for-replication">Utilisez les filtres de ressource par défaut pour la réplication.</a></li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Configurez les paramètres du serveur d’images Dynamic Media.</a></li> 
     <li><a href="#delivering-assets">Livrez les ressources.</a></li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>

## Activation de Dynamic Media {#enabling-dynamic-media}

[Dynamic Media](https://www.adobe.com/fr/marketing/experience-manager-assets/dynamic-media.html) est désactivé par défaut. Pour tirer parti des fonctionnalités de Dynamic Media, vous devez activer Dynamic Media à l’aide du **[!UICONTROL dynamicmedia]** le mode d’exécution comme vous le feriez, par exemple : **[!UICONTROL publier]** mode d’exécution. Avant l’activation, vérifiez les [exigences techniques](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on).

>[!NOTE]
>
>L’activation de Dynamic Media via le mode d’exécution remplace les fonctionnalités d’AEM 6.1 et d’AEM 6.0 dans lesquelles vous avez activé Dynamic Media en définissant la variable **[!UICONTROL dynamicMediaEnabled]** indicateur pour **[!UICONTROL true]**. Cet indicateur n’a aucune fonctionnalité dans AEM version 6.2 et ultérieure. De plus, vous n’avez pas besoin de redémarrer le démarrage rapide pour activer Dynamic Media.

En activant Dynamic Media, les fonctionnalités de média dynamique seront disponibles dans l’interface utilisateur et chaque ressource d’image chargée reçoit une `cqdam.pyramid.tiff` rendu utilisé pour la diffusion rapide des rendus d’image dynamiques. Ces fichiers PTIFF présentent des avantages significatifs, notamment (1) la possibilité de gérer une seule image maître et de générer des rendus infinis à la volée sans stockage supplémentaire et (2) la possibilité d’utiliser la visualisation interactive telle que le zoom, le panoramique, la rotation, etc.

Si vous souhaitez utiliser Dynamic Media Classic dans AEM, vous ne devez pas activer Dynamic Media, sauf si vous utilisez une [scénario spécifique](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media). Dynamic Media est désactivé, sauf si vous activez Dynamic Media en mode d’exécution.

Pour activer Dynamic Media, vous devez activer le mode d’exécution Dynamic Media à partir de la ligne de commande ou du nom du fichier de démarrage rapide.

**Pour activer Dynamic Media**:

1. Dans la ligne de commande, lorsque vous lancez le démarrage rapide, procédez de la façon suivante :

   * Ajouter **[!UICONTROL -r dynamicmedia]** à la fin de la ligne de commande lors du démarrage du fichier jar.

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -r dynamicmedia
   ```

   Si vous publiez sur s7delivery, vous devez également inclure les arguments trustStore suivants :

   ```shell
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. Requête `http://localhost:4502/is/image` et vérifiez que Image Server est en cours d’exécution.

   >[!NOTE]
   >
   >Pour résoudre les problèmes liés à Dynamic Media, reportez-vous aux journaux suivants dans la section **[!UICONTROL crx-quickstart/logs/]** directory:
   >
   >* ImageServer-&lt;PortId>-&lt;yyyy>&lt;mm>&lt;dd>.log - Le journal ImageServer fournit des statistiques et des informations permettant d’analyser le comportement du processus ImageServer interne.

      Exemple de nom de fichier de journal Image Server : `ImageServer-57346-2019-07-25.log`
   * s7access-&lt;yyyy>&lt;mm>&lt;dd>.log - Le journal s7access enregistre chaque requête envoyée à Dynamic Media via `/is/image` et `/is/content`.
   Ces journaux sont utilisés uniquement lorsque Dynamic Media est activé. Ils ne sont pas inclus dans la variable **Télécharger complet** qui est généré à partir du **[!UICONTROL system/console/status-Bundlelist]** page; lorsque vous appelez le service clientèle si vous rencontrez un problème Dynamic Media, ajoutez ces deux journaux au problème.

### Si vous avez installé AEM sur un autre port ou chemin d’accès au contexte... {#if-you-installed-aem-to-a-different-port-or-context-path}

Si vous déployez [AEM à un serveur d’applications](/help/sites-deploying/application-server-install.md) et que Dynamic Media est activé, vous devez configurer la variable **self** dans l’externaliseur. Sinon, la génération de miniatures pour les ressources ne fonctionnera pas correctement pour les ressources Dynamic Media.

En outre, si vous exécutez le démarrage rapide sur un autre port ou chemin de contexte, vous devez également modifier la variable **self** domaine.

Lorsque Dynamic Media est activé, les rendus de miniature statiques pour les ressources images sont générés à l’aide de Dynamic Media. Pour que la génération de miniatures fonctionne correctement pour Dynamic Media, AEM doit effectuer une requête d’URL vers elle-même et connaître le numéro de port et le chemin d’accès au contexte.

En AEM :

* Le **self** du domaine [externalizer](/help/sites-developing/externalizer.md) est utilisé pour récupérer le numéro de port et le chemin d’accès au contexte.
* Si non **self** est configuré, le numéro de port et le chemin d’accès au contexte sont récupérés à partir du service HTTP Jetty.

Dans un déploiement WAR QuickStart AEM, le numéro de port et le chemin d’accès au contexte ne peuvent pas être dérivés. Vous devez donc configurer une **self** domaine. Voir [documentation de l’externaliseur](/help/sites-developing/externalizer.md) sur la configuration de la variable **self** domaine.

>[!NOTE]
Dans un [AEM déploiement autonome de démarrage rapide](/help/sites-deploying/deploy.md), un **self** n’a généralement pas besoin d’être configuré, car le numéro de port et le chemin d’accès au contexte peuvent être configurés automatiquement. Toutefois, si toutes les interfaces réseau sont désactivées, vous devez configurer la variable **self** domaine.

## Désactivation de Dynamic Media  {#disabling-dynamic-media}

Dynamic Media n’est pas activé par défaut. Cependant, si vous avez précédemment activé Dynamic Media, vous pouvez le désactiver ultérieurement.

Pour désactiver Dynamic Media après l’avoir activé, supprimez la variable **[!UICONTROL -r dynamicmedia]** Indicateur du mode d’exécution.

**Pour désactiver Dynamic Media après son activation**:

1. Dans la ligne de commande, lorsque vous lancez le démarrage rapide, vous pouvez procéder de l’une des façons suivantes :

   * Ne pas ajouter `-r dynamicmedia` sur la ligne de commande lors du démarrage du fichier JAR.

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar
   ```

1. Requête `http://localhost:4502/is/image`. Vous recevez un message indiquant que Dynamic Media est désactivé.

   >[!NOTE]
   Une fois que le mode d’exécution Dynamic Media est désactivé, l’étape de workflow qui génère le rendu `qdam.pyramid.tiff` est automatiquement ignorée. Cette opération désactive également la prise en charge des rendus dynamiques et d’autres fonctionnalités de Dynamic Media.
   Notez également que lorsque le mode d’exécution Dynamic Media est désactivé après la configuration du serveur AEM, toutes les ressources qui ont été chargées sous ce mode d’exécution sont désormais invalides.

## (Facultatif) Migration des paramètres prédéfinis et des configurations Dynamic Media de 6.3 à 6.4 sans interruption {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Si vous effectuez une mise à niveau AEM Dynamic Media de la version 6.3 vers la version 6.4, qui inclut désormais la possibilité de réaliser des déploiements sans interruption (également appelés &quot;Opt-in&quot;), vous devez exécuter la commande curl suivante pour migrer tous vos paramètres prédéfinis et configurations à partir de `/etc` to `/conf` en CRXDE Lite.

**Remarque**: Si vous exécutez votre instance AEM en mode de compatibilité (c’est-à-dire que le package de compatibilité est installé), il n’est pas nécessaire d’exécuter ces commandes.

Pour migrer vos paramètres prédéfinis et configurations personnalisés depuis `/etc` to `/conf`, exécutez la commande curl Linux suivante :

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Pour toutes les mises à niveau, avec ou sans module de compatibilité, vous pouvez copier les paramètres prédéfinis de visionneuse prêts à l’emploi en exécutant la commande suivante :

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## Configuration de la réplication d’images {#configuring-image-replication}

La diffusion d’images Dynamic Media fonctionne en publiant des ressources d’image, y compris des miniatures vidéo, à partir de l’auteur AEM et en les répliquant vers le service de réplication à la demande de l’Adobe (l’URL du service de réplication). Les ressources sont ensuite diffusées par l’intermédiaire du service de diffusion d’images On-Demand (l’URL du service d’images).

Vous devez effectuer les opérations suivantes :

1. [Définissez une authentification](#setting-up-authentication).
1. [Configurez l’agent de réplication](#configuring-the-replication-agent).

L’agent de réplication publie les ressources Dynamic Media telles que des images, des métadonnées et des visionneuses de vidéo, vers le service d’images hébergé par Adobe. L’agent de réplication n’est pas activé par défaut.

Après avoir configuré l’agent de réplication, vous devez [valider et tester qu’il a été correctement configuré.](#validating-the-replication-agent-for-dynamic-media). Cette section décrit ces procédures.

>[!NOTE]
La limite de mémoire par défaut pour la création de PTIFF est de 3 Go pour tous les workflows. Par exemple, vous pouvez traiter une image qui nécessite 3 Go de mémoire pendant que d’autres workflows sont en pause, ou traiter 10 images en parallèle qui nécessitent chacune 300 Mo de mémoire.
La limite de mémoire est configurable et doit correspondre à la disponibilité de la ressource système et au type de contenu d’image en cours de traitement. Si vous disposez de nombreuses ressources très volumineuses et de suffisamment de mémoire sur le système, vous pouvez augmenter cette limite pour vous assurer que les images sont traitées en parallèle.
Une image qui nécessite plus de mémoire que la limite maximale est rejetée.
Pour modifier la limite de mémoire pour la création d’images PTIFF, accédez à **[!UICONTROL Outils > Opérations > Console Web > Adobe CQ Scene7 PTiffManager]** et modifiez la valeur `maxMemory`.

### Configuration de l’authentification {#setting-up-authentication}

Vous devez configurer l’authentification de réplication sur l’auteur afin de répliquer les images vers le service de diffusion d’images Dynamic Media. Pour ce faire, vous devez obtenir un KeyStore, puis l’enregistrer sous le **[!UICONTROL dynamic-media-replication]** et de le configurer. L’administrateur de votre société doit avoir reçu un e-mail de bienvenue contenant le fichier KeyStore et les informations d’identification nécessaires pendant le processus d’approvisionnement. Si vous ne l’avez pas reçu, contactez le service clientèle.

**Pour configurer l’authentification**:

1. Contactez le service clientèle pour obtenir votre fichier KeyStore et votre mot de passe si vous ne possédez pas déjà ce fichier. Cela fait partie de la configuration et vous associerez les clés à votre compte.
1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Sécurité > Utilisateurs]**.
1. Sur la page Gestion utilisateur, accédez à la **[!UICONTROL dynamic-media-replication]** , puis appuyez pour ouvrir.

   ![dm-replication](assets/dm-replication.png)

1. Dans la page Modifier les paramètres utilisateur pour la réplication Dynamic Media, appuyez sur le bouton **[!UICONTROL Keystore]** , puis appuyez sur **[!UICONTROL Créer KeyStore]**.

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. Saisissez un mot de passe, puis confirmez-le dans la boîte de dialogue **[!UICONTROL Définir le mot de passe d’accès KeyStore]**.

   >[!NOTE]
   Mémorisez le mot de passe que vous saisissez. Vous devrez le saisir à nouveau lorsque vous configurerez la variable **[!UICONTROL Agent de réplication]** plus tard.

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. Sur la page **[!UICONTROL Modifier les paramètres utilisateurs pour la réplication Dynamic Media]**, développez l’espace **[!UICONTROL Ajouter une clé privée depuis le fichier KeyStore]** et ajoutez les éléments suivants (voir image suivante) :

   * Dans le **[!UICONTROL Nouvel alias]** , saisissez le nom d’un alias que vous utiliserez ultérieurement dans la configuration de réplication ; par exemple, **réplication**.
   * Appuyer **[!UICONTROL Fichier KeyStore]**. Accédez au fichier KeyStore fourni par Adobe, sélectionnez-le, puis appuyez sur **[!UICONTROL Ouvrir]**.
   * Dans le champ **[!UICONTROL Mot de passe du fichier KeyStore]**, entrez le mot de passe du fichier KeyStore. Ceci est _not_ le mot de passe KeyStore que vous avez créé à l’étape 5, mais qui est l’Adobe Mot de passe du fichier KeyStore fourni dans le courriel de bienvenue qui vous a été envoyé lors de la mise en service. Contactez le service clientèle Adobe si vous n’avez pas reçu le mot de passe du fichier KeyStore.
   * Dans le **[!UICONTROL Mot de passe de la clé privée]** , saisissez le mot de passe de la clé privée (peut correspondre au mot de passe de la clé privée fourni à l’étape précédente). Adobe vous fournit ce mot de passe de clé privée dans l’e-mail de bienvenue qui vous est envoyé pendant le provisionnement. Contactez le service clientèle Adobe si vous n’avez pas reçu le mot de passe de clé privée.
   * Dans le champ **[!UICONTROL Alias de la clé privée]**, entrez l’alias de la clé privée, par exemple `companyname-alias`. Adobe vous fournit cet alias de clé privée dans l’e-mail de bienvenue qui vous est envoyé pendant le provisionnement. Contactez le service clientèle Adobe si vous n’avez pas reçu d’alias de clé privée.

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. Appuyer **[!UICONTROL Enregistrer et fermer]** pour enregistrer vos modifications pour cet utilisateur.

   Ensuite, vous devez [configurez l’agent de réplication.](#configuring-the-replication-agent)

### Configuration de l’agent de réplication {#configuring-the-replication-agent}

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**.
1. Sur la page Agents sur l’auteur, appuyez sur **[!UICONTROL Réplication des images hybrides Dynamic Media (s7delivery)]**.
1. Appuyez sur **[!UICONTROL Modifier]**.
1. Appuyez sur le bouton **[!UICONTROL Paramètres]** , puis saisissez ce qui suit :

   * **[!UICONTROL Activé]** : cochez cette option pour activer l’agent de réplication.
   * **[!UICONTROL Région]** : indiquez la région appropriée : Amérique du Nord, Europe ou Asie.
   * **[!UICONTROL ID du client]** : il s’agit du nom de votre société/client qui publie du contenu vers le service de réplication. C’est l’ID de client qu’Adobe vous fournit dans l’e-mail de bienvenue qui vous est envoyé lors du provisionnement. Contactez le service clientèle si vous n’avez pas reçu cet.
   * **[!UICONTROL Alias de magasin clé]** - Cette valeur est la même que la valeur** Nouvel alias** définie lors de la génération de la clé dans [Configuration de l’authentification](#setting-up-authentication); par exemple, `replication`. (Reportez-vous à l’étape 7 de la section [Configuration de l’authentification](#setting-up-authentication).)
   * **[!UICONTROL Mot de passe du magasin de clés]** : mot de passe KeyStore créé lorsque vous avez appuyé **[!UICONTROL Créer KeyStore]**. Adobe ne fournit pas ce mot de passe. Reportez-vous à l’étape 5 de la section [Configuration de l’authentification](#setting-up-authentication).

   L’image suivante montre l’agent de réplication avec des exemples de données :

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. Appuyez sur **[!UICONTROL OK]**.

### Validation de l’agent de réplication pour Dynamic Media {#validating-the-replication-agent-for-dynamic-media}

Pour valider l’agent de réplication pour Dynamic Media, procédez comme suit :

Appuyer **[!UICONTROL Tester la connexion]**. Voici un exemple de sortie :

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
Vous pouvez également vérifier en effectuant l’une des opérations suivantes :
* Vérifiez les journaux de réplication pour vous assurer que la ressource est répliquée.
* Publiez une image. Appuyez sur l’image et sélectionnez **[!UICONTROL Visionneuses]** dans le menu déroulant. Sélectionnez un paramètre prédéfini de visionneuse, puis appuyez sur **[!UICONTROL URL]**, puis copiez et collez l’URL dans le navigateur pour vérifier que vous pouvez voir l’image.


### Résolution des problèmes d’authentification {#troubleshooting-authentication}

Lors de la configuration de l’authentification, vous pouvez rencontrer certains problèmes avec leurs solutions. Avant de les vérifier, assurez-vous d’avoir configuré la réplication.

#### Problème : Code d’état HTTP 401 avec message - Autorisation requise {#problem-http-status-code-with-message-authorization-required}

Ce problème peut être dû à l’échec de la configuration du KeyStore pour l’utilisateur `dynamic-media-replication`.

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**Solution**: Vérifiez que la variable `KeyStore` est enregistré dans **[!UICONTROL dynamic-media-replication]** et est fourni avec le mot de passe correct.

#### Problème : Impossible de déchiffrer la clé - Impossible de déchiffrer les données {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**Solution**: Vérifiez le mot de passe. Le mot de passe enregistré dans l’agent de réplication n’est pas le même mot de passe que celui utilisé pour créer le KeyStore.

#### Problème : InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

Ce problème est dû à une erreur de configuration dans votre instance AEM Author. Le processus java sur l’auteur n’obtient pas le bon `javax.net.ssl.trustStore`. Cette erreur s’affiche dans le journal de réplication :

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

Ou le journal des erreurs :

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.
 
java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**Solution**: Assurez-vous que le processus java sur l’auteur AEM possède la propriété système **-Djavax.net.ssl.trustStore=** défini sur un TrustStore valide.

#### Problème : le KeyStore n’est pas configuré ou n’a pas été initialisé. {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

Ce problème peut être dû à un correctif ou à un pack de fonctionnalités qui remplace la fonction **[!UICONTROL dynamic-media-user]** ou **[!UICONTROL keystore]** noeud .

Exemple de journal de réplication :

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**Solution** :

1. Accédez au **[!UICONTROL Gestion des utilisateurs]** page :

   `localhost:4502/libs/granite/security/content/useradmin.html`
1. Sur le **[!UICONTROL Gestion des utilisateurs]** , accédez à la page **[!UICONTROL dynamic-media-replication]** , puis appuyez pour ouvrir.
1. Appuyez sur le bouton **[!UICONTROL KeyStore]** . Si la variable **[!UICONTROL Créer KeyStore]** s’affiche, puis vous devez rétablir les étapes sous [Configuration de l’authentification](#setting-up-authentication) plus tôt.
1. Si vous deviez rétablir la variable **[!UICONTROL KeyStore]** configuration, vous devrez peut-être effectuer les opérations suivantes : [Configuration de l’agent de réplication](config-dynamic.md#configuring-the-replication-agent) encore une fois.

   Reconfigurez l’agent de réplication s7delivery.

   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. Appuyer **[!UICONTROL Tester la connexion]** pour vérifier que la configuration est valide.

#### Problème : l’agent de publication utilise SSL à la place d’OAuth. {#problem-publish-agent-is-using-ssl-instead-of-oauth}

Ce problème peut être dû à un correctif ou à un Feature Pack qui ne s’est pas installé correctement ou qui a écrasé les paramètres.

Exemple de log de réplication :

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**Solution :**

1. Dans AEM, appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.

   `localhost:4502/crx/de/index.jsp`

1. Accédez au **[!UICONTROL Agent de réplication s7delivery]** noeud .

   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. Ajoutez ce paramètre à l’agent de réplication (Booléen avec la valeur **[!UICONTROL True]**) :

   `enableOauth=true`

1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Enregistrer tout]**.

### Test de votre configuration {#testing-your-configuration}

Adobe vous recommande d’effectuer un test complet de la configuration :

Assurez-vous d’avoir déjà effectué les opérations suivantes avant de commencer ce test :

* Ajout de paramètres d’image prédéfinis.
* Configurer **Configuration de Dynamic Media (version antérieure à 6.3)** under **[!UICONTROL Cloud Services]**. L’URL du service d’images est requise pour ce test.

Pour tester votre configuration :

1. Téléchargez une ressource image. (Dans Assets, appuyez sur **[!UICONTROL Créer > Fichiers]** et sélectionnez le fichier.)
1. Attendez que le workflow se termine.
1. Publiez la ressource image. (Sélectionnez la ressource et appuyez sur **[!UICONTROL Publication rapide]**.)
1. Accédez aux rendus de cette image en ouvrant l’image et en appuyant sur **[!UICONTROL Rendus]**.

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. Sélectionnez n’importe quel rendu dynamique.
1. Appuyer **[!UICONTROL URL]** pour obtenir l’URL de cette ressource.
1. Accédez à l’URL sélectionnée et vérifiez si l’image se comporte comme prévu.

Une autre manière de tester la diffusion de vos ressources consiste à ajouter req=exists à votre URL.

## Configuration des Cloud Services Dynamic Media {#configuring-dynamic-media-cloud-services}

Le service Cloud Dynamic Media prend en charge les services cloud tels que la publication et la diffusion hybrides d’images et de vidéos, d’analyses vidéo et de codage vidéo, entre autres.

Dans le cadre de la configuration, vous devez saisir un ID d’enregistrement, une URL de service vidéo, une URL de service d’images, une URL de service de réplication et configurer l’authentification. Vous devez avoir reçu toutes ces informations dans le cadre du processus de configuration du compte. Si vous n’avez pas reçu ces informations, contactez votre administrateur Adobe Experience Manager ou votre support technique d’Adobe pour obtenir ces informations.

>[!NOTE]
Avant de configurer les services cloud Dynamic Media, assurez-vous d’avoir configuré l’instance de publication. Vous devez également configurer la réplication avant de configurer les services cloud Dynamic Media.

**Pour configurer les services cloud Dynamic Media**:

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Cloud Services > Configuration Dynamic Media (version antérieure à 6.3)]**.
1. Sur le **[!UICONTROL Explorateur de configuration Dynamic Media]** , dans le volet de gauche, sélectionnez **[!UICONTROL global]**, puis appuyez sur **[!UICONTROL Créer]**.
1. Dans le **[!UICONTROL Création d’une configuration Dynamic Media]** , dans la boîte de dialogue **[!UICONTROL Titre]** , saisissez un titre.
1. Si vous configurez Dynamic Media pour la vidéo :

   * dans le champ **[!UICONTROL ID d’enregistrement]**, entrez votre ID d’enregistrement ;
   * dans le champ **[!UICONTROL URL du service vidéo]**, entrez l’URL du service vidéo pour la passerelle Dynamic Media.

1. Si vous configurez Dynamic Media pour l’imagerie, dans la variable **[!UICONTROL URL du service d’images]** , saisissez l’URL du service d’image pour la passerelle Dynamic Media.
1. Appuyer **[!UICONTROL Enregistrer]** pour revenir à la page du navigateur de configuration de Dynamic Media.
1. Appuyez sur le logo AEM pour accéder à la console de navigation globale.

## Configuration des rapports vidéo {#configuring-video-reporting}

Vous pouvez configurer les rapports vidéo pour plusieurs installations d’AEM à l’aide du mode hybride de Dynamic Media.

**Quand utiliser :** Au moment de la configuration **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]**, de nombreuses fonctionnalités sont lancées, notamment la création de rapports vidéo. La configuration crée une suite de rapports dans une entreprise Analytics régionale. Si vous configurez plusieurs nœuds Auteur, vous créez une suite de rapport séparée pour chacun. Par conséquent, les données de rapport sont incohérentes entre les installations. En outre, si chaque nœud Auteur se réfère au même serveur Hybrid Publish, la dernière installation Auteur modifie la suite de rapports de destination pour tous les rapports vidéo. Ce problème surcharge le système d’analyses avec de trop nombreuses suites de rapports.

**Prise en main :** Configurez les rapports vidéo en effectuant les trois tâches suivantes.

1. Créez un [!DNL Video Analytics] préconfigurer le module après la configuration **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]** sur le premier noeud Auteur. Cette première tâche est importante car elle permet à une nouvelle configuration de continuer à utiliser la même suite de rapports.
1. Installez le [!DNL Video Analytics] paramètre prédéfini le module à n’importe quel ***new*** Noeud Auteur ***before*** vous configurez la configuration de Dynamic Media (version antérieure à 6.3).

1. Vérifiez et déboguez l’installation du package.

### Création d’un [!DNL Video Analytics] module prédéfini après la configuration du premier noeud Auteur {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

Une fois cette tâche terminée, vous disposez d’un fichier de package contenant le [!DNL Video Analytics] paramètres prédéfinis. Ces paramètres prédéfinis contiennent une suite de rapports, le serveur de suivi, l’espace de noms de suivi et l’ID d’organisation de Marketing Cloud, le cas échéant.

1. Si vous ne l’avez pas déjà fait, configurez **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]**.
1. (Facultatif) Affichez et copiez la variable **[!UICONTROL Identifiant de suite de rapports]** (vous devez avoir accès au JCR). Lors de la **[!UICONTROL Identifiant de suite de rapports]** n’est pas obligatoire, cela facilite la validation.
1. Créez un package à l’aide de **[!UICONTROL Gestionnaire de modules]**.
1. Editez le package pour inclure un filtre.

   En AEM : `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. Créez le package.
1. Téléchargez ou partagez le [!DNL Video Analytics] préconfigurer le module afin qu’il puisse être partagé avec les nouveaux noeuds d’auteur suivants.

### Installation de la variable [!DNL Video Analytics] préconfigurer le module avant de configurer des noeuds d’auteur supplémentaires {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

Assurez-vous d’avoir effectué cette tâche _avant_**[!UICONTROL de paramétrer la Configuration Dynamic Media (version antérieure à 6.3)]**. Ignorer cette étape résultera en la création d’une autre suite de rapports non utilisée. En outre, même si les rapports vidéo continueront à fonctionner correctement, la collecte des données n’est pas optimisée.

Assurez-vous que la variable [!DNL Video Analytics] Le module prédéfini du premier noeud Auteur est accessible sur le nouveau noeud Auteur .

1. Téléchargez le [!DNL Video Analytics] module prédéfini que vous avez créé précédemment pour **[!UICONTROL Gestionnaire de modules]**.
1. Installez le [!DNL Video Analytics] module prédéfini.
1. Configurer **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]**.

### Vérification et débogage de l’installation du package {#verifying-and-debugging-the-package-installation}

1. Effectuez l’une des actions suivantes et, si nécessaire, déboguez l’installation du package :

   * **Vérifiez les [!DNL Video Analytics] prédéfini par le biais du JCR**
Pour vérifier la variable [!DNL Video Analytics] prédéfini au moyen du JCR, vous devez avoir accès à **[!UICONTROL CRXDE Lite]**.

      AEM - Dans **[!UICONTROL CRXDE Lite]**, accédez à `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata  `

      C&#39;est tout. `http://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

      Si vous n’avez pas accès à **[!UICONTROL CRXDE Lite]** sur le noeud Auteur, vous pouvez vérifier le paramètre prédéfini via le serveur de publication.

   * **Vérifiez les [!DNL Video Analytics] paramètre prédéfini via le serveur d’images**

      Vous pouvez valider la variable [!DNL Video Analytics] paramètre prédéfini directement à l’aide d’un serveur d’images `req=userdata` requête.

      Par exemple, pour afficher la variable [!DNL Video Analytics] sur le noeud Auteur , vous pouvez effectuer la requête suivante :

      `http://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

      Pour valider le paramètre prédéfini sur les serveurs de publication, vous pouvez adresser une requête directe similaire sur le serveur de publication. La réponse est la même sur les nœuds d’auteur et de publication. La réponse ressemble à ce qui suit :

      ```
      marketingCloudOrgId=0FC4E86B573F99CC7F000101
       reportSuite=aemaem6397618-2018-05-23
       trackingNamespace=aemvideodal
       trackingServer=aemvideodal.d2.sc.omtrdc.net
      ```

   * **Vérifiez les [!DNL Video Analytics] paramètre prédéfini par le biais de l’outil de création de rapports vidéo dans AEM**

      Appuyer **[!UICONTROL Outils > Ressources > Rapports vidéo]** `http://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

      Si le message d’erreur suivant s’affiche, la suite de rapports est disponible, mais non renseignée. Cette erreur est normale (et voulue) dans une nouvelle installation, avant que le système ne collecte des données.

      ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)
   Pour générer des données de rapport, téléchargez et publiez une vidéo. Utilisation **[!UICONTROL Copier l’URL]** et exécutez la vidéo au moins une fois.

   Gardez à l’esprit que cela peut prendre jusqu’à 12 heures avant que les données de rapport ne soient renseignées à partir de l’utilisation de la visionneuse vidéo.

   Si une erreur survient et que la suite de rapports n’est pas configurée correctement, l’avertissement suivant s’affiche.

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   Cette erreur s’affiche également si la création de rapports vidéo est exécutée avant la configuration. **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]** services.

### Résolution des problèmes de configuration des rapports vidéo {#troubleshooting-the-video-reporting-configuration}

* Pendant l’installation, les connexions au serveur API Analytics expirent. L’installation tente de relancer la connexion 20 fois, mais échoue toujours. Dans ce cas, le fichier journal enregistre plusieurs erreurs. Recherchez `SiteCatalystReportService`.
* Ne pas installer le [!DNL Video Analytics] le module prédéfini peut d’abord entraîner la création d’une suite de rapports.
* Mise à niveau d’AEM 6.3 vers AEM 6.4 ou 6.4.1, puis configuration **[!UICONTROL Configuration de Dynamic Media (version antérieure à 6.3)]**, crée toujours une suite de rapports. Ce problème est connu et devrait être corrigé pour AEM 6.4.2.

### À propos de [!DNL Video Analytics] paramètre prédéfini {#about-the-video-analytics-preset}

Le [!DNL Video Analytics] preset, parfois appelé simplement paramètre d’analyse prédéfini, est stocké en regard des paramètres prédéfinis de la visionneuse dans Dynamic Media. Il s’agit essentiellement de la même chose qu’un paramètre prédéfini de visionneuse, mais avec les informations utilisées pour configurer les rapports AppMeasurement et Video Heartbeat.

Les propriétés du paramètre prédéfini sont les suivantes :

* **[!UICONTROL reportSuite]**
* **[!UICONTROL trackingServer]**
* **[!UICONTROL trackingNamespace]**
* **[!UICONTROL marketingCloudOrgId]** (non présent dans les anciennes versions AEM)

AEM 6.4 et les versions plus récentes enregistrent ce paramètre prédéfini à l’adresse `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

## Réplication des paramètres du catalogue {#replicating-catalog-settings}

Vous devez publier vos propres paramètres de catalogue par défaut dans le cadre du processus de configuration via JCR. Pour répliquer les paramètres de catalogue :

1. Dans une fenêtre de terminal, exécutez ce qui suit :

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. Dans AEM, accédez à l’emplacement suivant dans **[!UICONTROL CRXDE Lite]** (nécessite des privilèges d’administrateur) :

   `https://<server>:<port>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. Appuyez sur le bouton **[!UICONTROL Réplication]** .
1. Appuyer **[!UICONTROL Répliquer]**.

## Réplication des paramètres prédéfinis de la visionneuse {#replicating-viewer-presets}

Pour diffuser une ressource avec un paramètre prédéfini de visionneuse, vous devez répliquer/publier le paramètre prédéfini de la visionneuse. (Tous les paramètres prédéfinis de la visionneuse doivent être activés _et_ répliqués pour obtenir l’URL ou le code intégré d’une ressource.) Voir [Publication de paramètres prédéfinis de visionneuse](managing-viewer-presets.md#publishing-viewer-presets) pour plus d’informations.

>[!NOTE]
Par défaut, le système affiche divers rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** et divers paramètres prédéfinis de visionneuse lorsque vous sélectionnez **[!UICONTROL Visionneuses]** dans la vue détaillée de la ressource. Vous pouvez augmenter ou diminuer le nombre affiché. Voir [Augmentation du nombre de paramètres d’image prédéfinis affichés](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) ou [Augmentation du nombre de paramètres prédéfinis de visionneuse qui s’affichent](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

## Filtrage des ressources pour la réplication {#filtering-assets-for-replication}

Dans les déploiements autres que Dynamic Media, vous effectuez une réplication. _all_ ressources (images et vidéo) de votre environnement de création AEM au noeud de publication AEM. Ce workflow est nécessaire, car les serveurs de publication AEM diffusent également les ressources.

Toutefois, dans les déploiements Dynamic Media, dans la mesure où les ressources sont diffusées par le biais du cloud, il n’est pas nécessaire de répliquer ces mêmes ressources sur AEM noeuds de publication. Un tel workflow de publication hybride permet d’éviter le coût d’un stockage supplémentaire et réduit les temps de traitement pour la réplication des ressources. D’autres contenus, tels que les visionneuses Dynamic Media, les pages du site et le contenu statique, continuent d’être diffusés à partir des noeuds de publication AEM.

D’autres éléments, qui ne sont pas des ressources, sont également répliqués :

* Configuration de diffusion Dynamic Media : `/conf/global/settings/dam/dm/imageserver/configuration/jcr:content/settings`
* Paramètres d’image prédéfinis : `/conf/global/settings/dam/dm/presets/macros`
* Paramètres prédéfinis de la visionneuse : `/conf/global/settings/dam/dm/presets/viewer`

Les filtres vous permettent de _exclude_ ressources de réplication vers le noeud de publication AEM.

### Utilisation des filtres de ressources par défaut pour la réplication {#using-default-asset-filters-for-replication}

Si vous utilisez Dynamic Media pour 1) l’imagerie en production _ou_ 2) l’imagerie et la vidéo, puis vous pouvez utiliser les filtres par défaut que nous fournissons en l’état. Les filtres suivants sont activés par défaut :

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filtrer</strong></td> 
   <td><strong>Type de MIME</strong></td> 
   <td><strong>Rendus</strong></td> 
  </tr> 
  <tr> 
   <td>Diffusion d’image Dynamic Media</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td> 
   <td><p>Commence par <strong>image/</strong></p> <p>Contient <strong>application/</strong> et se termine par <strong>set</strong>.</p> </td> 
   <td>Les « filter-images » d’usine (s’applique aux ressources d’images uniques, y compris aux images interactives) et les « filter-sets » (s’applique aux visionneuses à 360°, aux visionneuses de supports variés et aux visionneuses de carrousel) : 
    <ul> 
     <li>ajoutent des images et des métadonnées PTIFF pour la réplication (tout rendu commençant par <strong>cqdam</strong>) ;</li> 
     <li>suppriment de la réplication l’image d’origine et les rendus d’image statiques.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Diffusion vidéo Dynamic Media</td> 
   <td>filter-video</td> 
   <td>Commence par <strong>video/</strong></td> 
   <td>La « filter-video » d’usine : 
    <ul> 
     <li>comprend des rendus vidéo proxy, des images de miniatures/d’affiche vidéo, des métadonnées (à la fois pour les rendus vidéo et vidéo parents) pour la réplication (tout rendu commençant par <strong>cqdam</strong>) ;</li> 
     <li>exclue de la réplication la vidéo d’origine et les rendus de miniatures statiques.<br /> <br /> <strong>Remarque :</strong> les rendus de vidéo en mode proxy ne contiennent pas de données binaires, et ne sont en fait que des propriétés de nœud. Ils n’affectent donc pas la taille du référentiel de l’éditeur.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Intégration Dynamic Media Classic</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p>filter-video</p> </td> 
   <td><p>Commence par <strong>image/</strong></p> <p>Contient <strong>application/</strong> et se termine par <strong>set</strong>.</p> <p>Commence par <strong>video/</strong></p> </td> 
   <td><p>Vous configurez l’URI de transport pour qu’il pointe vers votre serveur de publication AEM au lieu de l’URL du service de réplication cloud Dynamic Media Adobe. La configuration de ce filtre permet à Dynamic Media Classic de diffuser des ressources au lieu de l’instance de publication AEM.</p> <p>Les « filter-images », « filter-sets » et « filter-video » prêts à l’emploi :</p> 
    <ul> 
     <li>ajoutent des images PTIFF, des rendus vidéo proxy et des métadonnées pour la réplication. Cependant, puisqu’ils n’existent pas dans le JCR pour ceux qui exécutent AEM intégration Dynamic Media Classic, il ne fait rien.</li> 
     <li>suppriment de la réplication l’image d’origine et les rendus d’image statiques, les vidéos d’origine et les rendus de miniature statiques. Au lieu de cela, Dynamic Media Classic diffuse des ressources image et vidéo.</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
Les filtres s’appliquent aux types MIME et ne peuvent pas être spécifiques au chemin.

### Configuration des filtres de ressources pour les déploiements vidéo uniquement {#setting-up-asset-filters-for-video-only-deployments}

Si vous utilisez Dynamic Media pour la vidéo uniquement, suivez les étapes suivantes pour configurer les filtres de ressource pour la réplication :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**.
1. Sur la page Agents sur l’auteur, appuyez sur **[!UICONTROL Agent par défaut (publication)]**.
1. Appuyez sur **[!UICONTROL Modifier]**.
1. Dans la boîte de dialogue **[!UICONTROL Paramètres d’agent]**, sous l’onglet [!UICONTROL Paramètres], cochez l’option **[!UICONTROL Activé]** pour activer l’agent.
1. Appuyez sur **[!UICONTROL OK]**.
1. Dans AEM, appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.
1. Dans l’arborescence de gauche, accédez à `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`.
1. Localiser [!UICONTROL filter-video], cliquez dessus avec le bouton droit et sélectionnez **[!UICONTROL Copier]**.
1. Dans l’arborescence de gauche, accédez à `/etc/replication/agents.author/publish`.
1. Localiser [!UICONTROL jcr:content], cliquez dessus avec le bouton droit et sélectionnez **[!UICONTROL Coller]**.

Cela permet de configurer l’instance de publication AEM pour diffuser l’image d’affiche vidéo ainsi que les métadonnées vidéo requises pour la lecture, tandis que la vidéo elle-même est diffusée par le service cloud Dynamic Media. Le filtre exclut également de la réplication les rendus vidéo et miniatures statiques d’origine, qui ne sont pas nécessaires sur l’instance de publication.

### Configuration des filtres de ressources pour l’imagerie dans les déploiements hors production {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

Si vous utilisez Dynamic Media pour les images dans des déploiements hors exploitation, suivez les étapes suivantes pour configurer les filtres de ressource pour la réplication :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**.
1. Sur la page Agents sur l’auteur, appuyez sur **[!UICONTROL Agent par défaut (publication)]**.
1. Appuyez sur **[!UICONTROL Modifier]**.
1. Dans la boîte de dialogue **[!UICONTROL Paramètres d’agent]**, sous l’onglet **[!UICONTROL Paramètres]**, cochez l’option **[!UICONTROL Activé]** pour activer l’agent.
1. Appuyez sur **[!UICONTROL OK]**.
1. Dans AEM, appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.
1. Dans l’arborescence de gauche, accédez à `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`.

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. Localiser **[!UICONTROL filter-images]**, cliquez dessus avec le bouton droit et sélectionnez **[!UICONTROL Copier]**.
1. Dans l’arborescence de gauche, accédez à `/etc/replication/agents.author/publish`.
1. Localiser **[!UICONTROL jcr:content]**, cliquez dessus avec le bouton droit et sélectionnez **[!UICONTROL Créer > Créer un noeud]**. Saisissez le nom `damRenditionFilters` de type `nt:unstructured`.
1. Localiser [!UICONTROL `damRenditionFilters`], cliquez dessus avec le bouton droit et sélectionnez **[!UICONTROL Coller]**.

Cela permet de configurer l’instance de publication AEM pour diffuser les images dans votre environnement hors production. Le filtre exclut également de la réplication l’image d’origine et les rendus statiques, qui ne sont pas nécessaires sur l’instance de publication.

>[!NOTE]
S’il existe de nombreux filtres dans un auteur, chaque agent nécessite qu’un autre utilisateur lui soit attribué. Le code granite applique un modèle de filtre par utilisateur. Disposez toujours d’un utilisateur différent pour chaque configuration de filtre.
Si vous utilisez plusieurs filtres sur un serveur (par exemple, un filtre pour la publication de réplication et un second filtre pour s7delivery), vous devez vous assurer que ces deux filtres ont un **userId** qui leur sont affectées dans la fonction **[!UICONTROL jcr:content]** noeud . Voir l’image suivante :

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### Personnalisation des filtres de ressources pour la réplication {#customizing-asset-filters-for-replication}

Pour personnaliser éventuellement les filtres de ressources en vue de la réplication :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.
1. Dans l’arborescence de gauche, accédez à `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters` pour parcourir les filtres.

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. Pour définir le type MIME du filtre, vous pouvez localiser le type MIME comme suit :

   Dans le rail de gauche, développez **[!UICONTROL content > dam > &lt;`locate_your_asset`> > jcr:content > métadonnées]**, puis dans le tableau, recherchez `dc:format`.

   L’illustration ci-dessous est un exemple de chemin d’une ressource vers `dc:format`.

   ![chlimage_1-512](assets/chlimage_1-512.png)

   Notez que la valeur `dc:format` de la ressource `Fiji Red.jpg` est `image/jpeg`.

   Pour appliquer ce filtre à toutes les images, quel que soit leur format, définissez la valeur sur `image/*` où `*` est une expression régulière qui est appliquée à toutes les images de n’importe quel format.

   Pour appliquer le filtre uniquement aux images de type JPEG, saisissez la valeur `image/jpeg`.

1. Définissez les rendus à inclure ou à exclure de la réplication.

   Voici des exemples de caractères que vous pouvez utiliser afin de filtrer la réplication :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Caractère à utiliser</strong></td> 
   <td><strong>Filtrage des ressources pour la réplication</strong></td> 
  </tr> 
  <tr> 
   <td>*</td> 
   <td>Caractère générique<br /> </td> 
  </tr> 
  <tr> 
   <td>+</td> 
   <td>Inclure les ressources à répliquer.</td> 
  </tr> 
  <tr> 
   <td>-</td> 
   <td>Exclure les ressources de la réplication.</td> 
  </tr> 
 </tbody> 
</table>

Accédez à `content/dam/<locate_your_asset>/jcr:content/renditions`.

L’illustration ci-dessous est un exemple de rendu d’une ressource.

![chlimage_1-513](assets/chlimage_1-513.png)

Dans l’exemple ci-dessus, pour ne répliquer que l’image PTIFF (image TIFF pyramidale), il vous faudrait entrer `+cqdam,*` qui inclut tous les rendus commençant par `cqdam`. Dans l’exemple, ce rendu est `cqdam.pyramid.tiff`.

Si vous souhaitez uniquement répliquer l’original, vous devez entrer `+original`.

## Configuration des paramètres du serveur d’images Dynamic Media {#configuring-dynamic-media-image-server-settings}

La configuration de Dynamic Media Image Server implique la modification du lot Adobe CQ Scene7 ImageServer et du lot Adobe CQ Scene7 PlatformServer.

>[!NOTE]
Dynamic Media est opérationnel [dès son activation](#enabling-dynamic-media). Cependant, vous pouvez éventuellement choisir d’affiner votre installation en configurant Dynamic Media Image Server afin de répondre à certaines spécifications ou exigences.

**Condition requise**: _Avant_ Si vous configurez Dynamic Media Image Server, assurez-vous que votre machine virtuelle Windows comprend une installation des bibliothèques Visual C++ Microsoft. Les bibliothèques sont nécessaires pour exécuter le serveur d’images Dynamic Media. Vous pouvez [Téléchargez le package redistribuable Microsoft Visual C++ 2010 (x64) ici](https://www.microsoft.com/fr-fr/download/details.aspx?id=26999).

**Pour configurer les paramètres du serveur d’images Dynamic Media**:

1. Dans le coin supérieur gauche de l’AEM, appuyez sur **[!UICONTROL Adobe Experience Manager]** pour accéder à la console de navigation globale, appuyez sur **[!UICONTROL Outils > Opérations > Console web]**.
1. Sur le **[!UICONTROL Configuration de la console web Adobe Experience Manager]** page, appuyez sur **[!UICONTROL OSGi > Configuration]** pour répertorier tous les lots en cours d’exécution dans AEM.

   Les serveurs de diffusion Dynamic Media sont répertoriés dans la liste sous les noms suivants :

   * **[!UICONTROL Adobe CQ Scene7 ImageServer]**
   * **[!UICONTROL Adobe CQ Scene7 PlatformServer]**

1. Dans la liste des lots, à droite de **[!UICONTROL Adobe CQ Scene7 ImageServer]**, appuyez sur le bouton **[!UICONTROL Modifier]** icône .
1. Dans le **[!UICONTROL Adobe CQ Scene7 ImageServer]** , définissez les valeurs de configuration suivantes :

   >[!NOTE]
   Dans la plupart des cas, il n’est pas nécessaire de modifier les valeurs par défaut. Cependant, si vous modifiez les valeurs par défaut, vous devez redémarrer le lot pour que les modifications soient prises en compte.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriété</strong></td> 
   <td><strong>Valeur par défaut</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>TcpPort.name</td> 
   <td><code><em>empty</em></code></td> 
   <td>Numéro de port à utiliser pour les communications avec le processus ImageServer. Le port disponible par défaut est automatiquement détecté.</td> 
  </tr> 
  <tr> 
   <td>AllowRemoteAccess.name</td> 
   <td><code><em>empty</em></code></td> 
   <td><p>Autorise ou refuse l’accès à distance au processus ImageServer. En cas de refus, le serveur d’images écoute uniquement sur le localhost.</p> <p>Les paramètres de l’externaliseur par défaut qui pointent vers localhost doivent spécifier le domaine ou l’adresse IP réel de l’instance VM spécifique. La raison en est que le localhost peut pointer vers le système parent de la machine virtuelle.</p> <p>Les domaines ou adresses IP de la machine virtuelle peuvent avoir besoin d’une entrée de fichier hôte pour pouvoir se résoudre.</p> </td> 
  </tr> 
  <tr> 
   <td>MaxRenderRgnPixels</td> 
   <td>16 MPixels</td> 
   <td>Taille maximale du rendu, en mégapixels.</td> 
  </tr> 
  <tr> 
   <td>MaxMessageSize</td> 
   <td>16 Mo</td> 
   <td>Taille maximale du message envoyé, en mégaoctets.</td> 
  </tr> 
  <tr> 
   <td>RandomAccessUrlTimeout</td> 
   <td>20</td> 
   <td>Délai d’expiration pour la durée (en secondes) pendant laquelle ImageServer attend que le JCR réponde à une demande de mosaïque de plage.</td> 
  </tr> 
  <tr> 
   <td>WorkerThreads</td> 
   <td>10</td> 
   <td>Nombre de threads de traitement.</td> 
  </tr> 
 </tbody> 
</table>

1. Appuyez sur **[!UICONTROL Enregistrer]**.
1. Dans la liste des lots, à droite de **[!UICONTROL Adobe CQ Scene7 PlatformServer]**, appuyez sur le bouton **[!UICONTROL Modifier]** icône .
1. Dans le **[!UICONTROL Adobe CQ Scene7 PlatformServer]** , définissez les options de valeur par défaut suivantes :

   >[!NOTE]
   Le serveur d’images Dynamic Media utilise son propre cache sur disque pour mettre les réponses en mémoire cache. Le cache HTTP AEM et le dispatcher ne peuvent pas être utilisés pour mettre en cache les réponses du serveur d’images Dynamic Media.

   | **Propriété** | **Valeur par défaut** | **Description** |
   |---|---|---|
   | **[!UICONTROL Cache enabled]** | Cochée | Indique si le cache de réponse est activé ou non. |
   | **[!UICONTROL Cache roots]** | cache | Un ou plusieurs chemins d’accès aux dossiers du cache de réponse. Les chemins d’accès relatifs sont résolus par rapport au dossier de lot s7imagerie interne. |
   | **[!UICONTROL Taille max. du cache]** | 200000000 | Taille maximale du cache de réponse en octets. |
   | **[!UICONTROL Cache Max Entries]** | 100 000 | Nombre maximal d’entrées autorisées dans le cache. |

### Paramètres du manifeste par défaut {#default-manifest-settings}

Le manifeste par défaut vous permet de configurer les valeurs par défaut qui sont utilisées pour générer les réponses du service de diffusion Dynamic Media. Vous pouvez affiner la qualité (qualité du JPEG, résolution, mode de rééchantillonnage), la mise en cache (expiration) et empêcher le rendu des images trop volumineuses (defaultpix, defaultthumbpix, maxpix).

La localisation de la configuration du manifeste par défaut est basée sur la valeur par défaut de la **[!UICONTROL Racine de catalogue]** du lot **[!UICONTROL Adobe CQ Scene7 PlatformServer]**. Par défaut, cette valeur se trouve à l’emplacement suivant dans **[!UICONTROL Outils > Général > CRXDE Lite]**:

`/conf/global/settings/dam/dm/imageserver/`

![configimageservercrxdelite](assets/configimageservercrxdelite.png)

Vous pouvez modifier les valeurs des propriétés décrites dans le tableau ci-dessous en saisissant de nouvelles valeurs.

Lorsque vous avez terminé d’apporter des modifications au manifeste par défaut, dans le coin supérieur gauche de la page, appuyez sur . **[!UICONTROL Enregistrer tout]**.

Assurez-vous d’appuyer sur le bouton **[!UICONTROL Contrôle d’accès]** (à droite du **[!UICONTROL Propriétés]** ), puis définissez les privilèges de contrôle d’accès sur `jcr:read` pour tous les utilisateurs et les utilisateurs de la réplication Dynamic Media.

![configimageservercrxdeliteAccoltab](assets/configimageservercrxdeliteaccesscontroltab.png)

Tableau des paramètres du manifeste et leurs valeurs par défaut :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriété</strong></td> 
   <td><strong>Valeur par défaut</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>bkgcolor</td> 
   <td>FFFFFF</td> 
   <td><p>Couleur d’arrière-plan par défaut. La valeur RVB est utilisée pour remplir toutes les zones d’une image de réponse qui ne contiennent aucune donnée d’image actuelle.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html?lang=fr">BkgColor</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>defaultpix</td> 
   <td>300,300</td> 
   <td><p>Taille d’affichage par défaut. Le serveur oblige les images de réponse à ne pas dépasser cette largeur et cette hauteur si la requête ne spécifie pas la taille d’affichage explicitement à l’aide de wid=, hei= ou scl=.</p> <p>Spécifiée sous la forme de deux nombres entiers de valeur supérieure ou égale à zéro, séparés par une virgule. Largeur et hauteur en pixels. L’une ou l’autre des valeurs (ou les deux) peuvent être définies sur 0 pour ne pas être contraintes. Ne s’applique pas aux requêtes imbriquées/intégrées.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html?lang=fr">DefaultPix</a> dans l’API du service d’images.</p> <p>Habituellement, cependant, vous utilisez un paramètre de visionneuse ou d’image prédéfini pour fournir la ressource. Defaultpix ne s’applique qu’à une ressource qui n’utilise pas de paramètre de visionneuse ou d’image prédéfini.</p> </td> 
  </tr> 
  <tr> 
   <td>defaultthumbpix</td> 
   <td>100,100</td> 
   <td><p>Taille de miniature par défaut. Utilisé à la place d’attribute::DefaultPix pour les demandes de miniature (req=tmb).</p> <p>Le serveur oblige les images de réponse à ne pas dépasser cette largeur et cette hauteur si une demande de miniature (req=tmb) ne spécifie pas explicitement la taille d’affichage à l’aide de wid=, hei= ou scl=.</p> <p>Spécifiée sous la forme de deux nombres entiers de valeur supérieure ou égale à zéro, séparés par une virgule. Largeur et hauteur en pixels. L’une ou l’autre des valeurs (ou les deux) peuvent être définies sur 0 pour ne pas être contraintes. </p> <p>Ne s’applique pas aux requêtes imbriquées/intégrées.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html?lang=fr">DefaultThumbPix</a> dans l’API du service d’images. </p> </td> 
  </tr> 
  <tr> 
   <td>expiration</td> 
   <td>36000000</td> 
   <td><p>Délai d’activation du cache client par défaut. Fournit un intervalle d’expiration par défaut au cas où un enregistrement de catalogue particulier ne contiendrait pas de valeur catalog::Expiration valide.</p> <p>Nombre réel, supérieur ou égal à zéro. Nombre de millisecondes avant expiration depuis la génération des données de réponse. Définissez la valeur sur zéro pour que l’image de réponse expire immédiatement, ce qui permet de désactiver efficacement la mise en cache de client. Par défaut, cette valeur est définie sur 10 heures, ce qui signifie que si une nouvelle image est publiée, il faut 10 heures pour que l’ancienne image quitte le cache de l’utilisateur. Contactez le service clientèle si vous avez besoin que la mémoire cache soit effacée plus rapidement.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html?lang=fr">Expiration</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>jpegquality</td> 
   <td>80</td> 
   <td><p>Attributs de codage du JPEG par défaut. Indique l’attribut par défaut des images de réponse au format JPEG.</p> <p>Nombre entier et indicateur, séparés par une virgule. La première valeur est comprise dans la plage 1..100 et définit la qualité. La seconde valeur peut être 0 pour le comportement normal, ou 1 pour désactiver le sous-échantillonnage chromatique RGB généralement utilisé par les encodeurs JPEG.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html?lang=fr">JpegQuality</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>maxpix</td> 
   <td>2000,2000</td> 
   <td><p>Renvoie la limite de taille des images. Largeur et hauteur maximales de l’image de réponse renvoyée au client.</p> <p>Le serveur renvoie une erreur si une requête provoque la création d’une image de réponse dont la largeur ou la hauteur est plus importante que la valeur d’attribute::MaxPix.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html?lang=fr">MaxPix</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>resmode</td> 
   <td>NET2</td> 
   <td><p>Mode de rééchantillonnage par défaut. Indique les attributs de rééchantillonnage et d’interpolation par défaut à utiliser pour le dimensionnement des données d’image.</p> <p>Utilisé lorsque resMode= n’est pas spécifié dans une requête.</p> <p>Les valeurs autorisées sont les suivantes : BILIN, BICUB ou SHARP2.</p> <p>Enum. Définissez cette variable sur 2 pour bilin, 3 pour bicub ou 4 pour le mode d’interpolation sharp2. Utilisez sharp2 pour obtenir de meilleurs résultats.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html?lang=fr">ResMode</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>resolution</td> 
   <td>72</td> 
   <td><p>Résolution d’objet par défaut. Fournit une résolution d’objet par défaut au cas où un enregistrement de catalogue particulier ne contiendrait pas de valeur catalog::Resolution valide.</p> <p>Nombre réel, supérieur à 0. Généralement exprimé en pixels par pouce, mais peut également se trouver dans d’autres unités, telles que les pixels par mètre.</p> <p>Consultez également la section <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html">Résolution</a> dans l’API du service d’images.</p> </td> 
  </tr> 
  <tr> 
   <td>thumbnailtime</td> 
   <td>1%,11%,21%,31%,41%,51%,61%,71%,81%,91%</td> 
   <td>Ces valeurs représentent un instantané du temps de lecture de la vidéo et sont transférées à <a href="https://encoding.com/">encoding.com</a>. Voir <a href="/help/assets/video.md#about-video-thumbnails">À propos des miniatures vidéo</a> pour plus d’informations.</td> 
  </tr> 
 </tbody> 
</table>

## Configuration de la gestion des couleurs Dynamic Media {#configuring-dynamic-media-color-management}

La gestion des couleurs Dynamic Media vous permet de corriger les couleurs des ressources pour la prévisualisation.

Avec la correction des couleurs, les ressources ingérées conservent leur espace colorimétrique (RGB, CMJN, gris) et leur profil de couleur intégré dans le rendu de TIFF pyramidal généré. Lorsque vous demandez un rendu dynamique, la couleur de l’image est corrigée dans l’espace colorimétrique cible. Vous configurez le profil colorimétrique de sortie dans les paramètres de publication Dynamic Media dans le JCR.

La gestion des couleurs d’Adobe utilise des profils ICC, un format défini par l’International Color Consortium (ICC).

Vous pouvez configurer la gestion des couleurs Dynamic Media et les paramètres d’image prédéfinis à l’aide de la sortie CMJN, RGB ou Gris. Reportez-vous à la section [Configuration des paramètres d’image prédéfinis](managing-image-presets.md).

Les cas d’utilisation avancés peuvent utiliser une configuration manuelle **[!UICONTROL icc=]** pour sélectionner explicitement un profil de couleurs de sortie :

* **[!UICONTROL icc]** - [Profil colorimétrique de sortie.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html?lang=fr)

* **[!UICONTROL iccEmbed]** - [Profil colorimétrique intégré.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html?lang=fr)

>[!NOTE]
L’ensemble standard de profils colorimétriques d’Adobe n’est disponible que si vous disposez des [Feature Pack 12445 de la distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445) installé. Tous les packs de fonctionnalité et de service sont disponibles dans la [distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Le Feature Pack 12445 fournit les profils de couleurs d’Adobe.

### Installation du Feature Pack 12445 {#installing-feature-pack}

Vous devez installer le Feature Pack 12445 pour utiliser les fonctionnalités de gestion des couleurs de Dynamic Media.

**Pour installer le Feature Pack 12445**:

1. Accédez à [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) et télécharger `cq-6.3.0-featurepack-12445`.

   Pour plus d’informations sur l’utilisation des packages dans [!DNL Adobe Experience Manager], consultez [Utilisation des packages](/help/sites-administering/package-manager.md).

1. Installez le Feature Pack.

### Configuration des profils de couleurs par défaut {#configuring-the-default-color-profiles}

Après avoir installé le Feature Pack, vous devez configurer les profils de couleurs par défaut appropriés pour activer la correction des couleurs lors de la demande de données d’image RGB ou CMJN.

**Pour configurer les profils de couleurs par défaut**:

1. Dans **[!UICONTROL Outils > Général > CRXDE Lite]**, accédez à `/conf/global/settings/dam/dm/imageserver/configuration/settings`, qui contient les profils de couleur par défaut d’Adobe.

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. Ajoutez une propriété de correction des couleurs en faisant défiler l’écran vers le bas de la page **[!UICONTROL Propriétés]** et saisir manuellement le nom, le type et la valeur de la propriété, qui sont décrits dans les tableaux suivants. Après avoir saisi les valeurs, appuyez sur **[!UICONTROL Ajouter]** puis **[!UICONTROL Enregistrer tout]** pour enregistrer vos valeurs.

   Les propriétés de correction des couleurs sont décrites dans la section **[!UICONTROL Propriétés de correction des couleurs]** table. Les valeurs que vous pouvez attribuer aux propriétés de correction des couleurs se trouvent dans la variable **[!UICONTROL Profil colorimétrique]** table.

   Par exemple, dans **[!UICONTROL Nom]**, ajoutez `iccprofilecmyk`, sélectionnez **[!UICONTROL Type]** `String` puis ajoutez `WebCoated` en tant que **[!UICONTROL Valeur]**. Appuyer **[!UICONTROL Ajouter]**, puis **[!UICONTROL Enregistrer tout]** pour enregistrer vos valeurs.

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **Tableau des propriétés de corrections des couleurs**

   <table> 
    <tbody> 
      <tr> 
      <td><strong>Propriété</strong></td> 
      <td><strong>Type</strong></td> 
      <td><strong>Valeur par défaut</strong></td> 
      <td><strong>Description</strong></td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html?lang=fr">iccprofilergb</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique RVB par défaut.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html?lang=fr">iccprofilecmyk</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique CMJN par défaut.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html?lang=fr">iccprofilegray</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique de niveaux de gris par défaut.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html?lang=fr">iccprofilesrcrgb</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique RGB par défaut utilisé pour les images RGB qui n’ont pas de profil colorimétrique intégré.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html?lang=fr">iccprofilesrccmyk</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique CMJN par défaut utilisé pour les images CMJN qui n’ont pas de profil colorimétrique incorporé.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html?lang=fr">iccprofilesrcgray</a></td> 
      <td>Chaîne</td> 
      <td>&lt;empty&gt;</td> 
      <td>Nom du profil colorimétrique de niveaux de gris par défaut utilisé pour les images CMJN qui n’ont pas de profil colorimétrique incorporé.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html?lang=fr">iccblackpointcompensation</a></td> 
      <td>Booléen</td> 
      <td>True</td> 
      <td>Indique si la compensation du point noir doit être effectuée lors de la correction des couleurs. Adobe recommande d’activer cette fonction.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html?lang=fr">iccdither</a></td> 
      <td>Booléen</td> 
      <td>False</td> 
      <td>Indique si le tramage doit être effectué lors de la correction des couleurs.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html?lang=fr">iccrenderintent</a></td> 
      <td>Chaîne</td> 
      <td>relative</td> 
      <td><p>Indique le mode de rendu. Les valeurs possibles sont : <strong>perception, relative, saturation, absolue. </strong><i></i>Adobe recommande d’utiliser <strong>colorimétrie relative</strong><i></i> comme valeur par défaut.</p> </td> 
      </tr> 
    </tbody> 
    </table>

   >[!NOTE]
   Les noms des propriétés sont sensibles à la casse et doivent être tous en minuscules.

   **Tableau de profils de couleurs**

   Les profils de couleurs suivants sont installés :

   <table> 
    <tbody> 
      <tr> 
      <th><p>Nom</p> </th> 
      <th><p>Espace colorimétrique</p> </th> 
      <th><p>Description</p> </th> 
      </tr> 
      <tr> 
      <td>AdobeRGB</td> 
      <td>RVB</td> 
      <td>Adobe RGB (1998)</td> 
      </tr> 
      <tr> 
      <td>AppleRGB</td> 
      <td>RVB</td> 
      <td>Apple RGB</td> 
      </tr> 
      <tr> 
      <td>CIERGB</td> 
      <td>RVB</td> 
      <td>CIE RGB</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra27</td> 
      <td>CMJN</td> 
      <td>Coated FOGRA27 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra39</td> 
      <td>CMJN</td> 
      <td>Coated FOGRA39 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedGraCol</td> 
      <td>CMJN</td> 
      <td>Coated GRACoL 2006 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>ColorMatchRGB</td> 
      <td>RVB</td> 
      <td>RGB ColorMatch</td> 
      </tr> 
      <tr> 
      <td>EuropeISOCoated</td> 
      <td>CMJN</td> 
      <td>Europe ISO Coated FOGRA27</td> 
      </tr> 
      <tr> 
      <td>EuroscaleCoated</td> 
      <td>CMJN</td> 
      <td>Euroscale Coated v2</td> 
      </tr> 
      <tr> 
      <td>EuroscaleUncoated</td> 
      <td>CMJN</td> 
      <td>Euroscale Uncoute v2</td> 
      </tr> 
      <tr> 
      <td>JapanColorCoated</td> 
      <td>CMJN</td> 
      <td>Japan Color 2001 Coated</td> 
      </tr> 
      <tr> 
      <td>JapanColorNewspaper</td> 
      <td>CMJN</td> 
      <td>Japan Color 2002 Newspaper</td> 
      </tr> 
      <tr> 
      <td>JapanColorUncoated</td> 
      <td>CMJN</td> 
      <td>Japan Color 2001 Uncoated</td> 
      </tr> 
      <tr> 
      <td>JapanColorWebCoated</td> 
      <td>CMJN</td> 
      <td>Japan Color 2003 Web Coated</td> 
      </tr> 
      <tr> 
      <td>JapanWebCoated</td> 
      <td>CMJN</td> 
      <td>Japan Web Coated (Ad)</td> 
      </tr> 
      <tr> 
      <td>NewsprintSNAP2007</td> 
      <td>CMJN</td> 
      <td>US Newsprint (SNAP 2007)</td> 
      </tr> 
      <tr> 
      <td>NTSC</td> 
      <td>RVB</td> 
      <td>NTSC (1953)</td> 
      </tr> 
      <tr> 
      <td>PAL</td> 
      <td>RVB</td> 
      <td>PAL/SECAM</td> 
      </tr> 
      <tr> 
      <td>ProPhoto</td> 
      <td>RVB</td> 
      <td>ProPhoto RGB</td> 
      </tr> 
      <tr> 
      <td>PS4Default</td> 
      <td>CMJN</td> 
      <td>Photoshop 4 Default CMYK</td> 
      </tr> 
      <tr> 
      <td>PS5Default</td> 
      <td>CMJN</td> 
      <td>Photoshop 5 Default CMYK</td> 
      </tr> 
      <tr> 
      <td>SheetfedCoated</td> 
      <td>CMJN</td> 
      <td>U.S. Sheetfed Coated v2</td> 
      </tr> 
      <tr> 
      <td>SheetfedUncoated</td> 
      <td>CMJN</td> 
      <td>U.S. Sheetfed Uncoated v2</td> 
      </tr> 
      <tr> 
      <td>SMPTE</td> 
      <td>RVB</td> 
      <td>SMPTE-C</td> 
      </tr> 
      <tr> 
      <td>sRVB</td> 
      <td>RVB</td> 
      <td>sRVB IEC61966-2.1</td> 
      </tr> 
      <tr> 
      <td>UncoatedFogra29</td> 
      <td>CMJN</td> 
      <td>Uncoated FOGRA29 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoated</td> 
      <td>CMJN</td> 
      <td>U.S. Web Coated (SWOP) v2</td> 
      </tr> 
      <tr> 
      <td>WebCoatedFogra28</td> 
      <td>CMJN</td> 
      <td>Web Coated FOGRA28 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade3</td> 
      <td>CMJN</td> 
      <td>Web Coated SWOP 2006 Grade 3 Paper</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade5</td> 
      <td>CMJN</td> 
      <td>Web Coated SWOP 2006 Grade 5 Paper</td> 
      </tr> 
      <tr> 
      <td>WebUncoated</td> 
      <td>CMJN</td> 
      <td>U.S. Web Uncoated v2</td> 
      </tr> 
      <tr> 
      <td>WideGamutRGB</td> 
      <td>RVB</td> 
      <td>Wide Gamut RGB</td> 
      </tr> 
    </tbody> 
    </table>

1. Appuyez sur **[!UICONTROL Enregistrer tout]**.

Par exemple, vous pouvez définir **[!UICONTROL iccprofilergb]** to `sRGB`, et **[!UICONTROL iccprofilecmyk]** to `WebCoated`. Cela permet d’effectuer les opérations suivantes :

* Active la correction des couleurs pour les images RGB et CMJN.
* Les images de RGB qui n’ont pas de profil colorimétrique sont censées se trouver dans la variable `sRGB` espace colorimétrique.
* Les images CMJN qui n’ont pas de profil colorimétrique sont considérées comme se trouvant dans l’espace colorimétrique `WebCoated`.
* Les rendus dynamiques qui renvoient une sortie de RGB la renvoient dans la variable `sRGB` espace colorimétrique.
* Les rendus dynamiques qui renvoient une sortie CMJN, la renvoient dans l’espace colorimétrique `WebCoated`.

## Diffusion des ressources {#delivering-assets}

Une fois que vous avez terminé toutes les tâches ci-dessus, les ressources Dynamic Media activées sont diffusées depuis le service d’images ou de vidéos. Dans AEM, cette fonctionnalité apparaît dans une **[!UICONTROL Copier l’URL de l’image]**, **[!UICONTROL Copier l’URL de la visionneuse]**, **[!UICONTROL Code de visionneuse intégré]** et dans la gestion de contenu web.

Reportez-vous à la section [Diffusion de ressources Dynamic Media](delivering-dynamic-media-assets.md).

<table> 
 <tbody> 
  <tr> 
   <td><strong>Action</strong></td> 
   <td><strong>Résultat</strong></td> 
  </tr> 
  <tr> 
   <td>Copier l’URL d’une image</td> 
   <td><p>La boîte de dialogue Copier l’URL affiche une URL similaire à celle qui suit (l’URL est utilisée à des fins de démonstration uniquement) :</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>où <code>IMAGESERVICEPUBLISHNODE</code> fait référence à l’URL du service d’images.</p> <p>Voir aussi <a href="/help/assets/delivering-dynamic-media-assets.md">Diffusion de ressources Dynamic Media</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Copie de l’URL d’une visionneuse</td> 
   <td><p>La boîte de dialogue Copier l’URL affiche une URL similaire à celle qui suit (l’URL est utilisée à des fins de démonstration uniquement) :</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>Où <code>PUBLISHNODE</code> fait référence au noeud de publication d’AEM standard et <code>IMAGESERVICEPUBLISHNODE</code> fait référence à l’URL du service d’images.</p> <p>Voir aussi <a href="/help/assets/delivering-dynamic-media-assets.md">Diffusion de ressources Dynamic Media</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Copie du code incorporé d’une visionneuse</td> 
   <td><p>La boîte de dialogue Copier le code affiche un fragment de code similaire à celui qui suit (le code est utilisé à des fins de démonstration uniquement) :</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>Où <code>PUBLISHNODE</code> fait référence au noeud de publication d’AEM standard et <code>IMAGESERVICEPUBLISHNODE</code> fait référence à l’URL du service d’images.</p> <p>Voir aussi <a href="/help/assets/delivering-dynamic-media-assets.md">Diffusion de ressources Dynamic Media</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Composants WCM Dynamic Media et Interactive Media {#wcm-dynamic-media-and-interactive-media-components}

Les pages WCM qui font référence aux composants Dynamic Media et Interactive Media font référence au service de diffusion.
