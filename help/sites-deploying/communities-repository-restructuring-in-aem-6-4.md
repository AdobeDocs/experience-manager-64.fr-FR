---
title: Restructuration des référentiels pour AEM Communities dans la version 6.4
seo-title: Repository Restructuring for AEM Communities in 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Communities.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Communities.
uuid: d161655f-4074-44a7-8d69-38e80934c58b
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 7383265b-0ed4-4ea7-b741-0a417d187bdd
feature: Upgrading
exl-id: f66e349f-09a1-47f1-88fc-61eb51f65664
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 62%

---

# Restructuration des référentiels pour AEM Communities dans la version 6.4{#repository-restructuring-for-aem-communities-in}

Comme décrit sur le parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md) , les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications de référentiel ayant un impact sur la solution AEM Communities. Certaines modifications demandent du travail lors du processus de mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avec la mise à niveau vers la version 6.4**

* [Modèles de notification par e-mail](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#e-mail-notification-templates)
* [Configurations des abonnements](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#subscription-configurations)

**Avant de procéder à la mise à niveau vers la version 6.5**

* [Configurations des badges](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#badging-configurations)
* [Conceptions des consoles des communautés classiques](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#classic-communities-console-designs)
* [Configurations des connexions au réseau social Facebook](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#facebook-social-login-configurations)
* [Configurations des options linguistiques](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#language-options-configurations)

* [Configurations des connexions au réseau social Pinterest](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#pinterest-social-login-configurations)
* [Configurations des scores](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#scoring-configurations)
* [Configurations des connexions au réseau social Twitter](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#twitter-social-login-configurations)
* [Divers](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md#misc)

## Avec la mise à niveau vers la version 6.4 {#with-upgrade}

### Modèles de notification par e-mail {#e-mail-notification-templates}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/community/notifications</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/community/notifications</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Une migration manuelle est nécessaire si vous souhaitez passer à un nouveau chemin sous "<code>/apps/settings</code>". Vous pouvez utiliser le Gestionnaire de configuration Granite pour effectuer la migration.</p> <p>Vous pouvez effectuer la migration en définissant la propriété . <code>mergeList</code> to <code>true</code> sur le<code>/libs/settings/community/subscriptions</code>" et ajoutez une <code>nt:unstructured</code> noeud enfant.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des abonnements {#subscription-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/community/subscriptions</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/community/subscriptions</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Une migration manuelle est nécessaire si vous souhaitez passer à un nouveau chemin sous "<code>/apps/settings</code>". Vous pouvez utiliser le Gestionnaire de configuration Granite pour effectuer la migration.</p> <p>Vous pouvez effectuer la migration en définissant la propriété . <code>mergeList</code> to <code>true</code> sur le<code>/libs/settings/community/subscriptions</code>" et ajoutez une <code>nt:unstructured</code> noeud enfant.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des mots-clés {#watchwords-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td>/etc/watchwords</td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td>/libs/community/watchwords</td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td>Une tâche de migration différée est disponible pour nettoyer les configurations de Communities.<br /> <p>La tâche déplace les mots-clés depuis <code>/etc/watchwords</code> to <code>/conf/global/settings/community/watchwords</code>.</p> <p>Si des mots-clés personnalisés sont stockés dans SCM, ils doivent être déployés sur <code>/apps/settings/...</code> et vous devez vous assurer qu’il n’y a pas de recouvrement <code>/conf/global/settings/...</code> qui aurait la priorité.</p> <p>Suppression de la tâche de migration <code>/etc</code> emplacements.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

## Avant de procéder à la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Configurations des badges {#badging-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/community/badging</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><strong>Règles de badge :</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Images de badge :</strong></p> <p>Pour les images par défaut : <code>/etc/community/badging/images are moved to /libs/community/badging/images</code></p> <p>Pour les images personnalisées : <code>/content/community/badging/images</code></p> <p> </p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Une migration manuelle est requise.</p> <p>Si votre instance a personnalisé les règles de badge/score, aucune méthode automatisée ne permet de placer toutes les règles dans un compartiment. Vous avez besoin d’informations de la part du client pour savoir quel compartiment de configuration (global ou spécifique à un site) vous souhaitez utiliser pour votre site.</p> <p>Aucune interface utilisateur n’est disponible pour configurer les badges et les scores d’un site.</p> <p>Pour vous aligner sur la nouvelle structure de référentiel :</p> 
    <ol> 
     <li>Créez un compartiment contextuel de site à l’aide de l’<strong>explorateur de configuration</strong> sous <strong>Outils</strong></li> 
     <li>Accédez à la racine du site</li> 
     <li>Définissez <code>cq:confproperty</code> sur le chemin du compartiment où vous souhaitez stocker tous vos paramètres. Le même résultat peut être obtenu par le biais de l’<strong>assistant de modification - Définir l’entrée de configuration du cloud</strong>.</li> 
     <li>Déplacer les règles de badge et de notation appropriées à partir de <code>/etc/community/*</code> dans le compartiment contextuel du site créé à l’étape précédente.</li> 
     <li>Ajustez les propriétés des règles de badge et de score à la racine du site pour avoir des références relatives aux nouveaux emplacements de règles. 
      <ol> 
       <li>Par exemple, si la propriété de <code>cq:conf = /conf/we-retail</code>, puis <code>badgingRules [] = community/badging/rules</code> si les règles sont maintenant déplacées vers ce nouveau compartiment.</li> 
      </ol> </li> 
     <li>De même, ajustez les références aux règles de score dans un nœud de règle de badge pour obtenir un chemin relatif.</li> 
    </ol> <p> </p> <p>Enfin, effectuez un nettoyage en supprimant la ressource. <code>/etc/community/badging</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Conceptions des consoles des communautés classiques {#classic-communities-console-designs}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/designs/social/console</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/social/console</code></p> <p><code>/apps/settings/wcm/designs/social/console</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td>N/A</td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des connexions au réseau social Facebook {#facebook-social-login-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/facebookconnect</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code class="code">/conf/global/settings/cloudconfigs/facebookconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p> </p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Toute nouvelle configuration de cloud Facebook doit faire l’objet d’une migration vers le nouvel emplacement.</p> 
    <ol> 
     <li>Migrez les configurations existantes de l’emplacement précédent vers le nouvel emplacement.
      <ol> 
       <li>Recréez manuellement les nouvelles configurations des connexions au réseau social Facebook via l’interface utilisateur de création AEM dans <strong>Outils &gt; Services cloud &gt; Configuration de la connexion au réseau social Facebook</strong>.<br /> ou <br /> </li> 
       <li>Copiez les nouvelles configurations de cloud Facebook de l’emplacement précédent vers le nouvel emplacement approprié, sous <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li> 
      </ol> </li> 
     <li>Mettez à jour toute racine de site AEM Communities pour faire référence à la nouvelle configuration de connexion au réseau social Facebook en définissant la variable <code>[cq:Page]/jcr:content@cq:conf</code> vers le chemin d’accès absolu dans le nouvel emplacement.</li> 
     <li>Dissociez l’ancien service de cloud Facebook Connect Cloud des racines de site AEM Communities mises à jour pour faire référence au nouvel emplacement.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des options linguistiques {#language-options-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/social/config/languageOpts</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/social/translation/languageOpts</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des connexions au réseau social Pinterest {#pinterest-social-login-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/pinterestconnect</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code class="code">/conf/global/settings/cloudconfigs/pinterestconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> <p> </p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Toute nouvelle configuration de cloud Pinterest doit faire l’objet d’une migration vers le nouvel emplacement.</p> 
    <ol> 
     <li>Migrez les configurations existantes de l’emplacement précédent vers le nouvel emplacement.
      <ol> 
       <li>Recréez manuellement les nouvelles configurations des connexions au réseau social Pinterest via l’interface utilisateur de création AEM dans <strong> Outils &gt; Services cloud &gt; Configuration de la connexion au réseau social Pinterest</strong>.<br /> ou</li> 
       <li>Copiez les nouvelles configurations de cloud Pinterest de l’emplacement précédent vers le nouvel emplacement approprié sous <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li> 
      </ol> </li> 
     <li>Mettez à jour toute racine de site AEM Communities pour faire référence à la nouvelle configuration de connexion au réseau social Pinterest en définissant la variable <code>[cq:Page]/jcr:content@cq:conf</code> vers le chemin d’accès absolu dans le nouvel emplacement.</li> 
     <li>Dissociez l’ancien service de cloud Pinterest Connect Cloud des racines de site AEM Communities mises à jour pour faire référence au nouvel emplacement.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des scores {#scoring-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/community/scoring</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/community/scoring</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Pour s’aligner sur la nouvelle structure de référentiel, les règles de notation peuvent être stockées dans <code>/apps/settings/</code> ou /<code>conf/.../settings</code></p> 
    <ol> 
     <li>Pour <code>/apps/settings</code>, cela agit comme des règles globales ou par défaut gérées dans SCM.</li> 
    </ol> <p>Création de configurations contextuelles dans <code>/conf/</code> en utilisant CRXDELite :</p> 
    <ol> 
     <li>Créez les configurations dans la <code>/conf/.../settings</code> location<br /> </li> 
     <li>Le site des communautés doit avoir la variable <code>cq:conf </code>ensemble de propriétés.
      <ol> 
       <li>Si non <code>cq:conf</code> est définie, les règles de notation sont directement lues à partir du chemin d’accès donné pour la propriété "".<code>scoringRules</code>" sur le noeud racine du site, par exemple : <code>/content/we-retail/us/en/community/jcr:content</code></li> 
      </ol> </li> 
    </ol> <p>Nettoyage : Supprimer la ressource <code>/etc/community/scoring</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurations des connexions au réseau social Twitter {#twitter-social-login-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><code>/etc/cloudservices/twitterconnect</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code class="code">/conf/global/settings/cloudconfigs/twitterconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p> </p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Toute nouvelle configuration de cloud Twitter doit faire l’objet d’une migration vers le nouvel emplacement.</p> 
    <ol> 
     <li>Migrez les configurations existantes de l’emplacement précédent vers le nouvel emplacement.
      <ol> 
       <li>Recréez manuellement les nouvelles configurations des connexions au réseau social Twitter via l’interface utilisateur de création d’AEM sous <strong> Outils &gt; Services cloud &gt; Configuration de la connexion au réseau social Twitter</strong>.<br /> ou <br /> </li> 
       <li>Copiez les nouvelles configurations de cloud Twitter de l’emplacement précédent vers le nouvel emplacement approprié, sous <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li> 
      </ol> </li> 
     <li>Mettez à jour toute racine de site AEM Communities pour faire référence à la nouvelle configuration de connexion au réseau social Twitter en définissant la variable <code>[cq:Page]/jcr:content@cq:conf</code> vers le chemin d’accès absolu dans le nouvel emplacement.</li> 
     <li>Dissociez l’ancien service de cloud Twitter Connect Cloud des racines du site AEM Communities mises à jour pour faire référence au nouvel emplacement.</li> 
    </ol> </td> 
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
   <td><code>/etc/community/templates</code></td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><code>/libs/settings/community/templates</code></td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Adobe a fourni un utilitaire de migration à l’adresse suivante :</p> <p><a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration">https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration</a></p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>Les modèles personnalisés existants sont déplacés vers <code>/conf/global/settings/community/template/&lt;groups/sites/functions&gt;</code></td> 
  </tr>
 </tbody>
</table>
