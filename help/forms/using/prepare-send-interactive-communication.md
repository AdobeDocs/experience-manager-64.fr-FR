---
title: Préparation et envoi d’une communication interactive à l’aide de l’interface utilisateur de l’agent
seo-title: Prepare and send Interactive Communication using the Agent UI
description: L’interface utilisateur de l’agent permet aux agents de préparer et d’envoyer la communication interactive au post-traitement. L’agent apporte les modifications nécessaires dans la mesure du possible et envoie la communication interactive en post-traitement, comme un courrier électronique ou une impression.
seo-description: Prepare and send Interactive Communication using the Agent UI
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interactive Communication
exl-id: 5ec33ef5-1722-4d29-9979-d8da32923e66
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 100%

---

# Préparation et envoi d’une communication interactive à l’aide de l’interface utilisateur de l’agent {#prepare-and-send-interactive-communication-using-the-agent-ui}

L’interface utilisateur de l’agent permet aux agents de préparer et d’envoyer la communication interactive au post-traitement. L’agent apporte les modifications nécessaires dans la mesure du possible et envoie la communication interactive en post-traitement, comme un courrier électronique ou une impression.

## Présentation {#overview}

Après la création d’une communication interactive, l’agent peut ouvrir la communication interactive dans l’interface utilisateur de l’agent et préparer une copie pour le destinataire en saisissant les données et en gérant le contenu et les pièces jointes. Enfin, l’agent peut envoyer la communication interactive en post-traitement.

Tout en préparant la communication interactive à l’aide de l’interface utilisateur de l’agent, l’agent gère les aspects suivants de la communication interactive dans l’interface utilisateur de l’agent avant de l’envoyer en post-traitement :

* **Données** : l’onglet Données de l’interface utilisateur de l’agent affiche toutes les variables modifiables par l’agent et les propriétés du modèle de données du formulaire non verrouillées dans la communication interactive. Ces variables/propriétés sont créées lors de la modification ou de la création de fragments de documents inclus dans la communication interactive. L’onglet Données comprend également tous les champs intégrés dans le modèle de canal d’impression/XDP. L’onglet Données n’apparaît que lorsque des variables, des propriétés de modèle de données de formulaire ou des champs de la communication interactive peuvent être modifiés par l’agent.
* **Contenu** : dans l’onglet Contenu, l’agent gère le contenu, tel que des fragments de documents et des variables de contenu dans la communication interactive. L’agent peut effectuer les modifications dans le fragment de document, comme autorisé, tout en créant la communication interactive dans les propriétés de ces fragments de document. L’agent peut également réorganiser, ajouter/supprimer un fragment de document et ajouter des sauts de page, si cela est autorisé.
* **Pièces jointes** : l’onglet Pièces jointes apparaît dans l’interface utilisateur de l’agent uniquement si la communication interactive comporte des pièces jointes ou si l’agent a accès à la bibliothèque. L’agent peut être autorisé ou non à modifier les pièces jointes.

## Préparation d’une communication interactive à l’aide de l’interface utilisateur de l’agent {#prepare-interactive-communication-using-the-agent-ui}

1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez la communication interactive appropriée et appuyez sur **[!UICONTROL Ouvrir l’interface utilisateur de l’agent]**.

   >[!NOTE]
   >
   >L’interface utilisateur de l’agent ne fonctionne que si la communication interactive sélectionnée possède un canal d’impression.

   ![openagentiui](assets/openagentiui.png)

   En fonction du contenu et des propriétés de la communication interactive, l’interface utilisateur de l’agent affiche les trois onglets suivants : Données, Contenu et Pièces jointes.

   ![agentuitabs](assets/agentuitabs.png)

   Procédez à la saisie des données, à la gestion du contenu et à la gestion des pièces jointes.

### Saisir des données {#enter-data}

1. Dans l’onglet Données, saisissez les données pour les variables, les propriétés du modèle de données de formulaire et les champs du modèle d’impression (XDP), selon les besoins. Remplissez tous les champs obligatoires identifiés par un astérisque (*) pour activer le bouton **Envoyer**.

   Appuyez sur une valeur de champ de données dans l’aperçu de la communication interactive pour mettre en surbrillance le champ de données correspondant dans l’onglet Données et vice versa.

