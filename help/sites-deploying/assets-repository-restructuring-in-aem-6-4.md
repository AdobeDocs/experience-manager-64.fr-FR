---
title: Restructuration des référentiels d’Assets dans AEM 6.4
seo-title: Assets Repository Restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Assets.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Assets.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
feature: Upgrading
exl-id: 3d5bbf95-bd1e-453b-b487-517a56fe727f
source-git-commit: cda63b9ece88d8172fa4d9817e315c9cff88c224
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 52%

---

# Restructuration des référentiels d’Assets dans AEM 6.4{#assets-repository-restructuring-in-aem}

Comme décrit sur le parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md) , les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications de référentiel ayant un impact sur la solution AEM Assets. Certaines modifications demandent du travail lors du processus de mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avec la mise à niveau vers la version 6.4**

* [Divers](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc)

**Avant de procéder à la mise à niveau vers la version 6.5**

* [Modèle de notification par e-mail d’événement de ressource/collection](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#asset-collection-event-e-mail-notification-template)
* [Conceptions classiques de partage de ressources](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#classic-asset-share-designs)
* [Modèle de notification par e-mail de téléchargement de ressource](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#download-asset-e-mail-notification-template)
* [Exemple de licences DRM](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#example-drm-licenses)

* [Modèle de notification par e-mail de lien de partage](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#link-share-e-mail-notification-template)
* [Scripts de workflow InDesign](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#indesign-workflow-scripts)
* [Configurations de transcodage vidéo](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#video-transcoding-configurations)
* [Divers](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc2)

## Avec la mise à niveau vers la version 6.4 {#with-upgrade}

### Divers {#misc}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td>/etc/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td>/var/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Si du code personnalisé dépend de cet emplacement (par exemple, le code repose explicitement sur ce chemin), il doit être mis à jour pour utiliser le nouvel emplacement avant de procéder à la mise à niveau. Idéalement, les API Java sont utilisées lorsqu’elles sont disponibles pour limiter les dépendances sur un chemin spécifique dans JCR.</p> <p>Emplacement temporaire pour contenir le fichier zip à télécharger par le client. Il n’est pas nécessaire d’effectuer une mise à jour, car lorsque le client demande de télécharger la ressource, il génère un fichier au nouvel emplacement.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr> 
 </tbody> 
</table>

## Avant de procéder à la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Modèle de notification par e-mail d’événement de ressource/collection {#asset-collection-event-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/notification/email/default</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Si les modèles d’e-mail ont été modifiés par le client, effectuez les actions suivantes afin de vous aligner sur la nouvelle structure de référentiel :</p> 
    <ol> 
     <li>Le <code>/libs/settings/dam/notification</code> Le modèle de courrier électronique doit être copié à partir de <strong><code>/etc/notification/email/default</code></strong> to <strong><code>/apps/settings/notification/email/default</code></strong> 
      <ol> 
       <li>Parce que la destination se trouve dans<strong> <code>/apps</code></strong> cette modification doit être conservée dans SCM.</li> 
      </ol> </li> 
     <li>Supprimez le dossier : <strong><code>/etc/dam/notification/email/default</code></strong> une fois les modèles d’email qu’il contient déplacés.<br /> 
      <ol> 
       <li>Si aucune mise à jour n’a été apportée au modèle d’e-mail sous<strong> <code>/etc/notification/email/default</code></strong>, le dossier peut être supprimé, car le modèle de courrier électronique d’origine existe sous <strong><code>/libs/settings/notification/email/default</code></strong> dans le cadre de l’installation d’AEM 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Conceptions classiques de partage de ressources {#classic-asset-share-designs}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/designs/assetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Pour les conceptions gérées dans SCM et qui ne sont pas écrites au moment de l’exécution via les boîtes de dialogue de conception, effectuez les actions suivantes pour vous aligner sur le dernier modèle :</p> 
    <ol> 
     <li>Copiez les conceptions de l’emplacement précédent vers le nouvel emplacement sous <code>/apps</code>.</li> 
     <li>Convertissez les ressources statiques, CSS et JavaScript dans la conception en une <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">bibliothèque cliente</a> avec <code>allowProxy = true</code>.</li> 
     <li>Mettez à jour les références à l’emplacement précédent dans la propriété <code>cq:designPath</code> via <strong>AEM &gt; Administrateur DAM &gt; Page de partage des actifs &gt; Propriétés de la page &gt; Onglet avancé &gt; Champ de conception</strong>.</li> 
     <li>Mettez à jour les pages faisant référence à l’emplacement précédent pour utiliser la nouvelle catégorie de bibliothèque cliente. Cela nécessite la mise à jour du code d’implémentation de la page.</li> 
     <li>Mettez à jour les règles de Dispatcher pour autoriser le service des bibliothèques clientes via le <code>/etc.clientlibs/</code> servlet proxy.</li> 
    </ol> <p>Pour les conceptions qui ne sont pas gérées dans SCM et modifiées au moment de l’exécution via les boîtes de dialogue de conception, ne déplacez pas les conceptions activées par l’auteur en-dehors de <code>/etc</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Modèle de notification par e-mail de téléchargement de ressource {#download-asset-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Si les modèles d’e-mail (<strong>downloadasset</strong><strong> ou transientworkflowcompleted</strong>) ont été modifiés, suivez la procédure ci-dessous pour vous aligner sur la nouvelle structure :</p> 
    <ol> 
     <li>Le modèle de courrier électronique mis à jour doit être copié à partir de <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> to <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong> 
      <ol> 
       <li>Parce que la destination se trouve dans<strong> <code>/apps</code></strong> cette modification doit être conservée dans SCM.</li> 
      </ol> </li> 
     <li>Supprimez le dossier : <code>/etc/dam/workflow/notification/email/downloadasset </code>une fois les modèles d’email qu’il contient déplacés.<br /> 
      <ol> 
       <li>Si aucune mise à jour n’a été apportée au modèle d’e-mail sous<strong> <code>/etc</code></strong>, le dossier peut être supprimé, car le modèle de courrier électronique d’origine existe sous <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> dans le cadre de l’installation d’AEM 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>while <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> est techniquement pris en charge pour la recherche (est prioritaire avant /apps via la recherche habituelle Sling CAConfig, mais après <code>/etc</code>) le modèle peut être placé dans <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Cependant, cela n’est pas recommandé car il n’y a pas d’IU d’exécution pour faciliter la modification du modèle d’e-mail.</td> 
  </tr> 
 </tbody> 
</table>

### Exemple de licences DRM {#example-drm-licenses}

| **Emplacement précédent** | `/etc/dam/drm/licenses/` |
|---|---|
| **Nouveaux emplacements** | `/libs/settings/dam/drm` |
| **Conseil de restructuration** | N/A |
| **Remarques** | N/A |

### Modèle de notification par e-mail de lien de partage {#link-share-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/adhocassetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Si le modèle d’e-mail a été modifié par le client, alignez-le sur la nouvelle structure de référentiel :</p> 
    <ol> 
     <li>Le modèle de courrier électronique mis à jour doit être copié à partir de <strong><code>/etc/dam/adhocassetshare</code></strong> to <strong><code>/apps/settings/dam/adhocassetshare</code></strong> 
      <ol> 
       <li>Parce que la destination se trouve dans<strong> <code>/apps</code></strong> cette modification doit être conservée dans SCM.</li> 
      </ol> </li> 
     <li>Supprimez le dossier : <strong><code>/etc/dam/adhocassetshare</code></strong> une fois les modèles d’email qu’il contient déplacés.<br /> 
      <ol> 
       <li>Si aucune mise à jour n’a été apportée au modèle d’e-mail sous<strong> <code>/etc</code></strong>, le dossier peut être supprimé, car le modèle de courrier électronique d’origine existe sous <strong><code>/libs/settings/dam/adhocassetshare</code></strong> dans le cadre de l’installation d’AEM 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>while <code>/conf/global/settings/dam/adhocassetshare</code> est techniquement pris en charge pour la recherche (elle est prioritaire avant <code>/apps</code> via la recherche habituelle Sling CAConfig, mais après <code>/etc</code>), le modèle peut être placé dans <code>/conf/global/settings/dam/adhocassetshare</code>. Cependant, cela n’est pas recommandé car il n’y a pas d’IU d’exécution pour faciliter la modification du modèle d’e-mail.</td> 
  </tr> 
 </tbody> 
</table>

### Scripts de workflow InDesign {#indesign-workflow-scripts}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/indesign/scripts</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Pour s’aligner sur la nouvelle structure de référentiel :</p> 
    <ol> 
     <li>Copie de tous les scripts personnalisés ou modifiés depuis <strong><code>/etc/dam/indesign/scripts</code></strong> to <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br /> 
      <ol> 
       <li>Seuls les scripts nouveaux ou modifiés copiés comme scripts non modifiés fournis par AEM seront disponibles via <strong><code>/libs/settings</code></strong> dans AEM 6.4</li> 
      </ol> </li> 
     <li>Recherchez tous les modèles de workflow qui utilisent l’étape de workflow Processus d’extraction de médias et 
      <ol> 
       <li>Pour chaque instance de l’étape de processus, mettez à jour les chemins dans la configuration afin qu’ils pointent explicitement vers les scripts appropriés sous<strong> <code>/apps/settings/dam/indesign/scripts</code></strong> ou <strong><code>/libs/settings/dam/indesign/scripts</code></strong> selon les besoins.</li> 
      </ol> </li> 
     <li>Supprimer<strong> <code>/etc/dam/indesign/scripts</code></strong> entièrement.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>Il est recommandé de stocker les scripts personnalisés sous <code>/apps</code>, puisqu’il s’agit de l’emplacement où le code doit être stocké.</td> 
  </tr> 
 </tbody> 
</table>

### Configurations de transcodage vidéo {#video-transcoding-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/video</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Les personnalisations au niveau du projet doivent être coupées et collées sous l’équivalent <code>/apps</code> ou <code>/conf</code> chemins d’accès, le cas échéant.</p> <p>Pour vous aligner sur la structure de référentiel AEM 6.4 :</p> 
    <ol> 
     <li>Copiez toutes les configurations vidéo modifiées depuis <code>/etc/dam/video</code> to <code>/apps/settings/dam/video</code></li> 
     <li>Remove <code>/etc/dam/video</code></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr> 
 </tbody> 
</table>

### Configurations des paramètres prédéfinis de la visionneuse {#viewer-preset-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/dam/presets/viewer</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Les paramètres prédéfinis prêts à l’emploi de la visionneuse ne seront disponibles que dans le nouvel emplacement.</p> <p>Pour les paramètres prédéfinis personnalisés de la visionneuse :</p> 
    <ul> 
     <li>vous devez exécuter un script de migration pour déplacer le noeud à partir de <code>/etc</code> to <code>/conf</code>. Le script se trouve à l’adresse <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>ou vous pouvez modifier la configuration pour qu’ils soient enregistrés automatiquement au nouvel emplacement.</li> 
    </ul> <p>Notez que vous n’avez pas à ajuster leur code copyURL/embed pour qu’il pointe vers <code>/conf</code>. La requête existante vers <code>/etc</code> sera redirigé vers le contenu correct à partir de <code>/conf</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A</td> 
  </tr> 
 </tbody> 
</table>

### Divers {#misc2}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/dam/clientlibs</code></td> 
  </tr> 
  <tr> 
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Ajustez les références pour qu’elles pointent vers les nouvelles ressources sous <code>/libs</code> en utilisant la variable <code>/etc.clientlibs/</code> préfixe proxy allow.</p> <p>Enfin, effectuez un nettoyage en supprimant les dossiers des bibliothèques clientes migrées depuis <code>/etc/clientlibs/foundation/</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr> 
 </tbody> 
</table>
