---
title: Test des composants principaux dans We.Retail
seo-title: Trying out Core Components in We.Retail
description: Test des composants principaux dans We.Retail
seo-description: null
uuid: 8d1cea0b-99d9-49b2-b275-41f14864b1ff
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: af3cd818-61cf-4da1-bfb5-87540911ddd5
exl-id: b77d0e6b-3005-4dba-8e88-70b4d04b1eba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 36%

---

# Test des composants principaux dans We.Retail{#trying-out-core-components-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les composants principaux sont des composants modernes et flexibles qui offrent une extensibilité facile et permettent une intégration simple à vos projets. Les composants principaux ont été créés selon plusieurs principes de conception majeurs tels que HTL, la convivialité prête à l’emploi, la configurabilité, le contrôle de version et l’extensibilité. We.Retail a été développé sur des composants principaux.

## Essayer de le faire {#trying-it-out}

1. Commencez AEM par l’exemple de contenu We.Retail et ouvrez le [Console Composants](/help/sites-authoring/default-components-console.md).

   **Navigation globale -> Outils -> Composants**

1. En ouvrant le rail dans la console Composants, vous pouvez filtrer un groupe de composants particulier. Les composants principaux se trouvent dans

   * `.core-wcm` : composants principaux standard
   * `.core-wcm-form` : composants principaux d’envoi de formulaire

   Choisissez `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Notez que tous les composants principaux sont nommés **v1**, ce qui indique qu’il s’agit de la première version de ce composant principal. Des versions régulières seront publiées à l’avenir, qui seront compatibles avec les versions d’AEM et vous permettront de mettre à niveau facilement afin de profiter des dernières fonctionnalités.
1. Cliquez sur **Texte (v1)**.

   Veillez à ce que le **Type de ressource** du composant soit `/apps/core/wcm/components/text/v1/text`. Les composants principaux sont disponibles sous `/apps/core/wcm/components` et versionnés par composant.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Cliquez sur l’onglet **Documentation** afin d’afficher la documentation du développeur pour le composant.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Revenez à la console de composants. Filtre pour le groupe **We.Retail** et sélectionnez la variable **Texte** composant.
1. Vérifiez que le **Type de ressource** pointe comme prévu vers un composant sous `/apps/weretail`, mais que le **Type de super-ressource** repointe vers le composant principal `/apps/core/wcm/components/text/v1/text`.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Cliquez sur l’onglet **Utilisation en direct** pour voir les pages sur lesquelles ce composant est utilisé actuellement. Cliquez sur la première **page de remerciement** pour modifier la page.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Sur la page de remerciement, sélectionnez le composant de texte et, dans le menu de modification du composant, cliquez sur l’icône Annuler l’héritage .

   [We.Retail possède une structure de site globalisée.](/help/sites-developing/we-retail-globalized-site-structure.md) où le contenu est transmis des gabarits de langue à [Live Copies par le biais d’un mécanisme appelé héritage](/help/sites-administering/msm.md). Pour cette raison, l’héritage doit être annulé pour permettre à un utilisateur de modifier manuellement le texte.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Cliquez sur **Oui** pour confirmer l’annulation.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Une fois que vous avez annulé l’héritage et sélectionné les composants de texte, bien d’autres options sont disponibles. Cliquez sur **Modifier**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. À présent, vous pouvez voir les options d’édition qui sont disponibles pour le composant de texte.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Dans la **Informations sur la page** menu **Modifier le modèle**.
1. Dans l’éditeur de modèles de la page, cliquez sur le **Stratégie** de l’icône du composant Texte dans la **Conteneur de mises en page** de la page.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Les composants principaux permettent à un auteur de modèles de configurer les propriétés disponibles pour les auteurs de pages. Il s’agit notamment de fonctionnalités telles que les sources de collage autorisées, les options de mise en forme, les styles de paragraphe disponibles, etc.

   Ces boîtes de dialogue de conception sont disponibles pour de nombreux composants principaux et fonctionnent main dans la main avec l’éditeur de modèles. Une fois activés, ils sont disponibles pour l’auteur via les éditeurs de composant.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Informations supplémentaires {#further-information}

Pour plus d’informations sur les composants principaux, voir le document de création [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) pour une présentation des fonctionnalités des composants principaux et du document destiné aux développeurs [Développement des composants principaux](https://helpx.adobe.com/fr/experience-manager/core-components/using/developing.html) pour une présentation technique.

Vous pouvez également effectuer des recherches approfondies sur les [modèles modifiables](/help/sites-developing/we-retail-editable-templates.md). Reportez-vous au document [Création de modèles de page](/help/sites-authoring/templates.md) ou à la page de documentation de développement [Modèles – Modifiables](/help/sites-developing/page-templates-editable.md) pour obtenir des informations complètes sur les modèles modifiables.
