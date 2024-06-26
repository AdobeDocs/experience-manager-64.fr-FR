---
title: Configuration manuelle de l’intégration à Adobe Target
seo-title: Manually Configuring the Integration with Adobe Target
description: Découvrez comment configurer manuellement l’intégration avec Adobe Target.
seo-description: Learn how to manually configure the integration with Adobe Target.
uuid: 0bb76a65-f981-4cc5-bee8-5feb3297137c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 20c8eb1d-5847-4902-b7d3-4c3286423b46
exl-id: 6abadd53-dab1-4e3b-84d8-10374e8a305c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2215'
ht-degree: 62%

---

# Configuration manuelle de l’intégration à Adobe Target {#manually-configuring-the-integration-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez soit modifier les configurations de l’assistant de souscription que vous avez effectuées lors de l’utilisation de l’assistant, soit intégrer manuellement Adobe Target sans utiliser l’assistant.

## Modification des configurations de l’assistant de souscription {#modifying-the-opt-in-wizard-configurations}

L’[assistant de souscription](/help/sites-administering/opt-in.md) qui [intègre AEM à Adobe Target](/help/sites-administering/target.md) crée automatiquement une configuration de cloud Target appelée Configuration Target mise en service. L’assistant crée également une structure Target pour la configuration de cloud appelée Structure Target mise en service. Vous pouvez modifier les propriétés de la configuration et de la structure cloud si nécessaire.

Vous pouvez également configurer Adobe Target pour utiliser Adobe Target en tant que source de création de rapports lors du ciblage de contenu en configurant la configuration d’Analytics Cloud A4T.

Pour trouver la configuration et le framework de cloud, accédez à **Services cloud** via **Outils** > **Déploiement** > **Cloud**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))\
Sous Adobe Target, cliquez ou appuyez sur . **Afficher les configurations**.

### Propriétés de configuration de Target configurées {#provisioned-target-configuration-properties}

Les valeurs de propriété suivantes sont utilisées dans la configuration cloud Configuration de Target mise en service créée par l’assistant d’Opt-in :

* **Code client :** tel que saisi dans l’assistant de souscription.
* **E-mail :** tel que saisi dans l’assistant de souscription.
* **Mot de passe :** tel que saisi dans l’assistant de souscription.
* **Type d’API :** REST.
* **Synchroniser les segments à partir d’Adobe Target :** sélectionné.

* **Bibliothèque cliente :** mbox.js.
* **Utiliser la gestion dynamique des balises pour diffuser la bibliothèque cliente :** non sélectionné. Sélectionnez cette option si vous [utilisez la gestion dynamique des balises](/help/sites-administering/dtm.md) ou un autre système de gestion des balises pour héberger le fichier mbox.js ou AT.js. Adobe vous recommande d’utiliser la gestion dynamique des balises plutôt qu’AEM pour livrer la bibliothèque.

* **Fichier mbox.js personnalisé :** aucun fichier n’est spécifié, pour que le fichier mbox.js par défaut soit utilisé. Spécifiez un fichier mbox.js personnalisé selon vos besoins. S’affiche uniquement si vous avez sélectionné mbox.js.
* **AT.js personnalisé :** aucun fichier n’est spécifié, pour que le fichier AT.js par défaut soit utilisé. Spécifiez un fichier AT.js personnalisé selon vos besoins.  S’affiche uniquement si vous avez sélectionné AT.js.

>[!NOTE]
>
>Dans AEM 6.3, vous pouvez sélectionner le fichier de bibliothèque cible, [AT.JS](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-download.html?lang=fr), qui est une nouvelle bibliothèque de mise en œuvre pour Adobe Target conçue à la fois pour les mises en œuvre web standard et les applications d’une seule page.
>
>AT.js offre plusieurs améliorations par rapport à la bibliothèque mbox.js :
>
>* Amélioration des temps de chargement des pages pour les implémentations web
>* Amélioration de la sécurité
>* Meilleures options de mise en oeuvre pour les applications d’une seule page
>* AT.js contient les composants qui étaient inclus dans target.js. Il n’y a donc plus d’appel à target.js.


### Propriétés de structure de Target configurées {#provisioned-target-framework-properties}

La structure de Target mise en service créée par l’assistant de souscription est configurée pour envoyer des données contextuelles à partir du magasin de données de profil. Les éléments de données du magasin relatifs à l’âge et au sexe sont envoyés à Target par défaut. Votre solution nécessite probablement l’envoi de paramètres supplémentaires.

![chlimage_1-158](assets/chlimage_1-158.png)

