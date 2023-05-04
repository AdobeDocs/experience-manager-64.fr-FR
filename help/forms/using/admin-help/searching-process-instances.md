---
title: Rechercher des instances de processus
seo-title: Searching for process instances
description: Utilisez la page Recherche de processus pour saisir les critères de recherche permettant de trouver une instance de processus.
seo-description: Use the Process Search page to enter search criteria for finding a process instance.
uuid: 4a9c5b05-add5-4278-9c6f-d1928b6860d2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 88b634bb-8f6c-4830-ad01-821668609615
exl-id: 25a01630-47ec-4823-ad11-9a636697f3dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 15%

---

# Rechercher des instances de processus{#searching-for-process-instances}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez la page Recherche de processus pour saisir les critères de recherche permettant de trouver une instance de processus. Vous pouvez accéder à la page Recherche de processus à partir de la page de processus des formulaires ou en cliquant sur Rechercher dans la page Instance du processus .

Vous pouvez saisir des critères de base pour effectuer une recherche générale, des attributs spécifiques pour effectuer une recherche détaillée ou une combinaison de critères de base et d’attributs spécifiques pour effectuer une recherche combinée.

## Exécution d’une recherche générale {#perform-a-general-search}

Une recherche générale d’un processus est plus appropriée si vous connaissez l’ID de processus de l’instance de processus, si vous recherchez un groupe d’instances de processus associées ou si seules quelques instances de processus sont en cours d’exécution.

Saisissez les critères de base pour effectuer une recherche générale. Si vous saisissez plusieurs critères, la recherche est effectuée avec une condition ET implicite.

1. Dans Administration Console, cliquez sur Services > Processus Forms > Recherche de processus.
1. Sur la page Recherche de processus, sous Recherche générale, fournissez les critères suivants :

   * **ID du processus :** entier positif qui identifie chaque instance de processus unique.
   * **Etat du processus :** sélectionnez un état dans la liste.
   * **Application :** sélectionnez une application dans la liste. Seules les applications déployées sont affichées.
   * **Nom du processus - Version :** sélectionnez un nom de processus dans le menu. Seuls les processus déployés s’affichent.

1. Cliquez sur Rechercher. La page Instance du processus s’affiche, répertoriant les instances trouvées.

## Recherche détaillée d’un processus {#perform-a-detailed-search-for-a-process}

Vous pouvez saisir des attributs spécifiques pour effectuer une recherche détaillée. Une recherche détaillée est plus appropriée si de nombreuses instances de processus sont en cours d’exécution et que vous devez limiter les recherches possibles en fonction de certains critères.

1. Dans Administration Console, cliquez sur Services > Processus Forms > Recherche de processus.
1. Sur la page Recherche de processus, sous Recherche détaillée, spécifiez votre premier jeu de critères :

   * Dans la liste Attribut, sélectionnez un attribut.
   * Dans la liste Filtre , sélectionnez un opérateur.
   * Dans la zone Value , saisissez une valeur appropriée à l’attribut que vous avez sélectionné.

1. Pour ajouter une autre ligne, sélectionnez Plus de filtres. Un autre ensemble de listes Attribut, Filtre et Valeur s’affiche, ainsi qu’une liste Condition.
1. Sous Condition, sélectionnez ET ou OU. Répétez les étapes 1 à 3 selon les besoins pour limiter davantage votre recherche.
1. Pour ajouter ou supprimer des lignes, cliquez sur Plus de filtres ou Moins de filtres. Vous pouvez avoir de une à quatre lignes.
1. Cliquez sur Rechercher. La page Instance du processus s’affiche, répertoriant les instances trouvées.

[A propos des états d’instances de processus](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Recherche combinée d’un processus {#perform-a-combined-search-for-a-process}

Pour créer une recherche basée à la fois sur une recherche générale et une recherche détaillée, avec un ET implicite entre les zones, saisissez vos critères de recherche dans les zones Recherche générale et Recherche détaillée de la page Recherche de processus.

Si la recherche est trop étroite, aucune instance ne sera trouvée.
