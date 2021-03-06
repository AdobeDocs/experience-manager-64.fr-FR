---
title: Développement d’applications avec l’interface de ligne de commande PhoneGap
seo-title: Developing Apps with PhoneGap CLI
description: Consultez cette page pour en savoir plus sur le développement d’applications avec l’interface de ligne de commande PhoneGap.
seo-description: Follow this page to learn about developing apps with PhoneGap CLI.
uuid: 9a66171d-19af-40db-9c07-f5dd9561e1b5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 4a034e15-3394-4be3-9e8e-bc894668946a
exl-id: 7f2fcebb-1769-481a-b4df-b891053b08b6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 4%

---

# Développement d’applications avec l’interface de ligne de commande PhoneGap{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

En tant que développeur, vous pouvez à tout moment exécuter votre application sur un appareil ou dans un émulateur, à condition d’avoir configuré votre environnement de développement.

Pour exécuter les exemples suivants, vous aurez besoin d’un système exécutant OSx (Mac) avec Xcode ou d’un système Mac/Win/Linux avec le SDK Android installé.

## Bootstrap de votre environnement de développement {#bootstrap-your-development-environment}

[Configuration de l’interface de ligne de commande PhoneGap](https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)

Pour iOS : Pour développer pour iPhone et iPad, vous avez besoin d’Apple Xcode IDE.

* Téléchargez-le gratuitement [here](https://developer.apple.com/xcode/downloads/).
* [Guide de la plateforme PhoneGap iOS](https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)

Pour Android : Pour développer pour iPhone et iPad, vous avez besoin de Google Android Studio IDE.

* Téléchargez-le gratuitement [here](https://developer.android.com/sdk/index.html).
* [Guide de la plateforme PhoneGap Android](https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide)

## Téléchargement de la source {#download-the-source}

Une fois que vous avez correctement redémarré votre environnement de développement, téléchargez la source à partir de la mosaïque AEM App Build :

* Cliquez sur le chevron de la liste déroulante PhoneGap Build.

![chlimage_1-45](assets/chlimage_1-45.png)

* Cliquez sur Télécharger la source.
* Sélectionnez la source souhaitée dans le modal Source de téléchargement .

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>La source de développement contient l’état le plus récent de votre application, tout en incluant des modifications non évaluées. Utilisez la source d’évaluation pour créer des candidats de version à envoyer aux fournisseurs de la boutique d’applications.
>
>Si vous n’effectuez jamais l’évaluation de votre application, la sélection de l’évaluation déclenche le processus d’évaluation (indice : cela s’affichera en tant qu’application intermédiaire dans l’application PhoneGap Enterprise Viewer disponible dans AppStore et Google PlayStore).

* Cliquez sur Télécharger et enregistrez le fichier ZIP sur votre ordinateur.
* Extrayez le fichier zip téléchargé dans votre espace de travail.

## Création et chargement de l’application (à partir de la source) {#build-and-load-the-app-from-source}

L’interface de ligne de commande de PhoneGap peut créer un projet de plateforme, compiler la source et déployer l’application dans une seule commande.

>[!NOTE]
>
>Vous pouvez effectuer toutes ces étapes séparément, voir [Documentation de l’interface de ligne de commande PhoneGap](https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/).

1. Vérifiez que vous avez installé l’interface de ligne de commande PhoneGap, voir ci-dessus.
1. Dans une fenêtre de console (ou de terminal), accédez au répertoire racine de la source extraite.
1. Saisissez la commande suivante :

```xml
phonegap run android

// -- or -- //

phonegap run ios
```

>[!NOTE]
>
>Si vous rencontrez des problèmes à ce stade, revenez aux concepts de base pour la résolution de problèmes.
>
>1. Création d’un dossier (test mkdir)
>1. Accédez à ce nouveau dossier (test cd)
>1. Exécutez &quot;phonegap create helloWorld&quot;
>1. Accédez à helloWorld (cd helloWorld).
>1. Exécutez &quot;phonegap run android (ou remplacez android par ios comme ci-dessus).
>1. L’émulateur ouvre l’exécution de votre application PhoneGap nouvellement créée, indiquant &quot;Prêt pour l’appareil&quot; si le pont JavaScript vers natif est opérationnel.

>
>Cela vous permet de vérifier que votre environnement de développement de l’interface de ligne de commande PhoneGap est opérationnel correctement.

## Débogage des scripts JavaScript avec Safari et débogage IOS {#debug-javascripts-with-safari-and-ios-debug}

Vous pouvez déboguer les scripts JavaScript de votre application à l’aide des outils de développement de Safari, comme vous le feriez avec une application web.

## Activation des outils de développement Safari {#enable-safari-developer-tools}

Pour activer les outils de développement :

* Ouvrez les préférences de Safari.

   * Cliquez sur Safari dans la barre de menus.
   * Cliquez sur Préférences

* Cliquez sur Avancé dans la fenêtre Préférence .

![chlimage_1-47](assets/chlimage_1-47.png)

* Cochez la case Afficher le menu Développer dans la barre de menus .
* Fermez la fenêtre Préférences

## Connexion de Safari à iOS {#connect-safari-to-ios}

Vous pouvez connecter Safari à un appareil iOS ou à un émulateur.

* Dans une fenêtre de console, accédez au répertoire racine de la source extraite.
* Saisissez la commande suivante pour lancer votre application sur votre appareil ou émulateur.

```xml
phonegap run <platform> --device

// -- or -- //

phonegap run <platform> --emulator
```

* Ouvrir Safari
* Cliquez sur Développer dans la barre de menus.
* Sélectionner le sous-menu du simulateur iOS
* Cliquez sur home.html

![chlimage_1-48](assets/chlimage_1-48.png)

## Débogage de JavaScript avec l’Inspecteur Web de Safari {#debug-javascript-with-safari-s-web-inspector}

Vous pouvez définir des points d’arrêt n’importe où dans votre source. Lorsque vous interagissez avec votre émulateur ou appareil, l’exécution de votre application s’arrête à ces points d’arrêt. Vous pouvez parcourir l’exécution et inspecter les valeurs des variables.

* Cliquez sur Ressources dans la fenêtre Inspecteur Web .
* Parcourez l’arborescence source et cliquez sur le fichier source souhaité.
* Cliquez sur le numéro de ligne adjacent pour ajouter un point d’arrêt.
* Interaction avec l’appareil ou l’émulateur

![chlimage_1-49](assets/chlimage_1-49.png)

* Utilisez les boutons de contrôle pour continuer l’exécution, passer à l’étape supérieure, entrer et sortir des méthodes :

![](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Pour afficher les valeurs des variables, dans la méthode actuelle, pointez avec la souris.

## Étapes suivantes {#the-next-steps}

Une fois que vous avez appris à propos du développement d’applications avec l’interface de ligne de commande de PhoneGap, voir [Accès aux fonctionnalités du périphérique](/help/mobile/phonegap-access-device-features.md).
