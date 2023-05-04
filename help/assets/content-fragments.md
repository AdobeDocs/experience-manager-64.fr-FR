---
title: Utilisation de fragments de contenu
seo-title: Working with Content Fragments
description: Découvrez comment les fragments de contenu vous permettent de concevoir, créer, organiser et utiliser du contenu indépendant des pages.
seo-description: Learn how Content Fragments allow you to design, create, curate and use page-independent content.
uuid: aa5acda2-4c20-4fe7-929d-6c065b252cf2
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 22ae0d3a-083f-40e4-bf4a-7a755ae9e312
exl-id: e2804707-7b75-4fae-937e-9e258481878f
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 53%

---

# Utilisation de fragments de contenu {#working-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0) ou version ultérieure](/help/release-notes/sp-release-notes.md).

Les fragments de contenu Adobe Experience Manager (AEM) vous permettent de concevoir, créer, organiser et [publier du contenu indépendant des pages](/help/sites-authoring/content-fragments.md). Ils permettent de préparer le contenu prêt à être utilisé dans des emplacements multiples/sur plusieurs canaux.

Les fragments de contenu peuvent également être diffusés au format JSON, à l’aide des fonctionnalités d’exportation du modèle Sling (JSON) des composants principaux d’AEM. Cette forme de diffusion :

* permet d’utiliser le composant pour gérer les éléments d’un fragment à diffuser.
* permet la diffusion en masse, en ajoutant plusieurs composants principaux de fragments de contenu sur la page utilisée pour la diffusion de l’API.

Cette page et les suivantes portent sur les tâches de création, de configuration et de gestion de vos fragments de contenu :

* [Gestion des fragments de contenu](content-fragments-managing.md)    : créez des fragments de contenu, puis modifiez-les, publiez-les et référencez-les.

* [Modèles de fragment de contenu](content-fragments-models.md) : activation, création et définition de vos modèles.

* [Variations – création de fragments de contenu](content-fragments-variations.md) : créez le contenu du fragment et créez des variantes du maître.

* [Texte (Markdown)](content-fragments-markdown.md) : utilisation de la syntaxe Markdown pour votre fragment.

* [Utilisation du contenu associé](content-fragments-assoc-content.md) : ajout de contenu associé.

* [Métadonnées – propriétés des fragments](content-fragments-metadata.md) : affichage et modification des propriétés des fragments.

>[!NOTE]
>
>Ces pages devraient être lues conjointement à [Création de pages avec des fragments de contenu](/help/sites-authoring/content-fragments.md).

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique; par exemple, bureau, mobile.
* Forme de diffusion sur un canal physique ; par exemple, la &quot;page des détails du produit&quot;, la &quot;page de catégorie de produit&quot; pour ordinateur de bureau ou &quot;web mobile&quot;, &quot;application mobile&quot; pour mobile.

Cependant, vous ne souhaitez (probablement) pas utiliser exactement le même contenu pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

Les fragments de contenu vous permettent d’effectuer les opérations suivantes :

* Étudions comment atteindre efficacement les audiences cibles sur plusieurs canaux.
* Créez et gérez du contenu éditorial neutre pour les canaux.
* Créez des pools de contenu pour divers canaux.
* Concevez des variations de contenu pour des canaux spécifiques.
* Ajoutez des images à votre texte en insérant des ressources (fragments de supports variés).

Ces fragments de contenu peuvent ensuite être assemblés pour offrir diverses expériences sur de multiples canaux.

## Fragments de contenu et services de contenu {#content-fragments-and-content-services}

AEM Content Services est conçu pour généraliser la description et la diffusion de contenu dans/à partir d’AEM à des canaux autres que des pages web.

Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients. Ces canaux peuvent inclure :

* des applications sur une seule page ;
* des applications mobiles natives ;
* d’autres canaux et points de contact externes à AEM.

La diffusion est effectuée au format JSON.

Les fragments de contenu AEM peuvent être utilisés pour décrire et gérer du contenu structuré. Le contenu structuré est défini dans des modèles qui peuvent contenir divers types de contenu ; texte, données numériques, valeur booléenne, date et heure, etc.

