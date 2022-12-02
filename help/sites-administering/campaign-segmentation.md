---
title: Configuration de la segmentation
seo-title: Configuring Segmentation
description: Découvrez comment configurer la segmentation pour AEM Campaign.
seo-description: Learn how to configure segmentation for AEM Campaign.
uuid: f22e41b6-d9d9-4f18-9925-2d4aebc167b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 49c9c9ab-632a-40f7-8c30-d6a8c0f1b420
exl-id: 92302067-3500-41ca-9855-87f36148bfbc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 98%

---

# Configuration de la segmentation{#configuring-segmentation}

>[!NOTE]
>
>Ce document traite de la configuration de la segmentation telle qu’utilisée avec ClientContext. Pour configurer des segments avec ContextHub à l’aide de l’interface utilisateur tactile, voir la rubrique [Configuration de la segmentation avec ContextHub](/help/sites-administering/segmentation.md).

La segmentation est un élément clé de la création d’une campagne. Voir le [Glossaire sur la segmentation](/help/sites-authoring/segmentation-overview.md) pour plus d’informations sur le fonctionnement de la segmentation et en connaître les termes clés.

En fonction des informations que vous avez déjà collectées sur les visiteurs de votre site et des objectifs que vous souhaitez atteindre, vous devez définir les segments et les stratégies requis pour votre contenu ciblé.

Ces segments sont ensuite utilisés pour fournir aux visiteurs du contenu spécifiquement ciblé. Ce contenu est conservé dans la section [Campagnes](/help/sites-authoring/personalization.md) du site web. Les pages de teaser définies ici peuvent être ajoutées en tant que paragraphes de teaser à n’importe quelle page et définissent à quel segment de visiteurs le contenu spécialisé s’applique.

AEM vous permet de facilement créer et mettre à jour des segments, des teasers et des campagnes. Il vous permet également de vérifier les résultats de vos définitions.

L’**éditeur de segment** vous permet de définir facilement un segment :

![segmenteditor-1](assets/segmenteditor-1.png)

Vous pouvez **Modifier** chaque segment pour spécifier un facteur **Titre**, **Description** et **Amplifier**. Avec le sidekick, vous pouvez ajouter des conteneurs **ET** et **OU** pour définir la **Logique de segment**, puis ajouter des **Caractéristiques de segment** pour définir les critères de sélection.

## Facteur d’amplification {#boost-factor}

Chaque segment comporte un paramètre **Amplifier** utilisé comme un facteur de pondération : une valeur plus élevée indique que le segment sera sélectionné de préférence à un segment présentant une valeur plus faible.

* Valeur minimale : `0`
* Valeur maximale : `1000000`

## Logique de segment {#segment-logic}

Les conteneurs logiques suivants sont disponibles clé en main et vous permettent de créer la logique de votre sélection de segments. Ils peuvent être déplacés du sidekick vers l’éditeur :

<table> 
 <tbody> 
  <tr> 
   <td> Conteneur ET<br /> </td> 
   <td> Opérateur ET booléen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Conteneur OU<br /> </td> 
   <td> Opérateur OU booléen.</td> 
  </tr> 
 </tbody> 
</table>

## Caractéristiques de segment {#segment-traits}

Les caractéristiques de segment suivantes sont disponibles clé en main ; elles peuvent être déplacées du sidekick vers l’éditeur :

<table> 
 <tbody> 
  <tr> 
   <td> Plage d’adresses IP<br /> </td> 
   <td>Définit une plage d’adresses IP que le visiteur peut avoir.<br /> </td> 
  </tr> 
  <tr> 
   <td> Accès à la page<br /> </td> 
   <td>Fréquence à laquelle la page a été demandée. <br /> </td> 
  </tr> 
  <tr> 
   <td> Propriété de page<br /> </td> 
   <td>Toute propriété de la page visitée.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mots-clés de référence<br /> </td> 
   <td>Mots-clés à associer aux informations du site web de référence. <br /> </td> 
  </tr> 
  <tr> 
   <td> Script</td> 
   <td>Expression JavaScript à évaluer.<br /> </td> 
  </tr> 
  <tr> 
   <td> Référence de segment <br /> </td> 
   <td>Référence à une autre définition de segment.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuage de balises<br /> </td> 
   <td>Balises à associer à celles des pages visitées.<br /> </td> 
  </tr> 
  <tr> 
   <td> Âge de l’utilisateur<br /> </td> 
   <td>Extrait du profil utilisateur.<br /> </td> 
  </tr> 
  <tr> 
   <td> Propriété de l’utilisateur<br /> </td> 
   <td>Toute autre information disponible dans le profil utilisateur. </td> 
  </tr> 
 </tbody> 
</table>

