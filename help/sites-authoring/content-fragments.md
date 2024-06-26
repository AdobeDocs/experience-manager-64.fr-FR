---
title: Création de page à partir de fragments de contenu
seo-title: Page Authoring with Content Fragments
description: Les fragments de contenu AEM vous permettent de concevoir, créer, organiser et utiliser du contenu indépendant des pages.
seo-description: AEM Content Fragments allow you to design, create, curate, and use page-independent content
uuid: 66ccdff8-1658-4374-8562-97f81f434488
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 076a3064-80c3-454b-93f9-6ae925c54328
exl-id: bbe4ae86-e9b8-4c3f-ada3-82470e371c4e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 54%

---

# Création de page à partir de fragments de contenu{#page-authoring-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0) ou version ultérieure](/help/release-notes/sp-release-notes.md).

Les fragments de contenu Adobe Experience Manager (AEM) sont [créés et gérés en tant que ressources indépendantes de la page](/help/assets/content-fragments.md).

Ils vous permettent de créer du contenu compatible avec tous les canaux, ainsi que des variations (éventuellement spécifiques aux canaux). Vous pouvez ensuite utiliser ces fragments et leurs variantes lors de la création de vos pages de contenu.

En même temps que l’outil d’exportation JSON mis à jour, les fragments de contenu structuré peuvent également être utilisés pour diffuser du contenu AEM via Content Services à des canaux autres que des pages AEM.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-authoring/experience-fragments.md)** représentent deux fonctions distinctes d’AEM :
>
>* **Fragments de contenu** sont du contenu éditorial, principalement du texte et des images associées. Il s’agit de contenu pur, sans conception ni mise en page.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.

>[!CAUTION]
>
>Cette page doit être consultée en complément de la page [Utilisation de fragments de contenu](/help/assets/content-fragments.md) (et des pages annexes), car elle présente la terminologie et les concepts de base, ainsi que la création et la gestion de fragments.

Les fragments de contenu permettent :

* **Stratégie de marketing et de campagne**

   * Examinez le contenu par le biais de fragments de contenu gérés de manière centralisée.

* **Creative Pro**

   * Suivi des ressources créatives via des collections associées à des fragments de contenu.

* **Copier les rédacteurs**

   * Écrivez dans l’éditeur de fragments de contenu AEM.
   * Peut créer des variations de contenu.
   * Peut associer du contenu pertinent au fragment de contenu.
   * Peut utiliser le contrôle de version/workflow.
   * Peut partager un fragment de contenu.
   * Peut gérer les traductions de manière centralisée.

* **Producteurs et responsable parcours**

   * Effectuez une sélection à partir de fragments et de variations prédéfinis avec la création dans AEM.
   * Peuvent compter sur la mise à jour constante des fragments et du contenu associé à mesure que les auteurs et créatifs effectuent leurs mises à jour dans des fragments et des ressources gérés de manière centralisée.
   * Peuvent compter sur le contenu multimédia associé traité pour être pertinent.
   * Peut créer des variations de contenu ad hoc à la volée tout en s’assurant que ces variations restent gérées de manière centralisée dans le fragment.

## Ajout d’un fragment de contenu à une page {#adding-a-content-fragment-to-your-page}

1. Ouvrez la page à modifier.

1. Ajoutez le composant **[!UICONTROL Fragment de contenu]** à partir du navigateur **[!UICONTROL Composants]** ou **[!UICONTROL Insérer un nouveau composant]**.

1. Vous pouvez effectuer l’une des actions suivantes :

   * Ouvrir l’explorateur de **[!UICONTROL ressources]** et filtrer sur **[!UICONTROL Fragments de contenu]** (la valeur par défaut est Images). Faites ensuite glisser le fragment requis sur l’instance de composant.
   * Sélectionnez le composant de fragment de contenu, puis **[!UICONTROL Configurer]** dans la barre d’outils. Dans la boîte de dialogue, vous pouvez ouvrir la boîte de dialogue de sélection afin de rechercher et de sélectionner le **[!UICONTROL fragment de contenu]** requis.

   >[!NOTE]
   >
   >L’autre méthode consiste à faire glisser un fragment de contenu directement sur la page. Le composant associé est ainsi automatiquement créé (Fragment de contenu).

