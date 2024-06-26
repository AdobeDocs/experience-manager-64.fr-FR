---
title: Migration de ressources et de documents AEM Forms
seo-title: Migrate AEM Forms assets and documents
description: L’utilitaire de migration vous permet de migrer des ressources et des documents AEM Forms d’AEM 6.3 Forms ou des versions antérieures vers AEM 6.4 Forms.
seo-description: The Migration utility allows you to Migrate AEM Forms assets and documents from AEM 6.3 Forms or prior versions to AEM 6.4 Forms.
uuid: 593fc421-b70e-4dbe-87bc-ea49ff025368
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-strategy: max-2018
discoiquuid: a8b1f7df-e36f-4d02-883a-72120fea7046
role: Admin
exl-id: 72ead30c-648d-43ad-9826-9c8945a8860d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 56%

---

# Migration de ressources et de documents AEM Forms {#migrate-aem-forms-assets-and-documents}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’utilitaire de migration convertit les [ressources des formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md), les [configurations du cloud](/help/sites-developing/extending-cloud-config.md), et les [ressources de Correspondence Management](/help/forms/using/cm-overview.md) du format utilisé dans les versions antérieures vers le format utilisé dans AEM 6.4 Forms. L’exécution de l’utilitaire de migration engendre la migration des éléments suivants :

* Composants personnalisés pour les formulaires adaptatifs
* Formulaires adaptatifs et modèles de Correspondence Management
* Configurations cloud
* Correspondence Management et ressources de formulaires adaptatifs

>[!NOTE]
>
>En cas de mise à niveau dynamique, pour les actifs de Correspondence Management, vous pouvez exécuter la migration à chaque importation des actifs. Pour la migration de Correspondence Management, le package de compatibilité Forms doit être installé.

## Approche de la migration {#approach-to-migration}

Vous pouvez [upgrade](/help/forms/using/upgrade.md) à la dernière version d’AEM Forms 6.4 à partir d’AEM Forms 6.3 ou 6.2 ou effectuez une nouvelle installation. Selon que vous avez mis à niveau votre installation précédente ou procédé à une nouvelle installation, vous devez effectuer l’une des opérations suivantes :

**En cas de mise à niveau statique**

Si vous avez effectué une mise à niveau statique, l’instance mise à niveau contient déjà les actifs et les documents. Toutefois, avant de pouvoir utiliser les actifs et les documents, vous devez installer [Package de compatibilité AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr) (comprend le package de compatibilité Correspondence Management)

