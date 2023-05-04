---
title: Configuration de AEM forms pour la prérécupération des informations de domaine
seo-title: Configure AEM forms to prefetchdomain information
description: Configurez AEM forms pour prérécupérer les informations de domaine si le temps de réponse est plus lent en raison de groupes profondément imbriqués ou si vous êtes membre de nombreux groupes.
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: 6b431cbd-2cea-4ae2-ad26-587ba524d2f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 30%

---

# Configuration de AEM forms pour la prérécupération des informations de domaine {#configure-aem-forms-to-prefetchdomain-information}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les utilisateurs peuvent avoir un temps de réponse plus lent s’ils appartiennent à de nombreux groupes (par exemple, 500 ou plus) ou si les groupes sont profondément imbriqués (par exemple, 30 niveaux). Si vous rencontrez ce problème, vous pouvez configurer AEM forms pour prérécupérer les informations de certains domaines.

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration]**.
1. Pour exporter le paramètre de configuration en cours dans un fichier, cliquez sur **[!UICONTROL Exporter]**, puis enregistrez le fichier de configuration dans un autre emplacement.
1. Ajoutez le noeud suivant (en gras) :

   ```as3
    <node name="UM"> 
    <map/>  
    <node name="PrincipalCache"> 
        <map> 
            <entry key="principalCacheSize" value="1000"/> 
            <entry key="principalCacheBatchFetchSize" value="10"/> 
            <entry key="rebuildCacheAfterSync" value="true /> 
            <entry key="enableFullPrefetch" value="false"/> 
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/> 
        <map> 
    </node> 
    <node name="APSAuditService">
   ```

   Dans cet exemple, plusieurs domaines sont configurés pour la prérécupération. Les noms de domaine sont séparés par un &quot;/&quot;. Ceci est illustré dans l’exemple ci-dessus avec *Domain_Name1*, *Domain_Name2*, et *Domain_Name3*.

1. Pour importer le fichier mis à jour, dans User Management, cliquez sur **[!UICONTROL Configuration > Importer et exporter des fichiers de configuration]**.
1. Cliquez sur **[!UICONTROL Parcourir]** pour trouver le fichier, puis sur Importer et enfin sur **[!UICONTROL OK]**.
