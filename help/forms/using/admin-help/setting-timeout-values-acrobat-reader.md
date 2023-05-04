---
title: Définir des délais d’expiration à utiliser avec les extensions d’Acrobat Reader DC
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Découvrez comment définir des valeurs de délai d’expiration à utiliser avec les extensions Acrobat Reader DC.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 49%

---

# Configuration des délais d’expiration à utiliser avec les extensions d’Acrobat Reader DC  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque vous travaillez sur de nombreux fichiers PDF dans les extensions d’Acrobat Reader DC, configurez comme suit les valeurs de délai d’expiration suivantes pour éviter l’expiration et l’échec des travaux :

**Délai avant suppression du document**

Cette valeur peut être définie dans Administration Console. Cliquez sur Paramètres > Paramètres de Core System > Configurations, puis spécifiez une valeur pour Délai d’expiration par défaut du partage des documents.

**Délai de gestion des utilisateurs dans AEM Forms :** cette valeur peut être définie en modifiant le fichier config.xml. Dans Administration Console, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration, puis cliquez sur Exporter. Ouvrez le fichier config.xml exporté et modifiez les lignes suivantes :

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Enregistrez le fichier config.xml, puis réimportez-le dans Administration Console.

**Délai d’expiration de session du serveur d’applications :** cette valeur peut être définie sur le serveur d’applications. Pour plus d’informations, consultez la documentation de votre serveur d’applications.
