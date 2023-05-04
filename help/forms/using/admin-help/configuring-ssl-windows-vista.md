---
title: Configurer SSL sous Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Découvrez comment configurer SSL sous Windows Vista.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 20%

---

# Configurer SSL sous Windows Vista {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour configurer SSL sous Windows Vista™, vous avez besoin d’un certificat SSL avec des clés RSA à des fins d’authentification. Vous pouvez utiliser l’outil Java keytool pour créer le certificat.

>[!NOTE]
>
>Windows Vista ne fonctionnera pas avec les clés DSA.

Vous pouvez exécuter keytool en utilisant une seule commande qui comprend toutes les informations requises pour créer le certificat et le KeyStore.

**Création d’un certificat SSL**

1. Dans une invite de commande, accédez à *[ACCUEIL JAVA]*/bin et saisissez la commande suivante pour créer le certificat et le fichier de stockage des clés :

   `keytool -genkey -keyalg RSA -dname "CN=`*Nom d’hôte* `, OU=`*Nom du groupe* `, O=`*Nom de la société* `,L=`*Ville******Name* `, S=`*État* `, C=`*Code pays* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`*_**password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Remplacer *[JAVA_HOME] avec le répertoire dans lequel le JDK est installé, et remplacez le texte en italique par les valeurs correspondant à votre environnement.*

1. Saisissez `changeit` comme mot de passe. Il s’agit du mot de passe par défaut d’une installation Java, mais l’administrateur système peut l’avoir modifié.
