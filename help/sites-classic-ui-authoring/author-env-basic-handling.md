---
title: Manipulation de base
seo-title: Basic Handling
description: Présentation de la gestion de base lors de l’utilisation de l’environnement de création AEM. Il s’appuie sur la console Sites.
seo-description: An overview of basic handling when using the AEM author environment. It uses the Sites console as a basis.
uuid: ab488d7c-7b7f-4a23-a80c-99d37ac84246
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9737ead9-e324-43c9-9780-7abd292f4e5b
exl-id: 49bf3e19-d299-4c99-896c-b12135f33fb7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 49%

---

# Manipulation de base{#basic-handling}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>* Cette page est conçue pour donner un aperçu des opérations de gestion de base lors de l’utilisation de l’environnement de création AEM. Il s’appuie sur la console **Sites**.
>
>* Certaines fonctionnalités ne sont pas disponibles dans toutes les consoles et/ou des fonctionnalités supplémentaires sont disponibles dans certaines consoles. Des informations spécifiques sur les consoles individuelles et leurs fonctionnalités associées seront traitées plus en détail sur d’autres pages.
>* Des raccourcis clavier sont disponibles dans toute l’application AEM, notamment lors de l’[utilisation des consoles](/help/sites-classic-ui-authoring/author-env-keyboard-shortcuts.md) et de la [modification de pages](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md).
>


## L&#39;écran de bienvenue {#the-welcome-screen}