1. Au début, le contenu des éléments **[!UICONTROL Principal]** et **[!UICONTROL Maître]** (variation) est affiché. Vous pouvez [sélectionner d’autres éléments et/ou variantes](#selecting-the-element-or-variation) en fonction de vos besoins.

   ![cfm-6420-01](assets/cfm-6420-01.png)

   >[!NOTE]
   >
   >Pour plus d’informations sur les autres fonctionnalités d’édition, consultez aussi :
   >
   >* [Mise en page réactive](/help/sites-authoring/responsive-layout.md)
   >* [Modification du contenu de la page](/help/sites-authoring/editing-content.md)


## Sélection de l’élément ou de la variation {#selecting-the-element-or-variation}

Ouvrez la boîte de dialogue **[!UICONTROL Configuration]** du fragment pour configurer le fragment à utiliser dans la page active. La boîte de dialogue peut dépendre du composant utilisé.

Dans la boîte de dialogue de configuration appropriée, vous pouvez sélectionner les paramètres disponibles, notamment :

* **[!UICONTROL Fragment de contenu]**

   Indiquez le fragment à utiliser.

* **[!UICONTROL Mode d’affichage]** :

   * **[!UICONTROL Un seul élément texte]**
   * **[!UICONTROL Plusieurs éléments]**

* **[!UICONTROL Élément]**

   * La valeur par défaut **[!UICONTROL Principal]** sera toujours disponible.
   * Une sélection est disponible si le fragment a été créé avec un modèle approprié.

   >[!NOTE]
   >
   >Les éléments disponibles dépendent du modèle utilisé.

* **[!UICONTROL Variation]**

   * Le **[!UICONTROL maître]** par défaut sera toujours disponible.
   * Une sélection est disponible si des variations ont été créées pour le fragment.

* **[!UICONTROL Paragraphes]**: spécifier la plage de paragraphes à inclure :

   * **[!UICONTROL Tous]**
   * **[!UICONTROL Plage]** : par exemple, `1`, `3-5`, `9-*`

      * **[!UICONTROL Gérer les en-têtes comme leurs propres paragraphes]**

* **[!UICONTROL Gérer les en-têtes comme leurs propres paragraphes]**

## Connexion rapide à l’éditeur de fragment {#quick-connection-to-fragment-editor}

Vous pouvez ouvrir la source du fragment à modifier (la ressource) à l’aide de l’icône **[!UICONTROL Modifier]** située dans la barre d’outils du composant. Vous pourrez ainsi [modifier et gérer le fragment de contenu](/help/assets/content-fragments.md).

>[!CAUTION]
>
>Comme toujours, la modification de la source du fragment affectera toutes les pages qui font référence à ce fragment de contenu.

## Ajout de contenu intermédiaire {#adding-in-between-content}

Lorsqu’un fragment de contenu spécifique est ajouté à la page, un événement **[!UICONTROL Faire glisser des composants ici]** espace réservé entre chaque paragraphe de HTML (et en haut/en bas) du fragment.

Vous pouvez ainsi ajouter du contenu supplémentaire. [intermédiaire (contenu intermédiaire)](/help/assets/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) le contenu du fragment (à l’un des points disponibles), sans avoir à modifier le fragment racine.

Pour le contenu intermédiaire, vous pouvez :

* Ajoutez des composants à partir du [Explorateur de composants](/help/sites-authoring/author-environment-tools.md#components-browser).
* Ajout de ressources à partir de la fonction [Explorateur de ressources](/help/sites-authoring/author-environment-tools.md#assets-browser).
* Utiliser du [contenu associé](#using-associated-content) comme source de contenu intermédiaire.

>[!CAUTION]
>
>Le contenu intermédiaire est du contenu de page. Il n’est pas stocké dans le fragment de contenu.

![cfm-6420-02](assets/cfm-6420-02.png)

>[!NOTE]
>
>Vous pouvez également [insérer des ressources visuelles (images) dans le fragment lui-même ;](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Les ressources visuelles insérées dans le fragment sont jointes au paragraphe précédent dans le fragment. Cela signifie que vous ne pouvez pas placer le contenu intermédiaire entre une ressource visuelle et le paragraphe précédent.

>[!CAUTION]
>
>Une fois le contenu intermédiaire ajouté à un fragment de votre page, la modification de la structure du fragment de contenu sous-jacent (c’est-à-dire dans l’éditeur de fragment de contenu) risque de donner lieu à des résultats erronés/inattendus.
>
>Si cela se produit, le contenu intermédiaire est conservé tel quel :
>
>* Les composants intermédiaires ont une position absolue dans la séquence de composants dans le flux de fragment. Cette position ne change pas, même lorsque le contenu des paragraphes du fragment change.\
   >  Cela peut donner l’impression que le positionnement relatif a changé, dans la mesure où les paragraphes intermédiaires n’ont aucune relation contextuelle avec les paragraphes (de fragment) près desquels ils sont placés.
>* À moins que ces deux structures de paragraphes ne soient en conflit ; dans ce cas, le contenu intermédiaire n’est pas affiché (bien qu’il soit toujours présent en interne).
>


## Utilisation de contenu associé {#using-associated-content}

Si vous avez [associé du contenu](/help/assets/content-fragments-assoc-content.md) au [fragment de contenu](/help/assets/content-fragments.md), ces ressources seront disponibles à partir du panneau latéral (après avoir placé le fragment sur la page de contenu). Le contenu associé est en fait une source spéciale de contenu pour le [contenu intermédiaire](#adding-in-between-content).

>[!NOTE]
>
>Plusieurs méthodes d’ajout [ressources visuelles (images, par exemple)](/help/assets/content-fragments.md#fragments-with-visual-assets) au fragment et/ou à la page.

>[!NOTE]
>
>Si une page contient plusieurs fragments de contenu, la variable **[!UICONTROL Contenu associé]** affiche les ressources appropriées à tous les fragments.

Une fois que vous avez ajouté un fragment avec du contenu associé à votre page, un nouvel onglet (**[!UICONTROL Contenu associé]**) s’ouvre dans le panneau latéral.

Dans cet onglet, vous pouvez faire glisser les ressources vers l’emplacement souhaité (un composant existant ou une position où le composant adéquat sera créé) :

![cfm-6420-03](assets/cfm-6420-03.png)

## Ressources insérées dans le fragment {#assets-inserted-into-the-fragment}

If [Les ressources (images, par exemple) ont été insérées dans le fragment lui-même.](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment), les options de modification de ces ressources dans l’éditeur de page sont limitées.

Dans le cas d’une image, par exemple, vous pouvez effectuer les opérations suivantes :

* Recadrer, faire pivoter ou retourner l’image.
* Ajouter un titre ou un texte secondaire.
* Spécifiez une taille.
* Vous pouvez également configurer la mise en page.

D’autres modifications, telles que le déplacement, la copie et la suppression, doivent être effectuées dans l’éditeur de fragment.

## Publication {#publishing}

Les fragments doivent être publiés pour pouvoir être utilisés dans les pages web que vous avez publiées :

* Un fragment peut être publié une fois [qu’il a été créé dans la console Ressources](/help/assets/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Si un *fragment dépublié* est utilisé dans une page en cours de publication, le fragment peut également être publié à ce moment.
