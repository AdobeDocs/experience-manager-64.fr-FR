---
title: Configurer AEM Forms pour la prélecture des informations de domaine
seo-title: Configure AEM forms to prefetchdomain information
description: 'Configurez AEM Forms pour prérécupérer les informations de domaine si vous rencontrez un délai de réponse plus lent en raison de groupes imbriqués profondément ou si vous êtes membre de nombreux groupes. '
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: 6b431cbd-2cea-4ae2-ad26-587ba524d2f5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Configurer AEM Forms pour la prélecture des informations de domaine {#configure-aem-forms-to-prefetchdomain-information}

Les utilisateurs appartenant à de nombreux groupes (500 ou plus par exemple) ou dont les groupes sont imbriqués profondément (30 niveaux) peuvent connaître un ralentissement du temps de réponse. Si vous rencontrez ce problème, vous pouvez configurer AEM Forms pour la prélecture des informations provenant de certains domaines.

1. Dans la console d’administration, cliquez sur **[!UICONTROL Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration]**.
1. Pour exporter le paramètre de configuration en cours dans un fichier, cliquez sur **[!UICONTROL Exporter]**, puis enregistrez le fichier de configuration dans un autre emplacement.
1. Ajoutez le nœud suivant (en gras) :

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

   Dans cet exemple, plusieurs domaines sont configurés pour la prélecture. Les noms de domaines sont séparés par un « / », comme le montre l’exemple ci-dessus avec *Domain_Name1*, *Domain_Name2* et *Domain_Name3*.

1. Pour importer le fichier mis à jour, dans User Management, cliquez sur **[!UICONTROL Configuration > Importer et exporter des fichiers de configuration]**.
1. Cliquez sur **[!UICONTROL Parcourir]** pour trouver le fichier, puis sur Importer et enfin sur **[!UICONTROL OK]**.
