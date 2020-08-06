---
title: À propos du chargement et du traitement de ressources 3D dans AEM
seo-title: À propos du téléchargement et du traitement des ressources 3D dans AEM
description: Adobe vous recommande de charger tous les fichiers référencés avant de télécharger le fichier du modèle 3D principal (ou simultanément à son téléchargement). Une fois le téléchargement terminé, vos fichiers 3D sont convertis et un traitement supplémentaire est appliqué afin de préparer la ressource en vue de la visualisation et du rendu.
seo-description: Adobe vous recommande de charger tous les fichiers référencés avant de télécharger le fichier du modèle 3D principal (ou simultanément à son téléchargement). Une fois le téléchargement terminé, vos fichiers 3D sont convertis et un traitement supplémentaire est appliqué afin de préparer la ressource en vue de la visualisation et du rendu.
uuid: 82ccfbf8-1f82-4960-b9e5-3ce65c16435a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 0be4a856-951b-4cb6-8103-8004052c63a0
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 80%

---


# À propos du téléchargement et du traitement des ressources 3D dans AEM{#about-the-uploading-and-processing-of-d-assets-in-aem}

Utilisez les mécanismes de synchronisation ou de chargement standard pour importer des ressources 3D et leurs fichiers référencés associés dans AEM Assets.

Voir la section [Chargement des ressources](/help/assets/managing-assets-touch-ui.md#uploading-assets).

L&#39;Adobe vous recommande de télécharger tous les fichiers référencés avant ou en même temps. Il vous est recommandé de télécharger le Principal fichier de modèle 3D. Cependant, ceci n’est pas obligatoire.

Une fois le téléchargement terminé, vos fichiers 3D sont convertis et un traitement supplémentaire est appliqué afin de préparer la ressource en vue de la visualisation et du rendu.

## Meilleures pratiques relatives au chargement des ressources 3D {#best-practices-for-uploading-d-assets}

* En règle générale, il n’existe aucune restriction quant à l’emplacement où vous chargez le contenu 3D dans la hiérarchie des dossiers d’AEM Assets. La résolution des dépendances de fichiers automatisés d’AEM 3D présente cependant des limites de plage pour contrôler le temps nécessaire pour rechercher de grands référentiels de ressources. Adobe recommande par conséquent de charger les ressources 3D et leurs dépendances de fichiers en appliquant une proximité raisonnable pour chaque fichier (dossier grand-parent commun). Une fois les dépendances de fichiers résolues, vous pouvez librement déplacer les ressources 3D et leurs dépendances n’importe où dans le référentiel sans perdre les relations établies.
* Adobe vous recommande de choisir une structure de dossiers cohérente pour le contenu 3D *avant le téléchargement. Les conseils suivants sont quelques exemples de méthodes conseillées que vous pouvez appliquer :

   * **Conservez un dossier distinct pour chaque ressource 3D que vous chargez**.

       Le dossier contient le fichier du modèle 3D principal et toutes ses dépendances. Bien que le déplacement de toutes les ressources et dépendances dans un seul dossier est facile à implémenter, la recherche de contenu s’avère être un procédé complexe. Cette opération complique le partage des dépendances (correspondances de texture) entre les modèles.

   * **Conservez les modèles dans un seul dossier et les dépendances dans un sous-dossier ou un dossier frère**.

       Cette approche prend facilement en charge le partage des dépendances entre les modèles. Cependant, il peut s’avérer difficile de trouver les fichiers dépendants spécifiques si le nombre de ressources est important.

   * **Maintenez des hiérarchies de dossiers parallèles distinctes pour les modèles et fichiers dépendants**.

      Vous pouvez modeler cette approche à la manière dont les applications de création 3D telles qu’Autodesk Maya préfèrent stocker le contenu.

* Les ressources dépendantes ne doivent pas être supprimées, à moins que la ou les ressources 3D associées qui les ont référencées soient également supprimées. Vous pouvez toutefois supprimer librement les ressources 3D sans avoir besoin de supprimer leurs ressources dépendantes. Si une dépendance est accidentellement perdue, vous pouvez facilement résoudre la dépendance pour la restaurer.

   Voir la section [Résolution des dépendances de fichier](/help/assets/resolve-file-dependencies.md).

## Remarques sur les performances lors du chargement de fichiers 3D {#performance-considerations-when-uploading-d-files}

La conversion et le traitement des fichiers 3D consomment généralement d’importantes ressources en termes de processeur et de mémoire sur un serveur. Cela prend également un temps considérable. Les délais de traitement varient souvent considérablement en fonction de la taille du modèle et des capacités du serveur. Par exemple, un petit modèle standard avec moins de 100 000 faces est généralement prêt pour l’affichage en moins d’une minute ; il est entièrement traité en 2 ou 3 minutes. En revanche, un grand modèle avec plus d’un million de faces peut prendre plusieurs dizaines de minutes pour être complètement traité.

Les tâches de conversion, de traitement et de rendu sont placées en file d’attente pour empêcher de trop ralentir le serveur. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Ce statut indique que d’autres tâches de traitement ou de rendu doivent se terminer avant que la ressource actuelle soit traitée.

## Surveillance de l’état du traitement de vos fichiers 3D chargés {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. Chaque modèle 3D téléchargé subit généralement les quatre ou six étapes de traitement ordonnées suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Phase de traitement</strong><br /> </td> 
   <td><strong>Noms de traitement</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Traitement en cours</td> 
   <td>extraction initiale de base du traitement et des métadonnées.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Format de conversion</td> 
   <td>Le modèle 3D est converti d'un format natif (Autodesk® Maya® ou Autodesk® 3ds Max®) en un format intermédiaire (FBX).</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Création de prévisualisation</td> 
   <td>Le fichier FBX ou OBJ est assimilé et traité. Les dépendances de fichier sont évaluées et résolues en tant que références de ressources, si possible.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Création de cartes lumineuses</td> 
   <td>Facultatif. Permet d’augmenter la qualité de l’aperçu interactif et d’accélérer le rendu avec le moteur de rendu par défaut.</td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>Création d’une animation</td> 
   <td>Facultatif. Permet d’effectuer le rendu d’une animation simple, qui est ensuite utilisée comme miniature visuelle en mode Carte.</td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>En attente de traitement</td> 
   <td>Montré lorsque d’autres ressources 3D ont la priorité de traitement. Par exemple, les ressources qui ont été chargées précédemment, mais dont le traitement n’est pas encore terminé.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. Il n’est pas nécessaire d’attendre que toutes les étapes de traitement soient terminées.

