---
title: Utilisation des révisions et du résumé des révisions (affichage)
seo-title: Utilisation des révisions et du résumé des révisions (affichage)
description: Ajout des composants Résumé des révisions et révisions à une page
seo-description: Ajout des composants Résumé des révisions et révisions à une page
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
exl-id: 5aae7744-73cc-472b-a4e6-ecd88284b70c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 51%

---

# Utilisation des révisions et du résumé des révisions (affichage) {#using-reviews-and-reviews-summary-display}

Le composant `Reviews`est un composite des composants [ `Comments`](comments.md) et [ `Rating`](rating.md) prêts à l’emploi.

Le composant `Reviews Summary (Display)` fournit un résumé d’une instance principale ou fermée d’un composant `Reviews` à afficher ailleurs sur le site.

>[!NOTE]
>
>La publication anonyme d’une révision n’est pas possible. Les visiteurs du site doivent s’inscrire (devenir membres) et se connecter pour participer. Les visiteurs connectés peuvent mettre à jour leurs révisions à tout moment.

## Ajout d’une révision à une page {#adding-a-review-to-a-page}

Pour ajouter un composant `Reviews` à une page en mode création, utilisez l’explorateur de composants pour localiser `Communities / Reviews` et faites-le glisser sur la page, par exemple à un emplacement relatif à la fonction à réviser pour les utilisateurs.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Lorsque les [bibliothèques côté client requises](reviews-basics.md#essentials-for-client-side) sont incluses, voici comment le composant `Reviews`apparaîtra.

![chlimage_1-340](assets/chlimage_1-340.png)

## Configuration des révisions {#configuring-reviews}

Sélectionnez le composant `Reviews` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-341](assets/chlimage_1-341.png)

Sous l’onglet **[!UICONTROL Évaluations autorisées]** , indiquez la liste complète des évaluations à présenter aux membres. La première note doit être une note globale/générale, car c’est la note qui fournit la note moyenne pour le composant `Review Summary (Display)`. Les deux évaluations suivantes dans la configuration par défaut doivent recevoir un titre différent, autre que &quot;Sous-évaluation 1&quot; ou &quot;Sous-évaluation 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Evaluations autorisées]**

   Liste d’évaluations à partir desquelles un membre peut choisir.

   Utilisez les flèches Haut et Bas, ainsi que les boutons de suppression, pour modifier les choix visibles.

   Cliquez sur **[!UICONTROL Ajouter un élément]** pour ajouter un autre choix d’évaluation.

Sous l’onglet **[!UICONTROL Évaluations requises]**, saisissez à nouveau les éléments de la liste **[!UICONTROL Évaluations autorisées]** qui doivent être évalués. Si un élément est spécifié uniquement dans l’onglet Évaluations autorisées, il peut être laissé non signalé lorsqu’il est soumis par le membre.

Sur le site web, les évaluations requises sont signalées d’un astérisque. Si un élément obligatoire n’est pas marqué, un message s’affiche à l’intention du membre, et sa soumission est refusée jusqu’à ce que toutes les évaluations requises soient marquées.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Evaluations requises]**

   Un sous-ensemble d’évaluations autorisées, indiquant les évaluations requises.

   Utilisez les flèches Haut et Bas, ainsi que les boutons de suppression, pour modifier les choix visibles.

   Cliquez sur **[!UICONTROL Ajouter un élément]** pour ajouter un autre choix de réponse.

>[!NOTE]
>
>Si un élément est saisi dans l’onglet **[!UICONTROL Évaluations requises]** qui n’est pas spécifié dans l’onglet **[!UICONTROL Évaluations autorisées]**, il n’est pas inclus dans les éléments à évaluer.

Sous l’onglet **[!UICONTROL Révisions]** , indiquez comment les révisions sont traitées.

![chlimage_1-344](assets/chlimage_1-344.png)

* **[!UICONTROL Autoriser les réponses]** Si cette option est cochée, les réponses aux révisions sont autorisées. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** Si cette option est cochée, la révision est fermée et n’accepte aucune nouvelle révision ou réponse. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les transferts de fichiers]** Si cette option est cochée, des fichiers peuvent être chargés avec une révision. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]** Paramètre à définir uniquement si l’option **[!UICONTROL Autoriser les chargements de fichiers]** est activée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est de 10 Mo.

* **[!UICONTROL Longueur de message max.]** Nombre maximal de caractères qui peuvent être saisis dans la zone de texte. La valeur par défaut est de 4 096 caractères.

* **[!UICONTROL Types de fichier autorisés]** Paramètre à définir uniquement si l’option **[!UICONTROL Autoriser les transferts de fichiers]** est activée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est cochée, les publications peuvent être saisies avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si cette option est cochée, la fonction de vote est ajoutée à un sujet. Cette option n’est pas cochée par défaut.

