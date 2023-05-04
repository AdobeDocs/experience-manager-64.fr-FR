---
title: Modifier l’ordre d’évaluation pour l’authentification
seo-title: Change the order of evaluation for authentication
description: Vous pouvez modifier l’ordre dans lequel AEM forms évalue plusieurs fournisseurs d’authentification.
seo-description: You can change the order in which AEM forms evaluates multiple authentication providers.
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
exl-id: cac16c50-a85d-4e40-a590-8a0a52be893c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 52%

---

# Modifier l’ordre d’évaluation pour l’authentification {#change-the-order-of-evaluation-for-authentication}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si vous avez configuré plusieurs fournisseurs d’authentification, vous pouvez modifier l’ordre dans lequel AEM forms les évalue pour authentification. L’ordre des fournisseurs d’authentification répertoriés dans le fichier config.xml détermine l’ordre d’évaluation pour l’authentification.

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Configuration > Importer et exporter des fichiers de configuration.
1. Pour exporter le paramètre de configuration en cours dans un fichier, cliquez sur Exporter, puis enregistrez le fichier de configuration dans un autre emplacement.
1. Recherchez le noeud suivant dans le fichier :

   ```as3
    <node name="AuthSchemes"> 
        <map />  
            <node name="CertificateAuth"> 
                <map> 
                    <entry key="order" value="3" />  
                    <entry key="name" value="edc.server.auth.scheme.certificate" />  
                </map> 
        </node> 
        <node name="Kerberos"> 
            <map> 
                <entry key="kerberosSPN" value="defaultSPN" />  
                <entry key="order" value="1" />  
                <entry key="name" value="edc.server.auth.scheme.kerberos" />  
            </map> 
    </node>
   ```

   Dans `<entry key="order" value="3" />`, modifiez la valeur de chaque nœud pour définir l’ordre de l’évaluation de l’authentification.

1. Pour importer le fichier mis à jour, dans Gestion des utilisateurs, cliquez sur Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Parcourir pour trouver le fichier, puis sur Importer et enfin sur OK.
