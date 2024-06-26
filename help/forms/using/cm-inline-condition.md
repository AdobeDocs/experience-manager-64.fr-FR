---
title: Condition intégrée et répétition dans les communications interactives et les lettres
seo-title: Inline condition and repeat in Interactive Communications and letters
description: En utilisant la condition intégrée et la répétition dans les communications interactives et les lettres, vous pouvez créer des communications hautement contextuelles et bien structurées.
seo-description: Using inline condition and repeat in Interactive Communications and letters, you can create communications that are highly contextual and well structured.
uuid: 16e38929-f81b-4582-9daf-6c756a4390e9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: interactive-communications, correspondence-management
discoiquuid: f376b8c1-e176-4fe6-b298-f3d493c59319
feature: Correspondence Management
exl-id: 1b669f86-5090-4618-9bd2-85fcec44d51a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 32%

---

# Condition intégrée et répétition dans les communications interactives et les lettres {#inline-condition-and-repeat-in-interactive-communications-and-letters}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

En utilisant la condition intégrée et la répétition dans les communications interactives et les lettres, vous pouvez créer des communications hautement contextuelles et bien structurées.

## Conditions intégrées {#inline-conditions}

AEM Forms vous permet d’utiliser des conditions intégrées dans des modules de texte afin d’automatiser le rendu du texte qui dépend du contexte ou des données associées au modèle de données de formulaire (dans la communication interactive) ou au dictionnaire de données (en lettres). La condition intégrée affiche du contenu spécifique en fonction de l’évaluation de condition vraie ou fausse.

Les conditions effectuent des calculs sur les valeurs de données fournies par le modèle de données de formulaire/le dictionnaire de données ou par les utilisateurs finaux. Grâce aux conditions intégrées, vous pouvez gagner du temps et réduire les erreurs humaines, tout en créant des communications/lettres interactives hautement contextuelles et personnalisées.

Pour en savoir plus, voir:

* [Créer une communication interactive](/help/forms/using/create-interactive-communication.md)
* [Présentation de Correspondence Management](/help/forms/using/cm-overview.md)
* [Texte dans les communications interactives](/help/forms/using/texts-interactive-communications.md)

### Exemple : Utilisation de règles pour conditionner le texte intégré dans la communication interactive {#example-using-rules-to-conditionalize-inline-text-in-interactive-communication}

Pour conditionner une phrase, un paragraphe ou une chaîne de texte dans une communication interactive, vous pouvez créer une règle dans le fragment de document texte approprié. L’exemple suivant utilise une règle pour afficher un numéro gratuit uniquement pour les destinataires américains de la communication interactive.

Pour plus dʼinformations, consultez la section Créer une règle dans le texte dans les [Textes dans les communications interactives](/help/forms/using/texts-interactive-communications.md).

Une fois que vous avez inclus le fragment de texte dans une communication interactive et que l’agent utilise l’interface utilisateur pour préparer une communication interactive, les données (modèle de données de formulaire) des destinataires sont évaluées et le texte n’est affiché qu’aux destinataires aux États-Unis.

### Exemple : Utilisation d’une condition intégrée dans une lettre pour effectuer le rendu de l’adresse appropriée  {#example-using-inline-condition-in-a-letter-to-render-the-appropriate-address}

Vous pouvez insérer une condition intégrée dans une lettre en insérant la condition intégrée dans le module de texte approprié. L&#39;exemple suivant utilise deux conditions pour évaluer et afficher l&#39;adresse appropriée, Monsieur ou Madame, dans une lettre basée sur le genre de l&#39;élément DD. En utilisant des étapes similaires, vous pouvez créer d’autres conditions.

>[!NOTE]
>
>Si vos actifs existants incluent les anciennes expressions de condition/répétition (antérieures à 6.2 SP1 CFP 4), les actifs affichent l’ancienne syntaxe de condition et de répétition. Toutefois, l’ancienne condition/répétition fonctionne. Les nouvelles et anciennes expressions de condition/répétition sont compatibles entre elles pour créer un mélange d’expressions de condition/répétition anciennes et nouvelles.

