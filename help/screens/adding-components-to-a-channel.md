---
title: Ajout de composants à un canal
seo-title: Ajout de composants à un canal
description: Suivez cette page pour en savoir plus sur l’ajout de composants aux canaux d’un projet AEM Screens.
seo-description: Suivez cette page pour en savoir plus sur l’ajout de composants aux canaux d’un projet AEM Screens.
uuid: dd35e7ad-b6df-4542-a91f-97db7baa4f6f
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 8f28c02c-e7ce-47e5-91b2-862e03c18bd8
translation-type: tm+mt
source-git-commit: 7115654670dbacb27ab9dc5c6d8ce7d39b6f9eab

---


# Ajout de composants à un canal{#adding-components-to-a-channel}

Les composants sont des éléments fondamentaux de l’expérience AEM (Adobe Experience Manager). Vous pouvez utiliser un certain nombre de composants et les ajouter au canal d’un projet AEM Screens.

## Composants utilisés dans AEM Screens      {#components-in-aem-screens}

AEM Screens fournit différents composants AEM qui peuvent être utilisés dans un projet Screens.

### Affichage des composants AEM Screens      {#viewing-aem-screens-components}

Lorsque vous créez un projet AEM Screens, vous pouvez voir la liste des composants par défaut qui peuvent être ajoutés au projet.

Pour afficher les composants par défaut dans le projet Screens, procédez comme suit :

1. Sélectionnez le canal. Par exemple, **We.Retail en magasin** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur AEM.
1. Cliquez sur l’icône **+** de la barre latérale pour ouvrir les composants.
1. Tous les composants fournis par défaut dans un projet AEM Screens s’affichent, comme illustré dans la figure ci-dessous.

![screen_shot_2017-12-18at21350pm](assets/addingComponents1.png)

### Ajout d’un nouveau composant {#adding-a-new-component}

AEM propose un certain nombre d’autres composants. Vous pouvez toujours ajouter d’autres composants (non fournis par défaut) au projet, à condition qu’ils soient compatibles avec AEM Screens.

L’exemple suivant illustre l’ajout d’un composant Livefyre à un projet AEM Screens :

1. Sélectionnez le canal dans lequel vous souhaitez ajouter un nouveau composant. Par exemple, **We.Retail en magasin** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
1. Sélectionnez le mode **Conception**.
1. Sélectionnez l’éditeur de conception complet à droite et cliquez sur le symbole de paramètres pour ouvrir la boîte de dialogue **Conception ParSys**.
1. Vous pouvez sélectionner les composants que vous souhaitez importer dans le projet AEM Screens. The following example shows the addition of **Livefyre** component to an AEM Screens project.


