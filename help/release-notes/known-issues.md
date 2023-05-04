---
title: Problèmes connus dans AEM 6.4
seo-title: Known Issues in AEM 6.4
description: Problèmes connus dans Adobe Experience Manager 6.4
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 10%

---

# Problèmes connus {#known-issues}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page contient la liste des problèmes connus d’Adobe Experience Manager 6.4, publiée en avril 2018. Pour plus d’informations sur les problèmes connus, [support technique](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr).

## Périphériques hybrides {#hybrid-devices}

Les périphériques hybrides ne sont pas pris en charge. Plusieurs problèmes peuvent être rencontrés lors de l’utilisation de tels appareils. Les procédures suggérées suivantes permettent de résoudre de nombreux problèmes :

Si vous utilisez Google Chrome comme navigateur :

* Type `chrome://flags/` dans la barre d’adresse et appuyez sur Entrée.
* Cliquez sur Activer les événements tactiles > Désactivé.
* Redémarrez le navigateur (tous les onglets et fenêtres).

Si vous utilisez Mozilla Firefox comme navigateur :

* Type `about:config` dans la barre d’adresse et appuyez sur Entrée.
* Filtrez les paramètres sur `dom.w3c`.
* Assurez-vous que les paramètres sont `0` et `false`.
* Redémarrez le navigateur.

Si vous utilisez Microsoft Edge comme navigateur :

* Type `about:flags` dans la barre d’adresse et appuyez sur Entrée.
* Accédez à Fonctionnalités expérimentales , puis **[!UICONTROL Touche]**.
* Cliquez sur **[!UICONTROL Activation des événements tactiles]**.
* Sélectionner **[!UICONTROL Toujours désactivé]**.
* Redémarrez le navigateur.

## Plateforme {#platform}

* **Tableau de bord des opérations :** La barre de progression n’est pas affichée lorsque l’extension .zip est manquante dans le fichier de sauvegarde. (GRANITE-10713)
* **HTL :** L’objet Use Java avec un espace de fin dans la déclaration du package gèle le SightlyJavaCompilerService (GRANITE-20836).
* **Apache Felix/Sling :** Fichier de configuration toujours présent dans le référentiel, même après configuration.delete() (GRANITE-20618)
* **Paramètres du cloud :** La console est rompue après la modification du conteneur de configuration (GRANITE-20726)
* **Sécurité :** L’intégration IMS échoue avec le chemin de contexte personnalisé (GRANITE-20639)
* **Sécurité :** Amélioration du classement JAAS par défaut des modules de connexion SSO, externe et par défaut (GRANITE-20590)
* **Outils - CRX DE Lite :** L’affichage des propriétés continue à augmenter (GRANITE-12040)
* **Outils - CRX DE Lite :** Impossible d’enregistrer les modifications apportées aux types de valeur &quot;Long&quot;, sauf si vous double-cliquez sur Nom de la propriété (GRANITE-12351).

* **Outils - CRX DE Lite :** La recherche ctrl+F sur les fichiers texte ouverts reste bloquée sur la recherche RegExp (GRANITE-5996).

* **Outils - CRX DE Lite :** La propriété de noeud ne s’affiche pas après avoir renommé le noeud (GRANITE-7160).
* **Interface utilisateur :** Menu déroulant &quot;plus...&quot; n’affiche pas tous les éléments lorsqu’ils sont ouverts sur un élément contextuel dans IE et Firefox (GRANITE-16326).
* **Interface utilisateur :** L’info-bulle est masquée lors de l’utilisation d’une disposition à colonnes fixes avec 2 colonnes côte à côte (GRANITE-16869).
* **Interface utilisateur :** Erreur non gérée lors de l’emprunt de l’identité d’un utilisateur qui n’existe pas (GRANITE-23228). Solution de contournement par [implémentation d’un gestionnaire d’erreurs](/help/sites-developing/customizing-errorhandler-pages.md) pour personnaliser le message d’erreur.

* **Omnisearch :** Les recherches avec barre oblique inverse provoquent une exception (GRANITE-11769)
* **Omnisearch :** L’ouverture de &quot;Paramètres d’affichage&quot; en mode Liste entraîne la modification du filtre de recherche (GRANITE-16524).
* **Omnisearch :** Liste incorrecte des configurations de colonne affichée lors de la recherche de ressources à partir de Sites (GRANITE-16527)

* **Omnisearch :** Les prédicats du rail de gauche s’entendent avec la requête du serveur Omni-recherche (GRANITE-20524)
* **Omnisearch :** Omnisearch ne prend pas en charge les chemins de contexte (GRANITE-16044).

## Ressources {#assets}

