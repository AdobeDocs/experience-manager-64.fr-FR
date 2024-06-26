---
title: Éditeur de boîtes de dialogue
seo-title: Dialog Editor
description: L’éditeur de boîtes de dialogue fournit une interface graphique pour créer et modifier facilement des boîtes de dialogue et des modèles automatiques.
seo-description: The dialog editor provides a graphical interface for easily creating and editing dialog boxes and scaffolds
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
exl-id: ee57a0c5-261e-4ffd-92ca-4804a9e1d132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 20%

---

# Éditeur de boîtes de dialogue{#dialog-editor}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’éditeur de boîtes de dialogue fournit une interface graphique qui permet de créer et de modifier facilement des boîtes de dialogue et des modèles automatiques.

Pour découvrir comment cet éditeur fonctionne, accédez à CRXDE Lite, développez l’arborescence de l’explorateur pour atteindre `/libs/foundation/components/chart`, puis double-cliquez sur le nœud `dialog` :

![chlimage_1-247](assets/chlimage_1-247.png)

Le nœud de boîtes de dialogue ouvre l’**éditeur de boîtes de dialogue** :

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Présentation de l’interface utilisateur {#user-interface-overview}

L’interface de l’éditeur de boîte de dialogue se compose de quatre volets :

* **Palette** (dans le coin supérieur gauche) : Ce volet contient les widgets disponibles pour créer une boîte de dialogue, tels que les panneaux à onglets, les champs de texte, les listes de sélection et les boutons. Vous pouvez développer les différentes catégories de la palette en cliquant sur la barre de séparation souhaitée.
* **Structure** (dans le coin inférieur gauche) : Ce volet affiche la structure hiérarchique des noeuds qui constituent la définition de la boîte de dialogue. Vous pouvez voir la même structure en développant le noeud dialog dans CRXDE Lite ou CRX Content Explorer.
* Le volet **Rendu**, au milieu de la fenêtre. Ce volet affiche la manière dont la définition de boîte de dialogue définie dans le volet de structure est présentée comme une boîte de dialogue réelle.
* **Propriétés** : Ce volet affiche les propriétés du noeud actuellement mis en surbrillance dans le volet de structure.

### Utilisation de l’éditeur de boîte de dialogue {#using-the-dialog-editor}

Pour créer une boîte de dialogue, l’utilisateur fait glisser des éléments de la palette vers le volet Structure dans la hiérarchie de définition de la boîte de dialogue.

Une fois la structure souhaitée terminée, l’utilisateur clique sur **Enregistrer**, en haut du volet de rendu.

>[!CAUTION]
>
>Notez que l’éditeur de boîtes de dialogue est destiné à la création de boîtes de dialogue relativement simples et qu’il peut ne pas être en mesure de modifier des définitions de boîte de dialogue plus complexes. Dans les cas où l’éditeur de boîte de dialogue n’autorise pas la modification d’une structure de boîte de dialogue, la définition de boîte de dialogue doit être créée et/ou modifiée manuellement en modifiant directement la structure de noeud à l’aide de l’explorateur de contenu CRX ou CRXDE Lite, par exemple.

### Création d’une boîte de dialogue {#creating-a-new-dialog}

Pour créer une boîte de dialogue, vous devez sélectionner le composant requis, cliquez sur **Créer...** puis **Boîte de dialogue Créer ...**.

Saisissez les informations requises, puis cliquez sur **Enregistrer tout**. Vous pouvez à présent double-cliquer sur la boîte de dialogue pour l’ouvrir dans l’éditeur.

### Utilisation de l’éditeur de boîte de dialogue pour les modèles automatiques {#using-the-dialog-editor-for-scaffolds}

Un modèle automatique est une page spéciale contenant un formulaire qui peut être rempli et envoyé en une seule étape. Vous pouvez ainsi créer rapidement une page à partir du contenu saisi.

Le formulaire qui constitue un modèle automatique est défini par une définition de boîte de dialogue, tout comme une boîte de dialogue normale, bien qu’il apparaisse sur la page de génération de modèles automatique sous une autre forme. Les définitions de boîte de dialogue étant utilisées pour définir des modèles automatiques, les modèles automatiques peuvent être conçus à l’aide de l’éditeur de boîte de dialogue. Notez que lorsque vous utilisez l’éditeur de boîte de dialogue de cette manière, le volet de rendu affiche toujours la définition de boîte de dialogue sous la forme d’une boîte de dialogue et non d’un modèle automatique.

Pour plus d’informations sur l’utilisation de l’éditeur de boîtes de dialogue pour créer des modèles automatiques, consultez [Génération de modèles automatiques](/help/sites-authoring/scaffolding.md).
