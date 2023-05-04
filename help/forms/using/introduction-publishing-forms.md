---
title: Présentation de la publication de formulaires sur un portail
seo-title: Introduction to publishing forms on a portal
description: AEM Forms fournit des composants que vous pouvez utiliser pour créer votre portail de formulaires. Cet article vous présente les composants Forms Portal disponibles.
seo-description: AEM Forms provides with components that you can use to build your forms portal. This articles introduces you to the available forms portal components.
uuid: 96aa4fe2-a111-4675-a33c-7dee8b82cbc2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 44871fe1-ddc9-492c-8784-5df3ca392f9b
exl-id: a91e23e8-339d-4090-9872-2e066ab66590
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 63%

---

# Présentation de la publication de formulaires sur un portail {#introduction-to-publishing-forms-on-a-portal}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation des composants du portail AEM Forms {#aem-forms-portal-components-overview}

Dans un scénario de déploiement de portail basé sur l’utilisation de formulaires standard, le développement de formulaires et le développement de portail sont deux activités distinctes. Lorsque les concepteurs de formulaires créent et stockent des formulaires dans un référentiel, les développeurs Web créent une application Web pour répertorier les formulaires et gérer l’envoi de formulaires. Forms est copié sur la plateforme web, car il n’existe aucune communication entre le référentiel de formulaires et l’application web.

De tels scénarios entraînent souvent des problèmes de gestion et des retards de production. Par exemple, si une version plus récente d’un formulaire est disponible dans le référentiel, vous devez remplacer le formulaire sur la plateforme web, modifier l’application web et redéployer le formulaire sur le site public. Le redéploiement de l’application web peut entraîner un temps d’arrêt du serveur. En règle générale, le temps d’arrêt du serveur est une activité planifiée et les modifications ne peuvent donc pas être transmises instantanément au site public.

AEM Forms fournit des composants de portail qui réduisent les surcharges de gestion et les délais de production. Les composants permettent aux développeurs Web de créer et de personnaliser un portail de formulaires sur les sites Web créés à l’aide d’Adobe Experience Manager (AEM).

![Portail AEM Forms](assets/aem-forms-portal.png)

Les composants de Forms Portal vous permettent d’ajouter les fonctionnalités suivantes :

* Créez une liste de formulaires dans des mises en page personnalisées. Mises en page de vues Liste, Carte et Panneau prêtes à l’emploi. Vous pouvez créer vos propres mises en page personnalisées.
* Permet d’afficher des métadonnées personnalisées ainsi que des actions personnalisées lors de leur mise en liste.
* Créez des listes de formulaires publiés par l’interface utilisateur d’AEM Forms sur l’instance de publication où sont utilisés les composants du portail Formulaires.
* Possibilité pour les utilisateurs finaux d’afficher les formulaires aux formats HTML et PDF.
* Utilisation d’un profil HTML personnalisé pour le rendu des formulaires.
* Activation de la recherche de formulaires en fonction de différents critères, tels que les propriétés, les métadonnées et les balises du formulaire.
* Envoi de données de formulaire vers une servlet.
* Utilisation de feuilles CSS pour la personnalisation de l’apparence du portail.
* Création de liens vers des formulaires.
* Répertorie les brouillons et les envois liés au formulaire adaptatif créé par l’utilisateur final.

## Composants disponibles du portail AEM Forms {#available-aem-forms-portal-components}

AEM Forms fournit les composants de portail suivants prêts à l’emploi, regroupés sous les groupes de composants **Services de document** et **Prédicats de services de document** :

### Search &amp; Lister {#search-amp-lister}

Le composant Search &amp; Lister vous permet de répertorier les formulaires du référentiel de formulaires sur votre page de portail et fournit des options de configuration pour répertorier les formulaires selon des critères spécifiés. Il permet également de spécifier des critères de recherche pour permettre aux utilisateurs et utilisatrices du portail d’effectuer des recherches dans la liste des formulaires.

### Brouillons et soumissions {#drafts-amp-submissions}

Tandis que le composant Search &amp; Lister affiche les formulaires rendus publics par l’auteur Forms, le composant Drafts &amp; Submissions (Brouillons et envois) affiche les formulaires enregistrés en tant que brouillons en vue de les compléter ultérieurement et les formulaires envoyés. Ce composant fournit une expérience personnalisée à tout utilisateur connecté.

### Lien {#link}

Le composant Lien vous permet de créer un lien vers un formulaire n’importe où sur la page. Supposons que vous proposiez un programme de formation et que vous souhaitiez que vos utilisateurs envoient un formulaire pour s’inscrire à la formation. Sur votre site web, vous avez publié les détails du programme. Vous trouverez ci-dessous les détails du formulaire d&#39;inscription. Le composant Lien peut vous aider à créer ce lien.

## Workflow du portail Formulaires {#forms-portal-workflow}

