---
title: Création d’un formulaire adaptatif
seo-title: Creating an adaptive form
description: Comment créer un formulaire adaptatif à l’aide d’AEM Forms. Les formulaires adaptatifs sont des formulaires HTML5 réactifs qui rationalisent la collecte et le traitement des informations.
seo-description: How to create an adaptive form using AEM Forms. Adaptive forms are responsive HTML5 forms that streamline information gathering and processing.
uuid: 444f461a-9e88-4385-b5ee-e985067ab7bc
content-type: reference
topic-tags: author
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f06b8cb2-6f98-465f-beec-1e91e3f45707
feature: Adaptive Forms
exl-id: 4b6d3533-cd1f-4944-b580-49fd90fcf87a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2053'
ht-degree: 40%

---

# Création d’un formulaire adaptatif {#creating-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## <strong>Création d’un formulaire adaptatif</strong> {#strong-create-an-adaptive-form-strong}

Pour créer un formulaire adaptatif, procédez comme suit.

1. Accédez à l’instance d’auteur AEM Forms à l’adresse `https://[server]:[port]/<custom-context-if-any>.`

   ```
   
   ```

1. Saisissez vos informations d’identification sur la page de connexion AEM.

   Une fois connecté, dans le coin supérieur gauche, appuyez sur **[!UICONTROL Adobe Experience Manager > Forms > Forms &amp; Documents]**.

   >[!NOTE]
   >
   >Dans le cadre d’une installation par défaut, l’identifiant est `admin` et le mot de passe est `admin`.

