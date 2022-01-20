---
title: Configuration de SSL sous Windows Vista
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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 60%

---

# Configuration de SSL sous Windows Vista {#configuring-ssl-on-windows-vista}

Pour configurer SSL sous Windows Vista™, vous avez besoin d’un certificat SSL avec des clés RSA à des fins d’authentification. Vous pouvez utiliser l’outil Java keytool pour créer ce certificat.

>[!NOTE]
>
>Windows Vista ne reconnaît pas les clés DSA.

Vous pouvez exécuter l’outil keytool en saisissant une seule commande qui comprend toutes les informations requises pour créer le certificat et le fichier de stockage des clés.

**Création de certificat SSL**

1. Dans une invite de commande, accédez à *[ACCUEIL JAVA]*/bin et saisissez la commande suivante pour créer le certificat et le fichier de stockage des clés :

   `keytool -genkey -keyalg RSA -dname "CN=`*Nom d’hôte* `, OU=`*Nom du groupe* `, O=`*Nom de la société* `,L=`*Ville******Name* `, S=`*État* `, C=`*Code pays* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`*_**password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Remplacer *[JAVA_HOME] avec le répertoire dans lequel le JDK est installé, et remplacez le texte en italique par les valeurs correspondant à votre environnement.*

1. Type `changeit` comme mot de passe. Il s’agit du mot de passe par défaut d’une installation Java, mais l’administrateur système peut l’avoir modifié.
