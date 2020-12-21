---
title: Configuration de SSL sous Windows Vista
seo-title: Configuration de SSL sous Windows Vista
description: Découvrez comment configurer SSL sous Windows Vista.
seo-description: Découvrez comment configurer SSL sous Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 63%

---


# Configuration de SSL sous Windows Vista {#configuring-ssl-on-windows-vista}

Pour configurer SSL sous Windows Vista™, vous avez besoin d’un certificat SSL avec des clés RSA à des fins d’authentification. Vous pouvez utiliser l’outil Java keytool pour créer ce certificat.

>[!NOTE]
>
>Windows Vista ne reconnaît pas les clés DSA.

Vous pouvez exécuter l’outil keytool en saisissant une seule commande qui comprend toutes les informations requises pour créer le certificat et le fichier de stockage des clés.

**Création de certificat SSL**

1. Dans une invite de commande, accédez à *[JAVA HOME]*/bin et saisissez la commande suivante pour créer le certificat et le fichier de stockage des clés :

   `keytool -genkey -keyalg RSA -dname "CN=`*Nom* `, OU=`*d&#39;hôte* `, O=`*Nom du groupe* `,L=`*Nom de la sociétéVille*****Nom* Code `, S=`** `, C=`** `" -alias`*ÉtatPays&quot;Cert LC&quot;* `-keypass` `*key*`*_*mot de passe nom_stockage *`.keystore`**`-keystore`*

   >[!NOTE]
   >
   >Remplacez *[JAVA_HOME] par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italique par les valeurs correspondant à votre environnement.*

1. Tapez `changeit` comme mot de passe. Il s’agit du mot de passe par défaut d’une installation Java, mais l’administrateur système peut l’avoir modifié.

