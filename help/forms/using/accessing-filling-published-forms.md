---
title: Accès et remplissage des formulaires publiés
seo-title: Accessing and filling published forms
description: Forms Portal fournit aux développeurs Web des composants pour la création et la personnalisation d’un portail de formulaires sur les sites Web créés à l’aide d’Adobe Experience Manager (AEM).
seo-description: Forms Portal equips Web Developers with components to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM).
uuid: dd03a9de-b412-4d7b-befe-981cb3aa8d0a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 0452062d-cf85-4009-a0a5-a1e891192ea8
exl-id: d68806f8-8ed8-4aff-9724-bafbe2b1f18e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 24%

---

# Accès et remplissage des formulaires publiés {#accessing-and-filling-published-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans une configuration de déploiement de portail axée sur les formulaires, le développement de formulaires et le développement de portail sont deux activités distinctes. Pendant que les concepteurs de formulaires créent et stockent des formulaires dans un référentiel, les développeurs Web créent une application Web qui répertorie les formulaires et gère les envois. Forms est ensuite copié sur la plateforme web, car il n’existe aucune communication entre le référentiel de formulaires et l’application web.

Cela entraîne souvent des problèmes lors de la gestion des délais de configuration et de production. Par exemple, si une version plus récente d’un formulaire est disponible dans le référentiel, le concepteur de formulaire remplace le formulaire sur la plateforme web, modifie l’application web et redéploie le formulaire sur le site public. Le redéploiement de l’application web peut entraîner un temps d’arrêt du serveur. Les temps d’arrêt du serveur étant une activité planifiée, les modifications ne peuvent pas être transférées immédiatement sur le site public.

Forms Portal réduit les surcharges de gestion et les délais de production. Il fournit aux développeurs Web des composants pour la création et la personnalisation d’un portail de formulaires sur les sites Web créés à l’aide d’Adobe Experience Manager (AEM).

Pour plus d’informations sur le portail des formulaires et ses fonctions, reportez-vous à la section [Présentation de la publication de formulaires sur un portail](/help/forms/using/introduction-publishing-forms.md).

## Prise en main de Forms Portal {#getting-started-with-forms-portal}

Accédez à la page Forms Portal publiée. Pour plus d’informations sur la création d’une page de portail de formulaires, reportez-vous à la section [Création d’une page de portail de formulaires](/help/forms/using/creating-form-portal-page.md).

Le composant Search and Lister de Forms Portal affiche les formulaires disponibles sur l’instance Publish du serveur AEM. Cette liste comprend tous les formulaires ou les formulaires définis dans le filtre au moment de la création de la page Forms Portal. Une page Forms Portal se présente comme illustré dans l’image suivante :

![Exemple de page de Forms Portal ](assets/forms-portal-page.png)
**Figure :** *Exemple de page Forms Portal*

### Search and Lister {#search-and-lister}

Le composant Search and Lister vous permet d’ajouter les fonctionnalités suivantes à votre portail de formulaires :

* Répertorier les formulaires en mode d’affichage Panneau, Carte ou Grille qui sont prêts à l’emploi. Il prend également en charge les formulaires templatesList personnalisés à partir de dossiers spécifiques dans Forms Manager.
* Spécifiez le mode de rendu des formulaires : HTML5, PDF ou les deux.
* Spécifiez le mode de rendu des formulaires PDF et XFA - HTML5, PDF ou les deux. Formulaires non-XFA au format HTML5.
* Activation de la recherche de formulaires en fonction de critères tels que les propriétés, les métadonnées et les balises de formulaire.
* Envoi de données de formulaire vers un servlet.
* Utilisation de feuilles de style (CSS) personnalisées pour la personnalisation de l’aspect et du style du portail.
* Création de liens vers des formulaires.

Vous pouvez rechercher des formulaires sur la page du portail Forms à l’aide des options suivantes :

* Recherche de texte intégral
* Recherche avancée

La recherche de texte intégral permet de rechercher et de répertorier des formulaires en fonction des mots-clés spécifiés.

