---
title: Intégration à Dynamic Media Classic
description: Découvrez comment intégrer AEM à Dynamic Media Classic.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: 0bfb05b8-7d10-4984-9e89-f1af88938c03
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '5492'
ht-degree: 11%

---

# Intégration à Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic est une solution hébergée qui permet de gérer, d’améliorer, de publier et de diffuser des ressources multimédias enrichies sur le Web, les appareils mobiles, les e-mails et les appareils d’impression connectés à Internet.

Pour utiliser Dynamic Media Classic, vous devez configurer la configuration cloud afin que Dynamic Media Classic et Adobe Experience Manager Assets puissent interagir entre eux. Ce document décrit comment configurer Experience Manager et Dynamic Media Classic.

Pour plus d’informations sur l’utilisation de tous les composants Dynamic Media Classic sur une page et l’utilisation de vidéos, voir [Utilisation de Dynamic Media Classic](../assets/scene7.md).

>[!NOTE]
>
>* La plateforme de la visionneuse DHTML de Dynamic Media Classic a officiellement atteint la fin de vie le 31 janvier 2014. Pour plus d’informations, voir [FAQ sur la fin de vie de la visionneuse DHTML](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Avant de configurer Dynamic Media Classic pour qu’il fonctionne avec Experience Manager, voir [Bonnes pratiques](#best-practices-for-integrating-scene-with-aem) pour intégrer Dynamic Media Classic à Experience Manager.
>* Si vous utilisez Dynamic Media Classic avec une configuration de proxy personnalisée, configurez les deux configurations de proxy client HTTP, car certaines fonctionnalités de Experience Manager utilisent les API 3.x et d’autres les API 4.x. 3.x est configuré avec [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) et la version 4.x est configurée avec [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator).

>


## Intégration de Experience Manager/Dynamic Media Classic par rapport à Dynamic Media {#aem-scene-integration-versus-dynamic-media}

Les utilisateurs de Experience Manager ont le choix entre deux solutions pour travailler avec Dynamic Media :

* Utilisation de votre instance intégrée de Experience Manager avec *Dynamic Media Classic*.
* Utilisation *Dynamic Media* qui est intégré à Experience Manager.

Utilisez les critères suivants pour déterminer la solution qui vous convient le mieux :

* Si vous êtes un **existant** Client Dynamic Media Classic dont les ressources multimédias enrichies résident dans Dynamic Media Classic pour publication et diffusion, mais que vous souhaitez intégrer ces ressources à la création de sites (WCM) et/ou à Experience Manager Assets pour gestion, puis utiliser la variable [Intégration point à point Experience Manager/Dynamic Media Classic](#aem-scene-point-to-point-integration) décrits dans ce document.

* Si vous êtes un **new** Un client Experience Manager ayant des besoins en diffusion de contenu multimédia, sélectionnez [Option Dynamic Media](#aem-dynamic-media). Cette option a plus de sens si vous ne disposez pas d’un compte S7 et que vous avez de nombreuses ressources stockées dans ce système.

* Dans certains cas, utilisez les deux solutions. Le [scénario à double usage](/help/sites-administering/scene7.md#dual-use-scenario) décrit ce scénario.

### Intégration point à point Experience Manager/Dynamic Media Classic {#aem-scene-point-to-point-integration}

Lorsque vous utilisez des ressources dans cette solution, vous effectuez l’une des opérations suivantes :

* Chargez des ressources directement dans Dynamic Media Classic, puis accédez à au moyen de l’option **Dynamic Media Classic** navigateur de contenu pour la création de pages ou
* Téléchargez vers Experience Manager Assets, puis activez la publication automatique vers Dynamic Media Classic. vous y accédez via **Ressources** navigateur de contenu pour la création de pages

Les composants que vous utilisez pour cette intégration se trouvent dans la variable **Dynamic Media Classic** zone de composant dans [Mode de conception.](/help/sites-authoring/author-environment-tools.md#page-modes)

### Experience Manager Dynamic Media {#aem-dynamic-media}

Experience Manager Dynamic Media est l’unification des fonctionnalités Dynamic Media Classic directement dans la plateforme de Experience Manager.

Lorsque vous travaillez avec des ressources dans cette solution, vous suivez ce workflow :

1. Chargez des ressources d’image et vidéo uniques directement dans Experience Manager.
1. Codez des vidéos directement dans Experience Manager.
1. Créez des visionneuses d’images directement dans Experience Manager.
1. Le cas échéant, ajouter une certaine interactivité aux images ou aux vidéos.

Les composants que vous utilisez pour Dynamic Media se trouvent dans la zone du composant **[!UICONTROL Dynamic Media]** en [mode Conception](/help/sites-authoring/author-environment-tools.md#page-modes). Ils comprennent les éléments suivants :

* **[!UICONTROL Dynamic Media]** : le composant **[!UICONTROL Dynamic Media]** est dynamique ; il propose des options différentes selon que vous ajoutez une image ou une vidéo. Le composant prend en charge les paramètres d’image prédéfinis, ainsi que les visionneuses d’images telles que les visionneuses d’images, les visionneuses à 360°, les visionneuses de médias mixtes et le contenu vidéo. En outre, la visionneuse est réactive : la taille de l’écran change automatiquement en fonction de la taille de l’écran. Toutes les visionneuses sont des visionneuses HTML5.

* **[!UICONTROL Média interactif]** - Le **[!UICONTROL Média interactif]** est destiné aux bannières de carrousel, aux images interactives et aux vidéos interactives qui intègrent des zones réactives ou des zones cliquables. Ce composant est intelligent. Selon que vous ajoutez une image ou une vidéo, vous disposez de différentes options. En outre, la visionneuse est réactive. En d’autres termes, la taille de l’écran change automatiquement en fonction de la taille à l’écran. Toutes les visionneuses sont des visionneuses HTML5.

### Scénario à double utilisation {#dual-use-scenario}

Vous pouvez utiliser simultanément les fonctionnalités d’intégration Dynamic Media et Dynamic Media Classic de Experience Manager prêtes à l’emploi. Le tableau suivant des cas pratiques décrit le moment où vous activez et désactivez certaines zones.

Pour utiliser Dynamic Media et Dynamic Media Classic simultanément :

1. Configurer [Dynamic Media Classic](#creating-a-cloud-configuration-for-scene) en Cloud Services.
1. Suivez les instructions spécifiques correspondant à votre cas d’utilisation :

   <table> 
    <tbody> 
    <tr> 
    <td> </td> 
    <td> </td> 
    <td><strong>Dynamic Media</strong></td> 
    <td> </td> 
    <td><strong>Intégration Dynamic Media Classic</strong></td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td><strong>Si vous êtes...</strong></td> 
    <td><strong>Workflow de cas d’utilisation</strong></td> 
    <td><strong>Imagerie/Vidéo</strong></td> 
    <td><strong>Composant Dynamic Media</strong></td> 
    <td><strong>Explorateur de contenu et composants S7</strong></td> 
    <td><strong>Chargement automatique d’Assets vers S7</strong></td> 
    </tr> 
    <tr> 
    <td>Nouveautés de Sites et Dynamic Media</td> 
    <td>Chargement de ressources dans Experience Manager et utilisation du composant Dynamic Media Experience Manager pour créer des ressources sur les pages Sites</td> 
    <td><p>Activé</p> <p>(Voir l’étape 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Activé</a></td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    </tr> 
    <tr> 
    <td>Dans la vente au détail et nouveaux dans Sites et Dynamic Media</td> 
    <td>Chargez des ressources non liées aux produits dans Experience Manager à des fins de gestion et de diffusion. Chargez des ressources PRODUCT dans Dynamic Media Classic et utilisez l’explorateur de contenu Dynamic Media Classic dans Experience Manager et le composant pour créer des pages Détails du produit sur Sites.</td> 
    <td><p>Activé</p> <p>(Voir l’étape 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Activé</a></td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Activé</a></td> 
    <td>Désactivé</td> 
    </tr> 
    <tr> 
    <td>Nouveautés d’Assets et de Dynamic Media</td> 
    <td>Chargement de ressources dans Experience Manager Assets et utilisation de l’URL publiée/du code intégré de Dynamic Media</td> 
    <td><p>Activé</p> <p>(Voir l’étape 3)</p> </td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    </tr> 
    <tr> 
    <td>Nouveautés de Dynamic Media et des modèles</td> 
    <td>Utilisez Dynamic Media pour les images et la vidéo. Créez des modèles d’image dans Dynamic Media Classic et utilisez l’outil de recherche de contenu Dynamic Media Classic pour inclure des modèles dans les pages Sites.</td> 
    <td><p>Activé</p> <p>(Voir l’étape 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Activé</a></td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Activé</a></td> 
    <td>Désactivé</td> 
    </tr> 
    <tr> 
    <td>Un client Dynamic Media Classic existant et de nouveaux utilisateurs de Sites</td> 
    <td>Chargement de ressources dans Dynamic Media Classic et utilisation de l’explorateur de contenu Dynamic Media Classic Experience Manager pour rechercher et créer des ressources sur les pages Sites</td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Activé</a></td> 
    <td>Désactivé</td> 
    </tr> 
    <tr> 
    <td>Un client Dynamic Media Classic existant et les nouveaux utilisateurs de Sites et Assets</td> 
    <td>Chargez des ressources dans la gestion des ressources numériques et publiez automatiquement sur Dynamic Media Classic pour diffusion. Utilisez le navigateur de contenu Dynamic Media Classic Experience Manager pour rechercher et créer des ressources sur les pages Sites.</td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Activé</a></td> 
    <td><p><a href="#configuringautouploadingfromaemassets">Activé</a></p> <p>(Voir l’étape 4)</p> </td> 
    </tr> 
    <tr> 
    <td>Client Dynamic Media Classic existant et nouveau dans Assets</td> 
    <td><p>Téléchargez des ressources vers Experience Manager et utilisez Dynamic Media pour générer des rendus à télécharger/partager. Publier automatiquement Experience Manager Assets vers Dynamic Media Classic pour diffusion.</p> <p><strong>Important :</strong> Crée un traitement en double et les rendus générés dans Experience Manager ne sont pas synchronisés dans Dynamic Media Classic.</p> </td> 
    <td><p>Activé</p> <p>(Voir l’étape 3)</p> </td> 
    <td>Désactivé</td> 
    <td>Désactivé</td> 
    <td><p><a href="#configuringautouploadingfromaemassets">Activé</a></p> <p>(Voir l’étape 4)</p> </td> 
    </tr> 
    </tbody> 
    </table>

1. (Facultatif) voir tableau des cas d’utilisation) - Configuration de la variable [Configuration du cloud Dynamic Media](/help/assets/config-dynamic.md) et [activation du serveur Dynamic Media](/help/assets/config-dynamic.md).
1. (Facultatif) (voir tableau des cas d’utilisation) - Si vous choisissez d’activer le téléchargement automatique des ressources vers Dynamic Media Classic, vous devez ajouter les éléments suivants :

   1. Configurez le chargement automatique vers Dynamic Media Classic.
   1. Ajoutez la variable **Chargement Dynamic Media Classic** après toutes les étapes du processus Dynamic Media *à la fin de* **Ressource de mise à jour de gestion des actifs numériques** workflow ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Facultatif) Limitation du chargement des ressources Dynamic Media Classic par type MIME dans [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl). Les types MIME de ressources qui ne figurent pas dans cette liste ne sont pas chargés sur le serveur Dynamic Media Classic.
   1. (Facultatif) Configurez la vidéo dans la configuration Dynamic Media Classic. Vous pouvez activer le codage vidéo simultanément pour Dynamic Media et Dynamic Media Classic, ou les deux. Les rendus dynamiques sont utilisés pour l’aperçu et la lecture localement dans l’instance de Experience Manager, tandis que les rendus vidéo Dynamic Media Classic sont générés et stockés sur les serveurs Dynamic Media Classic. Lors de la configuration de services de codage vidéo pour Dynamic Media et Dynamic Media Classic, appliquez une [profil de traitement vidéo](/help/assets/video-profiles.md) dans le dossier de ressources Dynamic Media Classic.
   1. (Facultatif) [Configuration de l’aperçu sécurisé dans Dynamic Media Classic](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Restrictions {#limitations}

Lorsque Dynamic Media Classic et Dynamic Media sont activés, les restrictions suivantes s’appliquent :

* Le téléchargement manuel vers Dynamic Media Classic en sélectionnant une ressource et en la faisant glisser vers un composant Dynamic Media Classic sur une page de Experience Manager ne fonctionne pas.
* Même si les ressources synchronisées Experience Manager-Dynamic Media Classic sont automatiquement mises à jour vers Dynamic Media Classic lorsque la ressource est modifiée dans Assets, une action de restauration ne déclenche pas de nouveau chargement. Par conséquent, Dynamic Media Classic n’obtient pas la dernière version immédiatement après une restauration. La solution consiste à modifier à nouveau une fois la restauration terminée.
* Si vous devez utiliser Dynamic Media pour un cas d’utilisation et l’intégration de Dynamic Media Classic pour un autre afin que les ressources Dynamic Media n’interagissent pas avec le système Dynamic Media Classic, n’appliquez pas la configuration de Dynamic Media Classic au dossier Dynamic Media. De plus, n’appliquez pas la configuration Dynamic Media (profil de traitement) à un dossier Dynamic Media Classic.

## Bonnes pratiques pour intégrer Dynamic Media Classic à Experience Manager {#best-practices-for-integrating-scene-with-aem}

Lors de l’intégration de Dynamic Media Classic à Experience Manager, certaines bonnes pratiques importantes doivent être observées dans les domaines suivants :

* Test de votre intégration
* Chargement direct de ressources à partir de Dynamic Media Classic recommandé pour certains scénarios

Voir [limites connues](#known-limitations-and-design-implications).

### Test de votre intégration {#test-driving-your-integration}

Adobe vous recommande de tester votre intégration en pointant votre dossier racine vers un sous-dossier uniquement plutôt que vers l’ensemble de l’entreprise.

>[!CAUTION]
>
>L’importation de ressources à partir d’un compte d’entreprise Dynamic Media Classic existant peut prendre un certain temps pour s’afficher dans Experience Manager. Veillez à désigner dans Dynamic Media Classic un dossier qui ne comporte pas trop de ressources (par exemple, le dossier racine comporte souvent trop de ressources et peut bloquer votre système).

### Chargement de ressources à partir de Experience Manager Assets ou de Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

Vous pouvez télécharger des ressources à l’aide de la fonctionnalité Ressources (gestion des ressources numériques) ou en accédant directement à Dynamic Media Classic dans Experience Manager à l’aide de l’explorateur de contenu Dynamic Media Classic. Votre choix dépend des facteurs suivants :

* Les types de ressources Dynamic Media Classic que Experience Manager Assets ne prend pas encore en charge doivent être ajoutés directement à un site web de Experience Manager à partir de Dynamic Media Classic, par le biais de l’explorateur de contenu Dynamic Media Classic. Par exemple, les modèles d’image.
* Pour les types de ressources pris en charge à la fois par Experience Manager Assets et Dynamic Media Classic, le choix de leur téléchargement dépend des éléments suivants :

   * L’emplacement actuel des ressources ET
   * L’importance de les gérer dans un référentiel commun

Si les ressources se trouvent déjà dans Dynamic Media Classic et que leur gestion dans un référentiel commun n’est pas importante, l’exportation vers Experience Manager Assets uniquement pour les synchroniser à nouveau avec Dynamic Media Classic pour diffusion est un aller-retour inutile. Dans le cas contraire, il est préférable de ne conserver que les ressources dans un seul référentiel et de ne synchroniser la diffusion qu’avec Dynamic Media Classic.

## Configuration de l’intégration Dynamic Media Classic {#configuring-scene-integration}

Vous pouvez configurer Experience Manager pour charger des ressources dans Dynamic Media Classic. Les ressources d’un dossier cible CQ peuvent être téléchargées (automatiquement ou manuellement) du Experience Manager vers un compte d’entreprise Dynamic Media Classic.

>[!NOTE]
>
>Adobe recommande d’utiliser uniquement le dossier cible désigné pour importer des ressources Dynamic Media Classic. Les ressources numériques qui se trouvent en dehors du dossier cible ne peuvent être utilisées que dans les composants Dynamic Media Classic sur les pages où la configuration Dynamic Media Classic a été activée. En outre, ils sont placés dans un dossier à la demande dans Dynamic Media Classic. Le dossier à la demande n’est pas synchronisé avec Experience Manager (mais les ressources peuvent être découvertes dans le navigateur de contenu Dynamic Media Classic).

Pour configurer Dynamic Media Classic afin de l’intégrer à Experience Manager, procédez comme suit :

1. [Définition d’une configuration de cloud](#creating-a-cloud-configuration-for-scene) - Définit le mappage entre un dossier Dynamic Media Classic et un dossier Assets. Effectuez cette étape même si vous souhaitez uniquement une synchronisation unidirectionnelle (Experience Manager Assets vers Dynamic Media Classic).
1. [Activez la variable **Écouteur de gestion des actifs numériques Adobe CQ s7dam**](#enabling-the-adobe-cq-scene-dam-listener) - Terminé dans le [!UICONTROL OSGi] console.
1. Si vous souhaitez que les ressources de Experience Manager soient automatiquement chargées vers Dynamic Media Classic, activez l’option et ajoutez Dynamic Media Classic au workflow Ressources de mise à jour de gestion des actifs numériques. Vous pouvez également télécharger les ressources manuellement.
1. Ajout de composants Dynamic Media Classic au sidekick. Cela permet aux utilisateurs d’utiliser les composants Dynamic Media Classic sur leurs pages de Experience Manager.
1. [Faire correspondre la configuration à la page dans Experience Manager](#enabling-scene-for-wcm) - Cette étape est nécessaire pour afficher les paramètres vidéo prédéfinis que vous avez créés dans Dynamic Media Classic. Elle est également requise si vous devez publier une ressource à partir du dossier cible CQ vers Dynamic Media Classic.

Cette section décrit comment effectuer toutes ces étapes et répertorie des restrictions importantes.

### Fonctionnement de la synchronisation entre Dynamic Media Classic et Experience Manager Assets {#how-synchronization-between-scene-and-aem-assets-works}

Lors de la configuration de la synchronisation Experience Manager Assets et Dynamic Media Classic, il est important de comprendre les éléments suivants :

#### Téléchargement vers Dynamic Media Classic à partir de Experience Manager Assets {#uploading-to-scene-from-aem-assets}

* Il existe un dossier de synchronisation désigné en Experience Manager pour les chargements Dynamic Media Classic.
* Les chargements vers Dynamic Media Classic peuvent être automatisés si les ressources numériques sont placées dans le dossier de synchronisation désigné.
* La structure de dossiers et de sous-dossiers dans Experience Manager est répliquée dans Dynamic Media Classic.

>[!NOTE]
>
>Experience Manager incorpore toutes les métadonnées comme XMP avant de les transférer vers Dynamic Media Classic, de sorte que toutes les propriétés du noeud de métadonnées soient disponibles dans Dynamic Media Classic as XMP.

#### Restrictions connues et implications en termes de conception {#known-limitations-and-design-implications}

Avec la synchronisation entre Experience Manager Assets et Dynamic Media Classic, il existe actuellement les limitations/implications de conception suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Limitation/implication dans la conception</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Un dossier de synchronisation désigné (cible)</td> 
   <td>Vous ne pouvez avoir qu’un seul dossier désigné par société dans Experience Manager pour les chargements Dynamic Media Classic. Vous pouvez créer plusieurs configurations si vous devez avoir accès à plusieurs comptes d’entreprise dans Dynamic Media Classic.</td> 
  </tr> 
  <tr> 
   <td>Structure du dossier</td> 
   <td>Si vous supprimez un dossier synchronisé comportant des ressources, toutes les ressources distantes de Dynamic Media Classic sont supprimées, mais le dossier reste.</td> 
  </tr> 
  <tr> 
   <td>Dossier ad hoc</td> 
   <td>Les ressources qui se trouvent en dehors du dossier cible et qui sont téléchargées manuellement vers Dynamic Media Classic dans la gestion de contenu web sont automatiquement placées dans un dossier ad hoc distinct sur Dynamic Media Classic. Configurez cette fonctionnalité dans la configuration cloud de Experience Manager.</td> 
  </tr> 
  <tr> 
   <td>Supports variés</td> 
   <td>Les visionneuses de médias mixtes apparaissent en Experience Manager bien qu’elles ne soient pas prises en charge dans Experience Manager.</td> 
  </tr> 
  <tr> 
   <td>PDF</td> 
   <td>Les PDF générés à partir des catalogues électroniques dans Dynamic Media Classic sont importés dans le dossier cible CQ.</td> 
  </tr> 
  <tr> 
   <td>Actualisation de l’interface utilisateur</td> 
   <td>Lors de la synchronisation entre Experience Manager et Dynamic Media Classic, veillez à actualiser l’interface utilisateur pour afficher les modifications. </td> 
  </tr> 
  <tr> 
   <td>Miniatures vidéo</td> 
   <td>Si vous téléchargez une vidéo vers Experience Manager Assets à des fins de codage via Dynamic Media Classic, les miniatures vidéo et les vidéos codées peuvent prendre un certain temps pour être disponibles dans Experience Manager Assets, en fonction du temps de traitement vidéo.</td> 
  </tr> 
  <tr> 
   <td>Sous-dossiers cible</td> 
   <td><p>Si vous utilisez des sous-dossiers dans le dossier cible, utilisez des noms uniques pour chaque ressource (quel que soit l’emplacement) ou configurez Dynamic Media Classic (dans la zone Configuration) pour ne pas remplacer les ressources, quel que soit l’emplacement.</p> <p>Dans le cas contraire, les ressources portant le même nom qui sont chargées dans un sous-dossier cible Dynamic Media Classic sont chargées, mais la ressource portant le même nom dans le dossier cible est supprimée. </p> </td> 
  </tr> 
 </tbody> 
</table>

### Configuration des serveurs Dynamic Media Classic {#configuring-scene-servers}

Si vous exécutez Experience Manager derrière un proxy ou que vous disposez de paramètres de pare-feu spéciaux, vous devez activer explicitement les hôtes des différentes régions. Les serveurs sont gérés dans le contenu de `/etc/cloudservices/scene7/endpoints` et peut être personnalisé selon les besoins. Appuyez sur une URL, puis modifiez-la, si nécessaire. Dans les versions précédentes de Experience Manager, ces valeurs étaient codées en dur.

Si vous accédez à `/etc/cloudservices/scene7/endpoints.html`, les serveurs sont répertoriés (et vous pouvez les modifier en cliquant sur l’URL) :

![chlimage_1-296](assets/chlimage_1-296.png)

### Création d’une configuration cloud pour Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Une configuration de cloud définit le mappage entre un dossier Dynamic Media Classic et un dossier Experience Manager Assets. Il doit être configuré pour synchroniser Experience Manager Assets avec Dynamic Media Classic. Voir Fonctionnement de la synchronisation pour en savoir plus.

>[!CAUTION]
>
>L’importation de ressources à partir d’un compte d’entreprise Dynamic Media Classic existant peut prendre un certain temps pour s’afficher dans Experience Manager. Veillez à désigner dans Dynamic Media Classic un dossier qui ne comporte pas trop de ressources. Par exemple, le dossier racine comporte souvent trop de ressources.
>
>Si vous souhaitez tester l’intégration, faites en sorte que le dossier racine pointe uniquement vers un sous-dossier, au lieu de l’ensemble de l’entreprise.

>[!NOTE]
>
>Vous pouvez avoir plusieurs configurations : une configuration de cloud représente un utilisateur dans une société Dynamic Media Classic. Si vous souhaitez accéder à d’autres sociétés ou utilisateurs Dynamic Media Classic, créez plusieurs configurations.

Pour configurer Experience Manager afin de pouvoir publier des ressources dans Dynamic Media Classic :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Déploiement > Cloud Services]** pour accéder à Adobe Dynamic Media Classic.

1. Appuyer **[!UICONTROL Configurer maintenant]**.

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Dans le champ **[!UICONTROL Titre]** et éventuellement dans le champ **[!UICONTROL Nom]**, saisissez les informations appropriées. Appuyez sur **[!UICONTROL Créer]**.

   >[!NOTE]
   >
   >Lors de la création d’autres configurations, la variable **[!UICONTROL configuration parente]** s’affiche.
   >
   >Ne modifiez **pas** la configuration du parent. La modification de la configuration du parent peut supprimer l’intégration.

1. Saisissez l’adresse électronique, le mot de passe et la région de votre compte Dynamic Media Classic, puis appuyez sur **[!UICONTROL Connexion à Dynamic Media Classic]**. Vous êtes connecté au serveur Dynamic Media Classic et la boîte de dialogue se développe avec d’autres options.

1. Saisissez le **[!UICONTROL Société]** name et **[!UICONTROL Chemin racine]**. Ces informations sont le nom du serveur publié, ainsi que tout chemin d’accès que vous souhaitez spécifier. Si vous ne connaissez pas le nom du serveur publié, dans Dynamic Media Classic, accédez à **[!UICONTROL Configuration > Configuration de l’application]**.

   >[!NOTE]
   >
   >Le chemin d’accès racine Dynamic Media Classic est le Experience Manager de dossiers Dynamic Media Classic auquel se connecte le client. Il peut être réduit à un dossier spécifique.

   >[!CAUTION]
   >
   >Selon la taille du dossier Dynamic Media Classic, l’importation d’un dossier racine peut prendre un certain temps. En outre, les données Dynamic Media Classic peuvent dépasser le stockage du Experience Manager. Vérifiez que vous importez le bon dossier. Importer trop de données peut arrêter votre système.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Cliquez sur **[!UICONTROL OK]**. Experience Manager enregistre votre configuration.

>[!NOTE]
>
>Si vous vous reconnectez :
>
>* Lors de la reconnexion à Dynamic Media Classic lors de la publication, réinitialisez le mot de passe lors de la publication ou la reconnexion ne fonctionne pas (ce n’est pas un problème sur l’instance d’auteur).
>* Si vous modifiez des valeurs telles que votre région ou le nom de votre société, vous devez vous reconnecter à Dynamic Media Classic. Si les options de configuration ont été modifiées mais ne sont pas enregistrées, Experience Manager indique toujours par erreur que la configuration est valide. N’oubliez pas de vous reconnecter.

>


### Activation de l’écouteur de gestion des actifs numériques Dynamic Media Classic Adobe CQ {#enabling-the-adobe-cq-scene-dam-listener}

Activez l’écouteur de gestion des actifs numériques Dynamic Media Classic Adobe CQ, qui est désactivé par défaut.

Pour activer l’écouteur de gestion des actifs numériques Dynamic Media Classic Adobe CQ :

1. Appuyez sur le bouton [!UICONTROL Outils] , puis accédez à **[!UICONTROL Opérations > Console web]**. La console Web s’ouvre.
1. Accédez à **[!UICONTROL Écouteur de gestion des actifs numériques Adobe CQ Dynamic Media Classic]** et sélectionnez la variable **[!UICONTROL Activé]** .

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Appuyez sur **[!UICONTROL Enregistrer]**.

### Ajout d’un délai d’expiration configurable au workflow de téléchargement Dynamic Media Classic {#adding-configurable-timeout-to-scene-upload-workflow}

Lorsqu’une instance de Experience Manager est configurée pour gérer le codage vidéo via Dynamic Media Classic, un délai d’attente de 35 minutes s’applique par défaut à toute tâche de téléchargement. Pour prendre en charge des tâches de codage vidéo potentiellement plus longues, vous pouvez configurer ce paramètre :

1. Accédez à **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Dans le champ **[!UICONTROL Délai d’expiration de la tâche active]**, modifiez le nombre selon les besoins. Sont acceptés tous les nombres non négatifs,avec l’unité de mesure en secondes. Par défaut, ce nombre est défini sur 2 100.

   >[!NOTE]
   >
   >Bonne pratique : la plupart des ressources sont assimilées en quelques minutes au plus (par exemple, les images). Cependant, dans certains cas, comme pour les vidéos plus volumineuses, augmentez la valeur du délai d’expiration à 7 200 secondes (deux heures) pour tenir compte du temps de traitement long. Sinon, cette tâche de chargement Dynamic Media Classic est marquée comme **[!UICONTROL UploadFailed]** dans les métadonnées JCR.

1. Appuyez sur **[!UICONTROL Enregistrer]**.

### Téléchargement depuis Experience Manager Assets {#autouploading-from-aem-assets}

À partir de la version 6.3.2 de Experience Manager, Experience Manager Assets est maintenant configuré pour vous afin que toutes les ressources numériques que vous chargez dans le gestionnaire de ressources numériques soient automatiquement mises à jour vers Dynamic Media Classic si elles se trouvent dans un dossier cible CQ.

Lorsqu’une ressource est ajoutée à Experience Manager Assets, elle est automatiquement chargée et publiée dans Dynamic Media Classic.

>[!NOTE]
>
>La taille de fichier maximale pour le chargement automatique de Experience Manager Assets vers Dynamic Media Classic est de 500 Mo.

Pour configurer le téléchargement automatique à partir de Experience Manager Assets :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Déploiement > Cloud Services]** Ensuite, sous l’en-tête Dynamic Media, sous Configurations disponibles, appuyez sur **[!UICONTROL dms7 (Dynamic Media)]**)
1. Appuyez sur le bouton **[!UICONTROL Avancé]** , sélectionnez la variable **[!UICONTROL Activation du téléchargement automatique]** , puis appuyez sur **[!UICONTROL OK]**. Vous devez maintenant configurer le workflow Ressources de gestion des actifs numériques pour inclure le téléchargement vers Dynamic Media Classic.

   >[!NOTE]
   >
   >Voir [Configuration de l’état (publié/non publié) des ressources transférées vers Dynamic Media Classic](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) pour plus d’informations sur l’envoi de ressources vers Dynamic Media Classic dans un état non publié.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Revenez à la page de bienvenue du Experience Manager et appuyez sur **[!UICONTROL Workflows]**. Double-cliquez sur le workflow **Ressources de mise à jour de gestion des actifs numériques** pour l’ouvrir.
1. Dans le sidekick, accédez au **[!UICONTROL Workflow]** composants, puis sélectionnez **[!UICONTROL Dynamic Media Classic]**. Faire glisser **[!UICONTROL Dynamic Media Classic]** dans le workflow, puis appuyez sur **[!UICONTROL Enregistrer]**. Les ressources ajoutées à Experience Manager Assets dans le dossier cible sont automatiquement chargées vers Dynamic Media Classic.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Lors de l’ajout de ressources après l’automatisation, si elles ne sont pas placées dans le dossier cible CQ, elles ne sont pas chargées vers Dynamic Media Classic.
   >* Experience Manager incorpore toutes les métadonnées comme XMP avant de les transférer vers Dynamic Media Classic, de sorte que toutes les propriétés du noeud de métadonnées soient disponibles dans Dynamic Media Classic as XMP.


### Configuration de l’état (publié/non publié) des ressources transférées vers Dynamic Media Classic {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Si vous poussez des ressources de Experience Manager Assets vers Dynamic Media Classic, vous pouvez les publier automatiquement (comportement par défaut) ou les envoyer vers Dynamic Media Classic dans un état non publié.

Il est possible que vous ne souhaitiez pas publier immédiatement les ressources sur Dynamic Media Classic si vous souhaitez les tester dans un environnement d’évaluation avant de les publier. Vous pouvez utiliser Experience Manager avec l’environnement de test sécurisé de Dynamic Media Classic pour envoyer directement des ressources d’ Assets vers Dynamic Media Classic dans un état non publié.

Les ressources Dynamic Media Classic restent disponibles via l’aperçu sécurisé. Ce n’est que lorsque les ressources sont publiées dans Experience Manager que les ressources Dynamic Media Classic sont également mises en production.

Si vous souhaitez publier des ressources immédiatement lors de leur publication dans Dynamic Media Classic, vous n’avez pas besoin de configurer d’options. Il s’agit du comportement par défaut.

Toutefois, si vous ne souhaitez pas que les ressources transférées vers Dynamic Media Classic soient publiées automatiquement, cette section décrit comment configurer Experience Manager et Dynamic Media Classic pour exécuter cette fonctionnalité.

#### Conditions préalables pour pousser les ressources vers Dynamic Media Classic non publiées {#prerequisites-to-push-assets-to-scene-unpublished}

Avant de pouvoir envoyer des ressources vers Dynamic Media Classic sans les publier, vous devez configurer les éléments suivants :

1. [Utilisez Admin Console pour créer un dossier d’assistance.](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Dans votre cas de prise en charge, demandez que l’aperçu sécurisé soit activé pour votre compte Dynamic Media Classic.
1. Suivez les instructions de la section [configurer l’aperçu sécurisé de votre compte Dynamic Media Classic.](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html#upload-publish)

Ces étapes sont les mêmes que pour créer une configuration de test sécurisée dans Dynamic Media Classic.

>[!NOTE]
>
>Si votre environnement d’installation est un système d’exploitation UNIX® 64 bits, reportez-vous à la section [https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) concernant les autres options de configuration que vous devez définir.

#### Limites connues pour pousser des ressources dans l’état dépublié  {#known-limitations-for-pushing-assets-in-unpublished-state}

Si vous utilisez cette fonctionnalité, notez les restrictions suivantes :

* Il n’existe aucune prise en charge du contrôle de version.
* Si une ressource est déjà publiée en Experience Manager et qu’une version ultérieure est créée, cette nouvelle version est immédiatement publiée en production. La publication sur activation ne fonctionne qu’avec la publication initiale d’une ressource.

>[!NOTE]
>
>Si vous souhaitez publier des ressources instantanément, la bonne pratique consiste à conserver **[!UICONTROL Activer l’aperçu sécurisé]** défini sur **[!UICONTROL Immédiatement]** et utilisez la fonction **[!UICONTROL Activation du téléchargement automatique]** fonction .

### Définition de l’état des ressources transmises à Dynamic Media Classic comme non publiées {#setting-the-state-of-assets-pushed-to-scene-as-unpublished}

>[!NOTE]
>
>Si un utilisateur publie la ressource dans Experience Manager, elle déclenche automatiquement la ressource S7 dans la ressource de production/en direct (la ressource n’est plus prévisualisée/non publiée en toute sécurité).

Pour définir l’état des ressources transmises à Dynamic Media Classic comme non publiées :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Déploiement > Cloud Services]**, appuyez sur **[!UICONTROL Dynamic Media Classic]**, puis sélectionnez votre configuration dans Dynamic Media Classic.
1. Sélectionnez l&#39;onglet **[!UICONTROL Avancé.]** Dans le **[!UICONTROL Activer la vue sécurisée]** menu déroulant, sélectionnez **[!UICONTROL Lors de l’activation de la publication AEM]** pour pousser des ressources vers Dynamic Media Classic sans les publier. (Par défaut, cette valeur est définie sur **[!UICONTROL Immédiatement]**, où les ressources Dynamic Media Classic sont publiées immédiatement.)

   Voir [Documentation Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html#upload-publish) pour plus d’informations sur le test des ressources avant de les rendre publiques.

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Appuyez sur **[!UICONTROL OK]**.

Avec l’option Activer la vue sécurisée, vos ressources sont poussées vers le serveur d’aperçu sécurisé sans être publiées.

Pour voir si l’aperçu sécurisé est activé, accédez à un composant Dynamic Media Classic sur une page dans Experience Manager. Appuyez sur **[!UICONTROL Modifier]**. Le serveur d’aperçu sécurisé de la ressource est répertorié dans l’URL. Après la publication dans Experience Manager, le domaine du serveur de la référence au fichier est mis à jour de l’URL d’aperçu vers l’URL de production.

### Activation de Dynamic Media Classic pour WCM {#enabling-scene-for-wcm}

L’activation de Dynamic Media Classic pour la gestion de contenu web est requise pour deux raisons :

* Elle active la liste déroulante des profils vidéo universels pour la création de pages. Sans cette liste, la variable **[!UICONTROL Paramètre prédéfini vidéo universel]** La liste déroulante est vide et ne peut pas être définie.
* Si une ressource numérique ne se trouve pas dans le dossier cible, vous pouvez la charger dans Dynamic Media Classic si vous activez Dynamic Media Classic pour cette page dans les propriétés de la page. Faites ensuite glisser et déposez la ressource sur un composant Dynamic Media Classic. Les règles d’héritage normales s’appliquent (ce qui signifie que les pages enfants héritent de la configuration de la page parente).

Lors de l’activation de Dynamic Media Classic pour la gestion de contenu web, comme pour d’autres configurations, les règles d’héritage s’appliquent. Vous pouvez activer Dynamic Media Classic pour la gestion de contenu web dans l’interface utilisateur optimisée pour les écrans tactiles ou classique.

#### Activation de Dynamic Media Classic pour WCM dans l’interface utilisateur optimisée pour les écrans tactiles {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

Pour activer Dynamic Media Classic pour la gestion de contenu web dans l’IU optimisée pour les écrans tactiles :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Sites]** puis la page racine de votre site web (non spécifique à la langue).

1. Dans la barre d’outils, sélectionnez l’option [!UICONTROL paramètres] icône et appuyez sur **[!UICONTROL Ouvrir les propriétés]**.

1. Appuyer **[!UICONTROL Cloud Services]** et appuyez sur **[!UICONTROL Ajouter une configuration]** et sélectionnez **[!UICONTROL Dynamic Media Classic]**.
1. Dans le **[!UICONTROL Adobe Dynamic Media Classic]** dans la liste déroulante, sélectionnez la configuration souhaitée, puis appuyez sur **[!UICONTROL OK]**.

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Les paramètres vidéo prédéfinis de cette configuration de Dynamic Media Classic peuvent être utilisés en Experience Manager avec le composant vidéo Dynamic Media Classic sur cette page et les pages enfants.

#### Activation de Dynamic Media Classic pour WCM dans l’interface utilisateur classique {#enabling-scene-for-wcm-in-the-classic-user-interface}

Pour activer Dynamic Media Classic pour WCM dans l’IU classique :

1. Dans Experience Manager, appuyez sur **[!UICONTROL Sites web]** et accédez à la page racine de votre site web (non spécifique à la langue).

1. Dans le sidekick, appuyez sur **[!UICONTROL Page]** icône et appuyez sur **[!UICONTROL Propriétés de la page]**.

1. Appuyer **[!UICONTROL Cloud Services > Ajouter des services > Dynamic Media Classic]**.
1. Dans le **[!UICONTROL Adobe Dynamic Media Classic]** dans la liste déroulante, sélectionnez la configuration souhaitée, puis appuyez sur **[!UICONTROL OK]**.

   Les paramètres vidéo prédéfinis de cette configuration de Dynamic Media Classic peuvent être utilisés en Experience Manager avec le composant vidéo Dynamic Media Classic sur cette page et les pages enfants.

### Configuration d’une configuration par défaut {#configuring-a-default-configuration}

Si vous disposez de plusieurs configurations Dynamic Media Classic, vous pouvez en spécifier une par défaut pour l’explorateur de contenu Dynamic Media Classic.

Une seule configuration Dynamic Media Classic peut être marquée comme configuration par défaut à un moment donné. La configuration par défaut est les ressources de l’entreprise qui s’affichent par défaut dans le navigateur de contenu Dynamic Media Classic.

Pour configurer la configuration par défaut :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Déploiement > Cloud Services]**, appuyez sur **[!UICONTROL Dynamic Media Classic]**, puis sélectionnez votre configuration dans Dynamic Media Classic.
1. Pour ouvrir la configuration, appuyez sur **[!UICONTROL Modifier]**.

1. Dans le **[!UICONTROL Général]** , sélectionnez la variable **[!UICONTROL Configuration par défaut]** pour en faire la société par défaut et le chemin d’accès racine qui s’affiche dans le navigateur de contenu Dynamic Media Classic.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >S’il n’existe qu’une seule configuration, le fait de cocher la case **[!UICONTROL Configuration par défaut]** est sans effet.

### Configuration du dossier ad hoc {#configuring-the-ad-hoc-folder}

Vous pouvez configurer le dossier vers lequel les ressources sont chargées dans Dynamic Media Classic lorsque la ressource ne se trouve pas dans le dossier cible CQ. Voir Publication de ressources en dehors du dossier cible CQ.

Pour configurer le dossier ad hoc :

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Déploiement > Cloud Services]**, appuyez sur **[!UICONTROL Dynamic Media Classic]**, puis sélectionnez votre configuration dans Dynamic Media Classic.
1. Pour ouvrir la configuration, appuyez sur **[!UICONTROL Modifier]**.

1. Sélectionnez l&#39;onglet **[!UICONTROL Avancé.]** Dans le champ **[!UICONTROL Dossier ad hoc]**, vous pouvez modifier le dossier **ad hoc**. Par défaut, il s’agit de **nom_de_l’entreprise/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Configuration de paramètres prédéfinis universels {#configuring-universal-presets}

Pour configurer les paramètres prédéfinis universels du composant vidéo, voir [Vidéo](/help/assets/s7-video.md).

## Activation de la prise en charge des paramètres de tâche de téléchargement Assets/Dynamic Media Classic basés sur le type MIME {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

Vous pouvez activer les paramètres de tâche de téléchargement Dynamic Media Classic configurables qui sont déclenchés par la synchronisation des ressources Digital Asset Manager/Dynamic Media Classic.

Plus précisément, vous configurez le format de fichier accepté par type MIME dans la zone OSGi (Open Service Gateway Initiative) du panneau Configuration de la console Web du Experience Manager. Vous pouvez ensuite personnaliser les paramètres de tâche de téléchargement individuels utilisés pour chaque type MIME dans le JCR (Java™ Content Repository).

**Pour activer les ressources basées sur le type MIME :**

1. Appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Outils > Opérations > Console web]**.
1. Dans le panneau Configuration de la console Web d’Adobe Experience Manager, sur la page **[!UICONTROL OSGi]** menu, appuyez sur **[!UICONTROL Configuration]**.
1. Sous la colonne Nom, recherchez et appuyez sur **[!UICONTROL Service de type MIME de ressource Dynamic Media Classic Adobe CQ]** pour modifier la configuration.
1. Dans la zone Mappage du type MIME , appuyez sur un signe plus (+) pour ajouter un type MIME.

   Voir [Types MIME pris en charge](/help/assets/assets-formats.md#supported-mime-types).

1. Dans le champ de texte, saisissez le nouveau nom de type MIME.

   Par exemple, vous devez saisir une `<file_extension>=<mime_type>` as in `EPS=application/postscript` OU `PSD=image/vnd.adobe.photoshop`.

1. Dans le coin inférieur droit de la fenêtre de configuration, appuyez sur **[!UICONTROL Enregistrer]**.
1. Revenez à Experience Manager et, dans le rail de gauche, appuyez sur CRXDE Lite.
1. Sur la page du CRXDE Lite, dans le rail de gauche, accédez à `/etc/cloudservices/scene7/<environment>` (substitution) `<environment>` pour le nom réel).
1. Développer `<environment>` (substitution) `<environment>` pour le nom réel) pour afficher la variable `mimeTypes` noeud .
1. Appuyez sur le MIMEType que vous venez d’ajouter.

   Par exemple : `mimeTypes > application_postscript` OU `mimeTypes > image_vnd.adobe.photoshop`.

1. Sur le côté droit de la page du CRXDE Lite, appuyez sur la **[!UICONTROL Propriétés]** .
1. Spécifiez un paramètre de tâche de téléchargement Dynamic Media Classic dans le **[!UICONTROL jobParam]** champ de valeur.

   Par exemple, `psprocess="rasterize"&psresolution=120` .

   Voir [API Adobe Dynamic Media Classic Image Production System](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html) pour plus de paramètres de tâche de téléchargement, vous pouvez utiliser .

   >[!NOTE]
   >
   >Si vous téléchargez des fichiers de PSD et que vous souhaitez les traiter en tant que modèles avec des extractions de calque, saisissez ce qui suit dans la variable **[!UICONTROL jobParam]** champ de valeur :
   >
   >`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`
   >
   >Assurez-vous que votre fichier PSD contient des calques. S’il s’agit strictement d’une image ou d’une image avec masque, elle est uniquement traitée comme une image, car il n’y a aucun calque à traiter.

1. Dans le coin supérieur gauche de la page du CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**.

## Dépannage de l’intégration Dynamic Media Classic et Experience Manager {#troubleshooting-scene-and-aem-integration}

Si vous rencontrez des problèmes pour intégrer Experience Manager à Dynamic Media Classic, reportez-vous aux scénarios suivants pour les solutions.

**Si la publication de ressources numériques sur Dynamic Media Classic échoue :**

* Vérifiez que la ressource que vous essayez de charger se trouve dans la variable **[!UICONTROL Cible CQ]** (vous spécifiez ce dossier dans la configuration cloud de Dynamic Media Classic).
* Si ce n’est pas le cas, vous devez configurer la configuration cloud dans **[!UICONTROL Propriétés de la page]** pour cette page afin d’autoriser le téléchargement vers le **[!UICONTROL CQ ad hoc]** dossier.

* Vérifiez les informations figurant dans les journaux.

**Si vos paramètres vidéo prédéfinis n’apparaissent pas :**

* Assurez-vous que vous avez configuré la configuration cloud de cette page dans la section **[!UICONTROL Propriétés de la page]**. Les paramètres vidéo prédéfinis sont disponibles dans le composant vidéo Dynamic Media Classic.

**Si vos ressources vidéo ne sont pas lues en Experience Manager :**

* Vérifiez que vous avez utilisé le bon composant vidéo. Le composant vidéo Dynamic Media Classic est différent du composant vidéo de base. Voir [Composant vidéo de base et composant vidéo Dynamic Media Classic](/help/assets/s7-video.md).

**Si des ressources nouvelles ou modifiées dans Experience Manager ne sont pas automatiquement chargées vers Dynamic Media Classic :**

* Assurez-vous que les ressources se trouvent dans le dossier cible CQ. Seules les ressources qui se trouvent dans le dossier cible CQ sont automatiquement mises à jour (à condition que vous ayez configuré Experience Manager Assets pour charger automatiquement les ressources).
* Assurez-vous d’avoir configuré la configuration de Cloud Services sur Activer le téléchargement automatique et d’avoir mis à jour et enregistré le workflow Ressources de gestion des actifs numériques pour inclure le chargement de Dynamic Media Classic.
* Lors du téléchargement d’une image dans un sous-dossier du dossier cible Dynamic Media Classic, assurez-vous d’effectuer l’une des opérations suivantes :

   * Assurez-vous que chaque ressource porte un nom unique, indépendamment de son emplacement. Dans le cas contraire, la ressource figurant dans le dossier cible principal est supprimée et seule subsiste la ressource qui se trouve dans le sous-dossier.
   * Modifiez la manière dont Dynamic Media Classic remplace les ressources dans la zone Configuration du compte Dynamic Media Classic. Ne configurez pas Dynamic Media Classic pour remplacer des ressources, quel que soit leur emplacement, si vous utilisez des ressources portant le même nom dans des sous-dossiers.

**Si les ressources ou dossiers supprimés ne sont pas synchronisés entre Dynamic Media Classic et Experience Manager :**

* Les ressources et les dossiers supprimés dans Experience Manager Assets apparaissent toujours dans le dossier synchronisé dans Dynamic Media Classic. Supprimez-les manuellement.

**Si le téléchargement vidéo échoue**

* Si le chargement de votre vidéo échoue et que vous utilisez Experience Manager pour coder la vidéo via l’intégration Dynamic Media Classic, reportez-vous à la section [Ajout d’un délai d’expiration configurable au workflow de téléchargement Dynamic Media Classic](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>L’importation de ressources à partir d’un compte d’entreprise Dynamic Media Classic existant peut prendre un certain temps pour s’afficher dans Experience Manager. Veillez à désigner dans Dynamic Media Classic un dossier qui ne comporte pas trop de ressources (par exemple, le dossier racine comporte souvent trop de ressources).
>
>Si vous souhaitez tester l’intégration, demandez que le dossier racine pointe uniquement vers un sous-dossier, au lieu de l’ensemble de l’entreprise.
