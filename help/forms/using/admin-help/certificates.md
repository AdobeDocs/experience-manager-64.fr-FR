---
title: Gérer des certificats
seo-title: Managing certificates
description: Découvrez comment importer et exporter un certificat et modifier ses paramètres de confiance.
seo-description: Learn how to import and export a certificate and edit its trust settings.
uuid: 46b1dbe5-517c-4294-bb52-cc6700a768e8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fd531c0-5206-4be0-a450-13e0dc806068
exl-id: b8d4f35b-dc9c-4e0a-b855-f49275d4ac1f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 52%

---

# Gérer des certificats {#managing-certificates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Trust Store Management vous permet d’importer, de modifier et de supprimer des certificats de confiance sur le serveur pour la validation des signatures numériques et l’authentification de certificats. Vous pouvez importer et exporter un nombre illimité de certificats. Une fois un certificat importé, vous pouvez modifier les paramètres d’approbation et le type de Trust Store. Tenez compte des options suivantes lorsque vous combinez des types de Trust Store :

* **Approbation de l’authentification de certificats avec l’autorité de certification :** pour la validation de CRL, sélectionnez également Approbation d’identité.
* **Approbation de l’authentification de certificats avec l’ICA :** sélectionnez uniquement Approbation d’identité.. Un ICA ne doit pas être approuvé pour l’authentification de certificats. Si vous faites confiance à l’ICA pour l’authentification de certificats, l’ICA devient une autorité de certification pour la création de chemins. Si l’ICA est approuvé pour l’authentification de certificats et l’identité, le certificat du fournisseur de l’autorité de certification est ignoré car l’ICA devient l’autorité de certification.
* **Approbation du serveur OCSP avec HTTPS :** si le serveur du répondant OSCP réside sur un site HTTPS, vous devez également sélectionner Approbation de connexions SSL. Si le répondant OSCP requiert une validation CRL, vérifiez que vous sélectionnez également Approbation d’identité.
* **Racine Adobe :** ne sélectionnez ni Connexions SSL ni Types de Trust Store du serveur OCSP. La racine de l’Adobe n’est pas approuvée pour les connexions SSL et le serveur OCSP. Adobe n’émet pas de certificats OCSP et SSL. Adobe Root est implicitement approuvé avec un alias name=&quot;ADOBEROOT&quot;.

Seuls les certificats X509v3 sont pris en charge. Ce type de certificat peut être fourni dans un fichier codé DER binaire (fichier .cer) ou un fichier texte contenant une version codée Base64 du même certificat codé DER (y compris les certificats X509 au format PEM (Privacy Enhanced Mail)).

Les certificats requis pour effectuer une vérification de signature doivent se trouver dans le même magasin (HSM ou base de données).

Vous pouvez également importer et supprimer des certificats à l’aide de l’API Trust Manager. Pour plus d’informations, voir &quot;Importation de certificats à l’aide de l’API Trust Manager&quot; et &quot;Suppression de certificats à l’aide de l’API Trust Manager&quot; dans [Programmation avec les AEM forms](https://www.adobe.com/go/learn_aemforms_programming_63_fr).

## Importer un certificat {#import-a-certificate}

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > Gestion de Trust Store > Certificats]**.
1. Cliquez sur Importer, puis, sous Type de Trust Store, sélectionnez l’une des options suivantes :

   * **Approbation de connexions SSL :** indique qu’AEM Forms peut utiliser des certificats pour établir une connexion à des systèmes externes via SSL.
   * **Approbation de certification de signature :** indique que des certificats sont approuvés dans des opérations de signature de document pour certifier les signatures numériques d’auteurs.
   * **Approbation de signature :** indique que des certificats sont approuvés dans des opérations de signature de document pour les signatures numériques de non-auteurs.
   * **Approbation d’authentification de certificats :** indique que des certificats sont utilisés par AEM forms pour authentifier des utilisateurs par le biais d’une authentification de certificat ou de carte à puce.
   * **Approbation de serveur OCSP :** indique qu’AEM forms peut utiliser des certificats pour établir une connexion à des répondeurs OCSP externes.
   * **Approbation d’identité :** indique que des certificats peuvent être utilisés pour approuver des types d’informations autres que ceux indiqués ci-dessus.

   >[!NOTE]
   >
   >Le Trust Store fait implicitement confiance à un certificat racine d’Adobe pour l’authentification, la signature, la certification de signature et l’identité du certificat.

1. Dans la zone Alias, saisissez l’identifiant du certificat.
1. Cliquez sur **[!UICONTROL Parcourir]** pour localiser le certificat, puis sur **[!UICONTROL OK]**.

## Exportation d’un certificat {#export-a-certificate}

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > Gestion de Trust Store > Certificats]**.
1. Cliquez sur le nom d’alias du certificat à exporter. La page **[!UICONTROL Détails du certificat]** s’affiche.
1. Cliquez sur **[!UICONTROL Exporter]**, suivez les instructions pour exporter le certificat, puis cliquez sur **[!UICONTROL OK]**.

## Modification des paramètres d’approbation et du type de Trust Store d’un certificat {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > Gestion de Trust Store > Certificats]**.
1. Cliquez sur le nom d’alias du certificat à modifier.
1. Cliquez sur **[!UICONTROL Mettre à jour le certificat]**.
1. Pour modifier le nom de l’alias du certificat, saisissez un nouveau nom dans la zone Alias .
1. Pour mettre à jour le type de Trust Store pour le certificat, sélectionnez le type de Trust Store approprié.
1. Pour mettre à jour les restrictions de la stratégie, dans la zone Stratégies des certificats, saisissez les informations de stratégie, puis cliquez sur **[!UICONTROL OK]**.

## Suppression d’un certificat {#delete-a-certificate}

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > Gestion de Trust Store > Certificats]**.
1. Cochez les cases des certificats à supprimer, cliquez sur **[!UICONTROL Supprimer]**, puis sur **[!UICONTROL OK]**.
