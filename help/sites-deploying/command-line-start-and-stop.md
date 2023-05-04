---
title: Démarrer et arrêter AEM à partir de la ligne de commande
seo-title: Command Line Start and Stop
description: Découvrez comment démarrer et arrêter AEM à partir de la ligne de commande.
seo-description: Learn how to start and stop AEM from the command line.
uuid: 585f071c-2286-4a2c-af07-404bf298cba8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9333ff84-f624-4cfa-a9e4-c5e3882171ff
exl-id: 9d2682c2-6360-402e-a020-0021f5051a2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 49%

---

# Démarrer et arrêter AEM à partir de la ligne de commande{#command-line-start-and-stop}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Démarrage d’Adobe Experience Manager à partir de la ligne de commande {#starting-adobe-experience-manager-from-the-command-line}

Le script `start` est disponible dans le répertoire *&lt;cq-installation>/bin*. Des versions sont fournies pour Unix et Windows. Le script démarre l’instance installée dans *&lt;cq-installation>* répertoire .

Les deux versions prennent en charge une liste de variables d’environnement qui peuvent être utilisées pour démarrer et configurer l’instance AEM.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Variable d’environnement </strong></td> 
   <td><strong>Description </strong></td> 
  </tr> 
  <tr> 
   <td>CQ_PORT</td> 
   <td>Port TCP utilisé pour les scripts stop et status.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_HOST</td> 
   <td>Nom de l’hôte.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_INTERFACE</td> 
   <td>Interface que doit écouter ce serveur.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_RUNMODE</td> 
   <td>Mode(s) d’exécution séparé(s) par une virgule.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JARFILE</td> 
   <td>Nom du fichier JAR.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_USE_JAAS</td> 
   <td>Utilisation de JAAS (si la valeur est true).<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JAAS_CONFIG</td> 
   <td>Chemin d’accès à la configuration JAAS.<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JVM_OPTS</td> 
   <td>Options JVM par défaut.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>Notez que certains modes d’exécution, parmi lesquels l’auteur et la publication, doivent être définis avant l’AEM de départ et ne peuvent pas être modifiés par la suite. Avant de configurer une instance d’AEM qui est censée être utilisée en production, reportez-vous à la section [documentation sur les modes d’exécution](/help/sites-deploying/configure-runmodes.md) pour plus d’informations.

### Exemple de script start.bat pour la plateforme Windows {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Exemple de script de démarrage de plateforme Unix {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Le script start lance le déploiement Quickstart AEM installé dans le dossier *&lt;cq-installation>/app*.

## Arrêt d’Adobe Experience Manager {#stopping-adobe-experience-manager}

Pour arrêter AEM, effectuez l’une des opérations suivantes :

* Selon la plateforme que vous utilisez :

   * Si vous avez démarré AEM à partir d’un script ou d’une ligne de commande, appuyez sur **Ctrl + C** pour arrêter le serveur.
   * Si vous avez utilisé le script start sous UNIX, vous devez utiliser le script stop pour arrêter AEM.

* Si vous avez commencé AEM en double-cliquant sur le fichier jar, cliquez sur le bouton **Activé** dans la fenêtre de démarrage (le bouton devient alors **Off**) pour arrêter le serveur.

   ![chlimage_1-63](assets/chlimage_1-63.png)

## Arrêt d’Adobe Experience Manager à partir de la ligne de commande {#stopping-adobe-experience-manager-from-the-command-line}

Le script `stop` est disponible dans le répertoire *&lt;cq-installation>/bin*. Des versions sont fournies pour Unix et Windows. Le script arrête l’instance en cours d’exécution installée dans le répertoire *&lt;cq-installation>*.

### Exemple de script stop de plateforme Unix {#unix-platform-stop-script-example}

```shell
./stop
```

### Exemple de script stop.bat pour la plateforme Windows {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Si vous souhaitez uniquement préconfigurer le référentiel (sans le relocaliser), vous devez uniquement :

* extraire `repository.xml` à l’emplacement requis ;

* mettre à jour `repository.xml` selon les besoins ;

* créer `bootstrap.properties` et définir `repository.config`.

Vous devez effectuer ces opérations avant de démarrer l’installation actuelle.
