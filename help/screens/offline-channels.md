---
title: Canaux hors ligne
seo-title: Canaux hors ligne
description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
seo-description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
uuid: 25766e79-a5a5-4b84-b235-e3050f725fbe
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: developing
discoiquuid: 609d5405-138f-47f7-9ac0-efaa32f8715b
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Canaux hors ligne{#offline-channels}

Le lecteur Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ***ContentSync***.

Les lecteurs utilisent un serveur http local pour diffuser le contenu décompressé.

Quand un canal est configuré de manière à s’exécuter *en ligne*, le lecteur met à disposition les ressources de canal en accédant au serveur AEM, mais lorsque le canal est configuré de sorte à s’exécuter *hors ligne*, le lecteur met à disposition les ressources de canal d’un serveur http local.

Le workflow du processus est le suivant :

1. Analyser la ou les pages demandées
1. Collecter tous les actifs associés
1. Encapsuler le tout dans un fichier zip
1. Télécharger le zip et l’extraire localement
1. Afficher une copie locale du contenu

## Mettre à jour les gestionnaires    {#update-handlers}

***ContentSync*** utilise des gestionnaires de mise à jour pour analyser et collecter toutes les pages et tous les actifs nécessaires à un projet spécifique. AEM Screens utilise les gestionnaires de mise à jour suivants :

### Options communes    {#common-options}

* *type* : type de gestionnaire de mise à jour à utiliser
* *path* : chemin d’accès à la ressource
* *[targetRootDirectory]* : dossier cible dans le fichier zip

<table> 
 <tbody>
  <tr>
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Options</strong></td> 
  </tr>
  <tr>
   <td>channels</td> 
   <td>collecte un canal</td> 
   <td>extension : extension de la ressource à collecter<br /> [pathSuffix='''] : suffixe à ajouter au chemin du canal<br /> [deep=true] : l’analyse récursive<br /> des pages enfants [includeImages=true] : inclure toutes les images dans la chaîne<br /> [includeVideos=true] : incluez toutes les vidéos dans la chaîne<br /> [includeProducts=true] : inclure tous les produits du canal</td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>collecte la bibliothèque cliente spécifiée</td> 
   <td>[extension='''] : peut être soit css, soit js, pour collecter uniquement la première, soit la seconde</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>collecte des rendus de ressources</td> 
   <td>[renditions=[]] : liste des rendus à collecter. Défini par défaut sur le rendu d’origine</td> 
  </tr>
  <tr>
   <td>Copier</td> 
   <td>copier la structure spécifiée à partir du chemin</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Test de la configuration de ContentSync {#testing-contentsync-configuration}

Suivez les étapes ci-dessous pour tester la configuration de ContentSync :

1. Ouvrez [http://localhost:4502/libs/cq/contentsync/content/console.html](http://localhost:4502/libs/cq/contentsync/content/console.html)
1. Sélectionner votre configuration dans la liste
1. Cliquer sur Effacer le cache
1. Cliquer sur Mettre à jour le cache
1. Cliquer sur Télécharger tout le module
1. Extraire le fichier zip
1. Démarrer un serveur local dans le dossier extrait
1. Ouvrir la page de démarrage et vérifier l’état de l’application

## Activation de la configuration hors ligne d’un canal    {#enabling-offline-config-for-a-channel}

Suivez les étapes ci-dessous pour activer la configuration hors ligne d’un canal :

1. Inspectez le contenu du canal et vérifiez s’il est demandé par une instance AEM (en ligne).

   ![chlimage_1-15](assets/chlimage_1-15.png)

1. Navigate to the channel dashboard and click **... **in the** CHANNEL INFORMATION **Panel to change the properties.

   ![chlimage_1-16](assets/chlimage_1-16.png)

1. Accédez aux propriétés des canaux et assurez-vous que la case à cocher est désactivée dans l’onglet **Canal**. Cliquez sur **Enregistrer et fermer**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Avant que le contenu ne soit correctement déployé sur le périphérique, cliquez sur **Mettre à jour le contenu hors ligne**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Le statut **Hors ligne** sous **PROPRIÉTÉ** est également mis à jour en conséquence.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspectez le contenu du canal et vérifiez s’il est demandé par le cache du lecteur local.

   ![chlimage_1-17](assets/chlimage_1-17.png)