* **Rechercher**: La recherche ne renvoie aucun résultat si la chaîne de recherche commence par un espace blanc. [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Rechercher**: Dans l’interface utilisateur classique et les balises ne sont pas visibles dans la recherche (CQ-4235239)

* **Interface utilisateur**: L’interface utilisateur des ressources ne répond plus après Copier-coller et Sélectionner tout (CQ-4236142)

* **Interface utilisateur**: Impossible de déplacer les ressources après le chargement différé (CQ-4236134)

* **Rapports**: Erreur lors de la création du rapport Modification d’une ressource (CQ-4239744)

* **Rapports**: La génération de rapports de ressources standard planifiés échoue de manière incohérente (certains rapports restent en file d’attente) (CQ-4239089)

* **Métadonnées**: Lors de l’ajout d’un champ de texte à plusieurs valeurs au schéma de ressource, la règle de cascade de champ obligatoire ne fonctionne pas (CQ-4239333).

* **Brand Portal**: La publication sur Brand Portal ne fonctionne pas pour les collections (CQ-4238731)

* **Télécharger**: Lors du chargement de ressources dont le nom de fichier contient des caractères spéciaux, le message d’erreur de validation relatif aux caractères non autorisés ne s’affiche pas pour chaque ressource. Bien qu’elle s’affiche uniquement pour la première ressource, l’interface indique clairement à l’utilisateur que le nom de fichier de la ressource fournie n’est pas autorisé. (CQ-4256876)

## Communities {#communities}

* **Modération** - Impossible de supprimer la publication parente en tant qu’opération de suppression unique dans l’interface utilisateur de modération en bloc (CQ-4236797)

* **Console** - Le lien Nom d’utilisateur ou Mot de passe oublié redirige vers la page de connexion au lieu du formulaire de récupération de mot de passe correspondant (CQ-4237682).

## Forms {#forms}

### Installation et déploiement

* (AEM Forms JEE uniquement) Lorsque vous démarrez le serveur d’applications JBoss lors de l’exécution de Configuration Manager, les erreurs d’appel EJB et d’échec d’amorçage sont renvoyées. Vous pouvez toutefois les ignorer. (Réf. CQ-4229793)
* Au démarrage d’AEM Forms, l’avertissement `SAX Security Manager could not be setup` s’affiche. (CQ-4297403)

### Communications interactives

* L’interface utilisateur de l’agent prend un certain temps pour charger les communications interactives qui incluent des éléments de graphique ou d’image. (CQ-4236630)
* Le format d’affichage des données dans l’aperçu avant impression est jj-mm-aaaa alors que dans l’aperçu web est `dd-mmm-yy` (CQ-4237045)
* Le canal web de communication interactive ne prend en charge que les listes triées et non triées. Dans les fragments de document de liste, la mise en retrait et la mise en retrait composites ne sont pas prises en charge pour le canal web de la communication interactive. (CQ-4233672)
* Les problèmes suivants sont observés lorsque le canal web se synchronise avec le canal d’impression :

   * La synchronisation du canal web prend un certain temps lors du premier basculement du canal d’impression.
   * Le canal web ne se synchronise pas si le canal d’impression comprend un composant graphique non configuré. Pour résoudre ce problème, supprimez le composant de graphique et resynchronisez-le.
   * La synchronisation échoue parfois avec l’erreur &quot;Une erreur s’est produite lors de la synchronisation de la Live Copy&quot;. Pour résoudre ce problème, actualisez la page.
   * Le texte statique d’un fragment de mise en page est remplacé par le nom de la cellule du tableau lorsque la première colonne du tableau est une colonne d’en-tête dans le modèle de canal d’impression.
   * Impossible d’ajouter des composants ou des ressources à un autre emplacement qu’au bas d’une communication de canal web. Pour le placer à un autre emplacement, ajoutez un panneau au bas du canal web et réorganisez-le à l’aide de l’arborescence de contenu.
   * Peut déplacer du contenu dans la zone cible héritée du canal web sans supprimer l’héritage de la Live Copy.

(CQ-4239780)

### Intégration de données

* Les configurations d’authentification des services web SOAP ne sont pas visibles et ne peuvent donc pas être configurées dans les services cloud. Pour résoudre le problème :

   1. Dans la console CRXDE Lite, accédez au noeud suivant.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Mettez à jour la valeur de la propriété value de la même manière que la valeur de la propriété text.
   1. Cliquez sur Enregistrer tout pour enregistrer la configuration.

(CQ-4238462)

### Intégration d’Acrobat Sign

* Le planificateur Acrobat Sign cesse de fonctionner par intermittence. Par conséquent, les formulaires en attente de signature ne passent pas à l’envoi. Pour résoudre le problème, redémarrez l’événement **Prise en charge du planificateur Apache Sling** à partir de la console web d’AEM à l’adresse https://[*server*]:[*port*]/system/console/bundles.

### Création de Forms adaptatif

* Le composant de graphique des formulaires adaptatifs prend plus d’espace qu’il ne le fait normalement.
* Une exception est renvoyée lors de l’enregistrement des propriétés des formulaires adaptatifs, des fragments de formulaire adaptatif ou des communications interactives dans l’interface utilisateur de Forms Manager.
* Le nombre maximal de caractères spécifié pour un champ de texte de formulaire adaptatif n’est pas honoré sur les périphériques Samsung sous Android 6.0. (Réf. CQ-4235205)
* Lorsque vous envoyez un formulaire contenant un champ de chargement HTML standard d’un appareil iOS d’Apple, le contenu du fichier n’est parfois pas envoyé et un fichier de 0 octet est reçu à l’autre bout. Apple iOS 15.1 apporte un correctif pour le problème.