Sous l’onglet **[!UICONTROL Modération d’utilisateur]** , indiquez comment les révisions publiées sont gérées. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Prémodération]** Si cette option est cochée, les révisions doivent être approuvées pour être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Supprimer les révisions]** Si cette option est cochée, le membre qui a publié la révision a la possibilité de la supprimer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Refuser les révisions]** Si cette option est cochée, les modérateurs ont le droit de refuser des révisions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les révisions]** Si cette option est cochée, les modérateurs sont autorisés à fermer et à rouvrir les révisions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les révisions]** Si cette option est cochée, les membres ont le droit de marquer des révisions comme étant inappropriées. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué une révision comme étant inappropriée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué une révision comme étant inappropriée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’une révision doit être marquée par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est une fois (1).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’une révision doit être marquée avant qu’elle ne soit plus visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au **[!UICONTROL seuil de modération]**. La valeur par défaut est 5.

### Ajout d’un résumé des révisions (affichage) à une page {#adding-a-review-summary-display-to-a-page}

Pour ajouter un composant `Reviews Summary (Display)` à une page en mode création, localisez le composant .

* `Communities / Reviews Summary (Display)`

et faites glisser le composant sur la page à l’endroit où le résumé d’une révision active ou fermée doit s’afficher.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Lorsque les [bibliothèques côté client requises](reviews-basics.md#essentials-for-client-side) sont incluses, voici comment le composant `Reviews Summary (Display)`apparaîtra.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>La « moyenne » reflète les votes pour le premier élément visible dans l’onglet Évaluations autorisées de la révision qui fait l’objet d’un résumé.

### Configuration du résumé des révisions (affichage) {#configuring-reviews-summary-display}

Sélectionnez le composant `Reviews Summary (Display)` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-347](assets/chlimage_1-347.png)

Sous l’onglet **[!UICONTROL Résumé des critiques]**

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   saisissez ou accédez à l’instance placée du composant `reviews`pour résumer, par exemple, s’il est ajouté à la page web du site [Geometrixx Engage,](getting-started.md) le chemin serait :

   /content/sites/engage/en/page/jcr:content/content/Principal/review

* `Include histogram`

   Si cette case est cochée, incluez l’affichage d’un graphique à barres indiquant le nombre de chaque évaluation des étoiles dans les révisions résumées. Cette option n’est pas cochée par défaut.

### Passage à un type de commentaire personnalisé {#changing-to-a-custom-review-type}

Le composant Révisions utilise le système de commentaires.

En modifiant le type de ressource de commentaire, le système de commentaires ne génère plus une instance d’un commentaire avec les paramètres par défaut, mais plutôt un commentaire personnalisé (étendu) par les développeurs.

Une fois les types de ressources personnalisés connus, saisissez [Mode de conception](../../help/sites-authoring/default-components-designmode.md) et double-cliquez sur le composant `Comments` inséré pour ouvrir une boîte de dialogue avec un onglet supplémentaire.

Sous l’onglet **[!UICONTROL Types de ressource]** , spécifiez le type de ressource personnalisé pour les nouvelles instances des composants `Comments or Voting`:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Type de ressource de commentaire]**

   Accédez au resourceType d’un composant `comment`étendu (commentaire unique) dans /apps. Par exemple, `/apps/social/commons/components/hbs/comments/comment`

   Cette ressource identifie le type de ressource du contenu créé par un visiteur lorsqu’il publie un commentaire.

* **[!UICONTROL Type de ressource de vote]**

   Accédez au resourceType d’un composant `voting`étendu dans /apps. Par exemple, `/apps/social/components/hbs/voting`

   Cette ressource identifie le type de ressource du contenu créé par un visiteur lorsqu’il publie un vote.

* **[!UICONTROL Type de ressource système de commentaires]**

   Accédez au resourceType d’un composant `comments`étendu (système de commentaires) dans /apps. Laissez vide, sauf si le modèle de page [inclut dynamiquement](scf.md#add-or-include-a-communities-component) le système de commentaires dans le script sous-jacent au lieu d’être ajouté à la page en tant que ressource (noeud de commentaires). Pour en savoir plus, consultez la section [{{include} Helper](handlebars-helpers.md#include)

## Expérience des visiteurs {#site-visitor-experience}

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’activités de modération autorisées par la configuration du composant, peu importe qui a créé la révision.

### Membres {#members}

Lorsque le visiteur est connecté, selon la configuration, il peut :

* Publier une nouvelle révision
* Modifier sa propre révision
* Supprimer sa propre révision
* Marquer les commentaires de révision des autres

Une seule évaluation est autorisée par membre.  Le membre peut modifier son évaluation à tout moment.

### Anonyme {#anonymous}

Les visiteurs non connectés peuvent lire les révisions publiées et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter une évaluation ou une révision, ni à marquer celles d’autres membres.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur la révision](reviews-basics.md) pour les développeurs.

Pour plus d’informations sur la modération des commentaires publiés, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Pour des informations sur la traduction des commentaires publiés, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
