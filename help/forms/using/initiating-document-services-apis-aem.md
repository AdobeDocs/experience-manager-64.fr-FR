---
title: Lancer des API de Services de document à partir d’un flux de travail AEM
seo-title: Initiate Document Services APIs from AEM Workflow
description: Découvrez comment appeler AEM Document Services sur DDX ou les entrées fournies. Découvrez également comment convertir le PDF en PDF/A
seo-description: Learn how to invoke AEM Document services on DDX or supplied inputs. Also see hwo to convert PDF to PDF/A
uuid: aacec2df-1ad6-4ff2-a99d-ef206efcdc09
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 8b85bdc7-3864-49c9-81b0-cf15b8e986d9
exl-id: a2821338-f31d-4b08-91e6-7f934dc01384
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 30%

---

# Lancement des API de Services de document à partir d’un flux de travail AEM  {#initiate-document-services-apis-from-aem-workflow}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Assembler {#assembler}

AEM Forms fournit des workflows personnalisés pour appeler les API du service Assembler suivantes :

* **invoke**: Appelle les opérations spécifiées dans input DDX sur les entrées fournies.
* **toPDFA**: Convertit le document du PDF d’entrée en document de PDF/A.

### Workflow Invoquer DDX {#invoke-ddx-workflow}

Le workflow **Appeler DDX** appelle l’API du service Assembler `Invoke`, que vous pouvez utiliser pour assembler ou désassembler des documents, ajouter des filigranes à des PDF, etc.

1. Faites glisser le **[!UICONTROL Invoquer DDX]** étape de workflow sous l’onglet Forms Workflow dans le sidekick.
1. Double-cliquez sur l’étape de workflow ajoutée pour modifier le composant.
1. Dans la boîte de dialogue Modifier le composant, configurez les documents d’entrée, les options d’environnement et les documents de sortie, puis cliquez sur **[!UICONTROL OK]**.

#### Documents d’entrée {#input-documents}

Le workflow Invoke DDX nécessite les documents d’entrée suivants :

* **DDX**: Il s’agit d’une entrée obligatoire pour l’étape de flux de travail Invoke DDX. Elle peut être spécifiée en sélectionnant l’une des options suivantes dans la liste déroulante d’entrée DDX.

   * *Relative To Payload* : le fichier DDX input est relatif au dossier de charge pour l’élément de flux de travail.
   * *Use Payload*: La charge utile de l’élément de workflow est utilisée comme document DDX d’entrée.
   * *Chemin absolu*: Chemin d’accès absolu au document DDX dans le référentiel CRX.

* **Create Map from PayLoad** : si vous activez cette option, les documents sous le dossier de charge sont ajoutés au mappage de document d’entrée pour l’API `invoke` dans Assembler. Le nom du nœud pour chaque document est utilisé comme clé dans la carte.

* **Input Document’s Map** : indique la carte de document d’entrée. Vous pouvez ajouter un nombre indéfini d’entrées, où chaque entrée spécifie la clé du document dans la carte et la source du document.

#### Options d’environnement {#environment-options}

L’onglet Options d’environnement vous permet de définir différentes options de traitement pour l’API d’appel.

* *Niveau de journal des tâches*: Indique le niveau de journal des journaux de traitement.
* *Validate Only* : vérifie la validité d’input DDX.

* *Échec en cas d’erreur*: Indique si l’appel au service Assembler doit échouer en cas d’erreur. La valeur par défaut est False.

#### Documents de sortie {#output-documents}

Selon le DDX d’entrée, l’API d’appel peut produire plusieurs documents de sortie. L’onglet Output documents vous permet de sélectionner le document de sortie à enregistrer.

1. *Save Output dans Payload* : enregistre les documents de sortie sous le dossier de payload, ou remplace la payload, si celle-ci est un fichier.
1. *Output Document&#39;s Map*: Permet de spécifier explicitement où enregistrer chaque document de sortie en ajoutant une entrée par document de sortie. Chaque entrée spécifie le document et l’emplacement d’enregistrement. Un document de sortie peut remplacer la charge utile ou l’enregistrer dans le dossier de charge utile. Cette option peut être utile lorsque qu’il y a plusieurs documents de sortie.

1. *Journal des tâches*: Indique l’emplacement d’enregistrement du document de journal des tâches, ce qui s’avère utile pour la résolution des problèmes.

### Processus de conversion en PDF/A {#convert-to-pdf-a-workflow}

L’étape de flux de travail Convert to PDF/A (Convertir en PDF/A) appel l’API du service d’Assembler `toPDFA`. Il est utilisé pour convertir des documents PDF en documents conformes au format PDF/A.

1. Faites glisser l’étape de flux de travail **[!UICONTROL ConvertToPDFA]** sous l’onglet Forms Workflow dans Sidekick.

1. Double-cliquez sur l’étape de workflow ajoutée pour modifier le composant.
1. Dans la boîte de dialogue Modifier le composant, configurez les documents d’entrée, les options de conversion et les documents de sortie, puis cliquez sur **[!UICONTROL OK]**.

#### Documents d’entrée {#input-documents-1}

Spécifiez la source du document à convertir en document conforme au PDF/A de l’une des manières suivantes.

