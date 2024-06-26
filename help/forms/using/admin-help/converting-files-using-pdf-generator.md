---
title: Conversion de fichiers à l’aide de PDF Generator
seo-title: Converting files using PDF Generator
description: Découvrez comment convertir des fichiers à l’aide de PDF Generator.
seo-description: Learn how to convert files using PDF Generator.
uuid: 295afb8f-130a-44f5-b0ab-e4c93c0c9e52
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 999ae2be-56ba-48c1-861b-8d4c991a0206
feature: PDF Generator
exl-id: 3eecff45-405f-482f-b0de-acf6557a7813
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 8%

---

# Conversion de fichiers à l’aide de PDF Generator{#converting-files-using-pdf-generator}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez utiliser les pages web de PDF Generator pour convertir des fichiers.

## Création d’un fichier de PDF {#create-a-pdf-file}

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Créer un PDF.
1. Cliquez sur Parcourir pour rechercher et sélectionner le fichier.

   >[!NOTE]
   >
   >PDF Generator peut détecter automatiquement le type de fichier des fichiers .doc, .xls, .ppt et .rtf, même si l’extension du fichier est absente du nom du fichier. Cette fonctionnalité ne fonctionne pas avec les fichiers .docx, .xlsx et .pptx.

1. Sous Paramètres de configuration, sélectionnez Utiliser des paramètres personnalisés ou Télécharger un fichier de paramètres.

   * Si vous utilisez des paramètres personnalisés, sélectionnez un paramètre Adobe PDF, un paramètre de sécurité et un paramètre de type de fichier, puis spécifiez un délai d’expiration.

      Les paramètres Adobe PDF s’appliquent uniquement aux conversions PS-vers-PDF, EPS-vers-PDF, PRN-vers-PDF, Image vers PDF avec la reconnaissance optique des caractères et Natif vers PDF. Le paramètre de délai d’expiration spécifie le temps maximal nécessaire à la fin de la conversion. La valeur par défaut est de 270 secondes. Ces paramètres ne sont pas utilisés lors des conversions Image vers PDF et OpenOffice vers PDF .

   * Si vous chargez un fichier de paramètres, saisissez son chemin d’accès et son nom dans la zone ou cliquez sur Parcourir pour rechercher et sélectionner le fichier.