Vous devez ensuite les mettre à jour en [exécutant l’utilitaire de migration](#runningmigrationutility).

**En cas d’installation dynamique**

S’il s’agit d’une nouvelle installation, afin de pouvoir utiliser les ressources et les documents, vous devez installer le [package de compatibilité AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr) (y compris le package de compatibilité Correspondence Management).

Ensuite, vous devez importer votre package de ressources (zip ou cmp) sur la nouvelle installation, puis mettre à jour les ressources et les documents en [exécutant l’utilitaire de migration](#runningmigrationutility). En raison de changements [liés à la rétrocompatibilité](/help/sites-deploying/backward-compatibility.md), les emplacements de quelques dossiers dans crx-repository ont changé. Exportez et importez manuellement les dépendances (bibliothèques et ressources personnalisées) de la configuration précédente vers un nouvel environnement.

## À lire avant de procéder à la migration {#prerequisites}

Pour les ressources de Correspondence Management :

* Pour les ressources importées de la plateforme précédente, une propriété est ajoutée : **fd:version=1.0**.
* Depuis AEM 6.1 Forms, les commentaires ne sont pas disponibles hors champ. Les commentaires ajoutés précédemment sont disponibles dans les actifs mais ne sont pas automatiquement affichés sur l’interface. Vous devez personnaliser la propriété extendedProperties dans l’interface utilisateur d’AEM Forms pour rendre les commentaires visibles.
* Dans certaines versions précédentes, telles que LiveCycle ES4, le texte était modifié à l’aide de Flex RichTextEditor, mais depuis AEM Forms 6.1, l’éditeur de HTML est utilisé. En raison de ce rendu et de l’aspect des polices, les tailles et les marges des polices peuvent différer des versions précédentes de l’interface utilisateur de création. Toutefois, l’aspect des lettres est identique lors du rendu.
* Les listes dans les modules de texte sont améliorées et le rendu est désormais différent. Il peut y avoir des différences visuelles. Nous vous recommandons d’afficher et d’afficher les lettres dans lesquelles vous utilisez des listes dans des modules de texte.
* Les modules de contenu d’image étant convertis en ressources de gestion des actifs numériques, les mises en page et les fragments sont ajoutés aux formulaires au cours de la migration, la propriété Mis à jour par de ces modules devient admin.
* L’historique des versions des ressources n’est pas migré et n’est pas disponible après la migration. L’historique des versions suivant après la migration est conservé.
* L’état Prêt à publier est déprécié depuis AEM 6.1 Forms, de sorte que tous les actifs à l’état Prêt à publier passent à l’état Modifié.
* L’interface utilisateur étant mise à jour dans AEM Forms 6.3, les étapes d’exécution des personnalisations sont également différentes. Vous devez rétablir la personnalisation si vous migrez depuis une version antérieure à 6.3.
* Les fragments de mise en page passent de /content/apps/cm/layouts/fragmentlayouts/1001 à /content/apps/cm/modules/fragmentlayouts. La référence au dictionnaire de données dans les ressources affiche le chemin d’accès du dictionnaire de données au lieu de son nom.
* Les espaces de tabulation utilisés pour l’alignement dans les modules de texte doivent être réajustés. Pour plus d’informations, voir [Correspondence Management - Utilisation de l’espacement des tabulations pour organiser le texte](https://helpx.adobe.com/fr/aem-forms/kb/cm-tab-spacing-limitations.html).
* Les configurations d’Asset Composer sont remplacées par celles de Correspondence Management.
* Les ressources sont déplacées dans des dossiers portant des noms tels que Texte existant et Liste existante.

## Utilisation de l’utilitaire de migration {#using-the-migration-utility}

### Exécution de l’utilitaire de migration {#runningmigrationutility}

Exécutez l’utilitaire de migration avant d’apporter des modifications aux ressources ou de créer des ressources. Nous vous recommandons de ne pas exécuter l’utilitaire après avoir apporté des modifications ou créé des ressources. Assurez-vous que l’interface utilisateur des ressources de Correspondence Management ou des formulaires adaptatifs n’est pas ouverte pendant que le processus de migration est en cours d’exécution.

Lorsque vous exécutez l’utilitaire de migration pour la première fois, un journal est créé avec le chemin et le nom suivants : `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Ce journal est constamment mis à jour avec les informations de migration de Correspondence Management et de Forms adaptatif, telles que le déplacement des ressources.

>[!NOTE]
>
>Avant d’exécuter l’utilitaire de migration, assurez-vous d’avoir effectué une sauvegarde de votre référentiel crx.

1. Dans une session de navigateur, connectez-vous à l’instance d’auteur AEM en tant qu’administrateur.

1. Ouvrez l’URL suivante dans le navigateur :

   https://[*nom de l’hôte*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Le navigateur affiche quatre options :

   * Migration des ressources d’AEM Forms
   * Migration de composants personnalisés de formulaires adaptatifs
   * Migration de modèles de formulaire adaptatif
   * Migration des configurations cloud AEM Forms

1. Procédez comme suit pour effectuer la migration :

   * Pour migrer les **ressources**, appuyez sur Migration des ressources d’AEM Forms et dans l’écran suivant, appuyez sur **Lancer la migration**. Les éléments suivants sont migrés :

      * Formulaires adaptatifs
      * Fragments de document
      * Thèmes
      * Lettres
      * Dictionnaires de données

   >[!NOTE]
   >
   >Lors de la migration des ressources, vous pouvez trouver des messages d’avertissement tels que &quot;Conflit trouvé pour...&quot;. Ces messages indiquent que les règles de certains composants des formulaires adaptatifs n’ont pas pu être migrées. Par exemple, si le composant possède un événement qui contient à la fois des règles et des scripts, si les règles se produisent après un script, aucune des règles du composant n’est migrée. Toutefois, ces règles peuvent être migrées en ouvrant l’éditeur de règles dans la création de formulaires adaptatifs.
   >
   >Ces composants peuvent être migrés en les ouvrant dans l’éditeur de règles dans l’éditeur de formulaires adaptatifs.
   >
   >* Pour migrer les règles et les scripts (ceci n’est pas nécessaire si vous effectuez une mise à niveau à partir de la version 6.3) dans les composants personnalisés, appuyez sur Migration des composants personnalisés des formulaires adaptatifs. Dans l’écran suivant, appuyez sur Démarrer la migration. Les éléments suivants sont migrés :
   >
   >  * Règles et scripts créés à l’aide de éditeur de règles (6.1 FP1 et versions ultérieures)
   >  * Scripts créés à l’aide de l’onglet Script dans l’interface utilisateur de la version 6.1 et versions antérieures
   >* Pour migrer des modèles (non requis si vous effectuez une mise à niveau à partir de la version 6.3), appuyez sur Migration de modèles de Forms adaptative, puis, dans l’écran suivant, appuyez sur Démarrer la migration. Les éléments suivants sont migrés :
   >
   >  * Anciens modèles : les modèles de formulaires adaptatifs créés sous /apps en utilisant AEM 6.1 Forms ou une version antérieure. Ceci inclut les scripts qui ont été définis dans les composants du modèle.
   >  * Nouveaux modèles : les modèles de formulaires adaptatifs créés en utilisant l’éditeur de modèles sous /conf. Cela inclut la migration des règles et des scripts créés à l’aide de l’éditeur de règles.


   * Pour migrer les composants personnalisés des formulaires adaptatifs, appuyez sur **Migration des composants personnalisés des formulaires adaptatifs**. Sur la page Migration des composants personnalisés, appuyez sur **Démarrer la migration**. Les éléments suivants sont migrés :

      * Composants personnalisés écrits pour le Forms adaptatif
      * Superpositions de composants, le cas échéant.
   * Pour migrer les modèles de formulaires adaptatifs, appuyez sur **Migration des modèles de formulaires adaptatifs**. Sur la page Migration des composants personnalisés, appuyez sur **Démarrer la migration**. Les éléments suivants sont migrés :

      * Modèles de formulaires adaptatifs créés sous /apps ou /conf à l’aide de l’éditeur de modèles d’AEM.
   * Migrez les services de configuration cloud d’AEM Forms pour exploiter le nouveau paradigme de service cloud contextuel comprenant l’interface utilisateur tactile (sous /conf). Lorsque vous migrez les services de configuration cloud d’AEM Forms, les services cloud dans /etc sont déplacés vers /conf. Si aucune de vos personnalisations de Services cloud ne dépendent de chemins d’accès hérités (/etc), il est recommandé d’exécuter l’utilitaire de migration juste après la mise à niveau vers la version 6.4 et d’utiliser l’interface utilisateur tactile de la configuration cloud pour toute autre tâche. Si vous disposez déjà de personnalisations de services cloud, continuez à utiliser l’interface utilisateur classique dans la configuration mise à niveau jusqu’à ce que les personnalisations soient mises à jour et concordent avec les chemins migrés (/conf), puis exécutez l’utilitaire de migration.

   Pour migrer les **services cloud d’AEM Forms** qui comprennent les services suivants, appuyez sur Migration des configurations cloud d’AEM Forms (la migration des configurations cloud est indépendante du package de compatibilité AEMFD), appuyez sur Migration des configurations cloud d’AEM Forms puis, sur la page Migration des configurations, appuyez sur **Démarrer la migration** :

   * Services cloud du modèle de données de formulaire

      * Chemin d’accès source : /etc/cloudservices/fdm
      * Chemin d’accès cible : /conf/global/settings/cloudconfigs/fdm
   * Recaptcha

      * Chemin d’accès source : /etc/cloudservices/recaptcha
      * Chemin d’accès cible : /conf/global/settings/cloudconfigs/recaptcha
   * Acrobat Sign

      * Chemin d’accès source : /etc/cloudservices/echosign
      * Chemin d’accès cible : /conf/global/settings/cloudconfigs/echosign
   * Services cloud typekit

      * Chemin d’accès source : /etc/cloudservices/typekit
      * Chemin d’accès cible : /conf/global/settings/cloudconfigs/typekit

   La fenêtre du navigateur affiche les éléments suivants pendant le processus de migration :

   * Lorsque les ressources sont mises à jour : Mise à jour des ressources réussie.
   * Une fois la migration terminée : Migration des ressources terminée.

   Une fois exécuté, l’utilitaire de migration effectue les opérations suivantes :

   * **Ajoute les balises aux ressources.**: Ajoute la balise &quot;Correspondence Management : Ressources migrées&quot; / &quot;Forms adaptatif : Ressources migrées&quot;. aux actifs migrés, afin que les utilisateurs et utilisatrices puissent identifier les actifs migrés. Lorsque vous exécutez l’utilitaire de migration, toutes les ressources existantes dans le système sont marquées comme étant migrées.
   * **Génération des balises** : les catégories et les sous-catégories présentes dans le système précédent sont créées sous forme de balises et ces balises sont associées aux actifs appropriés de Correspondence Management dans AEM. Par exemple, une catégorie (Demandes) et une sous-catégorie (Demandes) d’un modèle de lettre sont générées sous la forme de balises.
   * **Déplacement des mises en page et des fragments de mise en page vers l’interface utilisateur Forms 6.4 AEM**: Si vous effectuez une mise à niveau de la version 6.2 vers la version 6.4, les modèles de mise en page et les fragments de mise en page sont ajoutés sous forme de formulaires dans la section de l’interface utilisateur d’AEM Forms 6.4.

   >[!NOTE]
   >
   >Si vous effectuez une mise à niveau de la version 6.2 vers la version 6.4 pour Correspondence Management, de nouveaux dossiers peuvent apparaître dans l’interface utilisateur qui comprend vos ressources. Vous devrez peut-être vérifier ces dossiers pour localiser vos ressources.

1. Une fois l’utilitaire de migration en cours d’exécution, passez aux [tâches de maintenance](#housekeepingtasks).

### Tâches de maintenance après l’exécution de l’utilitaire de migration {#housekeepingtasks}

Après avoir exécuté l’utilitaire de migration, effectuez les tâches de maintenance suivantes :

1. Assurez-vous que la version XFA des dispositions et des dispositions de fragments est 3.3 ou une version ultérieure. L’utilisation des dispositions et des dispositions de fragments d’une version plus ancienne peut provoquer des problèmes de rendu de la lettre. Pour mettre à jour une version de XFA plus ancienne vers la version la plus récente, suivez la procédure suivante :

   1. [Téléchargez XFA sous la forme d’un fichier zip](/help/forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) depuis l’interface utilisateur de Forms.
   1. Extrayez le fichier.
   1. Ouvrez le fichier XFA dans la dernière version de Designer et enregistrez-le. La version de XFA est mise à jour vers la dernière version.
   1. Téléchargez le fichier XFA dans l’interface utilisateur de Forms.

1. Publiez tous les actifs qui ont été publiés dans le système précédent avant la migration. L’utilitaire de migration ne met à jour les ressources que sur l’instance d’auteur. Pour mettre à jour les ressources sur la ou les instances de publication, vous devez les publier.
1. Dans AEM Forms 6.4, certains droits des groupes d’utilisateurs de formulaires sont modifiés. Si vous souhaitez que l’un de vos utilisateurs puisse charger des fichiers XDP et des Forms adaptatifs contenant des scripts ou utiliser l’éditeur de code, vous devez les ajouter au groupe forms-power-users. De même, template-authors ne peut plus utiliser l’éditeur de code dans l’éditeur de règles. Pour que les utilisateurs puissent utiliser l’éditeur de code, ajoutez-les au groupe af-template-script-writers. Pour obtenir des instructions sur l’ajout d’utilisateurs à des groupes, consultez [Gestion des utilisateurs et groupes d’utilisateurs](/help/communities/users.md).
