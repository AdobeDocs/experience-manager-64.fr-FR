---
title: Configuration des extensions d’Acrobat Reader DC pour la capture de données
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Découvrez comment configurer des extensions Acrobat Reader DC pour la capture de données.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 11%

---

# Configuration des extensions d’Acrobat Reader DC pour la capture de données {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si les utilisateurs de votre installation AEM forms utilisent la fonctionnalité de capture de données de Content Services (obsolète), il est recommandé de créer un rôle avec un accès en lecture seule pour ces utilisateurs.

***Remarque** : Adobe® LiveCycle® Content Services ES (obsolète) est un système de gestion de contenu installé avec LiveCycle. Il permet aux utilisateurs de concevoir, gérer, surveiller et optimiser des processus pour des intervenants humains. La prise en charge de Content Services (obsolète) prend fin le 12/31/2014.

La capture de données requiert que vous attribuiez un rôle utilisateur pour accéder à SampleReaderExtensionsCredential. Vous pouvez attribuer le rôle Trust Administrator standard, mais considérez que ce rôle confère aux utilisateurs généraux et non administrateurs les privilèges d’administrateur puissants qui contrôlent les paramètres d’approbation PKI et gèrent les informations d’identification PKI, ce qui peut compromettre la sécurité de votre installation de AEM forms dans un environnement de production. Il est recommandé que l’administrateur système d’AEM forms crée un rôle qui accorde uniquement un accès en lecture seule à Trust Store et affecte ce nouveau rôle aux utilisateurs non-administrateurs qui utilisent la capture de données.

## Création d’un rôle pour les utilisateurs de la capture de données {#create-a-role-for-data-capture-users}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nouveau rôle.
1. Saisissez le nom du rôle (par exemple, Utilisateur de capture de données) et une description dans les champs appropriés, puis cliquez sur Suivant.
1. Dans l’écran Autorisations des rôles, cliquez sur Rechercher des autorisations, puis sélectionnez Lecture des informations d’identification dans la liste des autorisations disponibles.
1. Cliquez sur OK, puis sur Terminer.

## Attribution du rôle de capture de données {#assign-the-data-capture-role}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Rechercher.
1. Cliquez sur le rôle utilisateur de capture de données que vous avez créé.
1. Dans l’onglet Utilisateurs/groupes de rôle, cliquez sur Rechercher des utilisateurs/groupes.
1. Dans l’écran Rechercher des utilisateurs et des groupes, cliquez sur Rechercher, sélectionnez les utilisateurs nécessitant le rôle d’utilisateur de capture de données, puis cliquez sur OK.
1. Dans l’écran Modifier le rôle, cliquez sur Enregistrer.
