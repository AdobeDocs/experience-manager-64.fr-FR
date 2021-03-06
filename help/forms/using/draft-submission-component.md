---
title: Composant Drafts & Submissions
seo-title: Drafts and submissions component
description: Le composant Drafts & Submissions dresse la liste de tous les formulaires qui sont à l’état de brouillon et des formulaires déjà envoyés. Vous pouvez personnaliser l’aspect et le style du composant
seo-description: Drafts and submissions component lists forms that are in the draft state and are already submitted. You can customize appearance and style of the component.
uuid: 351d6df5-0dc3-4f7a-8bdf-0f1c8dd80f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 219dd379-5bc9-40b0-bdc2-2fb347da29d8
exl-id: d95d3586-ea4b-4068-a8f2-a198c27a0096
source-git-commit: 251000ec9a67e5175c708d558c3c71a2061a1c9e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 99%

---

# Composant Drafts &amp; Submissions {#drafts-and-submissions-component}

Le composant Drafts &amp; Submissions dresse la liste de tous les formulaires qui sont à l’état de brouillon et des formulaires déjà envoyés. Le composant dispose de sections distinctes (onglets) pour les brouillons et les formulaires envoyés. Les utilisateurs peuvent afficher leurs brouillons et leurs formulaires envoyés uniquement.

## Configuration du composant {#configuring-the-component}

Le composant Drafts &amp; Submissions comporte deux onglets : Brouillons et envois.

Pour autoriser un envoi de formulaire adaptatif à apparaître dans l’onglet des envois, définissez **Action d’envoi** sur **[Action d’envoi du Portail Formulaires](/help/forms/using/configuring-submit-actions.md).** Vous pouvez également activer l’option Envoyer du portail Formulaires. Lorsqu’un utilisateur envoie le formulaire, ce formulaire est ajouté à l’onglet des envois.

La fonctionnalité de brouillons est activée immédiatement. Lorsqu’un utilisateur clique sur **Enregistrer** sur un formulaire adaptatif, le formulaire est ajouté à l’onglet des brouillons.

Effectuez les étapes suivantes pour ajouter et configurer le composant Drafts &amp; Submissions :

1. Faites glisser le composant **Brouillons et envois** sous la catégorie Document Services dans le navigateur de composants sur votre page.
1. Cliquez sur le composant, puis sur ![settings_icon](assets/settings_icon.png) pour ouvrir la boîte de dialogue Modifier du composant.

   ![Composant Drafts &amp; Submissions](assets/drafts-submissions-edit.png)

1. Dans la boîte de dialogue Modifier, spécifiez les détails suivants et appuyez sur **Terminé** pour enregistrer les paramètres.

<table>
 <tbody>
  <tr>
   <th>Tabulation</th>
   <th>Configuration</th>
   <th>Description</th>
  </tr>
  <tr>
   <td>Général</td>
   <td>Résultat total</td>
   <td>Spécifie le nombre maximal de résultats à afficher. Si le nombre de résultats augmente la limite de résultat total, un lien <strong>Plus</strong> apparaît au bas du composant. Pour afficher tous les formulaires, cliquez sur <strong>Plus. </strong> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Type de style</td>
   <td>Indique le style du composant. Vous pouvez spécifier <strong>Aucun Style</strong>, <strong>Style par défaut</strong> ou <strong>Style personnalisé</strong> pour répertorier les formulaires. Pour l’option Style personnalisé, vous pouvez spécifier le chemin du fichier CSS personnalisé dans le champ <strong>Chemin d’accès au style personnalisé</strong><strong>.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Chemin d’accès au style personnalisé</td>
   <td>Si vous sélectionnez l’option <strong>Style personnalisé</strong> dans le champ <strong>Type de style</strong>, utilisez le champ <strong>Chemin d’accès au style personnalisé</strong> pour spécifier le chemin du fichier CSS personnalisé. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Options d’affichage :</td>
   <td><p>Spécifie les onglets à afficher. Vous pouvez choisir d’afficher des brouillons de formulaires, des formulaires envoyés, ou les deux. </p> <p><strong>Remarque</strong> :<em> Pour les <strong>Options d’affichage</strong>, si vous sélectionnez une option autre que <strong>Les deux</strong>, l’option du champ <strong>Tabulation par défaut</strong> n’est pas utilisée.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Tabulation par défaut</td>
   <td>Spécifie l’onglet à afficher au chargement de la page du portail de formulaires. Vous pouvez choisir entre <strong>l’onglet Brouillons de formulaires</strong> et <strong>l’onglet Formulaires envoyés</strong>.</td>
  </tr>
  <tr>
   <td>Configuration de l’onglet Brouillons de formulaires</td>
   <td>Titre personnalisé</td>
   <td>Spécifie le titre de l’onglet <strong>Brouillons de formulaires</strong>. La valeur par défaut est <strong>Brouillons de formulaires.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Modèle de mise en page</td>
   <td><p>Spécifie la mise en page à utiliser pour la liste Brouillons de formulaires.</p> <p><strong>Remarque :</strong> n’utilisez pas l’option par défaut (obsolète).<br /> </p> </td>
  </tr>
  <tr>
   <td>Configuration de l’onglet Formulaires envoyés</td>
   <td>Titre personnalisé </td>
   <td>Spécifie le titre de l’onglet <strong>Formulaires envoyés</strong>. La valeur par défaut est <strong>Formulaires envoyées.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Modèle de mise en page</td>
   <td>Spécifie l’affichage à utiliser pour la liste Formulaires<strong> </strong>envoyés. </td>
  </tr>
 </tbody>
