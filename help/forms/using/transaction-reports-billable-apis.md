---
title: API facturables des rapports de transaction
seo-title: Transaction Reports Billable APIs
description: Liste de toutes les API comptabilisées comme des transactions
seo-description: List of all the APIs that are accounted as transactions
uuid: 8861e325-7393-4d2c-9ec1-17f391ca3909
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 82e72ffb-2faa-45fe-8bb2-f485d8fa043e
exl-id: 18b5c6e2-3b0c-4ec8-9e65-c4105b47be4e
source-git-commit: eeaa70855980ca62574f89e280b46c02c0b65bdc
workflow-type: tm+mt
source-wordcount: '1859'
ht-degree: 10%

---

# API facturables des rapports de transaction {#transaction-reports-billable-apis}

Liste de toutes les API comptabilisées comme des transactions

AEM Forms fournit plusieurs API pour envoyer des formulaires, traiter des documents et générer des documents. Certaines API sont comptabilisées comme des transactions et d’autres sont libres d’utiliser. Ce document fournit une liste de toutes les API qui sont comptabilisées comme des transactions dans un rapport de transaction. Voici quelques scénarios courants dans lesquels une API facturable est utilisée :

* Envoi d’un formulaire adaptatif, d’un HTML5 et d’un jeu de formulaires
* Rendu d’une version imprimée ou web d’une communication interactive
* Conversion d’un document d’un format à un autre
* Aplatissement d’un document de PDF dynamique
* Génération d’un document d’enregistrement
* Fusion d’un document de PDF interactif avec un autre document de PDF
* Utilisation de l’étape Affecter une tâche et des étapes des services de documentation des processus AEM
* Utilisation d’un formulaire adaptatif dans un formulaire adaptatif

Les API de facturation ne prennent pas en compte le nombre de pages, la longueur d’un document ou d’un formulaire, ni le format final du document rendu. Un rapport de transaction répartit les transactions en trois catégories : Documents traités, Documents rendus et Forms envoyés.

* **Forms Envoyé :** Lorsque des données sont envoyées à partir de n’importe quel type de formulaire créé avec AEM Forms et que les données sont envoyées à un référentiel de stockage de données ou à une base de données sont considérées comme des envois de formulaire. Par exemple, l’envoi d’un formulaire adaptatif, d’un HTML 5, de PDF forms et d’un jeu de formulaires est comptabilisé comme des formulaires envoyés. Chaque formulaire d’un jeu de formulaires est considéré comme un envoi. Par exemple, si un jeu de formulaires comporte 5 formulaires, le service de reporting sur les transactions les comptabilise comme 5 envois lorsque le jeu de formulaires est envoyé.
* **Documents rendus :** La génération d’un document en combinant un modèle et des données, la signature ou la certification numérique d’un document, l’utilisation d’API Document Services facturables pour les services de document ou la conversion d’un document d’un format à un autre sont comptabilisées comme des documents rendus.

>[!NOTE]
>
>L’interface utilisateur des rapports de transaction affiche trois catégories : Forms envoyées, documents rendus et documents traités. Les documents rendus et les documents traités sont tous deux comptabilisés comme des documents rendus.

## API de services de document facturables {#billable-document-services-apis}