L’IU classique propose une sélection de consoles, qui utilisent des mécanismes connus pour parcourir et initier des actions, notamment cliquer, double-cliquer et [menus contextuels](#context-menus).

Lors de la connexion, l’écran de bienvenue s’affiche. Il fournit une liste de liens vers les consoles et services :

![screen_shot_2012-01-30at61745pm](assets/screen_shot_2012-01-30at61745pm.png)

## Consoles {#consoles}

Les principales consoles sont les suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Console</strong></td> 
   <td><strong>Objectif</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Bienvenue</strong></td> 
   <td>Fournit un aperçu et un accès direct (au moyen de liens) vers les principales fonctions d’AEM.</td> 
  </tr> 
  <tr> 
   <td><strong>Ressources numériques</strong><br /> </td> 
   <td>Ces consoles permettent d’importer et de <a href="/help/sites-classic-ui-authoring/classicui-assets.md">gérer des ressources numériques</a> telles que des images, des vidéos, des documents et des fichiers audio. Utilisez ces ressources dans n’importe quel site Web exécuté sur la même instance d’AEM. </td> 
  </tr> 
  <tr> 
   <td><strong>Lancements</strong></td> 
   <td>Avec cette console, vous pouvez gérer vos <a href="/help/sites-classic-ui-authoring/classic-launches.md">lancements</a> et élaborer ainsi le contenu pour une prochaine version d’une ou de plusieurs pages Web activées.<br /> <i>Remarque : dans l’IU activée pour les écrans tactiles, la plupart des fonctionnalités sont également disponibles dans la console Sites, avec le rail Références.</i> <i>Si nécessaire, vous pouvez accéder à cette console à partir de la console Outils ; pour ce faire, sélectionnez Opérations, puis Lancements.</i></td> 
  </tr> 
  <tr> 
   <td><strong>Boîte de réception </strong></td> 
   <td>Dans de nombreux cas, différentes personnes sont impliquées dans la sous-tâche d’un processus et chacune d’elles doit exécuter l’étape lui est attribuée avant de remettre le projet à la personne suivante. La boîte de réception vous permet d’afficher les notifications liées à ces tâches. Reportez-vous à la section <a href="/help/sites-administering/workflows.md">Utilisation des processus</a>. <br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Balisage</strong></td> 
   <td>Les consoles Balisage permettent de gérer des balises. Les balises sont des noms ou expressions courts servant à classer et à annoter des segments de contenu, afin qu’il soit plus facile de les rechercher et de les classer. Pour en savoir plus, voir <a href="/help/sites-classic-ui-authoring/classic-feature-tags.md">Utilisation et gestion des balises</a>.</td> 
  </tr> 
  <tr> 
   <td><strong>Outils</strong></td> 
   <td>Les <a href="/help/sites-administering/tools-consoles.md">consoles Outils</a> vous donnent accès à un certain nombre d’outils et de consoles spécialisés pour la gestion des sites Web, des ressources numériques et d’autres aspects du référentiel de contenu.</td> 
  </tr> 
  <tr> 
   <td><strong>Utilisateurs</strong></td> 
   <td>Ces consoles vous permettent de gérer les droits d’accès des utilisateurs et des groupes. Pour plus d’informations, reportez-vous à la section <a href="/help/sites-administering/security.md">Administration des utilisateurs et sécurité</a>.<br />  </td> 
  </tr> 
  <tr> 
   <td><strong>Sites web</strong></td> 
   <td>Les consoles Sites/Sites Web permettent <a href="/help/sites-classic-ui-authoring/classic-page-author.md">de créer, d’afficher et de gérer des sites Web</a> exécutés sur votre instance AEM. Grâce à ces consoles, vous pouvez créer, copier, déplacer et supprimer des pages de site Web, lancer des processus et activer (publier) des pages. Vous pouvez également ouvrir une page pour la modifier.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Workflows</strong></td> 
   <td>Un processus est une série d’étapes définies décrivant la procédure à suivre pour accomplir certaines tâches. Dans la plupart des cas, plusieurs personnes sont impliquées dans une tâche et chacune d’elles doit exécuter les étapes qui lui sont attribuées avant de remettre le projet à la personne suivante. La console Workflow vous permet d’élaborer des modèles de workflows et de gérer l’exécution des instances de workflow. Reportez-vous à la section <a href="/help/sites-administering/workflows.md">Utilisation des workflows</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Le **Sites web** La console propose deux volets grâce auxquels vous pouvez parcourir et gérer vos pages :

* Volet de gauche

   Présente l’arborescence de vos sites Web et les pages dans ces sites Web.

   Présente également des informations sur d’autres aspects d’AEM, y compris les projets, les plans directeurs et les ressources.

* Volet de droite

   Présente les pages (à l’emplacement sélectionné dans le volet de gauche) et permet d’utiliser des actions.

À partir de là, vous pouvez [gestion des pages](/help/sites-authoring/managing-pages.md) à l’aide de la barre d’outils, d’un menu contextuel ou en ouvrant une page pour d’autres actions.

>[!NOTE]
>
>Dans toutes les consoles, la gestion de base est la même. Cette section se concentre sur le **Sites web** console, car il s’agit de la Principale console utilisée lors de la création.

![chlimage_1-9](assets/chlimage_1-9.png)

## Accès à l’Aide {#accessing-help}

Sur diverses consoles (par exemple, Sites Web), il existe également **Aide** est disponible. Il ouvre Package Share ou le site de documentation.

![chlimage_1-10](assets/chlimage_1-10.png)

Lors de la modification d’une page, la variable [sidekick comporte également un bouton d’accès à l’aide](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#accessing-help).

## Navigation dans la console Sites web {#navigating-with-the-websites-console}

Le **Sites web** La console répertorie vos pages de contenu dans une arborescence (volet de gauche). Pour faciliter la navigation, les sections de l’arborescence peuvent être développées (+) ou réduites (-) selon les besoins :

* Un seul clic sur le nom de la page (dans le volet de gauche) permet d’effectuer les opérations suivantes :

   * Répertorier les pages enfants dans le volet de droite
   * Développez également la structure dans le volet de gauche.

      Pour des raisons de performances, cette action dépend du nombre de noeuds enfants. Avec une installation standard, cette méthode d’extension fonctionne avec un nombre de nœuds enfants inférieur ou égal à `30`.

* Un double-clic sur le nom de la page (volet de gauche) développe également l’arborescence. Cependant, étant donné que la page est ouverte en même temps, cet effet est moins visible.

>[!NOTE]
>
>Cette valeur par défaut (`30`) peut être modifiée pour chaque console dans les configurations du widget siteadmin spécifiques à votre application :
>
>Sur le noeud siteadmin :
>
>Définissez la valeur de la propriété :\
>`treeAutoExpandMax`\
>Sur :\
>`/apps/wcm/core/content/siteadmin`
>
>Ou globalement dans le thème :\
>Définissez la valeur de :\
>`TREE_AUTOEXPAND_MAX`\
>dans :\
>`/apps/cq/ui/widgets/themes/default/widgets/wcm/SiteAdmin.js`
>
>Voir [SiteAdmin dans l’API CQ Widget](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin) pour plus d’informations.

## Informations sur la page dans la console Sites web {#page-information-on-the-websites-console}

Le volet de droite de la **Sites web** La console fournit un mode Liste avec des informations sur les pages :

![page-info](assets/page-info.png)

Les informations suivantes sont disponibles ; un sous-ensemble de ces champs s’affiche par défaut :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Colonne</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Miniature</td> 
   <td>Affiche une miniature de la page.</td> 
  </tr> 
  <tr> 
   <td>Titre</td> 
   <td>Titre qui s’affiche sur la page.</td> 
  </tr> 
  <tr> 
   <td>Nom</td> 
   <td>Le nom AEM fait référence à la page.</td> 
  </tr> 
  <tr> 
   <td>Publié</td> 
   <td>Indique si la page a été publiée et indique la date et l’heure de publication.</td> 
  </tr> 
  <tr> 
   <td>Modifié</td> 
   <td>Indique si la page a été modifiée et fournit la date et l’heure de modification. Pour enregistrer toute modification, vous devez activer la page.</td> 
  </tr> 
  <tr> 
   <td>Publication Scene7</td> 
   <td>Indique si la page a été publiée sur Scene7.<br /> </td> 
  </tr> 
  <tr> 
   <td>Statut</td> 
   <td>Indique l’état actuel de la page, par exemple si la page fait partie d’un workflow ou d’une Live Copy, ou si une page est actuellement verrouillée.</td> 
  </tr> 
  <tr> 
   <td>Impressions</td> 
   <td>Affiche l’activité sur une page en nombre d’accès.</td> 
  </tr> 
  <tr> 
   <td>Modèle</td> 
   <td>Indique le modèle sur lequel repose une page.</td> 
  </tr> 
  <tr> 
   <td>Dans le processus</td> 
   <td>Indique le moment où la page se trouve dans un workflow.</td> 
  </tr> 
  <tr> 
   <td>Verrouillé par</td> 
   <td>Indique lorsqu’une page a été verrouillée et le compte utilisateur qui l’a verrouillée.</td> 
  </tr> 
  <tr> 
   <td>Live Copy</td> 
   <td>Indique si la page fait partie d’une Live Copy.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Pour sélectionner les colonnes visibles, pointez avec votre souris sur leurs titres. Un menu déroulant s’affiche. Vous pouvez utiliser la variable **Colonnes** .

Couleurs en regard des pages dans la variable **Publié** et **Modifié** les colonnes indiquent l’état de publication :

| **Colonne** | **Couleur** | **Description** |
|---|---|---|
| Publié | Vert | Publication réussie. Le contenu est publié. |
| Publié | Jaune | Publication en attente. Le système n&#39;a pas encore reçu la confirmation de publication. |
| Publié | Rouge | Échec de la publication. Il n’existe aucune connexion avec l’instance de publication. Cela peut également signifier que le contenu a été désactivé. |
| Publié | *blank* | Cette page n&#39;a jamais été publiée. |
| Modifié | Bleu | La page a été modifiée depuis la dernière publication. |
| Modifié | *blank* | Cette page n&#39;a jamais été modifiée ou n&#39;a pas été modifiée depuis la dernière publication. |

## Menus contextuels {#context-menus}

L’IU classique applique des mécanismes courants pour la navigation et le déclenchement des opérations, notamment clic et double-clic. En fonction de la situation actuelle, divers menus contextuels (généralement ouverts avec le bouton droit de la souris) sont également disponibles :

![chlimage_1-11](assets/chlimage_1-11.png)
