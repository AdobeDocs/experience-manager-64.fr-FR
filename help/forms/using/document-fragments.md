---
title: Fragments de document
seo-title: Document Fragments
description: Dans Correspondence Management, les fragments de document (texte, listes, conditions et mises en page, par exemple) permettent de former les composants statiques, dynamiques et répétables de la correspondance client.
seo-description: Document Fragments, such as Text, lists, conditions, and layout fragments, in Correspondence Management let you form the static, dynamic, and repeatable components of customer correspondence.
uuid: 053a17e5-69a5-463d-af4f-46a86534158f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 1f48548c-4222-454d-ad16-53da37170de2
feature: Correspondence Management
exl-id: 54159851-bae1-4efd-8c8f-3a855776ecc4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 39%

---

# Fragments de document {#document-fragments}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les fragments de document sont des parties/composants réutilisables d’une correspondance à l’aide de laquelle vous pouvez composer des communications/lettres interactives. Les fragments de document sont composés des types suivants :

* **Texte** : Un actif de texte est un élément de contenu comprenant un ou plusieurs paragraphes de texte. Un paragraphe peut être statique ou dynamique.

   * [Textes dans les communications interactives](/help/forms/using/texts-interactive-communications.md)

* **Condition** : les conditions vous permettent de définir le contenu à inclure lors de la création d’une correspondance, en fonction des données fournies. La condition est décrite en termes de variables de contrôle. Une variable de contrôle peut être un élément de dictionnaire de données ou un espace réservé.

   * [Conditions dans les communications interactives](/help/forms/using/conditions-interactive-communications.md)

* **Liste :** la liste est un groupe de fragments du document, incluant du texte, des listes, des conditions et des images. L&#39;ordre des éléments de la liste peut être fixe ou modifiable. Lors de la création d’une lettre, vous pouvez utiliser certains ou tous les éléments de liste pour répliquer un modèle d’éléments réutilisable.
* **Fragment de disposition**: Un fragment de mise en page est une mise en page pouvant être utilisée dans une ou plusieurs lettres. Un fragment de mise en page est utilisé pour créer des modèles répétables, en particulier des tableaux dynamiques. La mise en page peut contenir des champs de formulaire types tels qu’« Adresse » et « Numéro de référence ». Elle contient également des sous-formulaires vides indiquant les zones cible. Les mises en page (XDP) sont créées dans Designer, puis sont téléchargées vers AEM Forms.
