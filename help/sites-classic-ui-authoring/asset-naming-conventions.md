---
title: Conventions de dénomination pour le test des ressources
seo-title: Naming conventions for assets
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository. Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 46%

---

# Conventions de dénomination pour le test des ressources{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.

## Interface utilisateur classique {#classic-ui}

L’IU classique impose des restrictions plus strictes :

* Valide le nom de la ressource lorsqu’un nom de noeud explicite est utilisé dans l’une des situations suivantes :

   * un titre de ressource est fourni pour la conversion dans le nom de noeud.
   * un nom de noeud explicite est fourni.

* Caractères valides (seuls ces caractères sont réellement valides lors de la création d’une ressource dans l’interface utilisateur classique) :

   * &#39;a&#39; à &#39;z&#39;
   * &quot;A&quot; à &quot;Z&quot;
   * &#39;0&#39; à &#39;9&#39;
   * _ (trait de soulignement)
   * `-` (tiret/moins)
