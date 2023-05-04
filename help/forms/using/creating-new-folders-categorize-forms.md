---
title: Créer des dossiers pour classer les formulaires
seo-title: Create new folders to categorize forms
description: Utilisez des dossiers pour organiser vos modèles de formulaire, PDF, ressources et formulaires adaptatifs.
seo-description: Use folders to organize your form templates, PDFs, resources, and adaptive forms.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Admin
exl-id: 6c989701-10c7-466e-b3e5-008a6d377574
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 49%

---

# Créer des dossiers pour classer les formulaires {#create-new-folders-to-categorize-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez mieux organiser vos ressources à l’aide de dossiers. Comme AEM Forms prend en charge plusieurs types de ressources (modèles de formulaire, PDF, documents, ressources et formulaires adaptatifs, avec diverses métadonnées), vous pouvez utiliser des dossiers pour classer vos formulaires en fonction des critères souhaités.

AEM Forms vous permet de modifier le titre d’un dossier. Le titre est différent du nom du noeud sous lequel le dossier est stocké dans le référentiel. Le titre est conservé en tant que métadonnées pour le dossier. Si vous modifiez le titre d’un dossier, le chemin d’accès de toute ressource contenue dans le dossier n’est pas affecté.

## Créer un dossier {#create-a-folder}

Vous pouvez créer un dossier dans AEM Forms de l’une des manières suivantes :

* Téléchargement d’un fichier ZIP contenant les ressources dans la structure de dossiers souhaitée (voir [Obtention de documents XDP et PDF dans AEM Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Création d’un dossier vide

1. Connectez-vous à l’interface utilisateur d’AEM Forms à l’adresse `https://<server>:<port>/aem/forms.html`.
1. Accédez à l’emplacement où vous souhaitez créer un dossier.
1. Cliquez sur l’icône ![aem6forms_add](assets/aem6forms_add.png) de la barre d’outils, puis sélectionnez **[!UICONTROL Créer un dossier]**.

1. Saisissez les informations suivantes :

   * **Titre** : nom d’affichage du dossier.
   * **Nom** : *(Obligatoire)* nom du nœud sous lequel vous souhaitez stocker le dossier dans le référentiel.

   >[!NOTE]
   >
   >par défaut, la valeur du champ Nom est automatiquement renseignée à partir du titre. Le nom ne peut contenir que des caractères alphanumériques ou des tirets (-) et des traits de soulignement (_). Tous les autres caractères spéciaux saisis dans le titre sont automatiquement remplacés par un trait d’union. Vous êtes invité à confirmer le nouveau nom. Vous pouvez continuer avec le nom proposé ou le modifier davantage.

1. Cliquez sur **[!UICONTROL Envoyer].**

   Un nouveau dossier avec le titre que vous avez défini s’affiche à l’emplacement spécifié dans la liste des ressources.

   Si un dossier portant le même nom que celui spécifié existe déjà, l’envoi échoue avec une erreur. Vous pouvez afficher le message d’erreur en pointant sur l’icône d’erreur ![aem6forms_error_alert](assets/aem6forms_error_alert.png) qui s’affiche en regard du champ Nom.

### Modification du titre d’un dossier {#edit-the-folder-title-br}

1. Sélectionnez le dossier dont vous souhaitez modifier le titre.
1. Cliquez sur lʼicône Modifier ![aem6forms_edit](assets/aem6forms_edit.png) dans la barre d’outils.
1. Saisissez le nouveau titre. Le champ de texte est prérenseigné avec la valeur actuelle du titre du dossier. Vous pouvez remplacer cette valeur.
1. Cliquez sur **[!UICONTROL Envoyer].**
