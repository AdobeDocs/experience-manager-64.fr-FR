---
title: Problèmes connus dans AEM 6.4
seo-title: Problèmes connus dans AEM 6.4
description: Problèmes connus dans Adobe Experience Manager 6.4
seo-description: Problèmes connus dans Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 46%

---

# Problèmes connus {#known-issues}

Cette page contient la liste des problèmes connus d’Adobe Experience Manager 6.4, publiée en avril 2018. Pour plus d’informations sur les problèmes connus, [contactez le support](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr).

## Appareils hybrides {#hybrid-devices}

Les appareils hybrides ne sont pas pris en charge. Plusieurs problèmes peuvent être rencontrés lors de l’utilisation de tels appareils. Les procédures suggérées suivantes permettent de résoudre de nombreux problèmes :

Si vous utilisez Google Chrome comme navigateur :

* Saisissez `chrome://flags/` dans la barre d’adresse et appuyez sur Entrée.
* Cliquez sur Activer les événements tactiles > Désactivé.
* Redémarrez le navigateur (l’ensemble des onglets et des fenêtres).

Si vous utilisez Mozilla Firefox comme navigateur :

* Saisissez `about:config` dans la barre d’adresse et appuyez sur Entrée.
* Filtrez les paramètres sur `dom.w3c`.
* Vérifiez que les paramètres sont `0` et `false`.
* Redémarrez le navigateur.

Si vous utilisez Microsoft Edge comme navigateur :

* Saisissez `about:flags` dans la barre d’adresse et appuyez sur Entrée.
* Faites défiler l’écran jusqu’à Fonctionnalités expérimentales, puis **[!UICONTROL Touch]**.
* Cliquez sur **[!UICONTROL Activer les événements tactiles]**.
* Sélectionnez **[!UICONTROL Toujours désactivé]**.
* Redémarrez le navigateur.

## Plate-forme {#platform}

* **Tableau de bord des opérations :** la barre de progression n’apparaît pas lorsque l’extension .zip est manquante dans le fichier de sauvegarde. (GRANITE-10713)
* **HTL :** l’objet Java Use avec un espace de fin dans la déclaration du package gèle SightlyJavaCompilerService (GRANITE-20836).
* **Apache Felix/Sling : le fichier de configuration**  reste présent dans le référentiel même après configuration.delete() (GRANITE-20618)
* **Paramètres du cloud :** la console est rompue après la modification du conteneur de configuration (GRANITE-20726).
* **Sécurité :** l’intégration IMS échoue avec le chemin de contexte personnalisé (GRANITE-20639)
* **Sécurité :** amélioration du classement JAAS par défaut des modules de connexion SSO, externe et par défaut (GRANITE-20590)
* **Outils - CRX DE Lite :** l’affichage des propriétés continue à augmenter (GRANITE-12040)
* **Outils - CRX DE Lite :** impossible d’enregistrer les modifications apportées aux types de valeur &quot;Long&quot;, sauf si vous double-cliquez sur Nom de la propriété (GRANITE-12351).

* **Outils - CRX DE Lite : la recherche** ctrl+F sur les fichiers texte ouverts reste bloquée sur la recherche RegExp (GRANITE-5996).

* **Outils - CRX DE Lite : la propriété de noeud**  ne s’affiche pas après avoir renommé le noeud (GRANITE-7160).
* **Interface utilisateur :** Menu déroulant &quot;plus...&quot; n’affiche pas tous les éléments lorsqu’ils sont ouverts sur un élément contextuel dans IE et Firefox (GRANITE-16326).
* **Interface utilisateur :** l’info-bulle est masquée lors de l’utilisation d’une disposition à colonnes fixes avec 2 colonnes côte à côte (GRANITE-16869).
* **Interface utilisateur** : erreur non gérée lorsque vous empruntez l’identité d’un utilisateur qui n’existe pas (GRANIT -23228). Solution[ : mise en œuvre d’un gestionnaire d’erreur](/help/sites-developing/customizing-errorhandler-pages.md) pour personnaliser le message d’erreur.

* **Omnisearch :** les recherches avec barre oblique inverse provoquent une exception (GRANITE-11769).
* **Omnisearch :** l’ouverture de &quot;Paramètres d’affichage&quot; en mode Liste entraîne la modification du filtre de recherche (GRANITE-16524).
* **Omnisearch :** liste incorrecte des configurations de colonne affichée lors de la recherche de ressources à partir de sites (GRANITE-16527)

* **Omnisearch :** les prédicats de rail gauche s’entendent avec la demande de serveur Omnisearch (GRANITE-20524).
* **Omnisearch :** Omnisearch ne prend pas en charge les chemins de contexte (GRANITE-16044).

## Assets {#assets}