Vous pouvez configurer la structure pour envoyer des informations contextuelles supplémentaires à Target, comme décrit dans la section [Ajout d’une structure Target](/help/sites-administering/target-configuring.md#adding-a-target-framework).

### Configuration de la configuration d’Analytics Cloud A4T {#configuring-a-t-analytics-cloud-configuration}

Vous pouvez configurer Adobe Target pour utiliser Adobe Analytics comme source de création de rapports lors du ciblage du contenu.

Pour ce faire, vous devez spécifier la configuration de cloud d’A4T pour connecter votre configuration de cloud Adobe Target de la façon suivante :

1. Accédez à **Services cloud** via le **logo AEM** > **Outils** > **Déploiement** > **Services cloud**.
1. Dans la section **Adobe Target**, cliquez sur **Configurer maintenant**.
1. Reconnectez-vous à votre configuration Adobe Target.
1. Dans le **Configuration d’Analytics Cloud A4T** , sélectionnez la structure.

   >[!NOTE]
   >
   >Seules les configurations d’analyse activées pour A4T sont disponibles.
   >
   >En configurant A4T avec AEM, vous risquez de voir une entrée de référence de configuration manquante. Pour sélectionner la structure d’analyse, procédez comme suit :
   > 
   >1. Accédez à **Outils** > **Général** > **CRXDE Lite**.
   1. Accédez à **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**.
   1. Définissez la propriété **désactiver** sur **false**.
   1. Appuyez ou cliquez sur **Tout enregistrer**.


   ![chlimage_1-159](assets/chlimage_1-159.png)

   Cliquez sur **OK**. Lorsque vous ciblez du contenu avec Adobe Target, vous pouvez [sélectionner la source de votre rapport](/help/sites-authoring/content-targeting-touch.md).

## Intégration manuelle à Adobe Target {#manually-integrating-with-adobe-target}

Intégration manuelle avec Adobe Target au lieu d’utiliser l’assistant de souscription.

>[!NOTE]
Le fichier de bibliothèque cible, [AT.JS](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-download.html?lang=fr), est une nouvelle bibliothèque d’implémentation pour Adobe Target qui a été conçue pour les implémentations web classiques et les applications d’une seule page. Adobe vous recommande d’utiliser AT.js au lieu de mbox.js comme bibliothèque cliente.
AT.js offre plusieurs améliorations par rapport à la bibliothèque mbox.js :
* Amélioration des temps de chargement des pages pour les implémentations web
* Amélioration de la sécurité
* Meilleures options de mise en oeuvre pour les applications d’une seule page
* AT.js contient les composants qui étaient inclus dans target.js. Il n’y a donc plus d’appel à target.js.
>
Vous pouvez sélectionner AT.js ou mbox.js dans le menu déroulant **Bibliothèque cliente**.

### Création d’une configuration de cloud Target {#creating-a-target-cloud-configuration}

Pour permettre à AEM d’interagir avec Adobe Target, créez une configuration de cloud Target. Pour créer la configuration, vous fournissez le code client Adobe Target et les informations d’identification de l’utilisateur.

Vous créez la configuration de cloud Target une seule fois, car vous pouvez l’associer à plusieurs campagnes AEM. Si vous disposez de plusieurs codes client Adobe Target, créez une configuration pour chaque code client.

Vous pouvez configurer la configuration de cloud pour synchroniser les segments depuis Adobe Target. Si vous activez la synchronisation, les segments sont importés de Target en arrière-plan dès que la configuration du cloud est enregistrée.

Procédez comme suit pour créer une configuration cloud Target dans AEM :

1. Accédez à **Services cloud** via le **logo AEM** > **Outils** > **Déploiement** > **Services cloud**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   La page d’aperçu d’**Adobe Marketing Cloud** s’ouvre.

1. Dans la section **Adobe Target**, cliquez sur **Configurer maintenant**.
1. Dans la boîte de dialogue **Créer une configuration** :

   1. Donnez un **titre** à la configuration.
   1. Sélectionnez le modèle **Configuration d’Adobe Target**.
   1. Cliquez sur **Créer**.

   La boîte de dialogue de modification s’ouvre.

   ![chlimage_1-160](assets/chlimage_1-160.png)

   >[!NOTE]
   En configurant A4T avec AEM, vous risquez de voir une entrée de référence de configuration manquante. Pour sélectionner la structure d’analyse, procédez comme suit :
   1. Accédez à **Outils** > **Général** > **CRXDE Lite**.
   1. Accédez à **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**.
   1. Définissez la propriété **désactiver** sur **false**.
   1. Appuyez ou cliquez sur **Tout enregistrer**.


1. Dans la boîte de dialogue, saisissez les valeurs pour ces propriétés.

   * **Code client** : code client du compte Target.
   * **Courrier électronique**: Adresse électronique du compte Target.
   * **Mot de passe**: le mot de passe du compte Target.
   * **Type d’API**: REST ou XML
   * **Configuration d’A4T Analytics Cloud** : sélectionnez la configuration de cloud Analytics utilisée pour les objectifs et les mesures des activités de Target. Vous avez besoin de cette option si vous utilisez Adobe Analytics en tant que source de création de rapports lors du ciblage de contenu. Si vous ne voyez pas votre configuration cloud, consultez la remarque à ce sujet dans [Définition de la configuration cloud A4T Analytics](#configuring-a-t-analytics-cloud-configuration).

   * **Utiliser le ciblage précis** : par défaut, cette case est cochée. Si cette option est sélectionnée, la configuration du service cloud attend le chargement du contexte avant de charger le contenu. Voir la remarque suivante.
   * **Synchroniser les segments à partir d’Adobe Target** : sélectionnez cette option pour télécharger les segments définis dans Target pour les utiliser dans AEM. Vous devez sélectionner cette option lorsque la propriété Type d’API est REST, car les segments incorporés ne sont pas pris en charge, et vous devez toujours utiliser les segments de Target. (Notez que le terme AEM de &quot;segment&quot; équivaut à l’&quot;audience&quot; de Target.)
   * **Bibliothèque cliente** : indiquez si vous voulez la bibliothèque cliente mbox.js ou AT.js.
   * **Utiliser la gestion dynamique des balises pour diffuser la bibliothèque cliente** : sélectionnez cette option pour utiliser le mbox.js ou l’AT.js de la gestion dynamique des balises ou tout autre système de gestion des balises. Vous devez [configurer l’intégration de la gestion dynamique des balises](/help/sites-administering/dtm.md) pour utiliser cette option. Adobe vous recommande d’utiliser la gestion dynamique des balises plutôt qu’AEM pour livrer la bibliothèque.
   * **Fichier mbox.js personnalisé** : laissez ce champ vierge si vous avez coché la case Gestion dynamique des balises ou pour utiliser le fichier mbox.js par défaut. Vous pouvez également télécharger votre fichier mbox.js personnalisé. S’affiche uniquement si vous avez sélectionné mbox.js.
   * **AT.js personnalisé** : laissez ce champ vierge si vous avez coché la case Gestion dynamique des balises ou pour utiliser le fichier AT.js par défaut. Vous pouvez également télécharger votre fichier AT.js personnalisé. S’affiche uniquement si vous avez sélectionné AT.js.

   >[!NOTE]
   Par défaut, lorsque vous souscrivez à l’assistant de configuration Adobe Target, le ciblage précis est activé.
   Le ciblage précis implique que cette configuration du service cloud attend le chargement du contexte avant de charger le contenu. Par conséquent, en termes de performances, un ciblage précis peut créer un délai de quelques millisecondes avant le chargement du contenu.
   Le ciblage précis est toujours activé sur l’instance de création. Toutefois, sur l’instance de publication, vous pouvez choisir de le désactiver en désactivant la coche en regard de Ciblage précis dans la configuration du service cloud (**http://localhost:4502/etc/cloudservices.html**). Vous pouvez également activer et désactiver le ciblage précis pour chaque composant, quel que soit votre paramètre dans la configuration du service cloud.
   Si vous avez ***déjà*** créé les composants ciblés et si vous modifiez ce paramètre, vos modifications n’affectent pas ces composants. Vous devez apporter directement des modifications à ces composants.

1. Cliquez sur **Se connecter à Target** pour lancer la connexion à Target. Si la connexion est établie, le message ** Connexion réussie** s’affiche. Cliquez sur **OK** dans le message et **OK** dans la boîte de dialogue.

   Si vous ne pouvez pas vous connecter à Target, reportez-vous à la section [dépannage](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) .

### Ajout d’une structure Target {#adding-a-target-framework}

Une fois que vous avez configuré la configuration de cloud Target, ajoutez une structure Target. La structure identifie les paramètres par défaut qui sont envoyés à Adobe Target à partir des composants [ClientContext](/help/sites-administering/client-context.md) ou [ContextHub](/help/sites-administering/contexthub-config.md). Target utilise les paramètres pour déterminer les segments qui s’appliquent au contexte actuel.

Vous pouvez créer des structures multiples pour une même configuration Target. Les structures multiples s’avèrent utiles lorsque vous devez envoyer un jeu de paramètres différent à Target pour différentes sections de votre site web. Créez une structure pour chaque jeu de paramètres que vous avez besoin d’envoyer. Associez chaque section de votre site web à la structure appropriée. Notez qu’une page web ne peut utiliser qu’une seule structure à la fois.

1. Sur la page de configuration Target, cliquez sur le signe **+** en regard de Frameworks disponibles.
1. Dans la boîte de dialogue Créer un framework, spécifiez un **titre**, sélectionnez le **Framework Adobe Target** et cliquez sur **Créer**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

   La page de framework s’ouvre. Le sidekick fournit des composants qui représentent les informations de [ClientContext](/help/sites-administering/client-context.md) ou [ContextHub](/help/sites-administering/contexthub-config.md) que vous pouvez mettre en correspondance.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Faites glisser le composant ClientContext représentant les données que vous souhaitez utiliser pour mapper avec la cible de dépôt. Vous pouvez également faire glisser le composant **Boutique ContextHub** vers le framework.

   >[!NOTE]
   Lors de la mise en correspondance, les paramètres sont transmis à un mbox via des chaînes simples. Vous ne pouvez pas mapper des tableaux à partir de ContextHub.

   Par exemple, pour utiliser les **données du profil** des visiteurs de votre site afin de contrôler votre campagne Target, faites glisser le composant **Données du profil** vers la page. Les variables de données de profil qui sont disponibles pour la mise en correspondance des paramètres Target s’affichent.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Sélectionnez les variables que vous souhaitez rendre visibles pour le système Adobe Target en cochant la case **Partager** dans les colonnes appropriées.

   ![chlimage_1-164](assets/chlimage_1-164.png)

   >[!NOTE]
   La synchronisation des paramètres n’est qu’une seule voie : d’AEM à Adobe Target.

La structure est créée. Pour répliquer la structure sur l’instance de publication, utilisez la méthode **Activation de la structure** dans le sidekick.

### Association d’activités à la configuration du cloud Target  {#associating-activities-with-the-target-cloud-configuration}

Associez vos [activités AEM](/help/sites-authoring/activitylib.md) à la configuration de cloud Target afin de refléter les activités dans [Adobe Target](https://experienceleague.adobe.com/docs/target/using/experiences/offers/manage-content.html?=lang=fr).

>[!NOTE]
Les types d’activités disponibles sont déterminés par ce qui suit :
* Si la variable **xt_only** est activée sur le client Adobe Target (clientcode) utilisé côté AEM pour se connecter à Adobe Target, puis vous pouvez créer **only** Activités XT dans AEM.
* Si la variable **xt_only** options est **not** activée sur le client Adobe Target (clientcode), vous pouvez créer **both** Activités XT et A/B dans AEM.
>
**Remarque :** L’option **xt_only** est un paramètre appliqué à un certain client Adobe Target (clientcode) et peut uniquement être modifiée directement dans Adobe Target. Vous ne pouvez pas activer ni désactiver cette option dans AEM.

### Association de la structure Target à votre site {#associating-the-target-framework-with-your-site}

Après avoir créé une structure Target dans AEM, associez vos pages web à la structure. Les composants ciblés sur les pages envoient les données définies par la structure vers Adobe Target pour le suivi. (voir [Ciblage de contenu](/help/sites-authoring/content-targeting-touch.md)). 

Lorsque vous associez une page au framework, les pages enfants héritent de l’association.

1. Dans la console **Sites**, accédez au site à configurer.
1. À l’aide des [actions rapides](/help/sites-authoring/basic-handling.md#quick-actions) ou du [mode de sélection](/help/sites-authoring/basic-handling.md), sélectionnez **Afficher les propriétés.**
1. Sélectionnez l’onglet **Services cloud**.
1. Appuyez ou cliquez sur **Modifier**.
1. Appuyez/cliquez sur **Ajouter une configuration** under **Configurations de Cloud Service** et sélectionnez **Adobe Target**.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Sélectionnez la structure sous laquelle vous souhaitez **Référence de configuration**.

   >[!NOTE]
   Veillez à sélectionner la variable **framework** que vous avez créé et non la configuration cloud Target dans laquelle elle a été créée.

1. Appuyez/cliquez sur **Terminé.**
1. Activez la page racine du site web pour la répliquer sur le serveur de publication. (Voir [Publication de pages](/help/sites-authoring/publishing-pages.md).)

   >[!NOTE]
   Si la structure que vous avez jointe à la page n’a pas encore été activée, un assistant s’ouvre, vous permettant de la publier également.

## Résolution des problèmes de connexion à Target {#troubleshooting-target-connection-problems}

Effectuez les tâches suivantes pour résoudre les problèmes qui se produisent lors de la connexion à Target :

* Assurez-vous que les informations d’identification de l’utilisateur que vous fournissez sont correctes.
* Assurez-vous que l’instance AEM peut se connecter au serveur Target. Par exemple, assurez-vous que les règles de pare-feu ne bloquent pas les connexions AEM sortantes ou qu’AEM est configuré pour utiliser les proxies nécessaires.
* Recherchez des messages utiles dans le journal d’erreurs d’AEM. Le fichier error.log se trouve dans la variable **crx-quickstart/logs** répertoire dans lequel AEM est installé.
* Lors de la modification de l’activité dans Adobe Target, l’URL pointe sur localhost. Pour contourner ce problème, définissez l’externaliseur d’AEM sur l’URL correcte.
