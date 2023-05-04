---
title: Conventions de dénomination
seo-title: Naming Conventions
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 45%

---

# Conventions de dénomination{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Toutefois, AEM impose d’autres conventions pour le nom des nœuds de page.

## Conventions de dénomination pour les pages {#naming-conventions-for-pages}

Ces conventions de dénomination sont mises en oeuvre à différents niveaux :

* JcrUtil : la mise en oeuvre AEM de la [Utilitaires JCR](#jcr-utilities).
* PageManager : la valeur [Gestionnaire de pages](#page-manager) fournit des méthodes pour les opérations au niveau de la page.
* Selon l’interface utilisateur utilisée :

   * [IU tactile standard](#standard-ui)
   * [Interface utilisateur classique](#classic-ui)

### Utilitaires JCR {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) est l’implémentation AEM des utilitaires JCR. Les mappages de caractères qu’il contrôle et les validations suivantes présentent un intérêt particulier pour la validation des noms :

* `isValidName`

   * Vérifie si le nom n’est pas vide et contient uniquement des caractères valides.
   * Peut être utilisé pour vérifier si un nom proposé est valide.

* `createValidName`

   * Crée un libellé valide à partir d’une chaîne arbitraire.
   * Peut être utilisé pour créer un nom à partir d’un titre.

### Gestionnaire de pages {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) fournit des méthodes pour les opérations au niveau de la page, sur la base de [JCRUtil](#jcr-utilities).

### Interface utilisateur standard {#standard-ui}

L’IU tactile standard :

* Valide le nom en fonction des restrictions imposées par PageManager lorsque :

   * un titre de page est fourni pour la conversion dans le nom de noeud.
   * un nom de noeud explicite est fourni.

### Interface utilisateur classique {#classic-ui}

L’IU classique impose des restrictions plus strictes :

* Valide le nom lorsqu’un nom de noeud explicite se présente dans l’une des situations suivantes :

   * un titre de page est fourni pour la conversion dans le nom de noeud.
   * un nom de noeud explicite est fourni.

* Caractères valides (seuls ces caractères sont effectivement valides lorsqu’une page est créée dans l’IU classique, même si `PageManagerImpl` autorise des caractères supplémentaires) :

   * &#39;a&#39; à &#39;z&#39;
   * &quot;A&quot; à &quot;Z&quot;
   * &#39;0&#39; à &#39;9&#39;
   * _ (trait de soulignement)
   * `-` (tiret/moins)
