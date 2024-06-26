---
title: Afficher les composants en fonction du modèle utilisé
seo-title: Displaying components based on the template used
description: Lorsque vous créez un formulaire, découvrez comment activer les composants dans la barre latérale en fonction du modèle sélectionné.
seo-description: When you create a form, learn how you can enable components in the sidebar based on the template selected.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
exl-id: a4cee2e6-a56f-4355-8176-b3ed7478a775
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 59%

---

# Affichage des composants en fonction du modèle utilisé {#displaying-components-based-on-the-template-used}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsqu’un auteur de formulaire crée un formulaire adaptatif à l’aide d’un [modèle](/help/forms/using/template-editor.md), l’auteur du formulaire peut afficher et utiliser des composants spécifiques en fonction de la stratégie de modèle. Vous pouvez spécifier une stratégie de contenu de modèle qui vous permet de choisir un groupe de composants visible par l’auteur du formulaire au moment de la création du formulaire.

## Modification de la stratégie de contenu d’un modèle {#changing-the-content-policy-of-a-template}

Lorsque vous créez un modèle, il est créé sous `/conf` dans le référentiel de contenu. En fonction des dossiers que vous avez créés dans le répertoire `/conf`, le chemin d’accès à votre modèle est : `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Effectuez les étapes suivantes pour afficher les composants dans la barre latérale en fonction de la stratégie de contenu d’un modèle :

1. Ouvrez CRXDE Lite.

   URL : `https://<server>:<port>/crx/de/index.jsp`

1. Dans CRXDE, accédez au dossier dans lequel le modèle est créé.

   Par exemple : `/conf/<your-folder>/`

1. Dans CRXDE, accédez à : `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`.

   Pour sélectionner un groupe de composants, une nouvelle stratégie de contenu est requise. Pour créer une nouvelle stratégie, copiez-collez la stratégie par défaut, puis renommez-la.

   Le chemin d’accès à la stratégie de contenu par défaut est : `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`.

   Dans le dossier `gridFluidLayout`, copiez-collez la stratégie par défaut et renommez-la. Par exemple, `myPolicy`.

   ![Copie des stratégies par défaut](assets/crx-default1.png)

1. Sélectionnez la nouvelle stratégie que vous créez puis sélectionnez la propriété **composants** dans le panneau de droite avec le type `string[]`.

   Lorsque vous sélectionnez et ouvrez la propriété de composants, la boîte de dialogue Modifier les composants s’affiche. La boîte de dialogue Modifier les composants vous permet d’ajouter ou de supprimer des groupes de composants à l’aide du **+** et **-** des boutons. Vous pouvez ajouter le groupe de composants qui comprend des composants du formulaire que vous souhaitez que les auteurs utilisent.

   ![Ajouter ou supprimer des composants dans la stratégie](assets/add-components-list1.png)

   Après avoir ajouté un groupe de composants, cliquez sur **OK** pour mettre à jour la liste, puis cliquez sur **Enregistrer tout** au-dessus de la barre d’adresse de CRXDE et actualisez.

1. Dans le modèle, remplacez la stratégie de contenu par défaut par la nouvelle stratégie que vous avez créée. (`myPolicy` dans cet exemple.)

   Pour modifier la stratégie, dans CRXDE, accédez à `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   Dans la propriété `cq:policy`, modifiez `default` pour le nouveau nom de la stratégie (`myPolicy`).

   ![Stratégie de contenu de modèle mise à jour](assets/updated-policy.png)

   Lorsque vous créez un formulaire à l’aide du modèle, vous pouvez voir les composants supplémentaires dans la barre latérale.