* *Relatif À La Charge Utile*: Le document d’entrée est relatif au dossier de charge utile de l’élément de workflow.
* *Use Payload*: La charge utile de l’élément de workflow est utilisée comme document d’entrée.
* *Absolute Path* : chemin d’accès absolu au document d’entrée dans le référentiel CRX.

#### Options de conversion {#conversion-options}

Les options de conversion vous permettent de spécifier des options qui modifient le processus de conversion PDF/A.

* *Conformité* : Spécifie la norme PDF/A à laquelle le PDF/A de sortie doit se conformer.
* *Result Level * : Indique le niveau de journal à utiliser pour les journaux de conversion PDF/A.
* *Signatures* : Indique le mode de traitement des signatures dans le document d’entrée lors de la conversion.
* *Espace colorimétrique* : Spécifie l’espace colorimétrique prédéfini à utiliser pour le document du PDF/A de sortie.
* *Vérifier la conversion* : indique si le document converti en PDF/A doit être vérifié pour assurer la conformité PDF/A après conversion.
* *Job Log Level* : indique le niveau de journal à utiliser pour les journaux de traitement.

* *Metadata Extension Schema* : indique le chemin du schéma d’extension de métadonnées à utiliser pour les propriétés XMP dans les métadonnées du document PDF.

#### Documents de sortie {#output-documents-1}

L’onglet Output documents vous permet de spécifier la destination des documents de sortie.

* *Document PDFA*: Indique l’emplacement d’enregistrement du document converti/du PDF converti. Il peut remplacer le document de charge utile ou l’enregistrer dans le dossier de charge utile.
* *Conversion Log* : indique l’emplacement où les journaux de conversion sont enregistrés. Ce paramètre peut écraser le document de charge utile ou l’enregistrer dans le dossier de charge utile.

## Formulaires {#forms}

Le flux de travail Render PDF Form est une enveloppe de l’API du service Forms `renderPDFForm` qui permet de créer un PDF à l’aide d’un modèle XDP et de fichiers de données .xml.

### Processus du formulaire de rendu PDF {#render-pdf-form-workflow}

1. Faites glisser l’étape de processus Render PDF Form sous l’onglet Forms Workflow dans le sidekick.
1. Double-cliquez sur l’étape de workflow ajoutée pour modifier le composant.
1. Dans la boîte de dialogue Modifier le composant, configurez les documents d’entrée, les documents de sortie et d’autres paramètres, puis cliquez sur **[!UICONTROL OK]**.

#### Documents d’entrée {#input-documents-2}

* *Fichier modèle*: Spécifie l’emplacement du modèle XDP. Ce champ est obligatoire.

* *Document de données*: Spécifie l’emplacement du fichier XML de données à fusionner avec le modèle.

#### Documents de sortie {#output-documents-2}

* *Output Document*: - Indique le nom du formulaire de PDF généré.

#### Paramètres supplémentaires {#additional-parameters}

* *Racine du contenu*: Spécifie le chemin d’accès au dossier dans le référentiel où sont stockés les fragments ou les images utilisés dans le modèle XDP d’entrée.
* *Submit Url*: Indique l’URL d’envoi par défaut pour le formulaire de PDF généré.
* *Paramètres régionaux*: Indique le paramètre régional par défaut du formulaire de PDF généré.
* *Version d’Acrobat*: Indique la version Acrobat ciblée pour le formulaire de PDF généré.
* *PDF balisé*: Indique si le PDF généré doit être accessible.
* *Document XCI*: Spécifie le chemin d’accès au fichier XCI.

## Sortie {#output}

Le flux de travail Generate Non Interactive PDF Workflow (Générer un PDF non interactif) est une enveloppe de l’API de service Output `generatePDFOutput`. Il est utilisé pour générer des documents PDF non interactifs à partir de modèles XDP et des fichiers .xml de données.

### Flux de travail Generate Non Interactive PDF Output   {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Faites glisser le workflow Générer une sortie de PDF non interactif sous l’onglet Forms Workflow dans le sidekick.
1. Double-cliquez sur l’étape de workflow ajoutée pour modifier le composant.
1. Dans la boîte de dialogue Modifier le composant, configurez les documents d’entrée, les documents de sortie et d’autres paramètres, puis cliquez sur **[!UICONTROL OK]**.

#### Documents d’entrée {#input-documents-3}

* *Fichier modèle*: Spécifie l’emplacement du modèle XDP. Ce champ est obligatoire.

* *Document de données*: Spécifie l’emplacement du fichier XML de données à fusionner avec le modèle.

#### Document de sortie {#output-document}

*Output Document*: Indique le nom du formulaire de PDF généré.

#### Paramètres supplémentaires {#additional-parameters-1}

* *Racine du contenu*: Spécifie le chemin d’accès au dossier dans le référentiel où sont stockés les fragments ou les images utilisés dans le modèle XDP d’entrée.
* *Paramètres régionaux*: Indique le paramètre régional par défaut du formulaire de PDF généré.
* *Version d’Acrobat*: Indique la version Acrobat ciblée pour le formulaire de PDF généré.
* Linearized PDF : indique si le PDF généré doit être optimisé pour l’affichage Web.
* *PDF balisé*: Indique si le PDF généré doit être accessible.
* *Document XCI*: Spécifie le chemin d’accès au fichier XCI.
