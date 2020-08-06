---
title: À propos du chargement et du traitement de ressources 3D dans AEM
seo-title: À propos du chargement et du traitement de ressources 3D dans AEM
description: Meilleures pratiques relatives au chargement et au traitement des ressources 3D.
seo-description: Meilleures pratiques relatives au chargement et au traitement des ressources 3D.
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 78%

---


# À propos du chargement et du traitement de ressources 3D dans AEM {#about-the-uploading-and-processing-of-d-assets-in-aem}

Utilisez les mécanismes de synchronisation ou de chargement standard pour importer des ressources 3D et leurs fichiers référencés associés dans AEM Assets.

Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

L&#39;Adobe vous recommande de télécharger tous les fichiers référencés avant ou en même temps. Il vous est recommandé de télécharger le Principal fichier de modèle 3D. Cependant, ceci n’est pas obligatoire.

Une fois le téléchargement terminé, vos fichiers 3D sont convertis et un traitement supplémentaire est appliqué afin de préparer la ressource en vue de la visualisation et du rendu.

## Meilleures pratiques relatives au chargement des ressources 3D {#best-practices-for-uploading-d-assets}

* En règle générale, il n’existe aucune restriction quant à l’emplacement où vous chargez le contenu 3D dans la hiérarchie des dossiers d’AEM Assets. La résolution des dépendances de fichiers automatisés d’AEM 3D présente cependant des limites de plage pour contrôler le temps nécessaire pour rechercher de grands référentiels de ressources. Adobe recommande par conséquent de charger les ressources 3D et leurs dépendances de fichiers en appliquant une proximité raisonnable pour chaque fichier (dossier grand-parent commun). Une fois les dépendances de fichiers résolues, vous pouvez librement déplacer les ressources 3D et leurs dépendances n’importe où dans le référentiel sans perdre les relations établies.
* Adobe recommande d’opter pour une structure de dossiers cohérente pour le contenu 3D *avant* de lancer le chargement. Les conseils suivants sont quelques exemples de méthodes conseillées que vous pouvez appliquer :

   * **Conservez un dossier distinct pour chaque ressource 3D que vous chargez**.

       Le dossier contient le fichier du modèle 3D principal et toutes ses dépendances. Bien que le déplacement de toutes les ressources et dépendances dans un seul dossier est facile à implémenter, la recherche de contenu s’avère être un procédé complexe. Cette opération complique le partage des dépendances (correspondances de texture) entre les modèles.

   * **Conservez les modèles dans un seul dossier et les dépendances dans un sous-dossier ou un dossier frère**.

       Cette approche prend facilement en charge le partage des dépendances entre les modèles. Cependant, il peut s’avérer difficile de trouver les fichiers dépendants spécifiques si le nombre de ressources est important.

   * **Maintenez des hiérarchies de dossiers parallèles distinctes pour les modèles et fichiers dépendants**.

      Vous pouvez modeler cette approche à la manière dont les applications de création 3D telles qu’Autodesk Maya préfèrent stocker le contenu.

* Les ressources dépendantes ne doivent pas être supprimées, à moins que la ou les ressources 3D associées qui les ont référencées soient également supprimées. Vous pouvez toutefois supprimer librement les ressources 3D sans avoir besoin de supprimer leurs ressources dépendantes. Si une dépendance est accidentellement perdue, vous pouvez facilement résoudre la dépendance pour la restaurer.

   Voir la section Résolution des dépendances de fichier.

## Remarques sur les performances lors du chargement de fichiers 3D {#performance-considerations-when-uploading-d-files}

La conversion et le traitement des fichiers 3D consomment généralement d’importantes ressources en termes de processeur et de mémoire sur un serveur. Cela prend également un temps considérable. Les délais de traitement varient souvent considérablement en fonction de la taille du modèle et des capacités du serveur. Par exemple, un petit modèle standard avec moins de 100 000 faces est généralement prêt pour l’affichage en moins d’une minute ; il est entièrement traité en 2 ou 3 minutes. En revanche, un grand modèle avec plus d’un million de faces peut prendre plusieurs dizaines de minutes pour être complètement traité.

Les tâches de conversion, de traitement et de rendu sont placées en file d’attente pour empêcher de trop ralentir le serveur. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Ce statut indique que d’autres tâches de traitement ou de rendu doivent se terminer avant que la ressource actuelle soit traitée.

Des mécanismes sont disponibles pour limiter l’utilisation du processeur pour le traitement de l’assimilation de la gestion et du rendu. Voir la section [Paramètres de configuration avancés](advanced-config-3d.md) pour plus d’informations sur la configuration des limites du processeur.

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
   <td>Création d'une ombre au sol</td> 
   <td>Facultatif. Vous permet de générer une ombre portée pour l’occlusion ambiante sur le plan de masse dans l’objet 3D. Voir Paramètres <a href="/help/assets/advanced-config-3d.md">de configuration</a> avancés pour activer ou désactiver ce traitement.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>Création de cartes lumineuses</td> 
   <td>Facultatif. Vous pouvez ainsi augmenter la qualité de l’aperçu interactif et accélérer le rendu avec le convertisseur par défaut. Voir Paramètres <a href="/help/assets/advanced-config-3d.md">de configuration</a> avancés pour activer ou désactiver ce traitement.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>Création d’une animation</td> 
   <td>Facultatif. Vous permet d’obtenir le rendu d’une animation simple qui est ensuite utilisée comme miniature de vidéo en mode Carte. Voir Paramètres <a href="/help/assets/advanced-config-3d.md">de configuration</a> avancés pour activer ou désactiver ce traitement.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>En attente de traitement</td> 
   <td>Montré lorsque d’autres ressources 3D ont la priorité de traitement. Par exemple, les ressources qui ont été chargées précédemment, mais dont le traitement n’est pas encore terminé.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. Il n’est pas nécessaire d’attendre que toutes les étapes de traitement soient terminées.

