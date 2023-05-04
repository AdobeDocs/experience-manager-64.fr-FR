---
title: Synchronisation des utilisateurs
seo-title: User Synchronization
description: Découvrez la synchronisation des utilisateurs dans AEM.
seo-description: Learn about user synchronization in AEM.
uuid: 0c7c35a3-9fed-4d48-8bd5-7f4382bf5fa3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 707b150b-7759-437f-9150-9f4784856754
exl-id: 537b86f5-ad38-4419-8dde-40ec08091b7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2529'
ht-degree: 66%

---

# Synchronisation des utilisateurs{#user-synchronization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Lorsque le déploiement est une [ferme de publication](/help/sites-deploying/recommended-deploys.md#tarmk-farm), les membres doivent pouvoir se connecter et voir leurs données sur n’importe quel nœud public.

Les utilisateurs et les groupes d’utilisateurs (données utilisateur) créés dans l’environnement de publication ne sont pas nécessaires dans l’environnement de création.

La plupart des données utilisateur créées dans l’environnement de création sont destinées à rester dans l’environnement de création et à ne pas être copiées vers les instances de publication.

L’enregistrement et les modifications effectués sur une instance de publication doivent être synchronisés avec d’autres instances de publication afin qu’elles aient accès aux mêmes données utilisateur.

Depuis AEM 6.1, lorsque la synchronisation des utilisateurs est activée, les données utilisateur sont automatiquement synchronisées sur les instances de publication dans la ferme et ne sont pas créées en mode de création.

## Distribution Sling {#sling-distribution}

Les données utilisateur, avec leurs [ACL](/help/sites-administering/security.md), sont stockées dans le [cœur Oak](/help/sites-deploying/platform.md), la couche située en dessous du JCR Oak, et sont accessibles via l’[API Oak](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). Du fait de mises à jour peu fréquentes, il est judicieux que les données utilisateur soient synchronisées avec d’autres instances de publication à l’aide de la [Distribution de contenu Sling](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md).

Les avantages de la synchronisation des utilisateurs à l’aide de la distribution Sling par rapport à la réplication traditionnelle sont les suivants :

* *utilisateurs*, *profils utilisateur* et *groupes d’utilisateurs* créées lors de la publication ne sont pas créées sur l’auteur

* La distribution Sling définit les propriétés dans les événements jcr, ce qui permet d’agir dans les écouteurs d’événements côté publication sans se soucier des boucles de réplication infinies.
* La distribution Sling envoie uniquement les données utilisateur aux instances de publication non originaires, éliminant ainsi le trafic inutile.
* [ACL](/help/sites-administering/security.md) définis dans le noeud utilisateur sont inclus dans la synchronisation

>[!NOTE]
>
>Si des sessions sont requises, il est recommandé d’utiliser une solution SSO ou une session persistante et de demander aux clients de se connecter s’ils passent à un autre éditeur.

>[!CAUTION]
>
>Synchronisation du ***administrateurs** *Le groupe n’est pas pris en charge, même si la synchronisation des utilisateurs est activée. À la place, un échec de l’importation de la comparaison est consigné dans le journal des erreurs.
>
>Par conséquent, lorsqu’un déploiement est une ferme de publication, si un utilisateur est ajouté ou supprimé du ***administrateurs** *groupe, la modification doit être effectuée manuellement sur chaque instance de publication.

## Activation de la synchronisation des utilisateurs {#enable-user-sync}

>[!NOTE]
>
>Par défaut, la synchronisation des utilisateurs est `disabled`.
>
>L’activation de la synchronisation des utilisateurs implique de modifier *existant* Configurations OSGi.
>
>Aucune nouvelle configuration ne doit être ajoutée suite à l’activation de la synchronisation des utilisateurs.

La synchronisation des utilisateurs repose sur l’environnement de création pour gérer les distributions de données utilisateur, même si les données utilisateur ne sont pas créées en mode de création. Une grande partie, mais pas l’intégralité, de la configuration a lieu dans l’environnement de création et chaque étape identifie clairement si elle doit être effectuée en mode de création ou en mode de publication.