### Gérer le contenu {#manage-content}

Dans l’onglet Contenu, vous pouvez gérer du contenu, tel que des fragments de documents et des variables de contenu dans la communication interactive.

1. Sélectionnez **[!UICONTROL Contenu]**. L’onglet des Contenus de la communication interactive s’affiche.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. Modifiez les fragments de document, selon les besoins, dans l’onglet Contenu. Pour focaliser l’attention sur le fragment approprié dans la hiérarchie des contenus, vous pouvez appuyer sur la ligne ou le paragraphe approprié(e) dans l’aperçu de la communication interactive ou appuyer sur le fragment directement dans la hiérarchie des contenus.

   Par exemple, le fragment de document avec la ligne « Effectuer un paiement en ligne dès maintenant… » est sélectionné dans l’aperçu du graphique ci-dessous et le même fragment de document est sélectionné dans l’onglet Contenu.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   Dans l’onglet Contenu ou Données, en appuyant sur Mettre en surbrillance les modules sélectionnés dans les Contenus (![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) dans le coin supérieur gauche de l’aperçu, vous pouvez activer ou désactiver la fonctionnalité d’accès au fragment de document lorsque le texte, le paragraphe ou le champ de données approprié est sélectionné dans l’aperçu.

   Les fragments qui peuvent être modifiés par l’agent lors de la création de la communication interactive comportent l’icône Modifier le contenu sélectionné (![iconeditselectedcontent](assets/iconeditselectedcontent.png)). Appuyez sur l’icône Modifier le contenu sélectionné pour lancer le fragment en mode édition et y apporter des modifications. Utilisez les options suivantes pour formater et gérer le texte :

   * [Options de mise en forme](#formattingtext)

      * [Copier-coller du texte formaté depuis d’autres applications](#pasteformattedtext)
      * [Parties du texte en surbrillance](#highlightemphasize)
   * [Caractères spéciaux](#specialcharacters)
   * [Raccourcis clavier](/help/forms/using/keyboard-shortcuts.md)

   Pour plus d’informations sur les actions disponibles pour différents fragments de document dans l’interface utilisateur de l’agent, consultez la section [Actions et informations disponibles dans l’interface utilisateur de l’agent](#actionsagentui).

1. Pour insérer un saut de page sur la communication interactive imprimée, placez le curseur à l’endroit où vous souhaitez insérer un saut de page et sélectionnez Saut de page avant ou Saut de page après (![pagebreakbeforeafter](assets/pagebreakbeforeafter.png)).

   Un espace réservé explicite de saut de page est inséré dans la communication interactive. Pour voir comment un saut de page explicite affecte la communication interactive, reportez-vous à l’aperçu avant impression.

   ![explicitpagebreak](assets/explicitpagebreak.png)

   Procédez à la gestion des pièces jointes de la communication interactive.

### Gestion des pièces jointes {#manage-attachments}

1. Sélectionnez **[!UICONTROL Pièce jointe]**. L’interface utilisateur de l’agent affiche les pièces jointes disponibles de la manière dont elles ont été configurées lors de la création de la communication interactive.

   Vous pouvez choisir de ne pas envoyer de pièce jointe avec la communication interactive en appuyant sur l’icône Aperçu et en appuyant sur la croix dans la pièce jointe pour la supprimer de la communication interactive (si l’agent a le droit de supprimer ou de masquer la pièce jointe). Pour les pièces jointes spécifiées comme obligatoires, lors de la création de la communication interactive, les icônes Afficher et Supprimer sont désactivées.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. Appuyez sur l’icône d’accès à la bibliothèque (![libraryaccess](assets/libraryaccess.png)) pour accéder à la bibliothèque de contenus et insérer des ressources issues de la gestion des ressources numériques en tant que pièces jointes.

   >[!NOTE]
   >
   >L’icône d’accès à la bibliothèque n’est disponible que si l’accès à la bibliothèque a été activé lors de la création de la communication interactive (dans les propriétés du conteneur de documents du canal d’impression).

1. Si l’ordre des pièces jointes n’a pas été verrouillé lors de la création de la communication interactive, vous pouvez réorganiser les pièces jointes en sélectionnant une pièce jointe et en appuyant sur les flèches haut et bas.
1. Utilisez Aperçu web et Aperçu avant impression pour voir si les deux sorties sont conformes à vos besoins.

   Si vous trouvez les aperçus satisfaisants, appuyez sur **[!UICONTROL Envoyer]** pour soumettre/envoyer la communication interactive en post-traitement. Sinon, quittez l’aperçu pour revenir aux modifications.

## Formatage du texte {#formattingtext}

Lors de l’édition d’un fragment de texte dans l’interface utilisateur de l’agent, la barre d’outils change en fonction du type d’édition que vous choisissez d’effectuer (Police, Paragraphe ou Liste) :

![typeofformattingtoolbar](assets/typeofformattingtoolbar.png) ![Barre d’outils des polices](do-not-localize/fonttoolbar.png)

Barre d’outils de la police

![Barre d’outils Paragraphe](do-not-localize/paragraphtoolbar.png)

Barre d’outils Paragraphe

![Barre d’outils de la liste](do-not-localize/listtoolbar.png)

Barre d’outils de la liste

### Mettre des parties de texte en surbrillance/en évidence {#highlightemphasize}

Pour mettre des parties de texte en surbrillance\en évidence dans un fragment modifiable, sélectionnez le texte et appuyez sur Couleur de surbrillance.

![surlignttextagentui](assets/highlighttextagentui.png)

### Coller le texte formaté {#pasteformattedtext}

![pastedtext](assets/pastedtext.png)

### Insérer des caractères spéciaux dans le texte {#specialcharacters}

L’interface utilisateur de l’agent offre une prise en charge intégrée de 210 caractères spéciaux. L’administrateur peut [ajouter la prise en charge de plus de caractères/de caractères spéciaux grâce à la personnalisation](/help/forms/using/custom-special-characters.md).

#### Livraison des pièces jointes {#attachmentdelivery}

* Si la communication interactive est générée à l’aide des API côté serveur sous la forme d’un PDF, interactif ou non, alors le PDF généré contient des pièces jointes au format PDF.
* Si un post-traitement associé à une communication interactive est chargé dans le cadre des opérations d’envoi à l’aide de l’interface utilisateur de l’agent, les pièces jointes sont transmises en tant que paramètre List&lt;com.adobe.idp.Document> inAttachmentDocs.
* Les processus du mécanisme de livraison, tels que l’envoi par courrier électronique et l’impression, livrent les pièces jointes avec la version PDF de la communication interactive.

## Actions et informations disponibles dans l’interface utilisateur de l’agent {#actionsagentui}

### Fragments de document {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **Flèches haut/bas** : flèches permettant de déplacer les fragments de document vers le haut ou vers le bas dans la communication interactive.
* **Supprimer** : si cela est autorisé, supprimez le fragment de document de la communication interactive.
* **Saut de page avant** (applicable aux modules enfant de la zone cible) : insère un saut de page avant le fragment de document.
* **Retrait** : augmente ou réduit le retrait d’un fragment de document.
* **Saut de page après** (applicable aux modules enfant de la zone cible) : insère un saut de page après le fragment de document.

![docfragoptions](assets/docfragoptions.png)

* Modification (fragments de texte uniquement) : ouvrez l’éditeur de texte enrichi pour modifier le fragment de document texte. Pour plus d’informations, voir [Formatage de texte](#formattingtext).

* Sélection (icône représentant un œil) : inclut\exclut le fragment de document de la communication interactive.
* Valeurs vides (information) : indique le nombre de variables vides dans le fragment de document.

### Fragments de document de la liste {#list-document-fragments}

![listoptions](assets/listoptions.png)

* Insertion d’une ligne vide : permet d’insérer une nouvelle ligne vide.
* Sélection (icône représentant un œil) : inclut\exclut le fragment de document de la communication interactive.
* Ignorer les puces/numérotations : permet d’ignorer les puces/numéros dans le fragment de document de la liste.
* Valeurs vides (information) : indique le nombre de variables vides dans le fragment de document.