1. Dans le module de texte approprié, sélectionnez la partie de texte à laquelle vous voulez appliquer des conditions et appuyez sur **Condition**.

   ![1_selecttext](assets/1_selecttext.png)

   La boîte de dialogue Condition s’affiche avec une condition vide.

   ![2_condition_dialog](assets/2_conditiondialog.png)

   >[!NOTE]
   >
   >Une expression conditionnelle vide ou non valide ne peut pas être enregistrée. Il doit y avoir une expression conditionnelle valide à l’intérieur de `${}` pour enregistrer l’expression.

1. Procédez comme suit pour créer une condition permettant d’évaluer si le texte sélectionné/conditionnel apparaît dans la lettre, puis appuyez sur la coche pour enregistrer l’expression :

   Appuyez deux fois sur un élément DD pour l’insérer dans la condition. Insérez l’opérateur approprié et créez la condition suivante dans la boîte de dialogue.

   ```java
   ${DD_creditcard_Gender=="Male"}
   ```

   Pour plus d’informations sur la création d’une expression, voir **Création d’expressions et de fonctions distantes à l’aide du générateur d’expression** in [Générateur d’expression](/help/forms/using/expression-builder.md). La valeur spécifiée dans l’expression doit être prise en charge pour l’élément du dictionnaire de données. Pour de plus amples informations, voir [Dictionnaires de données](/help/forms/using/data-dictionary.md).

   Une fois la condition insérée, vous pouvez placer le pointeur de la souris sur la poignée gauche de la condition pour afficher la condition. Vous pouvez appuyer sur la poignée pour afficher le menu contextuel de la condition, qui vous permet de modifier ou de supprimer la condition.

   ![3_hoverhandle](assets/3_hoverhandle.png) ![4_editconditionremoveconditionpopup](assets/4_editconditionremoveconditionpopup.png)

1. Insérez une condition similaire en sélectionnant le texte `Ma'am`.

   ```java
   ${DD_creditcard_Gender == "Female"}
   ```

1. Prévisualisez la lettre appropriée et notez que le texte est rendu en fonction de la condition intégrée. Vous pouvez saisir la valeur de Genre de l’élément DD à l’aide de :

   * Un exemple de fichier de données XML créé à partir du dictionnaire de données approprié lors de la prévisualisation de la lettre avec des exemples de données.
   * Un fichier de données XML joint au dictionnaire de données approprié.

   Pour de plus amples informations, voir [Dictionnaires de données](/help/forms/using/data-dictionary.md).

   ![5_letteroutput](assets/5_letteroutput.png)

## Répéter {#repeat}

Vous pouvez disposer d’informations dynamiques dans votre communication interactive/lettre, telles que les transactions dans un relevé de carte de crédit, dont l’instance ou l’occurrence peut continuer de changer avec chaque lettre générée. La répétition permet de mettre en forme et structurer ces informations dynamiques dans votre fragment de document texte.

De plus, vous pouvez spécifier la condition/règle dans la structure de répétition pour appliquer une condition aux informations/entrées qui sont rendues dans la communication interactive/lettre.

### Exemple : utilisation de la répétition dans une communication interactive pour mettre en forme, structurer et afficher la liste des transactions de carte de crédit {#example-using-repeat-in-an-interactive-communication-to-format-structure-and-display-a-list-of-credit-card-transactions}

L’exemple suivant vous indique les étapes à suivre pour utiliser la répétition pour structurer et effectuer le rendu des transactions de carte de crédit dans une communication interactive.

1. Dans un fragment de document texte basé sur un modèle de données de formulaire, insérez les objets de modèle de données de formulaire appropriés (et le texte incorporé requis pour les libellés, comme dans cet exemple) :

   ![1_elementstext](assets/1_elementstext.png)

   >[!NOTE]
   >
   >Le contenu répétable doit inclure au moins une propriété du type Collection.

1. Sélectionnez le contenu sur lequel appliquer la répétition.

   ![2_selection](assets/2_selection.png)

