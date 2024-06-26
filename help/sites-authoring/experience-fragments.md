---
title: Fragments d’expérience
seo-title: Experience Fragments
description: Fragments d’expérience
seo-description: null
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
exl-id: 8906b3ab-cb08-4b3e-8796-334e36b1e491
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 59%

---

# Fragments d’expérience {#experience-fragments}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Un fragment d’expérience est un groupe d’un ou plusieurs composants comprenant un contenu et une disposition pouvant être référencés dans les pages. Ils peuvent contenir n’importe quel composant.

Un fragment d’expérience :

* Fait partie d’une expérience (page).
* Peut être utilisé sur plusieurs pages.
* est basé sur un modèle (modifiable uniquement) pour définir la structure et les composants ;
* est constitué d’un ou de plusieurs composants, avec mise en page, dans un système de paragraphes ;
* Peut contenir d’autres fragments d’expérience.
* Peut être combiné à d’autres composants (y compris d’autres fragments d’expérience) pour former une page complète (expérience).
* Peut avoir différentes variations, qui peuvent partager du contenu et/ou des composants.
* peut être scindé en blocs de création utilisables dans plusieurs variations du fragment.

Vous pouvez utiliser des fragments d’expérience :

* Si un auteur souhaite réutiliser des parties (un fragment d’expérience) d’une page, il doit copier et coller ce fragment. La création et la gestion de ces expériences de copier/coller sont chronophages et sources d’erreurs pour l’utilisateur. Les fragments d’expérience rendent inutiles les opérations de copier/coller.
* Pour prendre en charge le scénario d’utilisation de CMS découplé. Les auteurs souhaitent utiliser AEM uniquement dans une optique de création, mais pas pour diffuser du contenu au client. Un système/point de contact tiers utilise cette expérience, puis la diffuse à l’utilisateur final ou l’utilisatrice finale.

>[!NOTE]
>
>Dans le cas des fragments d’expérience, l’accès en écriture exige que le compte utilisateur soit enregistré dans le groupe :
>
>`experience-fragments-editors`
>
>Si vous rencontrez des problèmes, contactez votre administrateur système.

## Quand utiliser les fragments d’expérience ? {#when-should-you-use-experience-fragments}

Les fragments d’expérience doivent être utilisés :

* Lorsque vous souhaitez réutiliser des expériences.

   * Expériences qui seront réutilisées avec un même contenu ou un contenu similaire

* Lorsque vous utilisez AEM en tant que plateforme de diffusion de contenu à des tiers.

   * Toute solution qui souhaite utiliser AEM comme plateforme de diffusion de contenu
   * Intégration de contenu dans des points de contact tiers

* Si vous disposez d’une expérience avec des variations ou des rendus différents.

   * Variations spécifiques au canal ou au contexte
   * Expériences qu’il est logique de regrouper (par exemple, une campagne avec des expériences différentes sur plusieurs canaux)

* Lorsque vous avez recours au commerce omnicanal.

   * Partage de contenu commercial sur les canaux des réseaux sociaux à grande échelle
   * Conversion des points de contact en points de transaction

## Organisation des fragments d’expérience {#organizing-your-experience-fragments}

Nous vous encourageons à :
* utiliser des dossiers pour organiser vos fragments d’expérience ;