Vous pouvez combiner ces caractéristiques avec les opérateurs booléens OU et ET (voir la rubrique [Création d’un nouveau segment](#creating-a-new-segment)) afin de définir le scénario exact pour sélectionner ce segment.

Lorsque l’intégralité de l’instruction est vraie, alors ce segment a été résolu. Si plusieurs segments sont applicables, le facteur **[Amplifier](/help/sites-administering/campaign-segmentation.md#boost-factor)** est également utilisé.

>[!CAUTION]
>
>L’éditeur de segment ne vérifie aucune référence circulaire. Par exemple, le segment A fait référence à un autre segment B, qui à son tour référence le segment A. Vous devez vous assurer que vos segments ne contiennent aucune référence circulaire.

>[!NOTE]
>
>Les propriétés comportant le suffixe **_i18n** sont définies par un script faisant partie de la bibliothèque cliente d’interface utilisateur des personnalisations. Toutes les bibliothèques clientes liées à l’interface utilisateur sont chargées à la création uniquement, car l’interface utilisateur n’est pas nécessaire lors de la publication.
>
>Par conséquent, lors de la création d’un segment avec ces propriétés, il est normalement nécessaire de faire appel à **browserFamily**, par exemple, au lieu de **browserFamily_i18n**.

## Création d’un segment {#creating-a-new-segment}

Pour définir votre nouveau segment :

1. Dans le rail, choisissez **Outils > Opérations > Configuration**.
1. Cliquez sur la page **Segmentation** dans le panneau gauche, puis accédez à l’emplacement requis.
1. Créez une [nouvelle page](/help/sites-authoring/managing-pages.md) à l’aide du modèle **Segment**.
1. Ouvrez la nouvelle page pour afficher l’éditeur de segment :

   ![screen_shot_2012-02-02at101726am](assets/screen_shot_2012-02-02at101726am.png)

1. Utilisez le sidekick ou le menu contextuel (en général, cliquez avec le bouton droit de la souris, puis sélectionnez **Nouveau** pour ouvrir la fenêtre Insérer un nouveau composant) et recherchez la caractéristique de segment dont vous avez besoin. Faites alors glisser la caractéristique vers l’**éditeur de segment** pour qu’elle apparaisse dans le conteneur **ET** par défaut.
1. Double-cliquez sur la nouvelle caractéristique pour modifier les paramètres, par exemple la position de la souris :

   ![screen_shot_2012-02-02at103135am-1](assets/screen_shot_2012-02-02at103135am-1.png)

1. Cliquez sur **OK** pour enregistrer votre définition :
1. Vous pouvez **Modifier** la définition de segment pour lui attribuer un **Titre**, une **Description** et un facteur **[Amplifier](/help/sites-administering/campaign-segmentation.md#boost-factor)** :

   ![screen_shot_2012-02-02at103547am](assets/screen_shot_2012-02-02at103547am.png)

1. Ajoutez d’autres caractéristiques si nécessaire. Vous pouvez formuler des expressions booléennes à l’aide des composants **Conteneur ET** et **Conteneur OU** figurant dans **Logique de segment**. Avec l’éditeur de segment, vous pouvez supprimer des caractéristiques ou des composants qui ne sont plus utiles ou les faire glisser vers un nouvel emplacement dans l’instruction.

## Utilisation des conteneurs ET et OU {#using-and-and-or-containers}

Vous pouvez créer des segments complexes dans AEM. Ceci vous aide à tenir compte de certains aspects élémentaires :

* Le niveau supérieur de la définition est toujours le conteneur ET qui est initialement créé ; ceci ne peut pas être changé, mais n’a pas d’effet sur le reste de votre définition de segment.
* Assurez-vous que l’imbrication de votre conteneur a un sens. Les conteneurs peuvent être considérés comme les crochets de votre expression booléenne.

L’exemple suivant permet de sélectionner les visiteurs qui sont soit :

Homme et entre 16 et 65 ans

OU

Femme et entre 16 et 62 ans

Puisque l’opérateur principal est OU, vous devez commencer par le **Conteneur OU**. Celui-ci contient 2 instructions ET. Pour chacune de ces instructions, il vous faut un **Conteneur ET**, dans lequel vous pouvez ajouter les caractéristiques principales.

![screen_shot_2012-02-02at105145am-1](assets/screen_shot_2012-02-02at105145am-1.png)

## Test de l’application d’un segment {#testing-the-application-of-a-segment}

Une fois le segment défini, les résultats potentiels peuvent être testés avec l’aide du **[ClientContext](/help/sites-administering/client-context.md)** :

1. Sélectionnez le segment à tester.
1. Appuyez sur les touches **[Ctrl-Alt-C](/help/sites-authoring/keyboard-shortcuts.md)** pour ouvrir le **[ClientContext](/help/sites-administering/client-context.md)**, qui affiche les données collectées. À des fins de test, vous pouvez **Modifier** certaines valeurs ou **Charger** un autre profil pour y voir l’impact.

1. En fonction des caractéristiques définies, les données disponibles pour la page en cours peuvent ou non correspondre à la définition de segment. Le statut de la correspondance s’affiche sous la définition.

Par exemple, une seule définition de segment peut être fonction de l’âge et du sexe de l’utilisateur. Le chargement d’un profil spécifique indique que le segment a été résolu avec succès :

![screen_shot_2012-02-02at105926am-1](assets/screen_shot_2012-02-02at105926am-1.png)

Ou non :

![screen_shot_2012-02-02at110019am-1](assets/screen_shot_2012-02-02at110019am-1.png)

>[!NOTE]
>
>Toutes les caractéristiques sont résolues immédiatement, bien que la plupart ne soient modifiées qu’au rechargement de la page. Les modifications apportées à la position de la souris sont visibles immédiatement, ce qui est utile à des fins de test.

Ces tests peuvent également s’effectuer sur les pages de contenu et en combinaison avec des composants **Teaser**.

Survoler la photographie d’un teaser avec la souris affiche les segments appliqués et indique s’ils sont actuellement résolus et, par conséquent, pourquoi l’instance de teaser actuelle a été sélectionnée :

![chlimage_1-408](assets/chlimage_1-408.png)

## Utilisation de votre segment {#using-your-segment}

Les segments sont actuellement utilisés dans les [campagnes](/help/sites-authoring/personalization.md). Ils sont utilisés afin d’orienter le contenu réel affiché pour des audiences cible spécifiques. Voir la rubrique [Compréhension des segments](/help/sites-authoring/segmentation-overview.md) pour plus d’informations.
