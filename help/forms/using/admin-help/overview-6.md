---
title: Présentation de la configuration SSL
seo-title: Overview of configuring SSL
description: Découvrez comment améliorer la sécurité des communications en configurant SSL.
seo-description: Learn about how to enhance security of communication by configuring SSL.
uuid: 3e99d2bf-137b-45ba-8384-309624094623
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8e107abb-861f-4063-b600-c87e34639019
exl-id: 5dc68401-f6bc-42cb-84db-1db805b045c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 6%

---

# Présentation de la configuration SSL {#overview-of-configuring-ssl}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez créer des informations d’identification SSL (Secure Sockets Layer) et configurer SSL sur le serveur d’applications afin d’améliorer la sécurité de la communication avec votre serveur d’applications.

En tant que produit de sécurité, Rights Management requiert la configuration de SSL. Lors de la configuration des certificats SSL, veillez à n’utiliser que des clés RSA. Les certificats SSL avec clés DSA ne sont pas pris en charge.

Les informations fournies s’appliquent aux installations clé en main, automatiques et manuelles. Il offre un exemple de méthode de configuration SSL. Vous pouvez également utiliser d’autres méthodes plus appropriées à votre réseau ou organisation.

>[!NOTE]
>
>Il est recommandé de terminer l’installation, la configuration et le déploiement de vos modules forms AEM et de vous assurer que les produits s’exécutent correctement avant de configurer SSL sur le serveur d’applications.

>[!NOTE]
>
>Lors de la création de certificats de sécurité et d’informations d’identification SSL, utilisez les mêmes privilèges de compte d’utilisateur que ceux utilisés pour exécuter le serveur d’applications. Si le serveur d’applications est exécuté à l’aide d’autres privilèges utilisateur, le rendu du formulaire pour les rendus PDFForm peut échouer lorsque ContentRootURI pointe vers https.

Si vous disposez d’un serveur LDAP compatible SSL, configurez User Management pour l’utiliser. (Voir [Configuration de User Management pour un serveur LDAP compatible SSL](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
