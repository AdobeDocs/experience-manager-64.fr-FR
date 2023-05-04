---
title: Statut des fonctionnalités de l’IU tactile
seo-title: Touch UI Feature Status
description: Notes de mise à jour spécifiques à l’interface utilisateur tactile d’Adobe Experience Manager 6.3.
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 59%

---

# Statut des fonctionnalités de l’IU tactile {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>Avec la version 6.4 d’AEM, la variable [L’interface utilisateur classique est obsolète.](/help/release-notes/deprecated-removed-features.md). Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique et les utilisateurs sont encouragés à tirer parti des nouvelles fonctionnalités puissantes disponibles dans l’interface utilisateur tactile.

À compter de la version 6.0, AEM a introduit une nouvelle interface utilisateur appelée &quot;IU tactile&quot; (également appelée &quot;IU tactile&quot;) alignée sur Adobe Marketing Cloud et les directives générales de l’interface utilisateur de l’Adobe. Avec la quasi-partialité des fonctionnalités atteinte, cette interface est devenue l’interface standard d’AEM avec l’ancienne interface orientée bureau appelée &quot;IU classique&quot;.

Bien que la plupart des fonctionnalités soient déjà présentes dans l’interface utilisateur optimisée pour les écrans tactiles, il en reste certaines à intégrer, qui le seront dans les prochaines mises à jour.

La liste ci-dessous indique le statut actuel des fonctionnalités implémentées dans AEM 6.4.

Pour des recommandations destinées aux clients qui effectuent une mise à niveau vers AEM 6.4, reportez-vous à la section [Recommendations de l’interface utilisateur pour les clients](/help/sites-deploying/ui-recommendations.md) pour plus d’informations.

>[!NOTE]
>
>Notez que cette page couvre uniquement la parité des fonctionnalités avec l’IU classique.
>
>Les fonctionnalités ajoutées et uniques à l’IU tactile qui ne sont pas présentes dans l’IU classique ne sont pas répertoriées.

>[!NOTE]
>
>Cette liste s’efforce d’être complète, mais ne doit pas être considérée comme exhaustive.

## Légende {#legend}

* **Terminer**: Cette fonctionnalité est entièrement disponible dans l’IU tactile.
* **Principalement** : la fonctionnalité est principalement disponible dans l’IU optimisée pour les écrans tactiles.
* **Absente**: Cette fonctionnalité n’est pas présente dans l’IU tactile. L’IU classique doit être utilisée pour effectuer cette action.
* **Remplacé**: La fonctionnalité a été remplacée par une nouvelle mise en oeuvre qui fonctionne différemment.
* **Supprimée :** la fonctionnalité n’existe plus dans l’IU optimisée pour les écrans tactiles et elle ne sera pas remplacée.

## Statut des fonctionnalités : administration de sites {#feature-status-sites-admin}

Vous trouverez ci-dessous la liste des fonctionnalités de l’Administration de sites de l’IU classique (`/siteadmin`) et leur statut dans l’IU optimisée pour les écrans tactiles ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité<br /> </strong></td> 
   <td><strong>Statut<br /> </strong></td> 
   <td><strong>Commentaire</strong></td> 
  </tr>
  <tr>
   <td>Navigation dans l’arborescence du site</td> 
   <td>Complète<br /> </td> 
   <td>AEM 6.4 a introduit un <a href="/help/sites-authoring/basic-handling.md#content-tree">aperçu d’arborescence de contenu</a>.</td> 
  </tr>
  <tr>
   <td>Démarrer le workflow</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Création d’une page.</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Créer un site</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Créer un lancement</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Créer une Live Copy <br /> </td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Créer un dossier</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Afficher le statut de publication</td> 
   <td>Principalement</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Rechercher</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copier/coller la page (Dupliquer)</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Déplacer la ou les pages</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publier la ou les pages</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publier une ou plusieurs pages sans droits de réplication</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publier ultérieurement</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Arborescence de publication</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulation de la publication des pages</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annuler la publication de pages sans droits de réplication</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Dépublier ultérieurement</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Supprimer</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Verrouillage/déverrouillage</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Afficher/modifier les propriétés</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Définition des autorisations sur la ou les pages</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Historique des versions</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurer la version</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurer l’arborescence et restaurer les pages supprimées</td> 
   <td>Absente</td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
  <tr>
   <td>Afficher la différence entre l’ancienne et la nouvelle version<br /> </td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Actions de Live Copy (déploiement)</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Voir Copies de langue</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Rechercher et remplacer</td> 
   <td>Absente<br /> </td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
  <tr>
   <td>Boîte de réception de notifications (événements JCR)</td> 
   <td>Absente</td> 
   <td>Utiliser l’IU classique. Sera remplacé par une mise en oeuvre différente.</td> 
  </tr>
  <tr>
   <td>Références</td> 
   <td>Principalement</td> 
   <td>L'affichage des liens de pages entrantes sera ajouté dans la version 2019 d'AEM.</td> 
  </tr>
 </tbody>