* [configurer les modèles autorisés sur ces dossiers](#configure-allowed-templates-folder).

La création de dossiers vous permet d’effectuer les opérations suivantes :

* Créer une structure significative pour vos fragments d’expérience ; en fonction de la classification, par exemple

   >[!NOTE]
   >
   >Il n’est pas nécessaire d’aligner la structure de vos fragments d’expérience sur la structure de page de votre site.

* [Allouer les modèles autorisés au niveau du dossier](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Vous pouvez utiliser l’[éditeur de modèles](/help/sites-authoring/templates.md) pour créer votre propre modèle.

L’exemple suivant illustre les fragments d’expérience structurés en fonction de `Contributors`. La structure utilisée illustre également l’utilisation d’autres fonctionnalités, telles que la gestion multisite (y compris des copies de langue).

>[!CAUTION]
>
>La capture d’écran suivante a été tirée du site WKND à l’aide d’Adobe Experience Manager as a Cloud Service.

![Dossiers des fragments d’expérience](assets/xf-folders.png)

## Création et configuration d’un dossier pour vos fragments d’expérience {#creating-and-configuring-a-folder-for-your-experience-fragments}

Pour créer et configurer un dossier pour vos fragments d’expérience, il est recommandé de :

1. [Créer un dossier](/help/sites-authoring/managing-pages.md#creating-a-new-folder)

1. [Configurer les modèles de fragments d’expérience autorisés pour ce dossier](#configure-allowed-templates-folder)

>[!NOTE]
>
>Il est également possible de configurer la variable [Modèles autorisés pour votre instance](#configure-allowed-templates-instance), mais cette méthode est la suivante : **not** recommandé, car les valeurs peuvent être remplacées lors de la mise à niveau.

### Configuration des modèles autorisés pour votre dossier {#configure-allowed-templates-folder}

>[!NOTE]
>
>Il s’agit de la méthode recommandée pour spécifier les **[!UICONTROL Modèles autorisés]**, car les valeurs ne sont pas remplacées lors de la mise à niveau.

1. Accédez au dossier **[!UICONTROL Fragments d’expérience]** concerné.

1. Sélectionnez le dossier, puis **[!UICONTROL Propriétés]**.

1. Spécifiez l’expression régulière pour récupérer les modèles requis dans le champ **[!UICONTROL Modèles autorisés]**.

   Par exemple :
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![Propriétés des fragments d’expérience – Modèles autorisés](assets/xf-folders-templates.png)

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]**.

### Configuration des modèles autorisés pour votre instance {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Il n’est pas recommandé de modifier la variable **[!UICONTROL Modèles autorisés]** par cette méthode, car les modèles spécifiés peuvent être écrasés lors de la mise à niveau.
>
>Veuillez utiliser cette boîte de dialogue uniquement à titre d’information.

1. Accédez à la console **[!UICONTROL Fragments d’expérience]** concernée.

1. Sélectionnez **[!UICONTROL Options de configuration]** :

   ![Bouton Configuration](assets/xf-folders-18.png)

1. Spécifiez les modèles requis dans la boîte de dialogue **[!UICONTROL Configurer des Fragments d’expérience]** :

   ![Configurer des fragments d’expérience](assets/xf-folders-19.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

## Création d’un fragment d’expérience {#creating-an-experience-fragment}

Pour créer un fragment d’expérience :

1. Sélectionnez **[!UICONTROL Fragments d’expérience]** dans la navigation globale.

   ![screen_shot_2018-04-05at92221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. accédez au dossier requis et sélectionnez ensuite **[!UICONTROL Créer]** ;

1. Sélectionnez **[!UICONTROL Fragment d’expérience]** pour ouvrir l’assistant **[!UICONTROL Créer un fragment d’expérience]**.

   Sélectionnez le **[!UICONTROL Modèle]** requis, puis **[!UICONTROL Suivant]** :

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. Renseignez les **[!UICONTROL Propriétés]** de votre Fragment d’expérience.

   A **[!UICONTROL Titre]** est obligatoire. Si la variable **[!UICONTROL Nom]** n’est pas renseigné, il est dérivé de la variable **[!UICONTROL Titre]**.

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. Cliquez sur **[!UICONTROL Créer]**.

   Un message s’affiche. Sélectionnez :

   * **[!UICONTROL Terminé]** pour revenir à la console
   * **[!UICONTROL Ouvrir]** pour ouvrir l’éditeur de fragments

## Modification d’un fragment d’expérience {#editing-your-experience-fragment}

L’éditeur de fragment d’expérience vous offre des fonctionnalités similaires à celles de l’éditeur de page normal. Voir [Modification du contenu de la page](/help/sites-authoring/editing-content.md) pour plus d’informations sur son utilisation.

L’exemple de procédure suivant illustre la création d’un teaser pour un produit :

1. Faites glisser et déposez un **[!UICONTROL Teaser de catégorie]** de la [Explorateur de composants](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. Sélectionner **[[!UICONTROL Configurer]](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)** dans la barre d’outils du composant.
1. Ajoutez la **[!UICONTROL ressource]** et définissez les **[!UICONTROL propriétés]** selon vos besoins.
1. Confirmez les définitions avec **[!UICONTROL Terminé]** (icône de coche).
1. Ajoutez d’autres composants, en fonction de vos besoins.

## Création d’une variation de fragment d’expérience {#creating-an-experience-fragment-variation}

Vous pouvez créer des variantes de votre fragment d’expérience en fonction de vos besoins :

1. Ouvrez votre fragment pour [édition](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Ouvrez l’onglet **[!UICONTROL Variations]**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **Créer** vous permet de créer les éléments suivants :

   * **[!UICONTROL Variation]**
   * **[!UICONTROL Variation en tant que Live Copy]**.

1. Définissez les propriétés requises :

   * **[!UICONTROL Modèle]**
   * **[!UICONTROL Titre]**
   * **[!UICONTROL Nom]**; Si rien n’est indiqué, il est dérivé du titre
   * **[!UICONTROL Description]**
   * **[!UICONTROL Balises de variation]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. Confirmez en cliquant sur **[!UICONTROL Terminé]** (icône représentant une coche). La nouvelle variation est alors affichée dans le panneau :

   ![xf-authoring-08](assets/xf-authoring-08.png)

## Utilisation du fragment d’expérience {#using-your-experience-fragment}

Vous pouvez désormais utiliser votre fragment d’expérience lors de la création de vos pages :

1. Ouvrez une page à modifier.

   Par exemple : [http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. Créez une instance du composant Fragment d’expérience. Pour ce faire, faites glisser le composant sur le système de paragraphes de la page depuis l’explorateur de composants :

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. Ajoutez le fragment d’expérience proprement dit à l’instance de composant. Pour ce faire, vous pouvez effectuer l’une des opérations suivantes :

   * Faites glisser le fragment requis depuis l’Explorateur de ressources sur le composant.
   * Sélectionnez **[!UICONTROL Configurer]** dans la barre d’outils du composant et indiquez le fragment à utiliser. Confirmez en cliquant sur **Terminé** (icône représentant une coche).

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >L’option Modifier disponible dans la barre d’outils du composant sert de raccourci pour ouvrir le fragment dans l’éditeur de fragments.

## Blocs de création {#building-blocks}

Vous pouvez sélectionner un ou plusieurs composants pour créer un bloc de création à recycler dans votre fragment :

### Création d’un bloc de création {#creating-a-building-block}

Pour créer un bloc de création :

1. Dans l’éditeur de fragments d’expérience, sélectionnez les composants à réutiliser :

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. Dans la barre d’outils des composants, sélectionnez **[!UICONTROL Convertir en bloc de création]** :

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   Par exemple :

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. Saisissez le nom du **[!UICONTROL Bloc de création]** et confirmez en cliquant sur **[!UICONTROL Convertir]** :

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. Le **bloc de création** s’affiche dans l’onglet et peut être sélectionné dans le système de paragraphe :

   ![xf-authoring-15](assets/xf-authoring-15.png)

### Gestion d’un bloc de création {#managing-a-building-block}

Votre bloc de création est visible dans la variable **[!UICONTROL Blocs de création]** . Pour chaque bloc, les actions disponibles sont les suivantes :

* Atteindre l’élément principal : ouvre la variation principale dans un nouvel onglet
* Renommer
* Supprimer

![xf-authoring-16](assets/xf-authoring-16.png)

### Utilisation d’un bloc de création {#using-a-building-block}

Vous pouvez faire glisser votre bloc de création vers le système de paragraphes de n’importe quel fragment, comme avec n’importe quel composant.

## Rendu HTML brut {#the-plain-html-rendition}

Le sélecteur `.plain.` de l’URL permet d’accéder au rendu HTML brut.

Cette option est disponible à partir du navigateur, mais son Principal objectif est d’autoriser d’autres applications (par exemple, des applications web tierces et des implémentations mobiles personnalisées) à accéder directement au contenu du fragment d’expérience, en utilisant uniquement l’URL.

Le rendu en HTML brut ajoute le protocole, l’hôte et le chemin d’accès contextuel aux chemins suivants :

* sont du type `src`, `href` ou `action` ;

* se terminent par `-src` ou `-href`.

Par exemple :

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Les liens font toujours référence à l’instance de publication. Elles sont destinées à être utilisées par des tiers. Par conséquent, le lien sera toujours appelé à partir de l’instance de publication, et non de l’auteur.

![xf-authoring-17](assets/xf-authoring-17.png)

## Exportation de fragments d’expérience {#exporting-experience-fragments}

Par défaut, les fragments d’expérience sont fournis au format HTML. Cela peut être utilisé à la fois par les canaux AEM et tiers.

Pour l’exportation vers Adobe Target, le HTML est utilisé. Pour obtenir des informations complètes, consultez [Intégration de Target aux fragments d’expérience](/help/sites-administering/experience-fragments-target.md).