Le Portail Formulaires vous permet de répertorier les formulaires du référentiel de formulaires sur la page du portail. Il permet également de spécifier des critères de recherche pour permettre aux utilisateurs du portail d’effectuer des recherches dans la liste des formulaires. Vous pouvez également utiliser le composant Brouillons et envois pour afficher les formulaires enregistrés en tant que brouillon en vue de les remplir ultérieurement et de formulaires envoyés. Vous devez effectuer un certain ensemble d’opérations avant que ces fonctionnalités ne soient disponibles sur une page Sites. Suivez les étapes de la séquence répertoriée pour rendre les composants et les fonctionnalités correspondantes disponibles sur une page de Sites :

1. **Activer les composants du portail Formulaires** : les composants du portail Formulaires prêts à l’emploi ne sont pas disponibles. [Activez les composants depuis AEM sidekick](/help/forms/using/enabling-forms-portal-components.md) pour une page AEM Sites.
1. **Répertorier des formulaires sur une page (créer une page du portail Formulaires) :** vous pouvez répertorier les formulaires à la fois sur les pages AEM Sites et sur celles qui ne sont pas AEM Sites. La liste contient les formulaires disponibles sur l’instance de publication. Un utilisateur peut ouvrir des formulaires et commencer à les remplir. Chaque fois qu’un utilisateur ouvre un formulaire, une nouvelle instance de formulaire est créée :

   1. **Répertorier les formulaires sur une page AEM Sites** : ajoutez le composant **[Search &amp; Lister](/help/forms/using/creating-form-portal-page.md)** à la page et configurez le **[Volet Liste](/help/forms/using/creating-form-portal-page.md#p-list-pane-p)** dans la page pour répertorier les formulaires y contenus. Ajoutez et configurez le composant **[Volet Recherche](/help/forms/using/creating-form-portal-page.md#search-pane)** au composant **Search &amp; Lister** pour ajouter également la fonctionnalité de recherche à la page. La page contenant le composant Portail Formulaires est appelée [page du Portail Formulaires](/help/forms/using/creating-form-portal-page.md).
   1. **Répertorier les formulaires sur une page non AEM Sites :** utilisez les [API de recherche du Portail Formulaires](/help/forms/using/listing-forms-webpage-using-apis.md) pour interroger, récupérer et répertorier des formulaires sur des pages non AEM Sites.

1. **Répertorier les brouillons de formulaires et les formulaires envoyés sur une page du portail Formulaires** : ajoutez et configurez le composant Drafts &amp; Submissions (Brouillons et envois) sur la page du portail Formulaires. Le composant dresse la liste de tous les formulaires qui sont à l’état de brouillon et des formulaires déjà envoyés.

   Pour activer l’affichage d’un formulaire adaptatif envoyé dans l’onglet des envois, définissez **Action d’envoi** sur **[Action d’envoi du portail Formulaires](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/configuring-submit-actions.html).** Vous pouvez également activer l’option Envoyer du portail Formulaires. Lorsqu’un utilisateur envoie un formulaire, ce dernier est ajouté à l’onglet des envois.

1. **Configurez le stockage pour les données de brouillons de formulaires et formulaires envoyés :** par défaut, les données des brouillons et des envois sont stockées dans le référentiel AEM. Dans un environnement de production, il est recommandé de ne pas stocker des données de formulaire de brouillon ou envoyées dans le référentiel AEM. [Configurez le composant du portail Formulaires pour enregistrer les données à un emplacement sécurisé](/help/forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Facultatif) Personnaliser des composants du portail Formulaires :** [personnalisez des modèles de page du portail Formulaires](/help/forms/using/customizing-templates-forms-portal-components.md) pour donner un aspect distinctif aux composants.
1. **(Facultatif) Ajouter des métadonnées personnalisées aux formulaires :** [ajoutez des métadonnées personnalisées aux formulaires](/help/forms/using/customizing-templates-forms-portal-components.md) pour améliorer l’expérience de recherche et de mise en liste.
1. **Publier la page du portail Formulaires :** votre page du portail Formulaires est maintenant prête. Publiez la page.

## Articles connexes {#related-articles}

* [Activer des composants du portail Formulaires](/help/forms/using/enabling-forms-portal-components.md)
* [Créer une page du portail Formulaires](/help/forms/using/creating-form-portal-page.md)
* [Affichage de la liste des formulaires sur une page Web à l’aide d’API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Utiliser le composant Brouillons et Envois](/help/forms/using/draft-submission-component.md)
* [Personnaliser le stockage des brouillons de formulaires et des formulaires envoyés](/help/forms/using/draft-submission-component.md#customizing-the-storage)
* [Exemple d’intégration d’un composant brouillons et envois à une base de données](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html)

* [Personnalisation de modèles pour les composants Forms Portal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Présentation de la publication de formulaires sur un portail](/help/forms/using/introduction-publishing-forms.md)