1. Appuyez sur Répéter.

   La boîte de dialogue Répéter s’affiche.

   ![3_repeatdialog](assets/3_repeatdialog.png)

1. Sélectionnez Saut de ligne comme séparateur et, si nécessaire, appuyez sur Ajouter une condition pour créer une règle. Vous pouvez également utiliser le texte comme séparateur et spécifier les caractères à utiliser comme séparateur.

   La boîte de dialogue Créer une règle s’affiche.

1. Créez une règle pour afficher les transactions postérieures au 28 février 2018 afin d’inclure les transactions du mois de mars uniquement dans la communication interactive.

   >[!NOTE]
   >
   >Cet exemple suppose que l’agent créera l’instruction à la fin du mois de mars 2018. Sinon, vous pouvez créer une autre règle pour inclure les transactions antérieures au 2018-04-01 afin d’exclure les transactions postérieures à mars 2018.

   ![4_createrule](assets/4_createrule.png)

1. Enregistrez la condition/la règle, puis enregistrez la répétition. La répétition conditionnelle est appliquée au contenu sélectionné.

   ![5_onmouseoverconditionrule](assets/5_onmouseoverconditionrule.png)

   Au passage de la souris, le fragment de document texte affiche la condition et le séparateur utilisés dans la répétition appliquée au contenu.

1. Enregistrez le fragment de document texte et prévisualisez la communication interactive appropriée. En fonction des données du modèle de données de formulaire, la répétition appliquée aux éléments rend les détails de la transaction similaires aux éléments suivants dans l’aperçu :

   ![screen_shot_2018-03-09at155516copy](assets/screen_shot_2018-03-09at155516copy.png)

### Exemple : Utiliser la répétition dans une lettre pour formater, structurer et afficher une liste des transactions de carte de crédit {#example-using-repeat-in-a-letter-to-format-structure-and-display-a-list-of-credit-card-transactions}

L’exemple suivant vous indique les étapes à suivre pour utiliser la répétition pour structurer et effectuer le rendu des transactions de carte de crédit dans une lettre. En utilisant des étapes similaires, vous pouvez utiliser la répétition dans un scénario différent.

1. Ouvrez (lors de la modification ou de la création) un module de texte contenant des éléments DD qui effectuent le rendu de données répétées/dynamiques et incorporez le texte requis autour des éléments DD. Par exemple, un module de texte comporte les éléments DD suivants pour créer un relevé des transactions sur une carte de crédit :

   ```
   {^DD_creditcard_TransactionDate^} {^DD_creditcard_TransactionAmount^}
   {^DD_creditcard_TransactionType^} 
   ```

   Ces éléments DD affichent une liste des transactions effectuées sur la carte de crédit avec les informations suivantes :

   Date de transaction, montant de transaction et type de transaction (débit ou crédit)

1. Incorporez le texte dans les éléments DD pour rendre l’instruction plus lisible, par exemple :

   ![1_repeat](assets/1_repeat.png)

   ```
   Date: {^DD_creditcard_TransactionDate^} Amount (USD): {^DD_creditcard_TransactionAmount^} Transaction Type: {^DD_creditcard_TransactionType^} 
   ```

   Toutefois, la tâche de rendu d’une instruction correctement formatée n’est pas encore terminée. Si vous effectuez le rendu d’une lettre en fonction du travail effectué jusqu’à présent, elle s’affiche comme suit :

   ![1_1renderwithoutrepeat](assets/1_1renderwithoutrepeat.png)

   Pour répéter le texte statique avec les éléments DD, vous devez appliquer la répétition comme expliqué dans les étapes suivantes.

1. Sélectionnez le texte statique ainsi que les éléments DD à répéter, comme illustré ci-dessous :

   ![2_repeat_selecttext](assets/2_repeat_selecttext.png)

1. Appuyez sur **Répéter**. La boîte de dialogue Répéter s’affiche avec une condition intégrée vide.

   ![3_repeat_dialog](assets/3_repeat_dialog.png)