![Boîte de dialogue de recherche avancée](assets/search-panel.png)
**Figure :** *Boîte de dialogue de recherche avancée*

La recherche avancée vous permet de rechercher des formulaires en fonction de propriétés de formulaire spécifiées. Elle fournit des résultats plus précis que la recherche de texte intégral. La recherche avancée comprend une recherche basée sur des balises, des propriétés (telles que l’auteur, la description et le titre), la date de modification et le texte intégral.

Lister affiche des formulaires en fonction des paramètres de recherche. Chaque formulaire du résultat de la recherche est affiché avec une icône, qui est liée au formulaire associé. Vous pouvez cliquer sur l’icône pour ouvrir et utiliser le formulaire associé.

### Remplissage d’un formulaire {#filling-a-form}

![Exemple de formulaire adaptatif](assets/filling_a_form.png)
**Figure :** *Exemple de formulaire adaptatif*

Les formulaires sont accessibles à partir du lien fourni avec le formulaire dans le composant Search and Lister de la page.

Chaque formulaire contient des informations d’aide qui permettent à l’utilisateur de le remplir.

#### Brouillons et envois {#drafts-and-submission}

Un utilisateur a la possibilité d’enregistrer un brouillon de formulaire en cliquant sur le bouton Enregistrer . Cela permet à l’utilisateur de travailler sur un formulaire pendant un certain temps avant de l’envoyer.

Les données renseignées dans le formulaire (y compris les pièces jointes) sont enregistrées en tant que brouillon sur le serveur. Le brouillon d’un formulaire peut être enregistré un nombre illimité de fois. Le formulaire enregistré apparaît dans l’onglet Brouillons du composant Drafts &amp; Submission de la page.

Une fois le formulaire rempli, l’utilisateur l’envoie en cliquant sur le bouton Envoyer. Les formulaires envoyés apparaissent dans l’onglet Envois du composant Drafts &amp; Submission de la page.

>[!NOTE]
>
>Les formulaires envoyés n’apparaissent dans l’onglet Formulaires envoyés que si l’action Envoyer du formulaire adaptatif est configurée comme Action d’envoi du Portail Formulaires. Pour plus d’informations sur les actions d’envoi, reportez-vous à la section [Configuration de l’action Envoyer](/help/forms/using/configuring-submit-actions.md).

![Composant Brouillons et envois](assets/draft-submission.png)
**Figure :** *Composant Drafts &amp; Submissions*

## Démarrage d’un nouveau formulaire à l’aide de données de formulaire envoyées {#start-a-new-form-using-submitted-form-data}

Il existe certains formulaires que vous devez remplir et envoyer assez souvent. Par exemple, le formulaire de déclaration individuelle est envoyé chaque année. Dans de tels cas, alors qu&#39;une partie de l&#39;information change à chaque fois que vous remplissez le formulaire, la plupart comme les détails personnels et familiaux ne changent pas. Cependant, vous devez toujours remplir le formulaire en entier, à partir de zéro.

AEM Forms peut vous aider à optimiser l’opération de remplissage du formulaire et à réduire considérablement le temps de remplissage et d’envoi d’un formulaire déjà envoyé au préalable. Les utilisateurs finaux peuvent démarrer un nouveau formulaire à l’aide des données d’un formulaire envoyé. Cette fonctionnalité est intégrée à la fonction [Composant Drafts and Submissions](/help/forms/using/draft-submission-component.md). Lorsque vous ajoutez un composant Drafts and Submission à votre page Forms Portal et que vous le publiez, les utilisateurs finaux ont une option dans les onglets Formulaires envoyés et Brouillons de formulaires pour démarrer un nouveau formulaire en utilisant des données d’un formulaire déjà envoyé. L’image suivante illustre cette option.

![démarrer-un-nouveau-formulaire](assets/start-a-new-form.png)

Lorsque vous cliquez sur le bouton pour lancer un nouveau formulaire, un nouveau formulaire contenant les données du formulaire envoyé correspondant s’ouvre. Vous pouvez désormais consulter et mettre à jour les informations, selon les besoins, puis envoyer le formulaire.