1. (Facultatif) Sous Fichier de métadonnées XMP, saisissez le chemin et le nom du fichier XMP ou cliquez sur Parcourir pour rechercher et sélectionner le fichier. Un fichier XMP peut être utilisé pour inclure des informations de métadonnées standard. (Voir [À propos des fichiers XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Cliquez sur Créer. Lorsque le fichier est créé, un lien vers celui-ci s’affiche. Si une erreur se produit lors de la conversion, un avertissement s’affiche. Si vous créez un fichier Postscript, l’avertissement contient également un lien vers le fichier journal.
1. Cliquez sur le lien correspondant au fichier du PDF. Le fichier s’ouvre dans Acrobat.

### À propos des fichiers XMP {#about-xmp-files}

Les documents de PDF créés par PDF Generator dans Acrobat 5.0 ou version ultérieure contiennent des métadonnées de document au format XML. *Métadonnées* inclut des informations sur le document et son contenu, telles que le nom de l’auteur, les mots-clés et les informations de copyright que les utilitaires de recherche peuvent utiliser.

Les métadonnées du document contiennent (sans s’y limiter) des informations qui s’affichent également dans l’onglet Description de la boîte de dialogue Propriétés du document dans Acrobat. Les modifications apportées dans l’onglet Description sont répercutées dans les métadonnées du document. Les métadonnées du document peuvent être étendues et modifiées à l’aide de produits tiers.

Adobe Extensible Metadata Platform (XMP) fournit aux applications d’Adobe un framework XML commun qui normalise la création, le traitement et l’échange de métadonnées de document dans les workflows de publication. Vous pouvez enregistrer et importer le code source XML des métadonnées du document au format XMP, ce qui facilite le partage des métadonnées entre différents documents. Pour plus d’informations sur les fichiers XMP, voir [Plateforme de métadonnées extensible (XMP)](https://www.adobe.com/fr/products/xmp/) et [Adobe XMP Centre de développement](https://www.adobe.com/devnet/xmp.html).

Vous pouvez créer XMP fichiers dans Acrobat.

## Conversion d’un fichier de HTML ou ZIP en PDF {#convert-an-html-file-or-zip-file-to-pdf}

Vous pouvez utiliser PDF Generator pour convertir les types de fichiers suivants dans Adobe PDF :

* Fichiers de HTML, que vous pouvez convertir en téléchargeant un fichier de HTML ou en spécifiant l’URL d’une page web ou d’un site web.
* Fichiers archivés (ZIP), qui peuvent contenir des fichiers de HTML, des fichiers image ou les deux.

Si le fichier ZIP contient plusieurs fichiers HTML au niveau le plus bas de sa hiérarchie de dossiers, le fichier ZIP doit également contenir un fichier index.htm ou index.html.

>[!NOTE]
>
>La fonction HTML à PDF nécessite certaines polices dans le répertoire des polices système. Sur les systèmes Linux, Solaris et AIX, le répertoire des polices système doit contenir la police Courier. Sur les systèmes Windows, le répertoire des polices système doit contenir Times New Roman.

>[!NOTE]
>
>Pour charger un fichier à partir du système de fichiers local, utilisez l’option Télécharger le fichier sur la page HTML vers PDF.

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > HTML vers PDF.
1. Spécifiez le fichier à convertir en effectuant l’une des tâches suivantes :

   * Dans Télécharger le fichier, saisissez le chemin d’accès et le nom du fichier de HTML ou fichier ZIP, ou cliquez sur Parcourir pour le localiser et le sélectionner.
   * Dans la zone Définir l’URL, saisissez l’URL de la page ou du site Web à convertir.

   >[!NOTE]
   >
   >Le fichier que vous convertissez doit avoir une extension .html, .htm ou .zip.

1. Spécifiez les paramètres de configuration :

   * Pour utiliser des paramètres personnalisés, sélectionnez Utiliser des paramètres personnalisés, spécifiez les paramètres de sécurité et de type de fichier, puis spécifiez une valeur de délai d’expiration. La valeur par défaut est de 270 secondes.
   >[!NOTE]
   >
   >Si vous avez configuré le service Generate PDF pour utiliser Acrobat WebCapture, les paramètres de type de fichier que vous sélectionnez sur cette page n’ont aucune incidence sur le PDF généré. Apportez plutôt les modifications appropriées à la version d’Acrobat installée sur le serveur.

   * Pour utiliser un fichier de paramètres existant, sélectionnez Télécharger le fichier de paramètres, puis cliquez sur Parcourir pour accéder à l’emplacement du fichier.


1. Pour charger un fichier XMP, cliquez sur Parcourir et accédez à l’emplacement du fichier. Un fichier XMP peut être utilisé pour inclure des informations de métadonnées standard. (Voir [À propos des fichiers XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Cliquez sur Créer. Lorsque le fichier est créé, un lien vers le fichier du PDF s’affiche.
1. Cliquez sur le lien pour afficher le document du PDF dans Acrobat.

## Exportation d’un fichier PDF dans un autre format de fichier (Windows uniquement) {#export-a-pdf-file-to-another-file-format-windows-only}

Vous pouvez exporter des fichiers PDF vers différents formats de fichier, comme décrit dans le chapitre Generate PDF Service de [Référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Export PDF.
1. Cliquez sur Parcourir pour localiser le fichier de PDF à exporter.
1. Dans la liste Fichier Export PDF à répertorier, sélectionnez le format vers lequel exporter le fichier PDF.
1. Dans la zone Définir un délai d’expiration, saisissez le délai d’attente avant que l’application ne expire. La valeur par défaut est de 270 secondes.

   La durée de conversion affichée lors de la conversion du fichier peut être supérieure à la valeur spécifiée ici. Le temps de conversion inclut le temps passé à attendre le thread ou le processus, le temps nécessaire pour convertir le fichier et le temps pris par le convertisseur de secours (le cas échéant). fois. La valeur Spécifier un délai d’expiration correspond au temps nécessaire pour convertir le fichier.

1. (Facultatif) Dans l’option **Spécifier un profil de contrôle en amont personnalisé**, cliquez sur Parcourir et sélectionnez un [profil de contrôle en amont personnalisé](https://helpx.adobe.com/fr/acrobat/using/preflight-profiles-acrobat-pro.html). Les profils de contrôle en amont sont uniquement utilisés lors de la conversion de documents au format d’archivage PDF (PDF/A).
1. Cliquez sur Exporter. Une fois la conversion terminée, un lien vers le fichier exporté s’affiche.
1. Cliquez sur le lien pour visualiser le fichier converti.

## Optimisation d’un PDF (Windows uniquement) {#optimize-a-pdf}

PDF Generator prend en charge la réduction de la taille des fichiers de PDF.

>[!NOTE]
>
>L’optimisation d’un document signé numériquement supprime et invalide les signatures numériques.

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Optimize PDF.
1. Cliquez sur Parcourir pour localiser le fichier de PDF à optimiser.
1. Spécifiez les paramètres de configuration :

   * Pour utiliser des paramètres personnalisés, sélectionnez Utiliser des paramètres personnalisés, spécifiez les paramètres de type de fichier et spécifiez un délai d’expiration. La valeur par défaut est de 270 secondes.
   * Pour utiliser un fichier de paramètres existant, sélectionnez Télécharger le fichier de paramètres, puis cliquez sur Parcourir pour accéder à l’emplacement du fichier.

1. Cliquez sur Créer.
