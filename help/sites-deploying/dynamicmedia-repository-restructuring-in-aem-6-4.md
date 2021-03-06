---
title: Restructuration du référentiel Dynamic Media dans AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Dynamic Media.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 68%

---

# Restructuration du référentiel Dynamic Media dans AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

Comme décrit sur le parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md) , les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications de référentiel ayant un impact sur la solution Dynamic Media. Certaines modifications demandent du travail lors du processus de mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avant de procéder à la mise à niveau vers la version 6.5**

* [Configurations personnalisées du codage vidéo adaptatif](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configuration du cloud Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configuration du service cloud Dynamic Media (version hybride DM)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - Configuration du service cloud YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Divers](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Avant de procéder à la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Configurations personnalisées du codage de vidéo adaptative  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Vous pouvez exécuter le script de migration suivant pour migrer vers le nouvel emplacement :</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Vous pouvez également modifier la configuration dans l’interface utilisateur d’AEM. Les modifications seront enregistrées au nouvel emplacement.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configuration du cloud Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Le client peut exécuter un script de migration à cet emplacement :<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Redémarrez le lot OSGi Dynamic Media.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

### Configuration du Cloud Service Dynamic Media (hybride DM) {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Vous pouvez exécuter le script de migration suivant pour vous aligner sur le modèle le plus récent :</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - Configuration du Cloud Service YouTube  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>1. Annulez la publication de toutes les vidéos de YouTube<br /> 2. Créez la configuration YouTube à l’aide de la nouvelle interface utilisateur tactile (à partir de <code>/conf</code>), y compris la copie de tous les canaux de l’ancien emplacement ;<br /> 3. Publiez toutes les vidéos sur YouTube.</p> <p>Ce workflow génère de nouvelles URL YouTube. Si vous n’annulez pas la publication avant de créer une nouvelle configuration YouTube TouchUI, plusieurs URL YouTube seront répertoriées sous Propriétés, car les chaînes recréées seront publiées à nouveau si l’occasion se présente. Cela signifie que des URL inutiles seront répertoriées sous Propriétés.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Divers {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Le client peut exécuter le script de migration ci-dessous.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Vous pouvez également modifier la configuration dans l’interface utilisateur d’AEM. Les modifications seront enregistrées au nouvel emplacement.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Le client peut exécuter le script de migration ci-dessous.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>
