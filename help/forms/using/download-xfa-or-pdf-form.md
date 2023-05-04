---
title: Télécharger un modèle de formulaire XFA ou PDF
seo-title: Download an XFA or a PDF form template
description: Vous pouvez exporter des formulaires du référentiel vers le système local et migrer les formulaires téléchargés vers le nouveau référentiel.
seo-description: You can export forms from the repository to the local system and migrate the downloaded forms to new repository.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
role: Admin
exl-id: 68d881c6-7507-4018-b40e-205604221d0c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 38%

---

# Télécharger un modèle de formulaire XFA ou PDF {#download-an-xfa-or-a-pdf-form-template}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’opération de téléchargement, comme son nom l’indique, vous permet d’exporter des formulaires du référentiel vers le système local. Associée à l’opération de chargement, cette opération vous permet de migrer vos formulaires d’un référentiel vers un autre.

Dans AEM Forms, l’opération de téléchargement est prise en charge pour les types de ressources suivants :

* Modèles de formulaire (XFA Forms)
* PDF forms
* Documents (fichiers de PDF plats)

AEM Forms prend en charge le téléchargement de ces types de formulaires individuellement ou dans un dossier contenant un ou plusieurs formulaires pris en charge.

Outre ces ressources, vous pouvez télécharger le type `Resource` de ressources s’il est présent dans un dossier. L’objectif de cette fonctionnalité est de vous permettre de télécharger la ressource à laquelle fait référence un formulaire XFA, ainsi que le formulaire proprement dit.

## Téléchargement d’un ou de plusieurs formulaires {#download-one-or-more-forms}

1. Connectez-vous à l’interface utilisateur d’AEM Forms à l’adresse `https://<server>:<port>/aem/forms.html`.

1. Accédez à l’emplacement de la ressource que vous souhaitez télécharger.

1. Sélectionnez la ressource. Cliquez sur l’icône **[!UICONTROL Télécharger]** ![aem6forms_download](assets/aem6forms_download.png) dans la barre d’outils.

   >[!NOTE]
   >
   >Vous ne pouvez sélectionner qu’un seul formulaire à télécharger. Si vous souhaitez télécharger plusieurs formulaires, vous devez les télécharger sous la forme d’un dossier.

1. Dans la boîte de dialogue qui s’affiche, cliquez sur **[!UICONTROL Télécharger]**.

   AEM Forms génère un fichier ZIP contenant le fichier sélectionné ou le dossier sélectionné.

   Si vous téléchargez un dossier, les ressources prises en charge dans le dossier sont téléchargées dans leur hiérarchie existante.

   Le fichier ZIP est enregistré dans le dossier `Downloads` sur votre système.

## Remarques relatives à l’opération de chargement {#related-considerations-for-the-upload-operation}

* Vous pouvez charger le fichier ZIP vers n’importe quel autre emplacement du même référentiel ou d’un autre référentiel.
* La hiérarchie des ressources d’un dossier est conservée pendant l’opération de chargement.
* Toute modification des métadonnées apportée aux ressources téléchargées avant le téléchargement est répercutée lors du transfert. 