</table>

## Statut des fonctionnalités : éditeur de page {#feature-status-page-editor}

Vous trouverez ci-dessous la liste des fonctionnalités de l’éditeur de page de l’interface utilisateur classique (`/cf#`) et leur statut dans l’IU optimisée pour les écrans tactiles ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Statut</strong></td> 
   <td><strong>Commentaire</strong></td> 
  </tr>
  <tr>
   <td>Modifier les pages web</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les pages web mobiles<br /> </td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier le contenu importé via Design Importer <br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les courriers électroniques</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les applications mobiles</td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les formulaires</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les offres</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifier les modèles de workflows<br /> </td> 
   <td>Terminé</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ode : Modifier et prévisualiser</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Aperçu réactif<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mode : Modifier la conception</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mode : Génération de modèles automatique</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mode : Statut des Live Copy<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ajout d’annotations</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modification des propriétés<br /> </td> 
   <td>Terminé</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Page de déploiement</td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Démarrer et afficher le workflow</td> 
   <td>Terminé</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Gestion des packages de workflow</td> 
   <td>Principalement</td> 
   <td>Complètement accessible dans l’interface utilisateur tactile. Plusieurs payload de workflow sont toujours présentés dans l’IU classique.<br /> </td> 
  </tr>
  <tr>
   <td>Verrouiller/déverrouiller la page</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publier la page <br /> </td> 
   <td>Terminé<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Dépublication de la page</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copie de la page</td> 
   <td>Supprimé<br /> </td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copier les pages</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Déplacer la page</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">déplacer les pages</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Supprimer la page</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">supprimer les pages</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Afficher les références</td> 
   <td>Supprimé</td> 
   <td>Utilisez Administration de sites pour <a href="/help/sites-authoring/author-environment-tools.md#references">voir la liste de référence détaillée</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Journal d’audit</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites et <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">ouvrez le rail d’activité</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Créer la version</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">créer de nouvelles versions</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Restaurer la version</td> 
   <td>Supprimé</td> 
   <td>Utilisez Administration de sites pour <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">restaurer des versions</a>.</td> 
  </tr>
  <tr>
   <td>Changement de lancement</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-authoring/launches-promoting.md">basculer entre les lancements</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traduire la page</td> 
   <td>Supprimé</td> 
   <td>Utilisez l’Administration de sites pour <a href="/help/sites-administering/tc-manage.md">ajouter une page aux projets de traduction</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (choisissez la date/l’heure et parcourez le site tel qu’il était avant) <br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Définition des autorisations</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IU contextuelle du client <br /> </td> 
   <td>Remplacé</td> 
   <td>Utilisez la variable <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> Dorénavant, l’interface utilisateur est disponible.</td> 
  </tr>
  <tr>
   <td>Outil de recherche de contenu pour les différents types de médias<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Liste des composants</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copier et coller des composants<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Liste des composants dans le presse-papiers</td> 
   <td>Absente</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annuler/rétablir</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Faire glisser et déposer du contenu dans l’espace réservé du composant</td> 
   <td>Terminé</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Faites glisser et déposez directement le contenu dans l’espace réservé parsys avec la création automatique de composant.<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Statut des fonctionnalités : éditeurs de texte, d’image et de tableau {#feature-status-text-table-and-image-editors}

Vous trouverez ci-dessous la liste des fonctionnalités des éditeurs de texte, d’image et de tableau de l’interface utilisateur classique et leur statut dans l’IU optimisée pour les écrans tactiles.

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Statut </strong></td> 
   <td><strong>Commentaire<br /> </strong></td> 
  </tr>
  <tr>
   <td>Éditeur de texte enrichi</td> 
   <td>Complète</td> 
   <td>Utilisable sur place, dans une boîte de dialogue et en plein écran.</td> 
  </tr>
  <tr>
   <td>Activation/désactivation des modules externes de l’éditeur de texte enrichi</td> 
   <td>Complète<br /> </td> 
   <td>Cette opération peut être effectuée à l’aide de l’<a href="/help/sites-authoring/templates.md">Éditeur de modèles</a>.</td> 
  </tr>
  <tr>
   <td>Utilisation de l’éditeur de texte enrichi pour le texte brut</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : Liens et ancre</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : table de caractères</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : copier/coller</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : coller à partir de Microsoft Word<br /> </td> 
   <td>Terminé</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : Chercher et Remplacer</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : formats de texte (gras, ...)</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : Sub &amp; Subscription</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : justifier</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : listes (puce/nombres)</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : format de paragraphe</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : styles de texte</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : Éditeur de source (Modifier le HTML)<br /> </td> 
   <td>Terminé<br /> </td> 
   <td>Disponible uniquement dans la boîte de dialogue et en plein écran.<br /> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : vérificateur orthographique</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : tableau (éditeur de tableau incorporé)</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : annuler/rétablir<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe de l’éditeur de texte enrichi : autorisation des images en ligne</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Éditeur de tableau</td> 
   <td>Complète</td> 
   <td>Utilisable sur place, dans une boîte de dialogue et en plein écran.<br /> </td> 
  </tr>
  <tr>
   <td>Glisser-déposer une image dans une cellule de tableau<br /> </td> 
   <td>Complète</td> 
   <td>Utilisable en ligne</td> 
  </tr>
  <tr>
   <td>Éditeur d’image<br /> </td> 
   <td>Complète</td> 
   <td>Utilisable sur place, dans une boîte de dialogue et en plein écran.<br /> </td> 
  </tr>
  <tr>
   <td>Activation/désactivation des modules externes IPE</td> 
   <td>Complète</td> 
   <td>Il existe désormais une interface utilisateur dans <a href="/help/sites-authoring/templates.md">Éditeur de modèles</a>.</td> 
  </tr>
  <tr>
   <td>Module externe IPE : recadrer</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe IPE : retourner</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe IPE : annuler/rétablir</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe IPE : zone cliquable</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe IPE : rotation</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Module externe IPE : zoom</td> 
   <td>Complète<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Statut des fonctionnalités : outils {#feature-status-tools}

Il s’agit d’une liste des différents outils de l’IU classique et de leur état dans l’IU tactile.

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité<br /> </strong></td> 
   <td><strong>Statut<br /> </strong></td> 
   <td><strong>Commentaire</strong></td> 
  </tr>
  <tr>
   <td>Gestion des tâches</td> 
   <td>Remplacé</td> 
   <td>Introduction de la version 6.0 <a href="/help/sites-authoring/projects.md">Projets et tâches</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Boîte de réception des workflows<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configuration de modèle de workflow en page (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Absente<br /> </td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
  <tr>
   <td>Interface utilisateur d’administration du balisage<br /> </td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Centre de contrôle des plans directeurs / MSM</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface utilisateur du gestionnaire de plans directeurs</td> 
   <td>Complète</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface utilisateur de configuration du déploiement</td> 
   <td>Absente</td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
  <tr>
   <td>Interface utilisateur des utilisateurs, groupes et autorisations<br /> </td> 
   <td>Principalement complète<br /> </td> 
   <td>Pour la modification avancée d’autorisations, utilisez l’interface utilisateur classique.<br /> </td> 
  </tr>
  <tr>
   <td>Purge des versions (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Absente</td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
  <tr>
   <td>Vérificateur de lien externe (<code>/etc/linkchecker.html</code>)</td> 
   <td>Absente</td> 
   <td>Utiliser l’IU classique.<br /> </td> 
  </tr>
  <tr>
   <td>Éditeur en bloc (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Absente<br /> </td> 
   <td>Utiliser l’IU classique.</td> 
  </tr>
 </tbody>
</table>