### Service Generate PDF {#generate-pdf-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td> 
   <td>Crée Adobe PDF à partir des types de fichiers pris en charge.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td> 
   <td>Crée Adobe PDF à partir des types de fichiers pris en charge.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td> 
   <td>Convertit Adobe PDF en types de fichiers pris en charge. </td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td> 
   <td>Convertit Adobe PDF en types de fichiers pris en charge. </td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td> 
   <td>Convertit Adobe PDF en types de fichiers pris en charge. </td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td> 
   <td><p>Crée un PDF à partir de pages de HTML.</p> </td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td> 
   <td>Crée un PDF à partir des URL pointant vers une page de HTML.</td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td> 
   <td>Crée un PDF à partir des URL pointant vers une page de HTML.</td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td> 
   <td>Optimise le PDF pour réduire la taille du fichier en supprimant les métadonnées inutiles sans affecter la qualité.</td> 
   <td>Documents traités<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Distiller Service {#distiller-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td> 
   <td>Crée Adobe PDF à partir des types de fichiers pris en charge.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td> 
   <td>Crée Adobe PDF à partir des types de fichiers pris en charge.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Service de document d’enregistrement (service DoR) {#document-of-record-service-dor-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td> 
   <td>Appelle la méthode de rendu spécifiée pour générer un document d’enregistrement à l’aide des paramètres fournis.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Service Output {#output-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td> 
   <td>Fusionne des données et des modèles pour créer un document de PDF.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PDFOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePDFOutputBatch</a></td> 
   <td>Fusionne des données et des modèles pour créer un ensemble de documents de PDF.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td> 
   <td>Convertit les documents XDP et PDF aux formats de fichier PostScript (PS), PCL (Printer Command Language) et ZPL. </td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td> 
   <td>Convertit les documents XDP et PDF aux formats de fichier PostScript (PS), PCL (Printer Command Language) et ZPL. </td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PrintedOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePrintedOutputBatch</a></td> 
   <td>Convertit un ensemble de documents XDP et PDF en un ensemble de formats de fichiers PostScript (PS), PCL (Printer Command Language) et ZPL. </td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Service Forms {#forms-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td> 
   <td>Rend PDF Form à partir de modèles XDP. Les modèles XP sont créés dans Forms Designer.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td> 
   <td>Extrait les données d’un formulaire PDF ou de modèles XDP</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Convert PDF Service {#convert-pdf-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td> 
   <td>Convertit un document PDF en une liste de documents image. Les formats d’image pris en charge sont JPEG, JPEG2K, PNG et TIFF.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td> 
   <td>Convertit un fichier de PDF plat au format PostScript à l’aide des options spécifiées dans la spécification de l’option.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Service Barcoded Forms {#barcoded-forms-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td> 
   <td>Décode tous les codes à barres d’un objet Document et renvoie un objet org.w3c.dom.Document contenant les données extraites du code à barres.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Incohérence affectant le service assembleur {#assembler-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">invoke</a></td> 
   <td>Exécute le document DDX spécifié et renvoie une <a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a> contenant les documents créés. </td> 
   <td>Documents traités</td> 
   <td>Les opérations suivantes ne sont pas comptabilisées comme des transactions :
    <ul> 
     <li>Création de packages ou de portfolio</li> 
     <li>Assemblage de plusieurs fichiers XDP </li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">invoke</a></td> 
   <td>Exécute le document DDX spécifié et renvoie une <a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html"> AssemblerResult</a> contenant les documents créés. </td> 
   <td>Documents traités</td> 
   <td>Tous les formats de fichiers d’entrée pris en charge par PDF Generator, Forms et les services Output, le service Assembler prend en charge tous ces formats en tant que formats de fichiers de sortie. </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-" target="_blank">toPDFA</a></td> 
   <td>Convertissez un document spécifié en PDF/A à l’aide des options spécifiées.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* L’API invoke du service Assembler peut appeler en interne une API facturable d’un autre service selon l’entrée. Ainsi, l’API d’appel peut être comptabilisée comme aucune, une ou plusieurs transactions. Le nombre de transactions comptabilisées dépend de l’entrée et des API internes invoquées.
>* Un seul document de PDF produit à l’aide du service Assembler peut être comptabilisé comme aucune, une ou plusieurs transactions. Le nombre de transactions comptabilisées dépend du code DDX fourni.

>


### Service PDF Utility  {#pdf-utility-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td> 
   <td>Convertit un document de PDF en fichier XDP. Pour qu’un document de PDF soit converti correctement en fichier XDP, le document de PDF doit contenir un flux XFA dans le dictionnaire AcroForm.</td> 
   <td>Documents traités</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Service Doc Assurance {#doc-assurance-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/docassurance/client/api/DocAssuranceService.html#secureDocument-com.adobe.aemfd.docmanager.Document-com.adobe.fd.docassurance.client.api.EncryptionOptions-com.adobe.fd.docassurance.client.api.SignatureOptions-com.adobe.fd.docassurance.client.api.ReaderExtensionOptions-com.adobe.fd.signatures.pdf.inputs.UnlockOptions-">secureDocument</a></td> 
   <td>L’API vous permet de protéger votre document. Vous pouvez utiliser l’API pour signer, certifier, Reader étendre ou chiffrer un document de PDF. </td> 
   <td>Documents traités</td> 
   <td>Fonctionnement de signature et de certification uniquement de la fonction <a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/docassurance/client/api/DocAssuranceService.html#secureDocument-com.adobe.aemfd.docmanager.Document-com.adobe.fd.docassurance.client.api.EncryptionOptions-com.adobe.fd.docassurance.client.api.SignatureOptions-com.adobe.fd.docassurance.client.api.ReaderExtensionOptions-com.adobe.fd.signatures.pdf.inputs.UnlockOptions-">secureDocument</a> sont facturés.</td> 
  </tr>
 </tbody>
</table>

## API de capture de données facturables {#billable-data-capture-apis}

Tous les événements d’envoi des formulaires adaptatifs, de HTML5 Forms et du jeu de formulaires sont comptabilisés comme des transactions. Par défaut, l’envoi d’un formulaire de PDF n’est pas comptabilisé comme une transaction. Utilisez les [API des rapports sur les transactions](record-transaction-custom-implementation.md) pour enregistrer un envoi PDF forms en tant que transaction.

### Formulaires adaptatifs {#adaptive-forms}

<table> 
 <tbody>
  <tr>
   <td><p>Cas d’utilisation</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td>Envoi d’un formulaire adaptatif</td> 
   <td>Envoie un formulaire adaptatif à une action d’envoi configurée. </td> 
   <td>Formulaires envoyés</td> 
   <td>
    <ul> 
     <li>Les envois réussis comptabilisent une ou deux transactions. Le nombre de transactions comptabilisées dépend du type d’action d’envoi utilisée pour l’envoi. Par exemple, l’envoi d’un PDF par le biais d’une action d’envoi par courrier électronique comptabilise deux comptes de transactions. Une transaction pour l’envoi du formulaire et une autre pour le PDF généré à l’aide du service de document d’enregistrement (DOR). </li> 
     <li>L’utilisation du formulaire adaptatif dans un formulaire adaptatif (jeu de formulaires adaptatifs) ne tient compte que d’une seule transaction. Vous pouvez avoir un nombre illimité de formulaires adaptatifs dans un formulaire adaptatif.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Formulaires HTML5 {#html-forms}

<table> 
 <tbody>
  <tr>
   <td><p>Cas d’utilisation</p> </td> 
   <td>Description </td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td>Envoi d’un HTML5</td> 
   <td>Envoie un HTML5 Form pour envoyer l’URL configurée dans le formulaire.</td> 
   <td>Formulaires envoyés</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Jeu de formulaires {#form-set}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td>Envoi d’un jeu de formulaires</td> 
   <td>Envoie le jeu de formulaires à l’URL d’envoi configurée dans le jeu de formulaires.</td> 
   <td>Formulaires envoyés</td> 
   <td>
    <ul> 
     <li>L’utilisation du formulaire adaptatif dans un formulaire adaptatif (jeu de formulaires adaptatifs) ne tient compte que d’une seule transaction. Vous pouvez avoir un nombre illimité de formulaires adaptatifs dans un formulaire adaptatif.</li> 
     <li>Chaque formulaire d’un formulaire Forms HTML5 est comptabilisé comme une transaction distincte. </li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Processus de communication interactive facturable et d’AEM basés sur des formulaires sur les API OSGi {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Les étapes Affecter des tâches et des services de document des processus d’AEM basés sur l’utilisation de Forms sur OSGi et tous les rendus de communication interactive sont comptabilisés comme des transactions. La prévisualisation d’une communication interactive sur l’instance de création et la prévisualisation sur l’instance de publication à l’aide de l’interface utilisateur de l’agent ne sont pas comptabilisées comme des transactions. Si une étape de workflow comptabilise une transaction et que le workflow ne se termine pas, le nombre de transactions n’est pas inversé.

### Communication interactive - canal Web {#interactive-communication-web-channel}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td>Rendu d’un canal web</td> 
   <td>Ouvre la version web d’une communication interactive.</td> 
   <td>Documents rendus</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
 </tbody>
</table>

### Communication interactive - Canal d’impression {#interactive-communication-print-channel}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Description</td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (conversion en PDF)</td> 
   <td>Génère la version PDF d’une communication interactive.</td> 
   <td>Documents rendus</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
 </tbody>
</table>

### Processus AEM de formulaire sur OSGi  {#form-centric-aem-workflows-on-osgi}

<table> 
 <tbody>
  <tr>
   <td><p>Cas d’utilisation</p> </td> 
   <td>Catégorie de rapport de transaction</td> 
   <td>Informations supplémentaires</td> 
  </tr>
  <tr>
   <td>Envoi d’une étape Affecter une tâche</td> 
   <td>Formulaires envoyés</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
  <tr>
   <td>Envoi d’un point de départ d’application de workflow </td> 
   <td>Formulaires envoyés</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Envoi d’une communication interactive (canal d’impression) depuis l’interface utilisateur de l’agent vers un workflow</td> 
   <td>Documents rendus</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Enregistrement des API facturables en tant que transactions pour le code personnalisé {#recording-billable-apis-as-transactions-for-custom-code}

Les actions telles que l’envoi d’un formulaire de PDF, l’utilisation de l’interface utilisateur de l’agent pour prévisualiser une communication interactive, l’envoi d’un formulaire non standard et les implémentations personnalisées ne sont pas comptabilisées comme des transactions. AEM Forms fournit une API pour enregistrer des actions telles que des transactions. Vous pouvez appeler l’API depuis vos implémentations personnalisées vers [enregistrer une transaction](record-transaction-custom-implementation.md).

## Articles connexes {#related-articles}

* [Présentation des rapports de transaction](/help/forms/using/transaction-reports-overview.md)
* [Affichage et compréhension des rapports de transaction](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Enregistrer une transaction pour les implémentations personnalisées](/help/forms/using/record-transaction-custom-implementation.md)