1. Appuyez sur **[!UICONTROL Créer]** et sélectionner **[!UICONTROL Formulaire adaptatif]**.
1. Une option permettant de sélectionner un modèle s’affiche. Pour plus d’informations sur les modèles, voir [Modèles de formulaires adaptatifs](/help/forms/using/creating-adaptive-form.md#p-adaptive-form-templates-p). Appuyez sur un modèle pour le sélectionner, puis appuyez sur Suivant.
1. Une option Ajouter des propriétés s’affiche. Spécifiez les valeurs des champs de propriété suivants. Les champs Titre et Nom sont obligatoires :

   * **[!UICONTROL Titre :]** Indique le nom d’affichage du formulaire. Le titre vous permet d’identifier le formulaire dans l’interface utilisateur d’AEM Forms.
   * **[!UICONTROL Nom :]** indique le nom du formulaire. Un noeud portant le nom spécifié est créé dans le référentiel. Lorsque vous commencez à saisir un titre, la valeur du champ de nom est automatiquement générée. Vous pouvez modifier la valeur suggérée. Le champ Nom ne peut contenir que des caractères alphanumériques, des tirets et des traits de soulignement. Toutes les entrées non valides sont remplacées par un trait d’union.
   * **[!UICONTROL Description :]** indique des informations détaillées relatives au formulaire.
   * **[!UICONTROL Balises :]** indique les balises pour individualiser le formulaire adaptatif. Les balises aident à rechercher le formulaire. Pour créer des balises, saisissez les nouveaux noms de balise dans la boîte de dialogue **Balises.**

1. Vous pouvez créer un formulaire adaptatif basé sur l’un des modèles de formulaire suivants :

   * [Modèle de données de formulaire](#fdm)
   * [Modèle de formulaire XFA](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)
   * [Schéma XML ou JSON](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)
   * Aucun ou sans modèle de formulaire

   Vous pouvez les configurer à partir du **[!UICONTROL Modèle de formulaire]** sur l’onglet **[!UICONTROL Ajouter des propriétés]** page. Par défaut, le modèle de formulaire sélectionné est **[!UICONTROL Aucun]**.

1. Appuyez sur **Créer**. Un formulaire adaptatif est créé et une boîte de dialogue pour ouvrir le formulaire à modifier s’affiche.

   Une fois que vous avez fini de spécifier toutes les propriétés, cliquez sur **[!UICONTROL Créer]**. Un formulaire adaptatif est créé et une boîte de dialogue pour ouvrir le formulaire à modifier s’affiche.

   Une fois que vous avez fini de spécifier toutes les propriétés, cliquez sur **[!UICONTROL Créer]**. Un formulaire adaptatif est créé et une boîte de dialogue pour ouvrir le formulaire à modifier s’affiche.

1. Appuyez sur **[!UICONTROL Ouvrir]** pour ouvrir le formulaire nouvellement créé dans un nouvel onglet. Le formulaire s’ouvre pour modification et affiche le contenu disponible dans le modèle. Il affiche également la barre latérale permettant de personnaliser le formulaire nouvellement créé selon vos besoins.

   Selon le type de formulaire adaptatif, les éléments de formulaire présents dans le modèle de formulaire XFA, le schéma XML ou le schéma JSON associé sont affichés dans la variable **[!UICONTROL Objets de modèle de données]** de l’onglet **[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

   Pour plus d’informations sur l’interface de création de formulaires adaptatifs et les composants disponibles, voir [Présentation de la création de formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md).

   >[!NOTE]
   >
   >Autorisez les fenêtres contextuelles dans votre navigateur pour ouvrir le formulaire nouvellement créé dans un nouvel onglet.

## Créer un formulaire adaptatif basé sur un modèle de données de formulaire {#fdm}

[Intégration des données AEM Forms](/help/forms/using/data-integration.md) vous permet d’intégrer plusieurs sources de données et de rassembler leurs entités et services pour créer un modèle de données de formulaire. Il s’agit d’une extension du schéma JSON. Vous pouvez utiliser un modèle de données de formulaire pour créer un formulaire adaptatif. Les entités ou les objets de modèle de données configurés dans un modèle de données de formulaire sont disponibles en tant qu’objets de modèle de données pour la création de formulaire. Ils sont associés à des sources de données respectives et utilisés pour pré-remplir un formulaire et écrire les données envoyées dans les sources de données respectives. Vous pouvez également appeler les services configurés dans un modèle de données de formulaire à l’aide de règles de formulaire adaptatif.

Pour utiliser un modèle de données de formulaire pour créer un formulaire adaptatif :

1. Dans l’onglet Modèle de formulaire de l’écran Ajouter des propriétés, sélectionnez **[!UICONTROL Modèle de données de formulaire]** dans la liste déroulante **[!UICONTROL Sélectionner à partir de]**.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Appuyez pour développer le **[!UICONTROL modèle de données de formulaire sélectionné]**. Tous les modèles de données de formulaire disponibles sont répertoriés.

   Sélectionnez un modèle de données à partir de .

   ![create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>Vous pouvez également remplacer le modèle de données de formulaire par un formulaire adaptatif. Pour obtenir des instructions détaillées, consultez la page [Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif](#edit-form-model).

## Créer un formulaire adaptatif basé sur un modèle de formulaire XFA {#create-an-adaptive-form-based-on-an-xfa-form-template}

Vous pouvez réutiliser vos modèles de formulaire XFA pour créer des formulaires adaptatifs. Pour le réutiliser, téléchargez et associez un modèle de formulaire XFA à un formulaire adaptatif. Les éléments du modèle de formulaire (formulaire XFA) sont disponibles dans l’outil de recherche de contenu au moment de la création de formulaires adaptatifs. Dans l’outil de recherche de contenu, vous pouvez faire glisser les éléments de modèle de formulaire sur le formulaire.

>[!NOTE]
>
>[Téléchargement du modèle de formulaire XFA](/help/forms/using/get-xdp-pdf-documents-aem.md) à AEM Forms avant de commencer la création d’un formulaire adaptatif basé sur le modèle de formulaire.

Procédez comme suit pour utiliser un modèle de formulaire XFA comme modèle de formulaire pour votre formulaire adaptatif :

1. Sur le **[!UICONTROL Ajouter des propriétés]** , ouvrez la page **[!UICONTROL Modèle de formulaire]** .
1. Dans l’onglet Form Model (Modèle de formulaire), dans la liste déroulante, sélectionnez **[!UICONTROL Modèles de formulaire]**. Tous les modèles de formulaire qui sont téléchargés vers le référentiel via l’interface utilisateur d’AEM Forms sont répertoriés pour sélection. Sélectionnez un modèle dans la liste.

   ![Association d’un modèle de formulaire XFA à un formulaire adaptatif](assets/form_model_xfa_associate.png)
   **Figure :** *Sélection d’un modèle de formulaire*

   >[!NOTE]
   >
   >Vous pouvez également modifier le modèle de formulaire pour un formulaire adaptatif. Pour obtenir des instructions détaillées, consultez la page [Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif](#edit-form-model).

## Créer un formulaire adaptatif en fonction du schéma XML ou JSON {#create-an-adaptive-form-based-on-xml-or-json-schema}

Les schémas XML et JSON représentent la structure dans laquelle les données sont générées ou utilisées par le système principal de votre organisation. Vous pouvez associer un schéma à un formulaire adaptatif et utiliser ses éléments pour ajouter du contenu dynamique à un formulaire adaptatif. Les éléments du schéma sont disponibles dans l’onglet Objet du modèle de données du navigateur de contenu pour la création de formulaires adaptatifs. Vous pouvez faire glisser et déposer les éléments du schéma pour créer le formulaire.

Consultez les documents suivants pour savoir comment concevoir un schéma XML ou JSON pour créer des formulaires adaptatifs.

* [Création de formulaires adaptatifs à l’aide d’un schéma XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Création de formulaires adaptatifs à l’aide d’un schéma JSON](/help/forms/using/adaptive-form-json-schema-form-model.md)

Procédez comme suit pour utiliser un schéma XML ou JSON comme modèle de formulaire pour un formulaire adaptatif :

1. À l’étape **[!UICONTROL Ajouter des propriétés]** de la page de création de formulaires adaptatifs, appuyez sur l’onglet **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet Modèle de formulaire, sélectionnez **[!UICONTROL Schéma]** dans le champ déroulant **[!UICONTROL Choisir parmi]**.

1. Appuyez sur **[!UICONTROL Sélectionner le schéma]** et effectuez l’une des opérations suivantes :

   * **[!UICONTROL Télécharger à partir du disque]** : sélectionnez cette option et appuyez sur Charger une définition de schéma pour parcourir et charger un schéma XML ou un schéma JSON à partir de votre système de fichiers. Le fichier de schéma téléchargé réside avec le formulaire et n’est pas accessible aux autres formulaires adaptatifs.
   * **[!UICONTROL Recherche dans le référentiel]** - Sélectionnez cette option pour effectuer une sélection dans la liste des fichiers de définition de schéma disponibles dans le référentiel. Sélectionnez le fichier de schéma XML ou JSON comme modèle de formulaire. Le schéma sélectionné sera associé au formulaire par référence et sera accessible dans d’autres formulaires adaptatifs.

   >[!CAUTION]
   >
   >Assurez-vous que le nom de fichier du schéma JSON se termine par **.schema.json**. Par exemple : mySchema.schema.json

   ![Sélection du schéma XML ou JSON](assets/upload-schema.png)
   **Figure :** *Sélection d’un schéma XML ou JSON*

1. (Pour le schéma XML uniquement) Après avoir sélectionné ou chargé un schéma XML, spécifiez un élément racine du fichier XSD sélectionné à mapper avec le formulaire adaptatif.

   ![Sélection de l’élément racine de schéma XSD](assets/xsd-root-element.png)
   **Figure :** *Sélection de l’élément racine XSD*

>[!NOTE]
>
>Vous pouvez également remplacer le schéma par un formulaire adaptatif. Pour obtenir des instructions détaillées, consultez la page [Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif](#edit-form-model).

## Modèles de formulaires adaptatifs {#adaptive-form-templates}

Un modèle fournit une structure de base et définit l’aspect (mises en page et styles) d’un formulaire adaptatif. Il comporte des composants pré-formatés contenant certaines propriétés et une certaine structure de contenu. AEM Forms fournit des modèles de formulaire adaptatif prêts à l’emploi. Pour obtenir le package de modèles complet, y compris les modèles avancés, vous devez installer le package de module complémentaire AEM Forms. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).

En outre, vous pouvez utiliser l’éditeur de modèles pour créer vos propres modèles. Pour plus d’informations sur l’utilisation des modèles, voir [Modèles de formulaires adaptatifs](/help/forms/using/template-editor.md).

>[!NOTE]
>
>Lorsque vous ouvrez un formulaire adaptatif créé à l’aide du modèle avancé pour le modifier, un message d’erreur s’affiche. Le modèle avancé comporte un composant Étape de signature et Acrobat Sign est activé par défaut pour celui-ci. Créez et sélectionnez un [Configuration cloud Acrobat Sign](/help/forms/using/adobe-sign-integration-adaptive-forms.md) et [configuration d’un signataire](/help/forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) pour résoudre l’erreur.

## Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif {#edit-form-model}

Les formulaires adaptatifs sont créés sans modèle de formulaire (à l’aide de l’option Aucun pour le modèle de formulaire) ou à l’aide d’un modèle de formulaire, d’un schéma XML ou JSON ou d’un modèle de données de formulaire. Vous pouvez remplacer le modèle de formulaire d’un formulaire adaptatif Aucun par un autre. Pour un formulaire adaptatif basé sur un modèle de formulaire, vous pouvez choisir un autre modèle de formulaire, un schéma XML, un schéma JSON ou un modèle de données de formulaire pour le même modèle de formulaire. Cependant, vous ne pouvez pas passer d’un modèle de formulaire à un autre.

1. Sélectionnez le document adaptatif et appuyez sur l’icône **Propriétés**.
1. Ouvrez l’onglet **[!UICONTROL Modèle de formulaire]** et effectuez l’une des actions suivantes.

   * Si le formulaire adaptatif est dépourvu de modèle de formulaire, vous pouvez choisir un autre modèle de formulaire et sélectionner en conséquence un modèle de formulaire, un schéma XML ou JSON ou un modèle de données de formulaire.
   * Si le formulaire adaptatif est basé sur un modèle de formulaire, vous pouvez choisir un autre modèle de formulaire, un schéma XML ou JSON, ou un modèle de données de formulaire pour le même modèle de formulaire.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les propriétés.

## Enregistrement automatique d’un formulaire adaptatif {#auto-save-an-adaptive-form}

Par défaut, le contenu d’un formulaire adaptatif est enregistré sur une action de l’utilisateur, comme lorsque vous appuyez sur le bouton d’enregistrement. Vous pouvez également configurer un formulaire adaptatif pour commencer automatiquement à enregistrer le contenu en fonction d’un événement ou d’un intervalle de temps. L’option d’enregistrement automatique est utile dans les cas suivants :

* Enregistrement automatique du contenu pour les utilisateurs anonymes et connectés
* Enregistrement du contenu d’un formulaire sans intervention ou sans intervention minimale de l’utilisateur
* Commencer à enregistrer le contenu d’un formulaire en fonction d’un événement utilisateur
* Enregistrement répété du contenu d’un formulaire après un intervalle de temps spécifié

### Activation de l’enregistrement automatique d’un formulaire adaptatif {#enable-auto-save-for-an-adaptive-form}

Par défaut, l’option d’enregistrement automatique n’est pas activée. Vous pouvez activer l’option d’enregistrement automatique à partir de l’onglet Enregistrement automatique d’un formulaire adaptatif. L’onglet Enregistrement automatique fournit également plusieurs autres options de configuration. Effectuez les étapes suivantes afin d’activer et de configurer l’option d’enregistrement automatique pour un formulaire adaptatif :

1. Pour accéder à la section d’enregistrement automatique dans les propriétés, sélectionnez un composant, puis cliquez sur ![field-level](assets/field-level.png) > **[!UICONTROL Conteneur de formulaires adaptatifs]**, puis cliquez sur ![cmppr](assets/cmppr.png).
1. Dans le **[!UICONTROL Enregistrement automatique]** , **[!UICONTROL Activer]** l’option d’enregistrement automatique.
1. Dans le **[!UICONTROL Événement de formulaire adaptatif]** , spécifiez 1 ou TRUE pour lancer automatiquement l’enregistrement du formulaire lorsque celui-ci est chargé dans le navigateur. Vous pouvez également spécifier une expression conditionnelle pour un événement qui, lorsqu’il est déclenché et renvoie true (vrai), commence à enregistrer le contenu du formulaire.
1. Spécifiez le déclencheur. L’enregistrement automatique est déclenché en fonction de votre configuration. Vous avez le choix entre :

   * **[!UICONTROL Basé sur l’heure :]** sélectionnez l’option pour commencer à enregistrer le contenu selon un intervalle de temps spécifié.
   * **[!UICONTROL Basé sur les événements :]** sélectionnez l’option pour commencer à enregistrer le contenu sur la base d’un événement déclenché.

   Lorsque vous sélectionnez un déclencheur, la zone Configuration de la stratégie est activée. La zone Configuration de la stratégie vous permet d’effectuer les opérations suivantes :

   * Spécifiez un intervalle de temps si vous sélectionnez un déclencheur **[!UICONTROL basé sur l’heure]**.
   * Spécifiez un nom d’événement si vous sélectionnez un déclencheur **[!UICONTROL basé sur un événement.]**

   Vous pouvez également créer et ajouter votre propre stratégie personnalisée à la liste. Pour plus d’informations, voir [Mise en oeuvre d’une stratégie personnalisée pour enregistrer automatiquement les formulaires](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Enregistrement automatique basé sur le temps uniquement) Effectuez les étapes suivantes pour configurer les options de l’enregistrement automatique basé sur le temps.

   1. Dans le **[!UICONTROL Enregistrement automatique sur cet intervalle]** , spécifiez l’intervalle en secondes. Le formulaire est enregistré à plusieurs reprises après l’expiration du nombre de secondes spécifié dans la zone d’intervalle.

1. (Enregistrement automatique basé sur un événement uniquement) Effectuez les étapes suivantes pour configurer les options d’enregistrement automatique basé sur un événement.

   1. Dans la zone **Enregistrement automatique après cet événement**, spécifiez un événement [GuideBridge](https://helpx.adobe.com/fr/aem-forms/6/javascript-api/GuideBridge.html). Le formulaire est enregistré chaque fois que l’expression renvoie TRUE.

1. (Facultatif) Pour enregistrer automatiquement le contenu pour des utilisateurs anonymes, sélectionnez l’option **Activer l’enregistrement automatique pour les utilisateurs anonymes**, puis cliquez sur **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Pour que l’option d’enregistrement automatique fonctionne pour les utilisateurs anonymes, assurez-vous de configurer le service de configuration commun aux formulaires pour autoriser tous les utilisateurs à prévisualiser, vérifier et signer des formulaires.
   >
   >Pour configurer le service, accédez à la configuration d’AEM Web Console à l’adresse `https://[server]:[host]/system/console/configMgr`, puis modifiez le **[!UICONTROL Service de configuration commun Forms]** afin de choisir l’option **[!UICONTROL Tous les utilisateurs]** dans le champ **[!UICONTROL Autoriser]** et enregistrez la configuration.
