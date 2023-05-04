---
title: Service Forms
seo-title: Forms Service
description: L’article décrit le service Forms et les tâches liées aux formulaires que vous pouvez effectuer à l’aide du service Forms.
seo-description: The article describes Forms service and the form-related tasks you can perform using Forms service.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
exl-id: a1c7c90f-6b50-4bc1-9972-1d3bdf8887ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 56%

---

# Service Forms {#forms-service}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Le service Forms permet de créer des applications clientes interactives de capture de données qui valident, traitent, transforment et diffusent des formulaires généralement créés dans Designer. Le service Forms effectue le rendu en tant que documents de PDF de toute conception de formulaire que vous développez.

Le service Forms permet également aux entreprises d’étendre leurs processus de capture de données intelligentes en déployant des formulaires électroniques en tant que PDF d’Adobe. Vous pouvez également utiliser le service pour importer et exporter des données vers et depuis des PDF forms existants, respectivement.

Utilisez le service Forms pour effectuer les opérations suivantes :

* Rendu des PDF forms en fonction du modèle et des données XML.
* Activez l’intégration des données de formulaire pour importer des données dans des PDF forms et les extraire de ces derniers.
* Rendu des formulaires basés sur des fragments.

## Création de PDF forms  {#creating-pdf-forms-nbsp}

Utilisez le service Form pour créer des PDF forms pour la capture de données. En général, vous commencez avec un modèle AEM Forms Designer. Utilisez l’opération `renderPDFForm` (lien vers Javadoc) du service Forms pour convertir ce modèle en formulaire PDF.

Le premier paramètre de l’opération `renderPDFForm` est le nom du fichier de modèle (par exemple, `ExpenseClaim.xdp`). Vous pouvez stocker le fichier de modèle dans un système de fichiers local, un référentiel CRX ou à un emplacement HTTP ou FTP. Vous pouvez spécifier l’emplacement du fichier de modèle en définissant la racine du contenu dans le paramètre `PDFFormRenderOptions` de l’opération `renderPDFForm`. Voir la documentation Javadoc pour en savoir plus sur les autres options que vous pouvez spécifier pour le paramètre `PDFFormRenderOptions`.

L’opération `renderPDFForm` peut également accepter des données XML. Les données XML sont fusionnées avec le modèle lors de la création d’un formulaire PDF. Le formulaire PDF généré contient ainsi les données spécifiées. Le deuxième paramètre pour l’opération `renderPDFForm` peut accepter un objet de document (Javadoc) qui contient des données XML.

## Extraction de données des formulaires PDF  {#extracting-data-from-pdf-forms-nbsp}

Utilisez l’opération `exportData` (Javadoc) du service Forms pour extraire les données XML d’un formulaire PDF. Cette opération accepte un document comme premier paramètre. Vous pouvez exporter les données sous la forme d’un document XDP ou d’un fichier XML. Si vous exportez les données au format XML, les données exportées suppriment l’enveloppe XDP et renvoient un fichier XML brut. Vous pouvez définir cet arrangement à l’aide du deuxième paramètre.

## Importer des données en PDF forms {#importing-data-into-pdf-forms}

Le service Forms vous permet de fusionner un formulaire PDF créé en utilisant AEM Forms Designer ou l’opération `renderPDFForm` avec des données XML. L’opération `importData` (Javadoc) du service Forms accepte le formulaire PDF et les données XML et renvoie un formulaire PDF avec des données XML.

## Rendu de formulaires reposant sur des fragments {#rendering-forms-based-on-fragments}

Le service Forms peut restituer des formulaires reposant sur des fragments que vous créez à l’aide d’Adobe AEM Forms Designer. Un fragment est une partie réutilisable d’un formulaire. Il est enregistré sous la forme d’un fichier XDP distinct qui peut être inséré dans plusieurs conceptions de formulaire. Un fragment peut très bien inclure un bloc d’adresse ou un paragraphe juridique, par exemple.

L’utilisation de fragments simplifie et accélère la création et la gestion d’un grand nombre de formulaires. Lorsque vous créez un formulaire, insérez une référence au fragment requis pour que ce dernier apparaisse dans le formulaire. La référence au fragment contient un sous-formulaire pointant vers le fichier XDP physique.

L’utilisation de fragments présente les avantages suivants :

* **Réutilisation du contenu** : vous pouvez réutiliser du contenu dans plusieurs conceptions de formulaire. Pour réutiliser rapidement des parties du même contenu dans plusieurs formulaires, créez un fragment. La copie ou la recréation du contenu prend plus de temps. L’emploi de fragments permet par ailleurs de garantir l’homogénéité du contenu et de l’aspect de parties de formulaire reprises dans les différents formulaires de référencement.
* **Mises à jour globales** : vous pouvez apporter des changements généraux à plusieurs formulaires simultanément en effectuant cette opération une fois dans un seul fichier. Vous pouvez modifier le contenu, les objets de script, les liaisons de données, la mise en page ou les styles d’un fragment. Tous les formulaires XDP faisant référence au fragment reflètent les modifications.
* **Création de formulaires partagée** : vous pouvez partager la création de formulaires entre plusieurs ressources. Les développeurs de formulaires familiarisés avec le scripting ou d’autres fonctionnalités avancées d’AEM Forms Designer peuvent développer et partager des fragments qui utilisent le scripting et des propriétés dynamiques. Les concepteurs de formulaires peuvent utiliser les fragments pour concevoir des formulaires. En outre, ils peuvent utiliser les fragments pour s’assurer que toutes les parties d’un formulaire ont une apparence et une fonctionnalité cohérentes dans plusieurs formulaires.
