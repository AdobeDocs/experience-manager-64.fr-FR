---
title: Configuration d’une page de redirection
seo-title: Configuring redirect page
description: Après avoir rempli un formulaire adaptatif, les utilisateurs peuvent être redirigés vers une page web que les auteurs de formulaires peuvent configurer lors de la création du formulaire.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 75%

---

# Configuration d’une page de redirection {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour chaque formulaire, les auteurs peuvent configurer une page vers laquelle les utilisateurs seront redirigés après l’envoi du formulaire.

1. En mode d’édition, sélectionnez un composant, puis cliquez sur ![field-level](assets/field-level.png) > **Conteneur de formulaires adaptatifs**, puis cliquez sur ![cmppr](assets/cmppr.png).

1. Dans la barre latérale, cliquez sur **Envoi**.

1. Indiquez L’URL de la page de redirection sous Page de remerciement dans la section Envoyer. 
1. Sous Action Envoyer, vous pouvez éventuellement configurer le paramètre à transmettre à la page de redirection pour l’action Envoyer vers le point d’entrée REST.

![Configuration de la page de redirection](assets/thank-you-setting-1.png)
**Figure :** *Configuration de la page de redirection*

Les auteurs de formulaires peuvent utiliser les paramètres suivants qui sont transmis à la page de remerciement. Les paramètres `status` et `owner` sont transmis pour toutes les actions d’envoi disponibles. Outre ces deux paramètres, des paramètres supplémentaires sont transmis pour les actions d’envoi suivantes :

* **Action Stocker le contenu** (obsolète) : `contentPath`--le chemin d’accès du nœud dans le référentiel où sont stockées les données envoyées est transmis.

* **Action Stocker le PDF** (obsolète) : `contentPath`--des données envoyées et le chemin d’accès au nœud de stockage du fichier PDF dans le référentiel sont transmis.

* **Flux de travail Envoyer aux formulaires** : les paramètres de sortie renvoyés à partir du flux de travail des formulaires sont transmis.

* **Envoyer vers le point d’entrée REST** : les paramètres ajoutés pour la correspondance entre le champ et le paramètre sont transmis. Les paramètres `status` et `owner` ne sont pas transmis à cette action d’envoi. Pour en savoir plus, consultez [Configuration de l’action d’envoi Envoyer vers le point d’entrée REST](/help/forms/using/configuring-submit-actions.md). 