</table>

## Personnaliser l’espace de stockage {#customizing-the-storage}

Lorsque vous utilisez l’action d’envoi Forms Portal ou activez les données de stockage dans l’option de portail de formulaires dans un formulaire adaptatif, les données du formulaire sont stockées dans le référentiel AEM. Dans un environnement de production, il est recommandé de ne pas stocker des données de formulaire de brouillon ou envoyées dans le référentiel AEM. Au contraire, vous devez intégrer le composant de brouillons et d’envoi à un stockage sécurisé comme la base de données d’entreprise pour stocker des brouillons et des données de formulaires envoyés.

Le portail Formulaires vous permet de stocker des données dans un référentiel AEM local ou distant ou dans une base de données. AEM Forms vous permet de personnaliser l’implémentation du stockage des données utilisateur pour les brouillons et les envois. Vous pouvez remplacer les méthodes par défaut pour spécifier la manière dont les données de brouillon et d’envoi sont stockées dans un espace de stockage de votre choix. Vous pouvez, par exemple, stocker les données dans un entrepôt de données implémenté au sein de votre entreprise.

Le portail Formulaires fournit des services prêts à l’emploi (API) pour stocker des données sur le référentiel crx d’instances de publication AEM Forms locales et distantes. Vous pouvez remplacer les implémentations par défaut, décrites dans l’artickle [Configurer les services de stockage pour les brouillons et les envois](/help/forms/using/configuring-draft-submission-storage.md), par des implémentations personnalisées. Pour plus d’informations sur les méthodes requises dans le cadre d’une implémentation personnalisée visant à stocker du contenu dans un emplacement sécurisé, consultez la section [Personnaliser les services de données de brouillons et d’envois](/help/forms/using/custom-draft-submission-data-services.md) et [Stockage personnalisé des composant brouillons et envois.](/help/forms/using/adding-custom-storage-provider-forms.md)

La documentation d’AEM Forms fournit un [Exemple d’intégration d’un composant brouillons et envois à la base de données](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html). Vous pouvez utiliser l’exemple d’implémentation pour développer votre propre implémentation personnalisée.

## Articles connexes

* [Activer des composants du portail Formulaires](/help/forms/using/enabling-forms-portal-components.md)
* [Créer une page du portail Formulaires](/help/forms/using/creating-form-portal-page.md)
* [Affichage de la liste des formulaires sur une page Web à l’aide d’API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Utiliser le composant Brouillons et Envois](/help/forms/using/draft-submission-component.md)
* [Personnaliser le stockage des brouillons de formulaires et des formulaires envoyés](/help/forms/using/draft-submission-component.md)
* [Exemple d’intégration d’un composant brouillons &amp; envois à la base de données](/help/forms/using/integrate-draft-submission-database.md)
* [Personnalisation de modèles pour les composants Forms Portal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Présentation de la publication de formulaires sur un portail](/help/forms/using/introduction-publishing-forms.md)