* **Rechercher** : La recherche ne renvoie aucun résultat si la chaîne de recherche commence par un espace  [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Rechercher** : Dans l’interface utilisateur classique et les balises ne sont pas visibles dans la recherche (CQ-4235239)

* **Interface utilisateur** : L’interface utilisateur des ressources ne répond plus après Copier-coller et Sélectionner tout (CQ-4236142)

* **Interface utilisateur** : Impossible de déplacer les ressources après le chargement différé (CQ-4236134)

* **Rapports** : Erreur lors de la création du rapport Modification d’une ressource (CQ-4239744)

* **Rapports** : La génération de rapports de ressources standard planifiés échoue de manière incohérente (certains rapports restent en file d’attente) (CQ-4239089)

* **Métadonnées** : Lors de l’ajout d’un champ de texte à plusieurs valeurs au schéma de ressource, la règle de cascade de champ obligatoire ne fonctionne pas (CQ-4239333).

* **Brand Portal** : La publication sur Brand Portal ne fonctionne pas pour les collections (CQ-4238731)

* **Téléchargement** : lors du téléchargement de ressources dont le nom de fichier contient des caractères spéciaux, le message d’erreur de validation relatif aux caractères non autorisés ne s’affiche pas pour chacune des ressources. Bien que ce message s’affiche uniquement pour la première ressource, l’interface indique clairement à l’utilisateur que le nom de fichier de la ressource fournie n’est pas autorisé. (CQ-4256876)

## Communities {#communities}

* **Modération :** impossible de supprimer une publication parente en une seule opération de suppression à partir de l’interface utilisateur de modération en masse (CQ-4236797).

* **Console**  : le lien Nom d’utilisateur ou Mot de passe oublié redirige vers la page de connexion au lieu du formulaire de récupération de mot de passe correspondant (CQ-4237682).

## Formulaires {#forms}

### Installation et déploiement

* (AEM Forms JEE uniquement) En cas d’amorçage d’un serveur d’applications JBoss en cours d’exécution, le gestionnaire de configuration renvoie un appel EJB et des erreurs d’échec de l’amorçage. Vous pouvez toutefois les ignorer. (Réf. CQ-4229793)
* Lorsque AEM Forms est démarré, l’avertissement `SAX Security Manager could not be setup` s’affiche. (CQ-4297403)

### Communications interactives

* L’interface utilisateur de l’agent prend un certain temps à charger les communications interactives qui incluent des éléments d’images ou de graphiques. (CQ-4236630)
* Le format d’affichage des données dans l’aperçu avant impression est jj-mm-aaaa alors que dans l’aperçu web est `dd-mmm-yy` (CQ-4237045)
* Le canal web de communication interactive (Interactive Communication Web) prend uniquement en charge les listes ordonnées et désordonnées. Dans des fragments de document de liste, la mise en retrait et le listage composites ne sont pas pris en charge pour le canal web de la communication interactive. (CQ-4233672)
* Les problèmes suivants sont observés lors de la synchronisation du canal web avec le canal d’impression :

   * Le canal web prend un certain temps à se synchroniser lors du changement initial à partir du canal d’impression.
   * Le canal web ne se synchronise pas si le canal d’impression comprend un composant de graphique non configuré. Pour résoudre le problème, supprimez le composant de graphique et synchronisez à nouveau.
   * La synchronisation échoue parfois avec l’erreur &quot;Une erreur s’est produite lors de la synchronisation de la Live Copy&quot;. Actualisez la page pour résoudre l’erreur.
   * Le texte statique d’un fragment de disposition est remplacé par le nom d’une cellule de tableau lorsque la première colonne du tableau est une colonne d’en-tête dans le modèle de canal d’impression.
   * Impossible d’ajouter des composants ou des actifs dans tout autre emplacement que la partie inférieure d’une communication de canal web. Pour les placer à un autre emplacement, ajoutez un panneau dans la partie inférieure du canal web et réorganisez l’arborescence de contenu.
   * Impossible de déplacer du contenu dans une zone cible héritée du canal web sans supprimer l’héritage de Live Copy.

(CQ-4239780)

### Intégration de données

* Les configurations d’authentification des services web basés sur SOAP ne sont pas visibles et ne peuvent donc pas être configurées dans les services cloud. Pour résoudre le problème :

   1. Dans la console CRXDE Lite, accédez au nœud suivant.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Mettez à jour la valeur de la propriété value de la même manière que la valeur de la propriété text.
   1. Cliquez sur Enregistrer tout pour enregistrer la configuration.

(CQ-4238462)

### Intégration d’Adobe Sign

* Le planificateur d’Adobe Sign cesse de fonctionner par moments, ce qui empêche les formulaires en attente de signature de passer à la soumission. Pour résoudre ce problème, redémarrez le lot **Prise en charge du planificateur Apache Sling** à partir de la console web d’AEM à l’adresse https://[*server*]:[*port*]/system/console/bundles.

### Création de formulaires adaptatifs

* Le composant Graphique des formulaires adaptatifs prend davantage d’espace qu’il en prend normalement.
* Une exception est renvoyée lors de l’enregistrement des propriétés des formulaires adaptatifs, des fragments de formulaire adaptatif ou des communications interactives dans l’interface utilisateur de Forms Manager.
* Le nombre maximal de caractères spécifié pour un champ de texte de formulaire adaptatif n’est pas honoré sur les périphériques Samsung sous Android 6.0. (Réf. CQ-4235205)