Vous trouverez ci-dessous les étapes nécessaires pour activer la synchronisation des utilisateurs, suivies d’une section [Résolution des incidents](#troubleshooting) :

### Prérequis {#prerequisites}

1. Si les utilisateurs et les groupes d’utilisateurs ont déjà été créés sur un éditeur, il est recommandé de [synchroniser manuellement](#manually-syncing-users-and-user-groups) les données utilisateur sur tous les éditeurs avant de configurer et d’activer la synchronisation des utilisateurs.

   Une fois la synchronisation des utilisateurs activée, seuls les utilisateurs et les groupes nouvellement créés sont synchronisés.

1. Assurez-vous que la dernière version du code a été installée :

* [Mises à jour de la plateforme AEM](https://helpx.adobe.com/fr/experience-manager/kb/aem62-available-hotfixes.html)
* [Mises à jour d’AEM Communities](/help/communities/deploy-communities.md#latest-releases)

### 1. Agent de distribution Apache Sling - Fabrique d’agents de synchronisation {#apache-sling-distribution-agent-sync-agents-factory}

**Activation de la synchronisation des utilisateurs**

* **en mode de création**

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localisez `Apache Sling Distribution Agent - Sync Agents Factory`

      * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

         Vérifier `name` : **`socialpubsync`**

      * sélectionnez la case à cocher `Enabled`
      * sélectionnez `Save`



![chlimage_1-387](assets/chlimage_1-387.png)

### 2. Créez l’utilisateur autorisé {#createauthuser}

**Configurez des autorisations**
Cet utilisateur autorisé sera utilisé à l’étape 3 pour configurer la distribution Sling en mode de création.

* **sur chaque instance de publication**

   * connexion avec droits d’administrateur
   * accéder au [Console de sécurité](/help/sites-administering/security.md)

      * par exemple, [http://localhost:4503/useradmin](http://localhost:4503/useradmin)
   * créez un nouvel utilisateur

      * par exemple, `usersync-admin`
   * ajoutez cet utilisateur au groupe d’utilisateurs **`administrators`**
   * [ajoutez l’ACL de cet utilisateur à /home](#addacls)

      * `Allow jcr:all` avec restriction `rep:glob=*/activities/*`



>[!CAUTION]
>
>Un nouvel utilisateur doit être créé.
>
>* L’utilisateur affecté par défaut est l’utilisateur **`admin`**.
>* Ne pas utiliser `*communities-user-admin *user*.*`
>


#### Comment ajouter une liste de contrôle d’accès {#addacls}

* CRXDE Lite d’accès

   * par exemple, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* sélectionnez le nœud `/home`
* dans le volet de droite, sélectionnez l’onglet `Access Control`
* sélectionnez le bouton `+` pour ajouter une entrée ACL

   * **Principal** : *recherchez l’utilisateur créé pour la synchronisation des utilisateurs*
   * **Type** : `Allow`
   * **Autorisations** : `jcr:all`
   * **Restrictions** rep:glob: `*/activities/*`
   * select **OK**

* select **Enregistrer tout**

![chlimage_1-388](assets/chlimage_1-388.png)

Voir également

* [Gestion des droits d’accès](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Section de résolution des incidents [Modification de l’exception d’opération pendant le traitement de la réponse](#modify-operation-exception-during-response-processing)

### 3. Distribution Granite des Adobes - Fournisseur secret de transport de mot de passe chiffré {#adobegraniteencpasswrd}

**Configuration des autorisations**

Une fois qu’un utilisateur autorisé, membre du groupe d’utilisateurs **`administrators`**, a été créé sur toutes les instances de publication, cet utilisateur autorisé doit être identifié en mode de création comme étant autorisé à synchroniser les données utilisateur de la création à la publication.

* **en mode de création**

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localisez `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`
   * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

      Vérifier `property name` : **`socialpubsync-publishUser`**

   * définissez le nom d’utilisateur et le mot de passe de l’[utilisateur autorisé](#createauthuser) créé en mode de publication à l’étape 2

      * par exemple, `usersync-admin`


![chlimage_1-389](assets/chlimage_1-389.png)

### 4. Agent de distribution Apache Sling - Fabrique d’agents de file d’attente {#apache-sling-distribution-agent-queue-agents-factory}

**Activation de la synchronisation des utilisateurs**

* **en mode de publication** :

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localisez `Apache Sling Distribution Agent - Queue Agents Factory`

      * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

         Vérifier `Name` : `socialpubsync-reverse`

      * sélectionnez la case à cocher `Enabled`
      * sélectionnez `Save`
   * **répétez** l’opération pour chaque instance de publication.



![chlimage_1-390](assets/chlimage_1-390.png)

### 5. Distribution Granite des Adobes - Fabrique observateur diff. {#diffobserver}

**Activez la synchronisation des groupes**

* **sur chaque instance de publication** :

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localisez `Adobe Granite Distribution - Diff Observer Factory`

      * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

         Vérifier `agent name` : `socialpubsync-reverse`

      * sélectionnez la case à cocher `Enabled`
      * sélectionnez `Save`


![chlimage_1-391](assets/chlimage_1-391.png)

### 6. Déclencheur de distribution Apache Sling - Fabrique de déclencheurs planifiés {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Facultatif) modifiez l’intervalle d’interrogation**

Par défaut, l’auteur interroge les modifications toutes les 30 secondes. Pour modifier cet intervalle :

* **en mode de création**

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localisez `Apache Sling Distribution Trigger - Scheduled Triggers Factory`

      * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

         * Vérifier `Name` : `socialpubsync-scheduled-trigger`
      * définissez l’`Interval in Seconds` à l’intervalle souhaité.
      * sélectionnez `Save`



![chlimage_1-392](assets/chlimage_1-392.png)

## Configuration de plusieurs instances de publication {#configure-for-multiple-publish-instances}

La configuration par défaut couvre une instance de publication unique. Puisque l’objectif de l’activation de la synchronisation des utilisateurs est de synchroniser plusieurs instances de publication (par exemple, pour une ferme de publication), les instances de publication supplémentaires doivent être ajoutées à la fabrique d’agents de synchronisation.

### 7. Agent de distribution Apache Sling - Fabrique d’agents de synchronisation {#apache-sling-distribution-agent-sync-agents-factory-1}

**Ajoutez des instances de publication :**

* **en mode de création**

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localisez `Apache Sling Distribution Agent - Sync Agents Factory`

      * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

         Vérifier `Name` : `socialpubsync`


![chlimage_1-393](assets/chlimage_1-393.png)

* **Points d’entrée de l’exportateur**
Il doit exister un point d’entrée de l’exportateur pour chaque éditeur. Par exemple, s’il existe 2 éditeurs, localhost:4503 et 4504, il doit y avoir 2 entrées :

   * http://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse
   * http://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse

* **Points d’entrée de l’importateur**
Il doit exister un point d’entrée de l’importateur pour chaque éditeur. Par exemple, s’il existe 2 éditeurs, localhost:4503 et 4504, il doit y avoir 2 entrées :

   * http://localhost:4503/libs/sling/distribution/services/importers/socialpubsync
   * http://localhost:4504/libs/sling/distribution/services/importers/socialpubsync

* sélectionnez `Save`

### 8. Écouteur de synchronisation des utilisateurs AEM Communities {#aem-communities-user-sync-listener}

**(Facultatif) Synchroniser des noeuds JCR supplémentaires**

S’il existe des données personnalisées à synchroniser sur plusieurs instances de publication, alors :

* **sur chaque instance de publication** :

   * connexion avec droits d’administrateur
   * accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

      * par exemple, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localisez `AEM Communities User Sync Listener`
   * sélectionnez la configuration existante à ouvrir pour modification (icône de crayon)

      Vérifier `Name` : `socialpubsync-scheduled-trigger`


![chlimage_1-394](assets/chlimage_1-394.png)

* **Types de nœuds**

   Il s’agit de la liste des types de noeuds qui seront synchronisés. Tout type de nœud autre que sling:Folder doit être répertorié ici (sling:folder est traité séparément).
 

   Liste par défaut des types de nœuds à synchroniser :

   * rep:User
   * nt:unstructured
   * nt:resource

* **Propriétés ignorables**

   Il s’agit de la liste des propriétés qui seront ignorées si une modification est détectée. Les modifications apportées à ces propriétés peuvent être synchronisées comme effet secondaire d’autres modifications (la synchronisation ayant toujours lieu au niveau du nœud), mais les modifications apportées à ces propriétés ne déclenchent pas en elles-mêmes de synchronisation.
 

   Propriété par défaut à ignorer :

   * cq:lastModified

* **Noeuds ignorables**

   Sous-chemins qui seront entièrement ignorés lors de la synchronisation. Aucun élément figurant dans ces sous-chemins d’accès ne sera synchronisé à un moment donné.
 

   Nœuds par défaut à ignorer :

   * .jetons
   * system

* **Dossiers distribués**

   La plupart des dossiers sling:Folders sont ignorés car la synchronisation n’est pas nécessaire. Les quelques exceptions sont répertoriées ici.

   Dossiers par défaut à synchroniser

   * segments/notation
   * social/relations
   * activities

### 9. Identifiant Sling unique {#unique-sling-id}

>[!CAUTION]
>
>Si l’identifiant Sling correspond à deux instances de publication ou plus, la synchronisation de groupe d’utilisateurs échoue.

Si l’identifiant Sling est identique pour plusieurs instances de modification dans une ferme de publication, les groupes d’utilisateurs ne sont pas synchronisés.

Pour vérifier que toutes les valeurs d’identifiant Sling diffèrent, sur chaque instance de publication :

1. accédez à `http://<host>:<port>/system/console/status-slingsettings`
1. vérifiez la valeur de l’**identifiant Sling**

![chlimage_1-395](assets/chlimage_1-395.png)

Si l’identifiant Sling d’une instance de publication correspond à l’identifiant Sling d’une autre instance de publication, alors :

1. Arrêtez l’une des instances de publication ayant un identifiant Sling correspondant.
1. dans le répertoire crx-quickstart/launchpad/felix

   * Recherchez et supprimez le fichier nommé *sling.id.file*

      * par exemple, sur un système Linux :

         `rm -i $(find . -type f -name sling.id.file)`

      * par exemple, sur un système Windows :

         `use windows explorer and search for *sling.id.file*`

1. démarrez l’instance de publication

   * au démarrage, un nouvel identifiant Sling lui sera attribué.

1. validez la variable **Sling ID** est désormais unique

Répétez ces étapes jusqu’à ce que toutes les instances de publication aient un identifiant Sling unique.

## Fabrique de générateur de module vault {#vault-package-builder-factory}

Pour que les mises à jour soient correctement synchronisées, il est nécessaire de modifier le générateur de package vault en vue de la synchronisation des utilisateurs :

* sur chaque instance de publication AEM
* accéder au [Console web](/help/sites-deploying/configuring-osgi.md)

   * par exemple, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* localisez `Apache Sling Distribution Packaging - Vault Package Builder Factor`

   * `Builder name: socialpubsync-vlt`

* sélectionnez l’icône de modification
* ajouter deux `Package Filters` :

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* gestion des stratégies :

   * pour remplacer les nœuds rep:policy existants par de nouveaux nœuds, ajoutez un troisième filtre de package :

      * `/home/users|+.*/rep:policy`
   * pour empêcher la distribution des stratégies, définissez

      * `Acl Handling :` `IGNORE`


![chlimage_1-396](assets/chlimage_1-396.png)

## Que se passe-t-il lorsque ... {#what-happens-when}

### Auto-enregistrement ou modification du profil de l’utilisateur lors de la publication {#user-self-registers-or-edits-profile-on-publish}

Par défaut, les utilisateurs et les profils créés dans l’environnement de publication (inscription automatique) n’apparaissent pas dans l’environnement de création.

Lorsque la topologie consiste en une [ferme de publication](/help/sites-deploying/recommended-deploys.md#tarmk-farm) et que la synchronisation des utilisateurs a correctement été configurée, l’*utilisateur* et le *profil utilisateur* sont synchronisés dans la ferme de publication à l’aide de la distribution Sling.

### La création d’utilisateurs ou de groupes d’utilisateurs s’effectue dans la console de sécurité {#users-or-user-groups-are-created-using-security-console}

Par conception, les données utilisateur créées dans l’environnement de publication n’apparaissent pas dans l’environnement de création et vice versa.

Lorsque la console [Administration et sécurité des utilisateurs](/help/sites-administering/security.md) est utilisée pour ajouter de nouveaux utilisateurs dans l’environnement de publication, la synchronisation des utilisateurs synchronise les nouveaux utilisateurs et leur appartenance à un groupe sur d’autres instances de publication, si nécessaire. La synchronisation des utilisateurs synchronise également les groupes d’utilisateurs créés via la console de sécurité.

## Résolution des problèmes {#troubleshooting}

### Comment mettre la synchronisation des utilisateurs hors ligne {#how-to-take-user-sync-offline}

Pour mettre la synchronisation des utilisateurs hors ligne, afin de [suppression d’un éditeur](#how-to-remove-a-publisher) ou [synchronisation manuelle des données](#manually-syncing-users-and-user-groups), la file d’attente de distribution doit être vide et silencieuse.

Pour vérifier le statut de la file d’attente de distribution :

* en mode de création :

   * utilisation de [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * recherchez des entrées dans `/var/sling/distribution/packages`

         * nœuds de dossier nommés selon le motif `distrpackage_*`
   * using [Gestionnaire de modules](/help/sites-administering/package-manager.md)

      * rechercher les packages en attente (non encore installés) ;

         * nommés selon le motif `socialpubsync-vlt*`
         * créés par `communities-user-admin`


Lorsque la file d’attente de distribution est vide, désactivez la synchronisation des utilisateurs :

* en mode de création

   * *décochez* la case `Enabled` de l’[Agent de distribution Apache Sling - Fabrique d’agents de synchronisation](#apache-sling-distribution-agent-sync-agents-factory)

Une fois les tâches accomplies, pour réactiver la synchronisation des utilisateurs :

* en mode de création

   * cochez la case `Enabled` de l’[Agent de distribution Apache Sling - Fabrique d’agents de synchronisation](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnostics de synchronisation des utilisateurs {#user-sync-diagnostics}

L’outil Diagnostics de synchronisation des utilisateurs vérifie la configuration et tente d’identifier les problèmes.

En mode de création, de la console principale accédez simplement à **Outils, Opérations, Diagnostics, Diagnostics de synchronisation des utilisateurs.**

Entrer simplement dans la console Diagnostics de synchronisation des utilisateurs a pour effet d’afficher les résultats.

Voici ce qui s’affiche lorsque la synchronisation des utilisateurs n’a pas été activée :

![chlimage_1-397](assets/chlimage_1-397.png)

#### Exécution des diagnostics pour les éditeurs {#how-to-run-diagnostics-for-publishers}

Lorsque le diagnostic est exécuté à partir de l’environnement de création, les résultats de réussite/échec incluent une [INFO] qui affiche la liste des instances de publication configurées pour confirmation.

La liste comprend une URL de chaque instance de publication allant exécuter les diagnostics de cette instance. Le paramètre d’URL `syncUser` est ajouté à l’URL de diagnostic avec sa valeur définie sur l’*utilisateur de synchronisation autorisé* créé à l’[Étape 2](/help/sites-administering/sync.md#createauthuser).

**Remarque** : avant le lancement de l’URL, l’*utilisateur de synchronisation autorisé* doit déjà être connecté à cette instance de publication.

![chlimage_1-398](assets/chlimage_1-398.png)

### Configuration incorrectement ajoutée {#improperconfig}

Lorsque la synchronisation des utilisateurs ne fonctionne pas, le problème le plus courant est que des configurations supplémentaires ont été *ajoutées*. À la place, la configuration par défaut existante aurait dû être *modifiée*.

Voici comment les configurations par défaut modifiées doivent apparaître dans la console web. Si plusieurs instances apparaissent, la configuration supplémentaire doit être supprimée.

#### (création) Un agent de distribution Apache Sling - Fabrique d’agents de synchronisation {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![chlimage_1-399](assets/chlimage_1-399.png)

#### (auteur) Une distribution Granite Adobe - Fournisseur secret de transport de mot de passe chiffré {#author-one-adobe-granite-distribution-encrypted-password-transport-secret-provider}

![chlimage_1-400](assets/chlimage_1-400.png)

#### (publication) Un agent de distribution Apache Sling - Fabrique d’agents de file d’attente {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![chlimage_1-401](assets/chlimage_1-401.png)

#### (publication) Distribution Granite par Adobe - Fabrique observateur diff. {#publish-one-adobe-granite-distribution-diff-observer-factory}

![chlimage_1-402](assets/chlimage_1-402.png)

#### (auteur) Un déclencheur de distribution Apache Sling - Fabrique de déclencheurs planifiés {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![chlimage_1-403](assets/chlimage_1-403.png)

### Modifier l’exception d’opération lors du traitement de la réponse {#modify-operation-exception-during-response-processing}

Si les éléments suivants sont visibles dans le journal :

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

Vérifiez alors que la section [2. Création d’un utilisateur autorisé](#createauthuser) a été correctement suivie.

Cette section décrit la création d’un utilisateur autorisé, qui existe sur toutes les instances de publication, et son identification dans la configuration OSGi « Fournisseur secret » en mode de création. Par défaut, l’utilisateur est `admin`.

L’utilisateur autorisé doit être fait membre du groupe utilisateurs **`administrators`** et les autorisations de ce groupe ne doivent pas être modifiées.

L’utilisateur autorisé doit avoir explicitement les autorisations et la restriction suivante sur les instances de publication :

| **path** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | &amp;ast;/activities/&amp;ast; |
| /home/users | X | &amp;ast;/activities/&amp;ast; |
| /home/groups | X | &amp;ast;/activities/&amp;ast; |

En tant que membre du groupe d’`administrators`, l’utilisateur autorisé doit disposer des autorisations suivantes sur toutes les instances de publication :

| **path** | **jcr:all** | **jcr:read** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Échec de la synchronisation du groupe d’utilisateurs {#user-group-sync-failed}

Si l’identifiant Sling correspond à deux instances de publication ou plus, la synchronisation de groupe d’utilisateurs échoue.

Voir la section [9. Identifiant Sling unique](#unique-sling-id)

### Synchronisation manuelle des utilisateurs et des groupes d’utilisateurs {#manually-syncing-users-and-user-groups}

* sur l’éditeur sur lequel les utilisateurs et les groupes d’utilisateurs existent :

   * [si elle est activée, désactivez la synchronisation des utilisateurs](#how-to-take-user-sync-offline)
   * [créez un package](/help/sites-administering/package-manager.md#creating-a-new-package) de `/home`

      * lors de la modification du package

         * Onglet Filtres : Ajouter un filtre : Chemin racine : `/home`
         * Onglet Avancé : Traitement AC : `Overwrite`
   * [exportez le package](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* sur d’autres instances de publication :

   * [importez le package](/help/sites-administering/package-manager.md#installing-packages)

Pour configurer ou activer la synchronisation des groupes, allez à l’étape 1 : [Agent de distribution Apache Sling - Fabrique d’agents de synchronisation](#apache-sling-distribution-agent-sync-agents-factory).

### Lorsqu’un éditeur n’est plus disponible {#when-a-publisher-becomes-unavailable}

Lorsqu’une instance de publication n’est plus disponible, elle ne doit pas être supprimée si elle doit être de nouveau en ligne à l’avenir. Les modifications sont mises en file d’attente pour l’éditeur et, une fois l’instance de nouveau en ligne, elles sont traitées.

Si l’instance de publication ne doit pas être remise en ligne, si elle est définitivement hors ligne, elle doit être supprimée, car l’accumulation dans la file d’attente entraînera une utilisation notable de l’espace disque dans l’environnement de création.

Lorsqu’un éditeur est en panne, le journal de création comporte des exceptions similaires à :

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Suppression d’un éditeur {#how-to-remove-a-publisher}

Pour supprimer un éditeur du [Agent de distribution Apache Sling - Fabrique d’agents de synchronisation](#apache-sling-distribution-agent-sync-agents-factory), la file d’attente de distribution doit être vide et silencieuse.

* en mode de création :

   * [Application de la synchronisation des utilisateurs hors ligne](#how-to-take-user-sync-offline)
   * suivez l’[étape 7](#apache-sling-distribution-agent-sync-agents-factory) pour supprimer l’éditeur des deux listes de serveur :

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * réactivez la synchronisation des utilisateurs

      * cochez la case `Enabled` de l’[Agent de distribution Apache Sling - Fabrique d’agents de synchronisation](#apache-sling-distribution-agent-sync-agents-factory)
