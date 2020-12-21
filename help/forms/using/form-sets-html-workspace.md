---
title: Utilisation des jeux de formulaires dans l’espace de travail AEM Forms
seo-title: Utilisation des jeux de formulaires dans l’espace de travail AEM Forms
description: Un jeu de formulaires est un assortiment de formulaires HTML5 regroupés et présentés comme un ensemble unique de formulaires aux utilisateurs finaux. Découvrez comment utiliser des jeux de formulaires dans l’espace de travail AEM Forms.
seo-description: Un jeu de formulaires est un assortiment de formulaires HTML5 regroupés et présentés comme un ensemble unique de formulaires aux utilisateurs finaux. Découvrez comment utiliser des jeux de formulaires dans l’espace de travail AEM Forms.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 73%

---


# Utilisation des jeux de formulaires dans l’espace de travail AEM Forms {#working-with-formsets-in-aem-forms-workspace}

Un jeu de formulaires est un assortiment de formulaires HTML5 regroupés et présentés comme un ensemble unique de formulaires aux utilisateurs finaux. Lorsque les utilisateurs finaux commencent à compléter un jeu de formulaires, ils passent facilement d’un formulaire à l’autre. Le jeu de formulaires peut ensuite être envoyé en un simple clic. Pour plus d’informations sur les jeux de formulaires et sur leur configuration, voir [Jeu de formulaires en AEM Forms](/help/forms/using/formset-in-aem-forms.md).

L’espace de travail AEM Forms prend en charge les jeux de formulaires. Avec les jeux de formulaires, plusieurs formulaires associés à un service ou processus peuvent être regroupés pour automatiser un processus d’entreprise et présentés aux utilisateurs finaux. Dans ce cas, les utilisateurs peuvent remplir le jeu entier comme un seul et il n’est pas nécessaire de classer, envoyer et suivre des processus ou des formulaires individuels.

## Comment joindre un jeu de formulaires au point de départ dans l’application d’espace de travail AEM Forms {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Créez un flux de processus d’entreprise dans Workbench. Pour plus d’informations, voir [Aide de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Dans les propriétés de processus du point de départ, sélectionnez **Utiliser un actif CRX** dans Présentation et Données.

   ![1-1](assets/1-1.png)

1. Cliquez sur ![parcourir](assets/browse.png) (Parcourir) en regard du chemin d’accès de la ressource CRX. La boîte de dialogue Sélection de l’actif de formulaire s’affiche.

   ![2](assets/2.png)

1. Cliquez sur l’onglet **Jeu de formulaires**, sélectionnez le jeu de formulaires approprié dans la liste, puis cliquez sur **OK**.

1. Déployez l’application après la mise à jour d’autres propriétés de processus appropriées.

## Utilisation des jeux de formulaires dans l’espace de travail AEM Forms {#using-formset-in-nbsp-aem-forms-workspace}

Une fois qu’un jeu de formulaires est attaché à un point de départ, ce dernier peut être appelé, comme tout autre point de départ, à partir de l’espace de travail AEM Forms.

Les opérations prises en charge sur le jeu de formulaires via l’espace de travail AEM Forms sont les suivantes :

* Enregistrer en tant que brouillon
* Verrouiller
* Abandonner
* Envoyer
* Ajouter des pièces jointes
* Ajouter des remarques
* Se déplacer d’un formulaire à l’autre au sein d’un jeu de formulaires à l’aide des boutons Précédent et Suivant

![3-1](assets/3-1.png)

>[!NOTE]
>
>Pour améliorer les performances durant le déplacement d’un formulaire à l’autre d’un jeu de formulaires, tous les boutons de l’espace de travail (Précédent, Suivant, Envoyer, etc.) sont désactivés jusqu’à ce que le formulaire approprié soit complètement rendu.

