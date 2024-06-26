---
title: Restructuration des référentiels dans AEM 6.4
seo-title: Sites Repository Restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Sites.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Sites.
uuid: 6dc5f8bd-1680-40af-9b8f-26c1f4bc3304
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 3eccb2d5-c325-43a6-9c03-5f93f7e30712
feature: Upgrading
exl-id: d0cdb15d-196a-44e3-bd98-91588b6979ab
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 70%

---

# Restructuration des référentiels dans AEM 6.4{#sites-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Comme indiqué dans la page parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md), les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications des référentiels ayant un impact sur la solution AEM Sites. Certaines modifications nécessitent des efforts lors de la mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avec la mise à niveau vers la version 6.4**

* [Segments ContextHub](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#contexthub-segments)

**Avant la mise à niveau vers la version 6.5**

* [Bibliothèques clientes Adobe Analytics](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#adobe-analytics-client-libraries)
* [De Microsoft Word classique à la conception de pages web](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#classic-microsoft-word-to-web-page-designs)
* [Configurations de l’émulateur d’appareil mobile](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#mobile-device-emulator-configurations)
* [Configurations de plans directeurs de Multi-site Manager](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#multi-site-manager-blueprint-configurations)
* [Configurations du déploiement de Multi-site Manager](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#multi-site-manager-rollout-configurations)
* [Modèle d’e-mail de notification d’événement de page](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#page-event-notification-e-mail-template)
* [Génération de modèles automatique de pages](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#page-scaffolding)
* [Grille réactive LESS](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#responsive-grid-less)
* [Conceptions de modèles statiques](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#static-template-designs)
* [Bibliothèques clientes d’intégration d’Adobe Target](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#adobe-target-integration-client-libraries)
* [Bibliothèques clientes de gestion de contenu web de base](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#wcm-foundation-client-libraries)

## Avec la mise à niveau vers la version 6.4 {#with-upgrade}

### Segments ContextHub {#contexthub-segments}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/segmentation/contexthub</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/apps/settings/wcm/segments</code> </p> <p><code>/conf/settings/settings/wcm/segments</code> </p> <p><code>/conf/&lt;tenant&gt;/settings/wcm/segments</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Si des segments ContextHub nouveaux ou modifiés doivent être changés dans le contrôle de source plutôt que dans AEM, ils doivent être migrés vers le nouvel emplacement :</p> 
    <ol> 
     <li>Copiez les segments ContextHub nouveaux ou modifiés depuis l’emplacement précédent vers le nouvel emplacement approprié (/<code>apps</code>, <code>/conf/global</code> ou <code>/conf/&lt;tenant&gt;</code>).</li> 
     <li>Mettez à jour les références aux segments ContextHub de l’emplacement précédent vers les segments ContextHub migrés dans les nouveaux emplacements client (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li> 
    </ol> <p>La requête QueryBuilder ci-dessous recherche toutes les références aux segments ContextHub dans les emplacements précédents.<br /> <br /> <code class="code">path=/content
       property=cq:segments
       property.operation=like
       property.value=/etc/segmentation/contexthub/%</code><br /> <br /> Elle peut être exécutée dans l’<a href="/help/sites-developing/querybuilder-api.md" target="_blank">interface utilisateur du débogueur QueryBuilder AEM</a>. Notez qu’il s’agit d’une requête transversale. Par conséquent, ne l’exécutez pas en exploitation et vérifiez que les limites de traversée sont ajustées en fonction des besoins.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>Les segments ContextHub persistants à l’emplacement précédent s’affichent en lecture seule dans <strong>AEM &gt; Personnalisation &gt; Audiences</strong>.</p> <p>Si les segments ContextHub doivent être modifiables dans AEM, ils doivent être migrés vers le nouvel emplacement (<code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>). Tous les nouveaux segments ContentHub créés dans AEM sont persistants dans le nouvel emplacement (<code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>).</p> <p>Les propriétés de la page AEM Sites permettent uniquement la sélection de l’emplacement précédent (<code>/etc</code>) ou d’un nouvel emplacement unique (<code>/apps</code>, <code>/conf/global</code> or <code>/conf/&lt;tenant&gt;</code>). Les segments de ContextHub doivent donc être migrés en conséquence.</p> <p>Les segments ContextHub inutilisés des sites de référence d’AEM peuvent être supprimés et ne pas être migrés vers le nouvel emplacement :</p> 
    <ul> 
     <li>/etc/segmentation/geometrixx/</li> 
     <li>/etc/segmentation/geometrixx-outdoors</li> 
    </ul> <p>Remarque : Si ClientContext est en cours d’utilisation, il est recommandé de le convertir en ContextHub.</p> </td> 
  </tr>
 </tbody>
</table>

## Avant la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Bibliothèques clientes Adobe Analytics {#adobe-analytics-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/sitecatalyst</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Toute utilisation personnalisée de ces bibliothèques clientes doit faire référence à la bibliothèque cliente par catégorie, et non par chemin d’accès :</p> 
    <ol> 
     <li>Toute référence à la bibliothèque cliente par chemin d’accès à l’emplacement précédent doit être mise à jour pour utiliser <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM framework de référence de bibliothèque cliente</a>.</li> 
     <li>Si AEM framework de référencement de bibliothèque cliente ne peut pas être utilisé, le chemin absolu des bibliothèques clientes peut être référencé via AEM servlet proxy de bibliothèque cliente.
      <ul> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/appmeasurement.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/plugins.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/tracking.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/util.js</code></li> 
      </ul> </li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>La modification de ces bibliothèques clientes n’a jamais été prise en charge.</p> <p>Pour obtenir les catégories des bibliothèques clientes, accédez à chaque nœud <code>cq:ClientLIbraryFolder</code> via CRXDELite et inspectez la propriété des catégories.</p> 
    <ul> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/appmeasurement</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/plugins</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/tracking</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/util</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### De Microsoft Word classique à la conception de pages web {#classic-microsoft-word-to-web-page-designs}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/designs/wordDesign</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/wordDesign</code></p> <p><code>/apps/settings/wcm/designs/wordDesign</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Pour les conceptions gérées dans SCM et qui ne sont pas écrites au moment de l’exécution via les boîtes de dialogue de conception.</p> 
    <ol> 
     <li>Copiez les conceptions de l’emplacement précédent dans le nouvel emplacement (<code>/apps</code>).</li> 
     <li>Convertissez les ressources statiques, CSS et JavaScript dans la conception en <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">bibliothèque cliente</a> avec <code>allowProxy = true</code>.</li> 
     <li>Mettez à jour les références à l’emplacement précédent dans la propriété cq:designPath .</li> 
     <li>Mettez à jour les pages faisant référence à l’emplacement précédent pour utiliser la nouvelle catégorie de bibliothèque cliente (cela nécessite la mise à jour du code d’implémentation de la page).</li> 
     <li>Mettez à jour les règles du Dispatcher AEM pour autoriser le service des bibliothèques clientes via la servlet proxy <code>/etc.clientlibs/</code>.</li> 
    </ol> <p>Pour les conceptions NON gérées dans SCM et modifiées au moment de l’exécution via les boîtes de dialogue de conception :</p> 
    <ul> 
     <li>Ne déplacez pas les conceptions activées par l’auteur en dehors de <code>/etc</code>.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations de l’émulateur d’appareil mobile {#mobile-device-emulator-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/mobile</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/mobile</code></p> <p><code>/apps/settings/mobile</code></p> <p><code>/conf/global/settings/mobile</code></p> <p><code>/conf/&lt;tenant&gt;/settings/mobile</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td>Toute nouvelle configuration d’émulateur d’appareil mobile doit être migrée vers le nouvel emplacement.
    <ol> 
     <li>Copiez les nouvelles configurations d’émulateur d’appareil mobile de l’emplacement précédent vers le nouvel emplacement (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li> 
     <li>Pour toutes les pages AEM Sites qui dépendent de ces configurations d’émulateur d’appareil mobile, mettez à jour le nœud de la page <span class="code">
       <code>
        jcr
       </code>
       <code>
        :content
       </code></span> : <br /> <span class="code">[cq:Page]/jcr:content@cq:
       <code>
        deviceGroups
       </code> = String[ mobile/groups/responsive ]</span></li> 
     <li>Pour les modèles modifiables qui dépendent de ces configurations d’émulateur d’appareil mobile, mettez-les à jour, en faisant pointer <span class="code">
       <code>
        cq
       </code> :
       <code>
        deviceGroups
       </code></span> sur le nouvel emplacement.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>La résolution des configurations d’émulateur d’appareil mobile se produit dans l’ordre suivant :</p> 
    <ol> 
     <li><code>/conf/&lt;tenant&gt;/settings/mobile</code></li> 
     <li><code>/conf/global/settings/mobile</code></li> 
     <li><code>/apps/settings/mobile</code></li> 
     <li><code>/libs/settings/mobile</code></li> 
     <li><code>/etc/mobile</code></li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### Configurations de plans directeurs de Multi-site Manager {#multi-site-manager-blueprint-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/blueprints</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/apps/msm</code> (configurations de plans directeurs clientes)</p> <p><code>/libs/msm</code> (configurations de plans directeurs prêtes à l’emploi pour Screens, Commerce)</p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Les configurations de plans directeurs de Multi-site Manager nouvelles ou modifiées doivent être migrées vers le nouvel emplacement (<code>/apps</code>).</p> 
    <ol> 
     <li>Copiez les configurations de plans directeurs de Multi-site Manager nouvelles ou modifiées de l’emplacement précédent vers le nouvel emplacement (<code>/apps</code>).</li> 
     <li>Supprimez les configurations de plans directeurs de Multi-site Manager migrées de l’emplacement précédent.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>Toutes les configurations de plans directeurs de Multi-site Manager fournies par AEM existent dans le nouvel emplacement de <code>/libs</code>.</p> <p>Le contenu ne fait pas référence aux configurations bleues de Multi-site Manager. Il n’existe donc pas de références de contenu à ajuster.</p> </td> 
  </tr>
 </tbody>
</table>

### Configurations du déploiement de Multi-site Manager {#multi-site-manager-rollout-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/msm/rolloutConfigs</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/msm/wcm/rolloutconfigs</code></p> <p><code>/apps/msm/wcm/rolloutconfigs</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Toute configuration de déploiement de Multi-site Manager nouvelle ou modifiée doit être migrée vers le nouvel emplacement.</p> 
    <ol> 
     <li>Copiez les configurations de déploiement de Multi-site Manager nouvelles ou modifiées de l’emplacement précédent vers le nouvel emplacement (<code>/apps</code>).</li> 
     <li>Mettez à jour toutes les références sur les pages AEM vers les configurations de déploiement de Multi-site Manager de l’emplacement précédent, afin qu’elles pointent vers leurs homologues dans les nouveaux emplacements (<code>/libs</code> ou <code>/apps</code>).</li> 
    </ol> <p>Supprimez les configurations de déploiement de Multi-site Manager migrées de l’emplacement précédent.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>Si vous ne supprimez pas les configurations de déploiement multi-site Manager migrées de l’emplacement précédent, des options de déploiement en double s’affichent pour les auteurs AEM.</td> 
  </tr>
 </tbody>
</table>

### Modèle d’e-mail de notification d’événement de page {#page-event-notification-e-mail-template}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Les seuls nouveaux modèles d’e-mail de notification d’événement de page pris en charge sont la prise en charge de nouveaux paramètres régionaux.</p> <p>La résolution du modèle d’e-mail d’événement de page s’effectue dans l’ordre suivant :</p> 
    <ol> 
     <li><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></li> 
     <li><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></li> 
     <li><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>Tout modèle d’e-mail de notification d’événement de page nouveau ou modifié doit être migré vers le nouvel emplacement sous <code>/apps</code> :</p> 
    <ol> 
     <li>Copiez les modèles d’e-mail de notification d’événement de page nouveaux ou modifiés de l’emplacement précédent vers le nouvel emplacement (<code>/apps</code>).</li> 
     <li>Supprimez les modèles d’e-mail de notification d’événement de page migrés de l’emplacement précédent.</li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### Génération de modèles automatique de pages {#page-scaffolding}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/scaffolding</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><span class="code">/libs/settings/
      <code>
       wcm
      </code>/template-types/scaffolding/scaffolding</span></p> <p><span class="code">/apps/settings/
      <code>
       wcm
      </code>/template-types/scaffolding/scaffolding</span></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td>Les structures créées à l’emplacement précédent utilisent l’infrastructure existante et ne peuvent pas être migrées vers le nouvel emplacement. Pour s’aligner sur le nouvel emplacement, tout modèle de génération de modèles automatique hérité doit être redéveloppé à l’aide de la structure de génération de modèles automatique prise en charge.</td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Grille réactive LESS {#responsive-grid-less}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Toutes les références à l’emplacement précédent dans les fichiers LESS personnalisés doivent être mises à jour pour être importées à partir du nouvel emplacement.</p> 
    <ul> 
     <li>Mettez à jour tous les fichiers LESS personnalisés référençant grid_base.less dans l’emplacement précédent pour référencer le nouvel emplacement.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>Si vous référencez un fichier <code>grid_base.less</code> qui n’existe pas, le mode Mise en page de l’éditeur de pages et de modèles ne fonctionne pas et la mise en page est perturbée.</td> 
  </tr>
 </tbody>
</table>

### Conceptions de modèles statiques {#static-template-designs}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/designs/&lt;custom-site&gt;</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/apps/settings/wcm/designs/&lt;custom-site&gt;</code></td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Pour les conceptions gérées dans SCM et qui ne sont pas écrites au moment de l’exécution via les boîtes de dialogue de conception.</p> 
    <ol> 
     <li>Copiez les conceptions de l’emplacement précédent dans le nouvel emplacement (<code>/apps</code>).</li> 
     <li>Convertissez les ressources statiques, CSS et JavaScript dans la conception en <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">bibliothèque cliente</a> avec <code>allowProxy = true</code>.</li> 
     <li>Mettez à jour les références à l’emplacement précédent dans la propriété <code>cq:designPath</code> via <strong>AEM &gt; Sites &gt; Pages de site personnalisées &gt; Propriétés de page &gt; Onglet avancé &gt; Champ de conception</strong>.</li> 
     <li>Mettez à jour les pages faisant référence à l’emplacement précédent pour utiliser la nouvelle catégorie de bibliothèque cliente (cela nécessite la mise à jour du code d’implémentation de la page).</li> 
     <li>Mettez à jour les règles du Dispatcher AEM pour autoriser le service des bibliothèques clientes via la servlet proxy <code>/etc.clientlibs/</code>.</li> 
    </ol> <p>Pour les conceptions NON gérées dans SCM et modifiées au moment de l’exécution via les boîtes de dialogue de conception :</p> 
    <ul> 
     <li>Ne déplacez pas les conceptions activées par l’auteur en dehors de <code>/etc</code>.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>L’approche recommandée consiste à créer des sites et des pages AEM Sites à l’aide de modèles modifiables qui utilisent le contenu et les règles de la structure au lieu de conceptions.</td> 
  </tr>
 </tbody>
</table>

<!-- Search&Promote was end of life September 1, 2022. ### Adobe Search and Promote Integration Client Libraries {#adobe-search-and-promote-integration-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Previous location</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/searchpromote</code></p> </td> 
  </tr>
  <tr>
   <td><strong>New location(s)</strong></td> 
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td> 
  </tr>
  <tr>
   <td><strong>Restructuring guidance</strong></td> 
   <td><p>Any custom use of these Client Libraries should reference the Client Library by category, and not by path.</p> 
    <ol> 
     <li>Any references to the Client Library by path at the Previous Location should be updated to use <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM's Client Library referencing framework</a>.</li> 
     <li>If AEM's Client Library referencing framework cannot be used, the absolute path of the Client Libraries can be referenced via AEM's Client Library Proxy servlet:</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/cq/searchpromote/clientlibs/searchpromotei.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notes</strong></td> 
   <td><p>Editing of these Client Libraries was never supported.</p> <p>To obtain the Client Library categories, visit each cq:ClientLIbraryFolder node via CRXDELite and inspect the categories property:</p> 
    <ul> 
     <li><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table> -->

### Bibliothèques clientes d’intégration d’Adobe Target {#adobe-target-integration-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/target</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/cq/testandtarget/clientlibs/testandtarget</code></td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Toute utilisation personnalisée de ces bibliothèques clientes doit faire référence à la bibliothèque cliente par catégorie, et non par chemin d’accès.</p> 
    <ol> 
     <li>Toute référence à la bibliothèque cliente par chemin d’accès à l’emplacement précédent doit être mise à jour pour utiliser <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM framework de référence de bibliothèque cliente</a>.</li> 
     <li>Si AEM framework de référencement de bibliothèque cliente ne peut pas être utilisé, le chemin absolu des bibliothèques clientes peut être référencé via AEM servlet proxy de bibliothèque cliente :</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/testandtarget.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs-integration.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/init.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/mbox.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/parameters.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/util.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>La modification de ces bibliothèques clientes n’a jamais été prise en charge.</p> <p>Pour obtenir les catégories de la bibliothèque cliente, consultez chaque noeud cq:ClientLIbraryFolder via CRXDELite et examinez la propriété categories :</p> 
    <ul> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/testandtarget</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs-integration</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/init</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/mbox</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/parameters</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/util</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Bibliothèques clientes de gestion de contenu web de base {#wcm-foundation-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/clientlibs/wcm/foundation</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/wcm/foundation/clientlibs</code></td> 
  </tr>
  <tr>
   <td><strong>Conseils de restructuration</strong></td> 
   <td><p>Toute utilisation personnalisée de ces bibliothèques clientes doit faire référence à la bibliothèque cliente par catégorie, et non par chemin d’accès.</p> 
    <ol> 
     <li>Toute référence à la bibliothèque cliente par chemin d’accès à l’emplacement précédent doit être mise à jour pour utiliser <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM framework de référence de bibliothèque cliente</a>.</li> 
     <li>Si AEM framework de référencement de bibliothèque cliente ne peut pas être utilisé, le chemin absolu des bibliothèques clientes peut être référencé via AEM servlet proxy de bibliothèque cliente.</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/accessibility.css</code></li> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.css</code></li> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td><p>La modification de ces bibliothèques clientes n’a jamais été prise en charge.</p> <p>Pour obtenir les catégories des bibliothèques clientes, accédez à chaque nœud <code>cq:ClientLIbraryFolder</code> via CRXDELite et inspectez la propriété des catégories :</p> 
    <ul> 
     <li><code>/libs/wcm/foundation/clientlibs/accessibility</code></li> 
     <li><code>/libs/wcm/foundation/clientlibs/main</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>