![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>De la même façon, vous pouvez ajouter au projet autant de nouveaux composants que vous le souhaitez, s’ils sont compatibles avec AEM Screens.

## Présentation des composants AEM Screens      {#understanding-aem-screen-components}

La section suivante explique les composants d’AEM Screens que vous pouvez utiliser dans votre projet.

>[!NOTE]
>
>Pour afficher les propriétés d’un composant, sélectionnez-le, puis cliquez sur l’icône en forme de marteau afin d’ouvrir/d’afficher les propriétés.

### Application {#application}

Le composant **Application** permet d’ajouter une application au canal.

Le composant Application présente les propriétés suivantes :

| **Propriété** | **Description** |
|---|---|
| ***Chemin de l’application*** | Sélectionnez le chemin absolu où se trouve l’application. |
| ***Durée (ms)*** | Sélectionnez la durée de l’application. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute indéfiniment (il s’agit par conséquent d’une application sur une seule page). Si vous définissez une valeur supérieure à 0 pour la durée, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse. |

L’exemple suivant illustre la manière dont un composant d’application doit être incorporé avec l’aperçu de ses propriétés :

![adding_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Reportez-vous à l’exemple ci-dessus pour afficher les propriétés de chacun des composants suivants.

### Canal      {#channel}

Le composant **Canal** permet d’ajouter un canal entier au projet.

Le composant Canal présente les propriétés suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><strong><em>Chemin du canal</em></strong></td> 
   <td>Sélectionnez le chemin absolu où se trouve l’application.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong><em>Durée (ms)</em></strong></td> 
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td> 
  </tr> 
 </tbody> 
</table>

### Page incorporée {#embedded-page}

Une **page incorporée** permet d’ajouter une page incorporée à un projet. Par exemple, il peut s’agir d’une application Web ou d’un catalogue de produits.

La page incorporée présente les propriétés suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><strong><em>Chemin d’accès à la page<br /> </em></strong></td> 
   <td>Sélectionnez le chemin absolu où se trouve le canal.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong><em>Durée (ms)</em></strong></td> 
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td> 
  </tr> 
 </tbody> 
</table>

### Séquence incorporée {#embedded-sequence}

>[!NOTE]
>
>Reportez-vous à [Séquences incorporées](embedded-sequences.md) dans la section Création dans Screens pour en savoir plus sur les séquences incorporées.

Une séquence incorporée permet d’ajouter un canal de séquence incorporée dans le canal existant (avec d’autres ressources).

La séquence incorporée présente les propriétés suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Chemin du canal</td> 
   <td>Sélectionnez le chemin absolu de la séquence que vous souhaitez inclure dans le canal.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong><em>Durée (ms)</em></strong></td> 
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td> 
  </tr> 
  <tr> 
   <td><strong><em>Stratégie</em></strong></td> 
   <td>Définissez-la sur <strong>original</strong> ou <strong>seul(e)</strong>. La définition de cette valeur sur <strong>Original</strong> implique que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parent. L’autre valeur possible est <strong>seul(e)</strong> ; elle permet d’afficher un seul élément de la séquence secondaire à chaque exécution (par exemple, le premier élément de la première boucle, le deuxième élément de la deuxième boucle, etc.).</td> 
  </tr> 
 </tbody> 
</table>

### Séquence incorporée dynamique {#dynamic-embedded-sequence}

Une séquence incorporée dynamique permet d’ajouter une séquence semblable à la séquence incorporée susvisée, mais via le rôle de canal.

Reportez-vous à [Séquences incorporées](embedded-sequences.md) dans la section Création dans Screens pour en savoir plus sur les séquences incorporées.

La séquence incorporée dynamique présente les propriétés suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><strong><em>Rôle d’attribution de canaux</em></strong><br /> </td> 
   <td>Saisissez le rôle du canal.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong><em>Durée (ms)</em></strong></td> 
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td> 
  </tr> 
  <tr> 
   <td><strong><em>Stratégie</em></strong></td> 
   <td>Définissez-la sur <strong>original</strong> ou <strong>seul(e)</strong>. La définition de cette valeur sur <strong>Original</strong> implique que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parent. L’autre valeur possible est <strong>seul(e)</strong> ; elle permet d’afficher un seul élément de la séquence secondaire à chaque exécution (par exemple, le premier élément de la première boucle, le deuxième élément de la deuxième boucle, etc.).</td> 
  </tr> 
 </tbody> 
</table>

### Image {#image}

Cette fonction permet d’ajouter une image au canal.

La ressource image présente trois onglets, à savoir **Image**, **Accessibilité** et **Séquence** :

| **Propriété** | **Description** |
|---|---|
| **Image** |
| ***Ressource image*** | Sélectionnez la ressource image. |
| ***Titre*** | Titre de l’image. |
| ***Lier à*** | Ajoutez un lien vers l’image. |
| ***Description*** | Brève description de l’image. |
| ***Taille*** | Taille de l’image. |
| **Accessibilité** |
| ***Texte de remplacement*** | Texte de remplacement de l’image. |
| **Séquence** |
| ***Durée*** | Sélectionnez la durée complète de l’image. Si vous définissez la durée sur -1, cela signifie que l’image incorporée s’exécute pendant toute sa durée dans un canal donné. |

### Transition {#transition}

Le composant Transition permet d’ajouter une transition au projet Screens.

Le composant Transition présente les propriétés suivantes :

| **Propriété** | **Description** |
|---|---|
| ***Type*** | Type de la transition entre l’élément précédent et le suivant. Il peut s’agir d’un effet de fondu ou de glissement à partir des quatre diapositives de l’écran. |
| ***Durée (ms)*** | Sélectionnez la durée complète de la transition. La définition de la durée sur -1 indique que la transition incorporée exécutera toute sa longueur dans un canal particulier. |

### Vidéo {#video}

Le composant Vidéo permet d’ajouter une vidéo au projet Screens.

Le composant Vidéo présente les propriétés suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><em><strong>Contenu vidéo</strong></em></td> 
   <td>Sélectionnez le lien vers la vidéo.</td> 
  </tr> 
  <tr> 
   <td><em><strong>Durée</strong></em></td> 
   <td>Sélectionnez la durée de la vidéo. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute indéfiniment. Si vous définissez une valeur supérieure à 0 pour la durée, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse.<br /> </td> 
  </tr> 
  <tr> 
   <td><em><strong>Création de rendu</strong></em></td> 
   <td><p>Si le rapport d’aspect de la vidéo ne correspond pas à l’écran, vous pouvez modifier le rendu à l’aide des options <strong>Contenir</strong> ou <strong>Couverture</strong>.</p> <p><em>Contenir</em> signifie que l’intégralité de la vidéo est affichée et que les zones manquantes sont remplies d’une bordure noire.</p> <p><em>Couverture</em> signifie que la vidéo couvre toute la fenêtre, mais que certaines parties dépassant sur les côtés sont masquées.</p> </td> 
  </tr> 
  <tr> 
   <td><em><strong>Taille</strong></em></td> 
   <td>Taille de la vidéo.</td> 
  </tr> 
 </tbody> 
</table>

