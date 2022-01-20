---
title: Intégration à Adobe Search&Promote
seo-title: Integrating with Adobe Search&Promote
description: Découvrez comment appliquer l’intégration à Adobe Search&Promote.
seo-description: Learn how to integrate with Adobe Search&Promote.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
exl-id: 2bbcc8d0-c1c7-4901-836f-44b8a2153a46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 53%

---

# Intégration à Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Pour appeler le service Adobe Search&amp;Promote depuis votre site web, effectuez les opérations suivantes :

1. Indiquez l’URL du cloud.
1. Configurez la connexion au service Search&amp;Promote.
1. Ajouter des composants de Search &amp; Promote à [!UICONTROL Sidekick].
1. Utilisez les composants pour créer le contenu. (Voir [Ajout de fonctionnalités Search&amp;Promote à une page web](/help/sites-authoring/search-and-promote.md).)
1. Ajout de bannières à vos pages. Les images de bannière sont sensibles aux données Search&amp;Promote.
1. Générez un plan du site pour l’utilisation du service Search&amp;Promote.

>[!NOTE]
>
>Si vous utilisez Search&amp;Promote avec une configuration de proxy personnalisée, vous devez configurer les deux configurations de proxy client HTTP, car certaines fonctionnalités d’AEM utilisent les API 3.x et d’autres les API 4.x :
>
>* La version 3.x est configurée avec [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* Les API 4.x sont configurées avec [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>


## Modification de l’URL du service Search&amp;Promote {#changing-the-search-promote-service-url}

L’URL par défaut configurée pour le service Search &amp; Promote est `https://searchandpromote.omniture.com/px/`. Pour utiliser un autre service, utilisez la console OSGi afin de spécifier une autre URL.

**Pour modifier l’URL du service Search &amp; Promote**:

1. Ouvrez le [!UICONTROL OSGi] puis appuyez sur la console **[!UICONTROL Configuration]** . ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Cliquez sur le bouton **[!UICONTROL Configuration des Search &amp; Promote Day CQ]** élément .
1. Dans le **[!UICONTROL URI de serveur distant]** Champ de texte, saisissez l’URL, puis appuyez sur **[!UICONTROL Enregistrer]**.

## Configuration de la connexion à Search&amp;Promote {#configuring-the-connection-to-search-promote}

Configurez une ou plusieurs connexions à Search&amp;Promote afin que vos pages web puissent interagir avec le service. Pour vous connecter, vous avez besoin du numéro d’identification et de compte du membre de votre compte Search&amp;Promote.

**Pour configurer la connexion à Search &amp; Promote**:

1. Dans la **[!UICONTROL Outils]** icon > **[!UICONTROL Déploiement]**, sélectionnez **[!UICONTROL Cloud Services]**.

   Ceci vous amène au tableau de bord Services Cloud. Si vous utilisez un ordinateur local, l’URL du tableau de bord se présente comme suit :

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Dans le [!UICONTROL Cloud Services] , appuyez sur **[!UICONTROL Search &amp; Promote Adobe]** ou le lien **[!UICONTROL Search &amp; Promote]** icône .

1. S’il s’agit de la première fois que vous configurez le Search &amp; Promote Adobe, appuyez sur **[!UICONTROL Configurer maintenant]** pour ouvrir le [!UICONTROL Créer une configuration] du panneau.

   Si vous souhaitez en savoir plus sur les clics Search &amp; Promote **[!UICONTROL En savoir plus]** au lieu de .

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. Saisissez un **[!UICONTROL Titre]** qui est reconnaissable par les auteurs de pages, et saisissez une valeur unique **[!UICONTROL Nom]**, puis appuyez sur **[!UICONTROL Créer]**.

   De plus, la configuration nouvellement créée apparaît sous **[!UICONTROL Configurations disponibles]** dans l’élément de liste Adobe Search&amp;Promote **[!UICONTROL Tableau de bord Services cloud]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Dans le [!UICONTROL Modifier le composant] , ajoutez les éléments suivants aux champs :

   * **[!UICONTROL ID de membre]**
   * **[!UICONTROL Numéro de compte]**

   >[!NOTE]
   >
   >Pour obtenir ces informations vous-même, connectez-vous aux éléments suivants :
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >à l’aide de vos identifiants Search&amp;Promote (adresse électronique/mot de passe) valides.
   >
   >Notez l’URL dans la barre d’adresse de votre navigateur. Il doit ressembler à ce qui suit :
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >Où **XXXXXX** correspond à votre **[!UICONTROL Identifiant du membre]** et **[!UICONTROL spYYYYYY]** correspond à votre numéro de compte.

1. Appuyer **[!UICONTROL Connexion à Search &amp; Promote]**.

   Lorsque le message de réussite de la connexion s’affiche, appuyez sur **[!UICONTROL OK]**.

   (Une fois que vous êtes connecté, le texte du bouton est remplacé par **[!UICONTROL Reconnecter à Search&amp;Promote]**.)

1. Appuyez sur **[!UICONTROL OK]**. La page Paramètres Search&amp;Promote s’affiche pour la configuration que vous venez de créer.

## Configuration du centre de données {#configuring-the-data-center}

Si votre compte de Search &amp; Promote se trouve en Asie ou en Europe, vous devez modifier le centre de données par défaut afin qu’il pointe vers le bon (le centre de données par défaut est destiné aux comptes nord-américains).

**Pour configurer le centre de données**:

1. Accédez à la console Web à l’adresse `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. En fonction de l’emplacement du serveur, redéfinissez l’URI sur l’une des URI suivantes :

   * Amérique du Nord : [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA : [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC : [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Appuyez sur **[!UICONTROL Enregistrer]**.

## Ajout de composants Search&amp;Promote au sidekick {#adding-search-promote-components-to-sidekick}

Dans [!UICONTROL Conception] mode, modifier une **[!UICONTROL par]** pour autoriser les composants de Search &amp; Promote dans [!UICONTROL Sidekick]. (Voir la documentation [Composants](/help/sites-developing/components.md) pour en savoir plus.)

Pour plus d’informations sur l’utilisation des composants, voir [Ajout de fonctions de Search &amp; Promote à une page web](/help/sites-authoring/search-and-promote.md).

## Spécification du service Search&amp;Promote utilisé par vos pages {#specifying-the-search-promote-service-that-your-pages-use}

Configurez les pages web afin qu’elles utilisent un service Search&amp;Promote spécifique. Les composants Search&amp;Promote utilisent automatiquement le service de leur page hôte.

Lorsque vous configurez les propriétés Search&amp;Promote d’une page, toutes les pages enfants héritent des paramètres. Si nécessaire, vous pouvez configurer les pages enfants pour remplacer les paramètres hérités.

>[!NOTE]
>
>La connexion au service doit déjà être configurée. Voir [Configuration de la connexion à Search&amp;Promote](#configuring-the-connection-to-search-promote).

1. Ouvrez la boîte de dialogue **[!UICONTROL Propriétés de la page]**. Par exemple, sur la page **[!UICONTROL Sites Web]**, cliquez avec le bouton droit sur la page et cliquez sur **[!UICONTROL Propriétés]**.

1. Cliquez sur l’onglet **[!UICONTROL Services Cloud]**.

1. Pour désactiver l’héritage des configurations des services cloud d’une page parent, cliquez sur l’icône en forme de cadenas en regard du chemin d’héritage.

   ![sandpinheritpadlock](assets/sandpinheritpadlock.png)

1. Cliquez sur **[!UICONTROL Ajouter un service]**, sélectionnez **[!UICONTROL Search &amp; Promote Adobe]**, puis cliquez sur **[!UICONTROL OK]**.

1. Sélectionnez la configuration de la connexion pour votre compte Search &amp; Promote, puis cliquez sur **[!UICONTROL OK]**.

## Flux de produit {#product-feed}

L&#39;intégration de Search &amp; Promote permet d&#39;effectuer les opérations suivantes :

* Utilisez la variable [!UICONTROL eCommerce] API, indépendamment de la structure de référentiel sous-jacente et de la plateforme commerciale.
* Tirer parti de [!UICONTROL Connecteur d’index] fonction de Search &amp; Promote permettant de fournir un flux de produit au format XML.
* Tirer parti de [!UICONTROL Contrôle à distance] de Search &amp; Promote pour effectuer des demandes à la demande ou planifiées du flux de produits.
* Génération de flux pour différents comptes de Search &amp; Promote, configurés en tant que configurations de services cloud.

Pour plus d’informations, voir [Flux de produit](/help/sites-administering/product-feed.md).