1. Si nécessaire, insérez une condition pour effectuer le rendu sélectif des transactions, par exemple pour effectuer le rendu des montants de transaction supérieurs à 50 cents :

   ```
   ${DD_creditcard_TransactionAmount > 0.5}
   ```

   Sinon, si vous n’avez pas besoin d’effectuer un rendu des informations (ici les transactions) de manière sélective, laissez la condition vide en supprimant ce qui suit dans la boîte de dialogue : `${}`. L’enregistrement d’une expression de répétition est activé lorsque la fenêtre d’expression de répétition est vide (sans ${} lorsqu’aucune répétition n’est nécessaire) ou lorsqu’elle contient une condition valide pour la répétition.

1. Sélectionnez un séparateur pour le formatage du texte dynamique et appuyez sur la coche à enregistrer :

   * **Saut de ligne**: Insère un saut de ligne après chaque entrée de transaction dans la lettre de sortie.
   * **Texte**: Insère le caractère de texte spécifié après chaque entrée de transaction dans la lettre de sortie.

   Une fois la condition insérée, le texte avec répétition est mis en surbrillance en rouge et une poignée apparaît sur sa gauche. Vous pouvez placer le pointeur de la souris sur la poignée gauche de la répétition pour afficher la structure de la répétition.

   ![4_repeat_hoverdetail](assets/4_repeat_hoverdetail.png)

   Vous pouvez appuyer sur la poignée pour afficher le menu contextuel de la répétition, qui permet de modifier ou de supprimer la structure de la répétition.

   ![5_repeateditremove](assets/5_repeateditremove.png)

1. Prévisualisez la lettre appropriée et notez que le texte est rendu en fonction de la répétition. Vous pouvez saisir la valeur des éléments DD à l’aide des éléments suivants :

   * Un exemple de fichier de données XML créé à partir du dictionnaire de données approprié lors de la prévisualisation de la lettre avec des exemples de données.
   * Un fichier de données XML joint au dictionnaire de données approprié.

   Pour de plus amples informations, voir [Dictionnaires de données](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=fr).

   ![6_repeatoutputpreview](assets/6_repeatoutputpreview.png)

   Le texte statique se répète avec les détails de la transaction. La répétition du texte statique est facilitée par la répétition appliquée au texte dans cette procédure. La condition ${DD_creditcard_TransactionAmount > 0.5} garantit que les transactions inférieures à 0,5 USD ne sont pas rendues dans la lettre.

   >[!NOTE]
   >
   >Vous pouvez insérer une condition et la répéter uniquement lors de la création ou de la modification du module de texte approprié. Lors de l’aperçu de la lettre, bien que vous puissiez apporter des modifications au module de texte, vous ne pouvez pas insérer de condition ou répéter.

## Utilisation d’une condition intégrée et d’une répétition - certains cas d’utilisation  {#using-inline-condition-and-repeat-some-use-cases}

### Répéter dans la condition {#repeat-within-condition}

Vous devrez peut-être utiliser la répétition dans une condition. Correspondence Management vous permet d’utiliser la répétition dans un concept de condition intégré.

Par exemple, la répétition (mise en forme en rouge) qui suit dans une condition (mise en forme en vert).

Bien que la répétition effectue le rendu des transactions de carte de crédit, la condition ${DD_creditcard_nooftransactions > 0} garantit que la structure de répétition est générée uniquement s’il existe au moins une transaction.

![repeatwitincondition](assets/repeatwitincondition.png)

De même, selon vos besoins, vous pouvez créer :

* Une ou plusieurs conditions dans une condition
* Une ou plusieurs conditions dans une répétition
* Combinaison de conditions et répétition dans une condition ou une répétition

### Condition intégrée vide {#empty-inline-condition}

Vous devrez peut-être insérer des conditions intégrées vides et incorporer du texte et des éléments DD ultérieurement. Correspondence Management vous permet de le faire.

![emptycondition](assets/emptycondition.png)

Il est toutefois recommandé, dans la mesure du possible, d’insérer le texte et les éléments DD en premier dans le module de texte avec la mise en forme prévue, telle que des puces, et d’appliquer une condition intégrée par la suite.
