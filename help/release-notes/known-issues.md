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
translation-type: tm+mt
source-git-commit: 9b6c1efe1f6281892648c7b41820856d2e3fcac1

---


# Problèmes connus {#known-issues}

Cette page répertorie les problèmes connus d’Adobe Experience Manager 6.4, publiés en avril 2018. Pour plus d’informations sur les problèmes connus, [contactez l’assistance](https://helpx.adobe.com/support/experience-manager.html).

## Appareils hybrides {#hybrid-devices}

Les appareils hybrides ne sont pas pris en charge. Plusieurs problèmes peuvent être rencontrés lors de l’utilisation de tels appareils. Les procédures suggérées suivantes permettent de résoudre de nombreux problèmes :

Si vous utilisez Google Chrome comme navigateur :
* Type `chrome://flags/` in the address bar and press Enter.
* Cliquez sur Activer les événements tactiles > Désactivé.
* Redémarrez le navigateur (l’ensemble des onglets et des fenêtres).

Si vous utilisez Mozilla Firefox comme navigateur :
* Type `about:config` in the address bar and press Enter.
* Filter the settings to `dom.w3c`.
* Vérifiez que les paramètres sont `0` et `false`.
* Redémarrez le navigateur.

Si vous utilisez Microsoft Edge comme navigateur :

* Type `about:flags` in the address bar and press Return.
* Scroll to Experimental features then **[!UICONTROL Touch]**.
* Cliquez sur **[!UICONTROL Activer les événements]** tactiles.
* Select **[!UICONTROL Always Off]**.
* Redémarrez le navigateur.

## Plate-forme {#platform}

* **Tableau de bord des opérations :** la barre de progression n’apparaît pas lorsque l’extension .zip est manquante dans le fichier de sauvegarde. (GRANITE-10713)
* **** HTL : L’objet Java Use avec l’espace de fin dans la déclaration du package gèle SightlyJavaCompilerService (GRANITE-20836).
* **** Apache Felix/Sling : Fichier de configuration toujours présent dans le référentiel, même après configuration.delete() (GRANITE-20618)
* **** Paramètres du cloud : La console est rompue après la modification du conteneur de configuration (GRANITE-20726)
* **** Sécurité : Échec de l&#39;intégration IMS avec le chemin de contexte personnalisé (GRANITE-20639)
* **** Sécurité : Amélioration du classement JAAS par défaut des modules de connexion SSO, externes et par défaut (GRANITE-20590)
* **** Outils - CRX DE Lite: Déplacement de la vue Propriétés vers le haut (GRANITE-12040)
* **** Outils - CRX DE Lite: Impossible d&#39;enregistrer les modifications dans les types de valeurs &quot;Long&quot; sauf si vous double-cliquez sur Nom de propriété (GRANITE-12351)

* **** Outils - CRX DE Lite: ctrl+F sur les fichiers texte ouverts reste bloqué sur la recherche RegExp (GRANITE-5996)

* **** Outils - CRX DE Lite: Propriété de noeud non affichée après avoir renommé le noeud (GRANITE-7160)
* **** IU : &quot;Plus...&quot; n’affiche pas tous les éléments lorsqu’ils sont ouverts dans un élément contextuel sur IE et Firefox (GRANITE-16326)
* **** IU : L’info-bulle est masquée lors de l’utilisation d’une disposition à colonnes fixes avec deux colonnes côte à côte (GRANITE-16869).
* **Interface utilisateur** : erreur non gérée lorsque vous empruntez l’identité d’un utilisateur qui n’existe pas (GRANIT -23228). Solution[ : mise en œuvre d’un gestionnaire d’erreur](/help/sites-developing/customizing-errorhandler-pages.md) pour personnaliser le message d’erreur.

* **** Omnisearch : Recherches avec une exception de cause de barre oblique inverse (GRANITE-11769)
* **** Omnisearch : L’ouverture de &quot;Paramètres d’affichage&quot; en mode Liste provoque la modification du filtre de recherche (GRANITE-16524).
* **** Omnisearch : Liste incorrecte des configurations de colonne affichées lors de la recherche de ressources à partir de sites (GRANITE-16527)

* **Omnisearch :** les prédicats de rail gauche s’entendent avec la demande de serveur Omnisearch (GRANITE-20524).
* **** Omnisearch : Omnisearch ne prend pas en charge les chemins de contexte (GRANITE-16044)

## Assets {#assets}

* **Rechercher**: La recherche ne renvoie aucun résultat si la chaîne de recherche commence par un espace blanc [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Rechercher**: Dans l’interface utilisateur classique et les balises ne sont pas visibles dans la recherche (CQ-4235239)

* **Interface utilisateur**: L’interface utilisateur des ressources ne répond plus après Copier-coller et Sélectionner tout (CQ-4236142)

* **Interface utilisateur**: Impossible de déplacer les fichiers après un chargement différé (CQ-4236134)

* **Rapports**: Erreur lors de la création du rapport Modification des ressources (CQ-4239744)

* **Rapports**: La génération régulière et planifiée de rapports sur les ressources échoue de manière incohérente (certains rapports restent en file d’attente) (CQ-4239089)

* **Métadonnées**: Lors de l’ajout d’un champ de texte à plusieurs valeurs au schéma d’actif, la règle de cascade de champ obligatoire ne fonctionne pas (CQ-4239333)

* **BrandPortal**: La publication sur BrandPortal ne fonctionne pas pour les collections (CQ-4238731)

* **Téléchargement** : lors du téléchargement de ressources dont le nom de fichier contient des caractères spéciaux, le message d’erreur de validation relatif aux caractères non autorisés ne s’affiche pas pour chacune des ressources. Bien que ce message s’affiche uniquement pour la première ressource, l’interface indique clairement à l’utilisateur que le nom de fichier de la ressource fournie n’est pas autorisé. (CQ-4256876)

## Communities {#communities}

* **Modération :** impossible de supprimer une publication parente en une seule opération de suppression à partir de l’interface utilisateur de modération en masse (CQ-4236797).

* **Console** - Le lien Nom d’utilisateur ou Mot de passe oublié redirige vers la page de connexion au lieu du formulaire de récupération du mot de passe correspondant (CQ-4237682).

## Forms {#forms}

### Installation et déploiement

* (AEM Forms JEE uniquement) En cas d’amorçage d’un serveur d’applications JBoss en cours d’exécution, le gestionnaire de configuration renvoie un appel EJB et des erreurs d’échec de l’amorçage. Vous pouvez toutefois les ignorer. (Réf. CQ-4229793)

### Communications interactives

* L’interface utilisateur de l’agent prend un certain temps à charger les communications interactives qui incluent des éléments d’images ou de graphiques. (CQ-4236630)
* The data display format in print preview is dd-mm-yyyy while in the web preview is `dd-mmm-yy` (CQ-4237045)
* Le canal web de communication interactive (Interactive Communication Web) prend uniquement en charge les listes ordonnées et désordonnées. Dans des fragments de document de liste, la mise en retrait et le listage composites ne sont pas pris en charge pour le canal web de la communication interactive. (CQ-4233672)
* Les problèmes suivants sont observés lors de la synchronisation du canal web avec le canal d’impression :

   * Le canal web prend un certain temps à se synchroniser lors du changement initial à partir du canal d’impression.
   * Le canal web ne se synchronise pas si le canal d’impression comprend un composant de graphique non configuré. Pour résoudre le problème, supprimez le composant de graphique et synchronisez à nouveau.
   * La synchronisation échoue parfois avec l’erreur &quot;Une erreur s’est produite lors de la synchronisation de Live Copy&quot;. Actualisez la page pour résoudre l’erreur.
   * Le texte statique d’un fragment de disposition est remplacé par le nom d’une cellule de tableau lorsque la première colonne du tableau est une colonne d’en-tête dans le modèle de canal d’impression.
   * Impossible d’ajouter des composants ou des actifs dans tout autre emplacement que la partie inférieure d’une communication de canal web. Pour les placer à un autre emplacement, ajoutez un panneau dans la partie inférieure du canal web et réorganisez l’arborescence de contenu.
   * Impossible de déplacer du contenu dans une zone cible héritée du canal web sans supprimer l’héritage de Live Copy.

(CQ-4239780)

### Intégration de données

* Les configurations d’authentification des services web basés sur SOAP ne sont pas visibles et ne peuvent donc pas être configurées dans les services cloud. Pour résoudre le problème :

   1. Dans la console CRXDE Lite, accédez au nœud suivant.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigWizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Mettez à jour la valeur de la propriété value pour qu’elle soit identique à la valeur de la propriété text.
   1. Cliquez sur Enregistrer tout pour enregistrer la configuration.

(CQ-4238462)

### Intégration d’Adobe Sign

* Le planificateur d’Adobe Sign cesse de fonctionner par moments, ce qui empêche les formulaires en attente de signature de passer à la soumission. To resolve the issue, restart the **Apache Sling Scheduler Support** bundle from AEM web console at https://[*server*]:[*port*]/system/console/bundles.

### Création de formulaires adaptatifs

* Le composant Graphique des formulaires adaptatifs prend davantage d’espace qu’il en prend normalement.
* Une exception est renvoyée lors de l’enregistrement des propriétés pour les formulaires adaptatifs, les fragments de formulaire adaptatif ou les communications interactives dans l’interface utilisateur de Forms Manager.
* Le nombre maximal de caractères spécifié pour un champ de texte de formulaire adaptatif n’est pas honoré sur les périphériques Samsung sous Android 6.0. (Réf. CQ-4235205)
