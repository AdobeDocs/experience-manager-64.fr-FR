---
title: Consoles Outils
seo-title: Consoles Outils
description: Découvrez les différentes consoles Outils disponibles dans AEM.
seo-description: Découvrez les différentes consoles Outils disponibles dans AEM.
uuid: d01382f8-0c8f-4d76-9271-bed9e34b3b4b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 2bf8496d-a485-4b39-a6c9-07222b66d0cd
translation-type: tm+mt
source-git-commit: e9c5fcd8f939d88317c5184b6352b227918088e5
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 96%

---


# Consoles Outils{#tools-consoles}

Les consoles **Outils** permettent d’accéder à différents outils spécialisés pour administrer des sites web, des ressources numériques et d’autres aspects du référentiel de contenu. Pour le moment, il existe deux versions de la console **Outils** selon l’interface utilisateur que vous utilisez :

* [Outils – IU classique](#tools-classic-ui)
* [Outils – IU optimisée pour les écrans tactiles](#tools-touch-optimized-ui)

## Outils – IU classique  {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Page ou dossier</th> 
   <th> </th> 
   <th>Objectif</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM Control Center</a></td> 
   <td> </td> 
   <td>Point centralisé pour gérer plusieurs sites.</td> 
  </tr> 
  <tr> 
   <td>Configurations de ClientContext<br /> </td> 
   <td> </td> 
   <td><a href="/help/sites-developing/client-context.md">ClientContext</a> représente une collection de données utilisateur assemblées dynamiquement. Les configurations de cloud par défaut et marketing sont définies ici.<br /> </td> 
  </tr> 
  <tr> 
   <td>Configuration de Cloud Services<br /> </td> 
   <td> </td> 
   <td>Contient les configurations liées à l’<a href="/help/sites-administering/marketing-cloud.md">intégration à Adobe Marketing Cloud</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">Commerce</a></td> 
   <td> </td> 
   <td>Permet d’accéder aux importateurs et aux différentes données de produit.</td> 
  </tr> 
  <tr> 
   <td>Gestion des actifs numériques : gestion des droits numériques<br /> </td> 
   <td> </td> 
   <td>Permet d’accéder aux informations sur les droits numériques et aux licences.</td> 
  </tr> 
  <tr> 
   <td>Gestion des actifs numériques : outil de vérification d’état<br /> </td> 
   <td> </td> 
   <td>Compare <code>/var/dam</code> et <code>/content/dam</code> et recherche <br /> les incohérences éventuelles. Les fichiers/dossiers répertoriés peuvent alors être synchronisés ou supprimés. Les types de nœuds pour la comparaison de dossiers peuvent être configurés dans la console web.</td> 
  </tr> 
  <tr> 
   <td>Gestion des actifs numériques : Adobe InDesign<br /> </td> 
   <td> </td> 
   <td>Scripts à utiliser conjointement à Adobe InDesign.</td> 
  </tr> 
  <tr> 
   <td>Gestion des actifs numériques : profils vidéo<br /> </td> 
   <td> </td> 
   <td>Profils configurables pour les transcodages FFMPEG.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">Tableaux de bord</a></td> 
   <td> </td> 
   <td>Vous donne la possibilité de créer des tableaux de bord de rapports, ce qui permet de définir des pages qui affichent des données consolidées de façon personnalisée.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">Conceptions</a></td> 
   <td> </td> 
   <td>Contient la liste des conceptions définies, dont les images et les fichiers CSS à utiliser.</td> 
  </tr> 
  <tr> 
   <td>Documentation personnalisée</td> 
   <td> </td> 
   <td>Utilisée lors de l’extension de la documentation et de l’aide en ligne.</td> 
  </tr> 
  <tr> 
   <td>Envoi de formulaires</td> 
   <td> </td> 
   <td>Contient la liste des envois de formulaires reçus.</td> 
  </tr> 
  <tr> 
   <td>Importateurs – <a href="/help/sites-administering/bulk-editor.md">Éditeur en bloc</a></td> 
   <td> </td> 
   <td>Permet de rechercher des éléments et de les modifier en bloc. Vous pouvez également exporter et importer du contenu (en bloc) dans le référentiel.</td> 
  </tr>
  <tr> 
   <td>Importateurs – Importateur de flux</td> 
   <td> </td> 
   <td><p>L’importateur de flux est une structure qui permet d’importer, dans votre référentiel, du contenu provenant de sources externes, de façon répétée. Il consiste à interroger une ressource distante selon un intervalle spécifié, à l’analyser et à créer des nœuds dans le référentiel qui représentent le contenu de la ressource distante.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">Vérificateur de lien externe</a></td> 
   <td> </td> 
   <td>Analyse toutes les pages de contenu de l’instance AEM et vérifie les liens externes. Une liste des liens valides et non valides s’affiche.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">Mobile</a></td> 
   <td> </td> 
   <td>Permet de créer des sites web conçus pour les appareils mobiles.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>Gère le contenu multilingue et multinational, ce qui permet d’équilibrer le branding avec le contenu localisé.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">Notification</a></td> 
   <td> </td> 
   <td>Modèles de notification.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">Modules</a></td> 
   <td> </td> 
   <td>Autre lien vers le gestionnaire de modules, qui affiche les modules chargés pour la gestion de contenu web AEM. Similaire aux informations affichées dans le gestionnaire de modules de CRX.</td> 
  </tr> 
  <tr> 
   <td>Réplication – <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">Agents de réplication</a></td> 
   <td> </td> 
   <td>Servent à répliquer des données de l’environnement de création vers l’environnement de publication lorsque vous publiez des pages ou, en cas de réplication inverse, à transmettre les commentaires des utilisateurs de l’environnement de publication vers l’environnement de création.</td> 
  </tr> 
  <tr> 
   <td>Importateurs – <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">Activer l’arborescence</a></td> 
   <td> </td> 
   <td>Vous pouvez activer les différentes pages à partir de l’onglet Sites web. Après avoir saisi, ou mis à jour, un nombre élevé de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus simple d’activer toute l’arborescence en une seule opération. Vous pouvez également effectuer une Exécution d’essai afin d’émuler une activation et de mettre en surbrillance les pages à activer.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">Rapports</a></td> 
   <td> </td> 
   <td>AEM fournit divers rapports personnalisés et permet de créer des rapports personnalisés et/ou d’élaborer le vôtre.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">Génération de modèles automatique de page par défaut</a></td> 
   <td> </td> 
   <td>En mode Génération de modèles automatique, vous pouvez créer un formulaire (que l’on désigne sous le nom de modèle automatique) dont les champs représentent la structure souhaitée pour vos pages, puis l’utiliser afin de créer aisément des pages sur la base de cette structure.</td> 
  </tr> 
  <tr> 
   <td>Sécurité - <a href="/help/sites-administering/notification.md">Configuration en libre-service </a> </td> 
   <td> </td> 
   <td>Permet de configurer les messages électroniques que les utilisateurs reçoivent automatiquement lorsqu’ils créent un compte ou réinitialisent un mot de passe et pour confirmer qu’un mot de passe a été réinitialisé.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentation </a></td> 
   <td> </td> 
   <td>Les intérêts et objectifs des visiteurs qui se rendent sur un site sont variés. La compréhension de ces objectifs et la satisfaction de ces attentes constituent un important facteur de réussite en matière de marketing en ligne. La segmentation permet d’y parvenir en analysant et en caractérisant les détails d’un visiteur.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>Configuration SRP par défaut. Voir <a href="/help/communities/srp-config.md">Console Configuration de stockage</a>.</td> 
  </tr> 
  <tr> 
   <td>taskmanagement</td> 
   <td> </td> 
   <td>Aucune fonctionnalité active n’est liée à cette entrée.</td> 
  </tr> 
  <tr> 
   <td>clients</td> 
   <td> </td> 
   <td>Aucune fonctionnalité active n’est liée à cette entrée.</td> 
  </tr> 
  <tr> 
   <td>Contrôle de version – <a href="/help/sites-deploying/version-purging.md">Purger les versions</a></td> 
   <td> </td> 
   <td>Permet de purger les versions de page, au besoin.</td> 
  </tr> 
  <tr> 
   <td>Référentiels virtuels</td> 
   <td> </td> 
   <td>Vous pouvez configurer un référentiel virtuel à l’aide de la fonctionnalité de montage d’espace de travail afin que les applications de contenu compatibles JCR puissent accéder de façon simplifiée à l’infrastructure de contenu JCR basée sur CRX ainsi qu’aux connecteurs JCR.</td> 
  </tr> 
  <tr> 
   <td>mots-clés</td> 
   <td> </td> 
   <td>Obsolète. Voir <a href="/help/communities/moderate-ugc.md#watchwords">Modération du contenu d’une communauté</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">Workflow</a></td> 
   <td> </td> 
   <td>Les workflows contrôlent une série d’actions dans des pages ou des ressources numériques prenant en charge tout processus éditorial.</td> 
  </tr> 
 </tbody> 
</table>

## Outils – IU optimisée pour les écrans tactiles  {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Section</th> 
   <th>Option</th> 
   <th>Objectif</th> 
  </tr> 
  <tr> 
   <td>Création  </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">Campagnes</a></td> 
   <td>Gérer les campagnes marketing.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">Les lancements  </a></td> 
   <td>Gérez vos lancements marketing</td> 
  </tr> 
  <tr> 
   <td>Tâches</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">Boîte de réception</a></td> 
   <td>Gérez vos éléments de boîte de réception.</td> 
  </tr> 
  <tr> 
   <td>Opérations</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">Utilisateurs et groupes </a></td> 
   <td>Gérer les utilisateurs et les groupes.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">Gestion des balises</a></td> 
   <td>Organiser vos balises et leurs espaces de noms.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">Cloud Services</a></td> 
   <td>Connectez-vous à Adobe Marketing Cloud.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">Workflows</a></td> 
   <td>Modélisez et gérez les workflows.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">Réplication</a></td> 
   <td>Créez et gérez plusieurs sites Web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">Rapports</a></td> 
   <td>Créez et contrôlez des rapports personnalisés.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">Tests</a></td> 
   <td>Exécuter les tests définis pour votre application.</td> 
  </tr> 
  <tr> 
   <td>Opérations Granite</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>Développez des applications avec un IDE Web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">Modules</a></td> 
   <td>Regroupez et partagez des applications.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">Partage de modules</a></td> 
   <td>Téléchargez des applications depuis Adobe et la communauté.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">Navigateur de topologies</a></td> 
   <td>Afficher la topologie des instances.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">Déchargement du navigateur</a></td> 
   <td>Gérer le déchargement.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">Sauvegarde</a></td> 
   <td>Effectuer les tâches de sauvegarde.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Console web<br /> </td> 
   <td>Configurez et gérez la plate-forme d’applications.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Image mémoire de la configuration de la console Web<br /> </td> 
   <td>Téléchargez l'état de la configuration à partir de la console Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Utilisateurs</td> 
   <td>Gérer les utilisateurs.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Groupes</td> 
   <td>Gérer les groupes.</td> 
  </tr> 
  <tr> 
   <td>Ressources externes<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Documentation</td> 
   <td>Affichez la documentation de Web Experience Management.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Références pour les développeurs</td> 
   <td>Références et téléchargements pour les développeurs.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Certaines des options ci-dessus conduisent réellement vers l’interface utilisateur classique.

