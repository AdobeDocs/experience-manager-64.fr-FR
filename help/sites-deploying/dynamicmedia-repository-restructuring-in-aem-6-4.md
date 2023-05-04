---
title: Restructuration du référentiel Dynamic Media dans AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires afin de migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Dynamic Media.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 55%

---

# Restructuration du référentiel Dynamic Media dans AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Comme décrit sur le parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md) , les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications de référentiel ayant un impact sur la solution Dynamic Media. Certaines modifications nécessitent des efforts lors de la mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avant la mise à niveau vers la version 6.5**

* [Configurations personnalisées du codage vidéo adaptatif](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configuration du cloud Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configuration du service cloud Dynamic Media (version hybride de DM)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - Configuration du service cloud YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Divers](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Avant la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Configurations personnalisées du codage vidéo adaptatif  {#custom-adaptive-video-encoding-configurations}

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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Vous pouvez exécuter le script de migration suivant pour migrer vers le nouvel emplacement :</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Vous pouvez également modifier la configuration dans AEM interface utilisateur et les modifications seront enregistrées au nouvel emplacement.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configuration du cloud Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Le client peut exécuter un script de migration à cet emplacement :<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Redémarrez le lot OSGi Dynamic Media.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>S/O</td> 
  </tr>
 </tbody>
</table>

### Configuration du service cloud Dynamic Media (version hybride de DM) {#cloudserviceconfiguration}

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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Vous pouvez exécuter le script de migration suivant pour vous aligner sur le modèle le plus récent :</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - Configuration du service cloud YouTube  {#youtubecloudserviceconfiguration}

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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>1. Dépubliez toutes les vidéos de YouTube.<br /> 2. Créez la configuration YouTube à l’aide de la nouvelle TouchUI (à partir de <code>/conf</code>), y compris en copiant toutes les chaînes de l’ancien emplacement.<br /> 3. Publiez toutes les vidéos sur YouTube.</p> <p>Ce workflow génère de nouvelles URL YouTube. Si vous n’annulez pas la publication avant de créer une nouvelle configuration de YouTube TouchUI, plusieurs URL YouTube sont répertoriées sous Propriétés, car les canaux recréés publient à nouveau, si l’occasion vous en est donnée. Cela signifie que vous disposez d’URL inutiles répertoriées sous Propriétés.</p> </td> 
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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Le client peut exécuter le script de migration ci-dessous.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Vous pouvez également modifier la configuration dans AEM interface utilisateur et les modifications seront enregistrées au nouvel emplacement.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>S/O</td> 
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
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Le client peut exécuter le script de migration ci-dessous.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>S/O</td> 
  </tr>
 </tbody>
</table>
