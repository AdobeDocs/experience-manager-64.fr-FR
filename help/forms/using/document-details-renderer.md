---
title: Détails du document pour le moteur de rendu
seo-title: Document details for renderer
description: Informations conceptuelles sur le fonctionnement des rendus dans l’espace de travail AEM Forms pour le rendu des différents types de formulaires et de fichiers pris en charge.
seo-description: Conceptual information on how renders work in AEM Forms workspace to render the various supported form and file types.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
exl-id: 192ba4c4-a133-4e16-9882-98005f25ba7f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 60%

---

# Détails du document pour le moteur de rendu {#document-details-for-renderer}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Dans l’espace de travail AEM Forms, plusieurs types de formulaires sont pris en charge en toute simplicité. Celles-ci comprennent les éléments suivants :

* PDF forms (XDP/Acroform/PDF plats)
* Nouveaux formulaires de HTML
* Images
* Applications tierces (par exemple, Correspondence Management)

Ce document explique le fonctionnement de ces rendus du point de vue de la personnalisation sémantique/réutilisation des composants, afin que les exigences du client soient satisfaites sans compromettre le rendu. L’espace de travail AEM Forms autorise tous les changements d’interface utilisateur/sémantiques, mais il est recommandé de ne pas modifier la logique de rendu de différents types de formulaires car les résultats peuvent être imprévisibles. Ce document fournit des conseils/des connaissances pour prendre en charge le rendu du même formulaire, en utilisant les mêmes composants de l’espace de travail dans différents portails, et non pour modifier la logique de rendu elle-même.

## PDF forms {#pdf-forms}

Les formulaires PDF sont rendus par `PdfTaskForm View`.

Lorsqu’un formulaire XDP est rendu au format PDF, un `FormBridge` JavaScript™ est ajouté par le service FormsAugmenter. Ce JavaScript™ (dans le formulaire PDF) permet d’effectuer des actions telles que l’envoi d’un formulaire, la sauvegarde d’un formulaire ou la mise hors ligne d’un formulaire.

Dans l’espace de travail AEM Forms, la vue PDFTaskForm communique avec le Javascript `FormBridge` par le biais d’un fichier HTML intermédiaire présent à `/lc/libs/ws/libs/ws/pdf.html`. Le flux est :

**Vue PDFTaskForm - pdf.html**

Communique à l’aide de `window.postMessage` / `window.attachEvent('message')`.

Cette méthode est la méthode standard de communication entre un cadre parent et un iframe. Les écouteurs d’événement existants issus de formulaires PDF précédemment ouverts sont supprimés avant d’en ajouter un nouveau. Cette purge prend également en compte le passage de l’onglet Formulaire à l’onglet Historique dans la vue Détails de la tâche.

**PDF.html - `FormBridge` javascript dans le PDF rendu**

Communique à l’aide de `pdfObject.postMessage` / `pdfObject.messageHandler`.

Cette méthode est le moyen standard de communication avec un JavaScript PDF à partir d’un HTML. La vue PdfTaskForm prend également en charge le PDF plat et le rend clair.

>[!NOTE]
>
>Il n’est pas recommandé de modifier le pdf.html/contenu de la vue PdfTaskForm.

## Nouvelle Forms de HTML {#new-html-forms}

Les nouveaux formulaires de HTML sont rendus par la vue NewHTMLTaskForm.

Lorsqu’un formulaire XDP est rendu en tant que HTML à l’aide du package de formulaires mobiles déployé sur CRX, il ajoute également des `FormBridge` JavaScript vers le formulaire, qui expose différentes méthodes d’enregistrement et d’envoi de données de formulaire.

Ce JavaScript est différent de celui référencé dans les PDF forms ci-dessus, mais a un objectif similaire.

>[!NOTE]
>
>Il n’est pas recommandé de modifier le contenu de la vue NewHTMLTaskForm.

## Forms et guides Flex {#flex-forms-and-guides}

Flex Forms est rendu par SwfTaskForm et les guides sont rendus par les vues HtmlTaskForm respectivement.

Dans l’espace de travail AEM Forms, ces vues communiquent avec le SWF réel qui constitue le formulaire/guide flex en utilisant un fichier SWF intermédiaire présent à `/lc/libs/ws/libs/ws/WSNextAdapter.swf`.

La communication se fait par `swfObject.postMessage` / `window.flexMessageHandler`.

Ce protocole est défini par le `WsNextAdapter.swf`. Les `flexMessageHandlers` existants sur l’objet de la fenêtre, issus des formulaires SWF précédemment ouverts sont supprimés avant d’en ajouter un nouveau. La logique tient également compte du passage de l’onglet Formulaire à l’onglet Historique et vice-versa dans la vue Détails de la tâche. `WsNextAdapter.swf` est utilisé pour effectuer diverses actions de formulaire, comme la sauvegarde ou l’envoi.

>[!NOTE]
>
>il n’est pas recommandé de modifier `WSNextAdapter.swf` ou le contenu de la vue SwfTaskForm / HtmlTaskForm.

## Applications tierces (par exemple, Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Les applications tierces sont rendues à l’aide de la vue ExtAppTaskForm.

**Communication entre l’application tierce et l’espace de travail AEM Forms**

L’espace de travail AEM Forms écoute sur `window.global.postMessage([Message],[Payload])`.

[Message] peut être une chaîne spécifiée comme `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` dans le `runtimeMap`. Les applications tierces doivent utiliser cette interface pour informer l’espace de travail AEM Forms selon les besoins. L’utilisation de cette interface est obligatoire, car l’espace de travail AEM Forms doit savoir lorsque la tâche est envoyée pour nettoyer la fenêtre de tâche.

**Communication entre lʼespace de travail AEM Forms et l’application tierce**

Si les boutons d’action directe de l’espace de travail AEM Forms sont visibles, il appelle `window.[External-App-Name].getMessage([Action])`, où `[Action]` est lu à partir de `routeActionMap`. L’application tierce doit écouter sur cette interface, puis informer lʼespace de travail AEM Forms via l’API `postMessage ()`.

Par exemple, une application Flex peut définir `ExternalInterface.addCallback('getMessage', listener)` pour prendre en charge cette communication. Si l’application tierce souhaite gérer l’envoi de formulaire via ses propres boutons, vous devez spécifier `hideDirectActions = true() in the runtimeMap` et vous pouvez ignorer cet écouteur. Par conséquent, ce concept est facultatif.

Vous pouvez en savoir plus sur l’intégration d’applications tierces en ce qui concerne Correspondence Management à l’adresse [Intégration de Correspondence Management dans l’espace de travail AEM Forms](/help/forms/using/integrating-correspondence-management-html-workspace.md).
