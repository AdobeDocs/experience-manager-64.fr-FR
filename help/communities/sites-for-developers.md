---
title: Site communautaire Essentials
seo-title: Site communautaire Essentials
description: Exportation et suppression de sites communautaires et création de modèles de sites personnalisés
seo-description: Exportation et suppression de sites communautaires et création de modèles de sites personnalisés
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---


# Community Site Essentials {#community-site-essentials}

## Modèle de site personnalisé {#custom-site-template}

Un modèle de site personnalisé peut être spécifié séparément pour chaque copie de langue d’un site communautaire.

Pour ce faire,

* Création d’un modèle personnalisé
* Recouvrir le chemin d&#39;accès au modèle de site par défaut
* Ajouter le modèle personnalisé au chemin d’accès de l’incrustation
* Spécifiez le modèle personnalisé en ajoutant une propriété `page-template` au noeud `configuration`.

**Modèle** par défaut :

/**libs**/social/console/components/hbs/sitepage/**sitepage**.hbs

**Modèle personnalisé dans le chemin** d’incrustation :

/**applications**/social/console/components/hbs/sitepage/**&quot;a3/>nom-modèle&lt;a4/&quot;**.hbs **

**Propriété** : page-template\
**Type** : String\
**Valeur** :  &lt;>template-name *> (sans extension)*

**Noeud** de configuration :

/content/&quot;a0/>chemin d&#39;accès au site de la communauté&#x200B;*/* lang&lt;a3/&quot;/configuration **

Par exemple : /content/sites/engagement/fr/configuration

>[!NOTE]
>
>Tous les noeuds du chemin superposé doivent uniquement être de type `Folder`.

>[!CAUTION]
>
>Si le modèle personnalisé porte le nom *sitepage.hbs,*, tous les sites de la communauté seront personnalisés.

### Exemple de modèle de site personnalisé {#custom-site-template-example}

Par exemple, `vertical-sitepage.hbs` est un modèle de site qui permet de placer les liens de menu verticalement sur le côté gauche de la page, plutôt que horizontalement sous la bannière.

[Get ](assets/vertical-sitepage.hbs)
FilePlacez le modèle de site personnalisé dans le dossier d&#39;incrustation :

/**applications**/social/console/components/hbs/sitepage/**vertical-sitepage**.hbs

Identifiez le modèle personnalisé en ajoutant une propriété `page-template` au noeud de configuration :

/content/sites/sample/fr/configuration

![chlimage_1-80](assets/chlimage_1-80.png)

Veillez à **Enregistrer tout** et à répliquer le code personnalisé sur toutes les instances AEM (le code personnalisé n’est pas inclus lorsque le contenu du site de la communauté est publié à partir de la console).

La pratique recommandée pour la réplication du code personnalisé consiste à [créer un package](../../help/sites-administering/package-manager.md#creating-a-new-package) et le déployer sur toutes les instances.

## Exportation d’un site de la communauté {#exporting-a-community-site}

Une fois un site communautaire créé, il est possible d&#39;exporter le site sous la forme d&#39;un package AEM stocké dans le gestionnaire de packages et disponible pour téléchargement et téléchargement.

Cette information est disponible à partir de la [console Sites communautaires](sites-console.md#exporting-the-site).

Notez que l’UGC et le code personnalisé ne sont pas inclus dans le package du site de la communauté.

Pour exporter l’UGC, utilisez l’[outil de migration AEM Communities UGC Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration), un outil de migration open source disponible sur GitHub.

## Suppression d&#39;un site de la communauté {#deleting-a-community-site}

Depuis AEM Communities 6.3 Service Pack 1, l’icône Supprimer le site s’affiche en survolant le site de la communauté à partir de la console Communautés > Sites. Au cours du développement, si vous souhaitez supprimer un site communautaire et un début actualisé, vous pouvez utiliser cette fonctionnalité. La suppression d’un site communautaire supprime les éléments suivants qui lui sont associés :

* [UGC](#user-generated-content)
* [Groupes d’utilisateurs](#community-user-groups)
* [Ressources](#enablement-assets)
* [Enregistrements de base de données](#database-records)

### Identifiant de site unique de la communauté {#community-unique-site-id}

Pour identifier l’identifiant de site unique associé au site de la communauté, utilisez CRXDE :

* Accédez à la racine de langue du site, telle que `/content/sites/*<site name>*/en/rep:policy`

* Recherchez le noeud `allow<#>` avec un `rep:principalName` au format `rep:principalName = *community-enable-nrh9h-members*`

* L&#39;identifiant de site est le troisième composant de `rep:principalName`
Par exemple, si 
`rep:principalName = community-enable-nrh9h-members`

   * **nom**  du site=  *activer*
   * **ID**  du site=  *nrh9h*
   * **ID**  de site unique=  *enable-nrh9h*

### Contenu généré par l&#39;utilisateur {#user-generated-content}

Obtenez le projet community-srp-tools de Github :

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Il contient une servlet pour supprimer toutes les UGC de tout SRP.

Tout UGC peut être supprimé ou pour un site spécifique, par exemple :

* path=/content/usergenerate/asi/mongo/content/sites/engagement

Cela supprime uniquement le contenu généré par l’utilisateur (saisi lors de la publication) et non le contenu créé (saisi lors de la création). Par conséquent, [les noeuds fantômes](srp.md#shadownodes) ne sont pas affectés.

### Groupes d’utilisateurs de la communauté {#community-user-groups}

Sur toutes les instances d’auteur et de publication, dans la [console de sécurité](../../help/sites-administering/security.md), recherchez et supprimez les [groupes d’utilisateurs](users.md) qui sont :

* Préfixe avec `community`
* Suivi de [l&#39;identifiant de site unique](#community-unique-site-id)

Par exemple, `community-engage-x0e11-members`.

### Ressources d&#39;activation {#enablement-assets}

Depuis la console principale :

* Sélectionner **[!UICONTROL Ressources]**
* Entrez le mode **[!UICONTROL Sélectionner]**
* Sélectionnez le dossier nommé avec l&#39;[identifiant de site unique](#community-unique-site-id)
* Sélectionnez **[!UICONTROL Supprimer]** (peut-être doit-on sélectionner **[!UICONTROL Plus...]**)

### Enregistrements de base de données {#database-records}

Il n&#39;existe aucun outil permettant de supprimer de manière sélective les entrées de base de données pour un site communautaire d&#39;activation spécifique.

Lorsque tous les sites de la communauté sont supprimés, déposez les options enablementdb et scormenginedb à l’aide de MySQL Workbench.