Associé aux fonctionnalités d’exportation JSON des composants de base AEM, ce contenu structuré peut ensuite être utilisé pour livrer le contenu AEM à des canaux autres que les pages AEM.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-authoring/experience-fragments.md)** représentent deux fonctions distinctes d’AEM :
>
>* **Fragments de contenu** sont du contenu éditorial, principalement du texte et des images associées. Il s’agit de contenu pur, sans conception ni mise en page.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir également [Présentation des fragments de contenu et des fragments d’expérience dans AEM](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>Les fragments de contenu ne sont pas disponibles dans l’IU classique.
>
>Le composant Fragment de contenu est visible dans le sidekick de l’interface utilisateur classique, mais aucune fonctionnalité supplémentaire n’est disponible.

>[!NOTE]
>
>AEM prend également en charge la traduction des fragments de contenu. Voir [Création de projets de traduction pour des fragments de contenu](creating-translation-projects-for-content-fragments.md) pour plus d’informations.

## Types de fragments de contenu {#types-of-content-fragment}

Les fragments de contenu peuvent être comme suit :

* Fragments simples

   * Ils n’ont pas de structure prédéfinie. Ils contiennent uniquement du texte et des images.
   * Ils sont basés sur le modèle de fragment simple.

* Fragments présentant du contenu structuré

   * Ils sont basés sur un [modèle de fragment de contenu](content-fragments-models.md), servant à prédéfinir une structure pour le fragment résultant.
   * Ils peuvent également être utilisés pour réaliser des Content Services à l’aide de l’exportateur JSON.

## Type de contenu {#content-type}

Les fragments de contenu sont :

* stockés en tant que **ressources** :

   * Les fragments de contenu (et leurs variations) peuvent être créés et conservés à partir de la fonction **Ressources** console.
   * Créés et modifiés dans l’éditeur de fragment de contenu.

* Utilisés dans l’[éditeur de page au moyen du composant Fragment de contenu](/help/sites-authoring/content-fragments.md) (qui fait référence au composant) :

   * Le composant **Fragment de contenu** est disponible pour les créateurs de pages. Il leur permet de référencer et de livrer le fragment de contenu requis au format HTML ou JSON.

Les fragments de contenu sont une structure de contenu qui :

* ne sont pas mises en page ou mises en page (certaines mises en forme de texte sont possibles en mode Texte enrichi) ;
* Contenir un ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* Peut [contenir des images ou être connecté à celles-ci ;](#fragments-with-visual-assets).
* peut utiliser du [contenu intermédiaire](#in-between-content-when-page-authoring-with-content-fragments) en cas de référencement sur une page ;

* est indépendant du mécanisme de livraison (c’est-à-dire de la page ou du canal).

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour donner aux auteurs plus de contrôle sur leur contenu, il est possible d’ajouter et/ou d’intégrer des images à un fragment de contenu.

Les ressources peuvent être utilisées avec un fragment de contenu de plusieurs façons ; chacune présentant ses propres avantages :

* **Insérer une ressource** dans un fragment (fragments de supports variés)

   * font partie intégrante du fragment (voir [Parties constituantes d’un fragment de contenu](#constituent-parts-of-a-content-fragment)).
   * Définissez la position de la ressource.
   * Voir [Insertion de ressources dans votre fragment](content-fragments-variations.md#inserting-assets-into-your-fragment) dans l’éditeur de fragments pour plus d’informations.

   >[!NOTE]
   >
   >Les ressources visuelles insérées dans le fragment de contenu sont liées au paragraphe précédent. Lorsque le fragment est ajouté à une page, ces ressources sont déplacées avec le paragraphe en question lorsque du contenu intermédiaire est ajouté.

* **Contenu associé**

   * sont connectés à un fragment ; mais pas une partie fixe du fragment (voir [Parties constituantes d’un fragment de contenu](#constituent-parts-of-a-content-fragment)).
   * Permettent une certaine souplesse de positionnement.
   * Sont facilement disponibles pour utilisation (comme contenu intermédiaire) lors de l’utilisation du fragment sur une page.
   * Voir [Contenu associé](content-fragments-assoc-content.md) pour plus d’informations.

* Ressources disponibles dans le **navigateur Ressources** de l’éditeur de page

   * Permettent une flexibilité totale pour la sélection d’une ressource.
   * Permettent une certaine souplesse de positionnement.
   * N’appliquent pas le concept d’approbation pour un fragment spécifique.
   * Voir [Explorateur de ressources](/help/sites-authoring/author-environment-tools.md#assets-browser) pour plus d’informations.

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources de fragment de contenu se composent des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Pour les fragments avec du contenu structuré, vous utilisez un modèle de contenu pour créer le fragment de contenu. Les éléments (champs) spécifiés dans le modèle définissent la structure du fragment. Ces éléments (champs) peuvent être de différents types de données.
   * Pour les fragments simples :

      * Le contenu est conservé dans un ou plusieurs champs de texte multiligne ou éléments.
      * Les éléments sont définis dans le modèle de fragment (ils ne peuvent pas être définis lors de la création du fragment, voir [Modèles de fragment de contenu](/help/sites-developing/content-fragment-templates.md)).

* **Paragraphes de fragment**

   * Des blocs de texte, qui sont :

      * séparés par des espaces verticaux (retour chariot) ;
      * dans des éléments de texte multiligne ; au sein de fragments simples ou structurés.
   * Dans les modes [Texte enrichi](content-fragments-variations.md#rich-text) et [Markdown](content-fragments-variations.md#markdown), un paragraphe peut être formaté en tant qu’en-tête, auquel cas celui-ci et le paragraphe suivant sont considérés comme une unité.
   * Activez le contrôle du contenu lors de la création de pages.


* **Ressources insérées dans un fragment (fragments de supports variés)**

   * Ressources (images) insérées dans le fragment et utilisées en tant que contenu interne d’un fragment.
   * Sont intégrées dans le système de paragraphe du fragment.
   * Peut être formaté lorsque la variable [fragment utilisé/référencé sur une page](/help/sites-authoring/content-fragments.md).
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide de l’éditeur de fragment. Ces actions ne peuvent pas être effectuées dans l’éditeur de page.
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide de [Format Texte enrichi dans l’éditeur de fragments](content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Peuvent uniquement être ajoutées aux éléments de texte multiligne (tout type de fragment).
   * Sont liées au texte précédent (paragraphe).

   >[!CAUTION]
   >
   >Peut être supprimé d’un fragment (par inadvertance) en passant au format Texte brut .

   >[!NOTE]
   >
   >Les ressources peuvent également être ajoutées en tant que [contenu supplémentaire (intermédiaire)](/help/sites-authoring/content-fragments.md#using-associated-content) lors de l’utilisation d’un fragment sur une page ; à l’aide du contenu associé ou des ressources de l’explorateur de ressources.

* **Contenu associé**

   * Il s’agit d’un contenu externe à un fragment, mais présentant une pertinence éditoriale pour celui-ci. En règle générale, images, vidéos ou autres fragments.
   * Les ressources individuelles de la collection peuvent être utilisées avec le fragment dans l’éditeur de page lorsqu’il est ajouté à une page. Cela signifie qu’elles sont facultatives, selon les exigences du canal spécifique.
   * Les ressources sont [associées aux fragments via des collections](content-fragments-assoc-content.md) ; les collections associées permettent à l’auteur de déterminer les ressources à utiliser lors de la création d’une page.

      * Les collections peuvent être associées à des fragments via des modèles, en tant que contenu par défaut, ou par les auteurs lors de la création de fragments.
      * [Collections de ressources (DAM)](managing-collections-touch-ui.md) sont la base du contenu associé des fragments.
   * Vous pouvez également ajouter le fragment lui-même à une collection pour faciliter le suivi.


* **Métadonnées de fragment**

   * Utilisez la variable [Schémas de métadonnées Assets](metadata.md).
   * Les balises peuvent être créées lorsque vous :

      * Création et création du fragment
      * Ou plus tard :

         * En affichant/modifiant le fragment **Propriétés** depuis la console
         * En modifiant les **Métadonnées** dans l’éditeur de fragments

   >[!CAUTION]
   >
   >Les profils de traitement des métadonnées ne s’appliquent pas aux fragments de contenu.

* **Maître**

   * Partie intégrante du fragment

      * Chaque fragment de contenu comporte une instance de Principal.
      * Le Principal ne peut pas être supprimé.
   * L’instance maître est accessible dans l’éditeur de fragment sous **[Variations](content-fragments-variations.md)**.
   * L’instance maître n’est pas une variation en tant que telle, mais plutôt la base de toutes les variations.


* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * Sont créées en tant que copies de l’instance **maître**, mais peuvent ensuite être modifiées si besoin. Il existe généralement un chevauchement de contenu entre les différentes variations.
   * Peuvent être définies lors de la création de fragments ou prédéfinies dans des modèles de fragments.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [synchronisé](content-fragments-variations.md#synchronizing-with-master) par Principal si le contenu du Principal a été mis à jour.
   * Peuvent être [résumées](content-fragments-variations.md#summarizing-text) afin de tronquer rapidement le texte sur une longueur prédéfinie.
   * Disponibles sous l’onglet [Variations](content-fragments-variations.md) de l’éditeur de fragment.

### Contenu intermédiaire lors de la création de page avec des fragments de contenu {#in-between-content-when-page-authoring-with-content-fragments}

Contenu intermédiaire :

* Il est disponible dans l’[éditeur de page lorsque vous utilisez des fragments de contenu](/help/sites-authoring/content-fragments.md).
* Il s’agit de [contenu supplémentaire ajouté dans le flux d’un fragment](/help/sites-authoring/content-fragments.md#adding-in-between-content) une fois qu’il a été utilisé ou référencé sur une page.
* Le contenu intermédiaire peut être ajouté à n’importe quel fragment, où seul un élément est visible.
* Le contenu associé peut être utilisé, de même que les ressources et/ou les composants du navigateur approprié.

>[!CAUTION]
>
>Le contenu intermédiaire est du contenu de page. Il n’est pas stocké dans le fragment de contenu.

### Conditions requises pour utiliser des fragments {#required-by-fragments}

Pour créer, modifier et utiliser des fragments de contenu, vous aurez également besoin des éléments suivants :

* **Modèles de contenu**

   * Are [activé puis créé à l’aide des outils](content-fragments-models.md).
   * Obligatoire pour [création d’un fragment structuré](content-fragments-managing.md#creating-content-fragments).
   * Définissent la structure d’un fragment (titre, éléments de contenu et définitions de balise).
   * Les définitions de modèles de contenu requièrent un titre et un élément de données ; tous les autres attributs sont facultatifs. Le modèle définit une portée minimale du fragment et du contenu par défaut, le cas échéant. Les auteurs ne peuvent pas modifier la structure définie lors de la création du contenu d’un fragment.

* **Modèle de fragment**

   * Obligatoire pour [création d’un fragment simple](content-fragments-managing.md#creating-content-fragments).
   * Généralement [développé pendant la mise en oeuvre du projet](/help/sites-developing/content-fragment-templates.md); ne peut pas être créé lors de la création.
   * Définit les propriétés de base d’un fragment simple (titre, nombre d’éléments de texte, définitions de balises).
   * Les définitions de modèle nécessitent un titre et un élément de texte ; tout le reste est facultatif. Le modèle définit une portée minimale du fragment et du contenu par défaut, le cas échéant. Les auteurs peuvent ultérieurement étendre un fragment au-delà de ce qui a été défini dans le modèle.

* **Composant de fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML et/ou JSON.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-authoring/content-fragments.md).
   * Responsable de la mise en page et de la diffusion d’un fragment, c’est-à-dire des canaux.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la mise en page, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Faire glisser un fragment sur une page en mode Création permet d’associer automatiquement le composant requis.

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception d’un fragment, vous devez prendre en compte où vous utiliserez chacun de ses éléments.

### Exemple We.Retail {#we-retail-sample}

Un exemple de fragment est visible à l’adresse suivante :

[http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)
