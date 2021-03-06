---
title: Fragments de contenu – considérations sur la suppression
seo-title: Content Fragments - Delete Considerations
description: Fragments de contenu – considérations sur la suppression
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 88%

---

# Fragments de contenu – considérations sur la suppression {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0) ou version ultérieure](/help/release-notes/sp-release-notes.md).

## Autorisations – Supprimer ou ne pas supprimer {#permissions-delete-or-not-delete}

Pouvoir supprimer du contenu est une capacité puissante, mais potentiellement sensible. Pour cette raison, de nombreux secteurs d’activité doivent limiter et contrôler la manière dont ces privilèges sont distribués.

En ce qui concerne les autorisations de suppression, les fragments de contenu doivent être pris en compte à deux niveaux :

1. **Le fragment de contenu en tant qu’entité unique.**

   * **Cas d’utilisation** : un utilisateur qui a besoin de modifier/mettre à jour un fragment de contenu **et de supprimer un fragment entier**.
   * **Autorisations**[](/help/sites-administering/security.md#actions)[ : l’autorisation Supprimer peut être affectée via la gestion des utilisateurs et/ou des groupes](/help/sites-administering/security.md#managing-permissions).

1. **Les multiples sous-entités qui constituent un fragment de contenu ; par exemple, les variantes, les sous-nœuds.**

   Le fonctionnement de base de l’éditeur de fragment de contenu nécessite que ces sous-éléments transitoires puissent être supprimés. Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

   * **Cas d’utilisation** : un utilisateur qui a besoin de modifier/mettre à jour un fragment de contenu, **sans être autorisé à supprimer un fragment entier**.
   * **Autorisations** : voir [Autorisations requises pour la fonctionnalité d’éditeur uniquement](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Lorsqu’un utilisateur ne dispose d’aucune autorisation [Supprimer](/help/sites-administering/security.md#actions), l’éditeur de fragment de contenu fonctionne en mode *lecture seule*.

>[!NOTE]
>
>Voir également [Contrôle des opérations de gestion des utilisateurs dans AEM](/help/sites-administering/audit-user-management-operations.md).

## Autorisations requises pour la fonctionnalité d’éditeur uniquement {#permissions-required-for-editor-functionality-only}

Dans le cas des utilisateurs qui doivent modifier/mettre à jour un fragment de contenu, **sans leur permettre de supprimer l’intégralité d’un fragment**, des autorisations spécifiques doivent être attribuées, car l’opération de base de l’éditeur de fragment de contenu nécessite la possibilité de supprimer des sous-éléments transitoires.

Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

>[!NOTE]
>
>Les autorisations de suppression, requises pour modifier/mettre à jour un fragment de contenu, sont incluses dans l’autorisation [Supprimer](/help/sites-administering/security.md#managing-permissions) affectée via la gestion des utilisateurs et/ou des groupes.

Les autorisations nécessaires à la modification/mise à jour d’un fragment doivent être appliquées au nœud contenant le fragment de contenu ou à un nœud parent approprié (à n’importe quel niveau sous `/content/dam`/). Lorsqu’elles sont affectées à un tel nœud parent, les autorisations sont appliquées à tous les nœuds figurant dans cette branche.

Par exemple, un dossier allant contenir tous les fragments de contenu, tels que :

* `/content/dam/contentfragments`

>[!CAUTION]
>
>La définition des autorisations sur `/content/dam` est également possible, car tous les fragments de contenu y sont stockés.
>
>Toutefois, cette action applique les mêmes autorisations de suppression à *tous* les autres types de ressources également.

Les conditions requises pour autoriser un utilisateur et/ou un groupe spécifique à modifier/mettre à jour un fragment de contenu sont les suivantes :

>[!NOTE]
>
>Cette liste répertorie tous les privilèges requis et non simplement les privilèges de suppression.

* Pour les nœuds ou dossiers de fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Pour le nœud `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`

* Pour tous les nœuds situés sous `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`, `jcr:removeNode`

Ces `remove` Les privilèges doivent être [géré à l’aide des listes de contrôle d’accès, dans CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

Le `add` et `modify` Les privilèges peuvent également être gérés dans CRXDE Lite ou à l’aide de la console User Management.

Par exemple, la définition de la variable `remove` privilèges d’un groupe `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
