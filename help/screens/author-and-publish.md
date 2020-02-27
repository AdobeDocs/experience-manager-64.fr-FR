---
title: Configuration de l’Auteur et de la Publication dans AEM Screens
seo-title: Configuration de l’Auteur et de la Publication dans AEM Screens
description: L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance de création AEM avant d’être répliqué sur plusieurs instances de publication. Consultez cette page pour apprendre comment configurer l’Auteur et la Publication pour AEM Screens.
seo-description: L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance de création AEM avant d’être répliqué sur plusieurs instances de publication. Consultez cette page pour apprendre comment configurer l’Auteur et la Publication pour AEM Screens.
uuid: 2bea5594-8a89-4aa2-8f3c-35ce84c84cc6
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: a6886b33-3bf1-4a81-8b9b-b6c154ca06d7
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Configuration de l’Auteur et de la Publication dans AEM Screens{#configuring-author-and-publish-in-aem-screens}

Cette page met l’accent sur les sujets suivants :

* **Configuration des instances de création et de publication**
* **Configuration de la topologie de publication**
* **Gestion de la publication : diffusion des mises à jour de contenu de l’auteur à la publication sur le périphérique**

## Conditions préalables {#prerequisites}

Avant de vous familiariser avec les serveurs de création et de publication, vous devez connaître au préalable :

* **Topologie AEM**
* **Création et gestion de projet AEM Screens**
* **Processus d’enregistrement de périphérique**

>[!NOTE]
>
>Cette fonctionnalité AEM Screens n’est disponible que si vous avez installé AEM 6.4 Screens Feature Pack 2. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.

## Configuration des instances de création et de publication {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Pour en savoir plus sur la présentation de l’architecture de création et de publication et sur la manière dont le contenu est créé sur une instance de l’Auteur AEM avant d’être répliqué sur plusieurs instances de publication, reportez-vous à [Présentation de l’architecture de création et de publication](author-publish-architecture-overview.md).

La section suivante explique comment configurer les agents de réplication sur la topologie de création et de publication.

Vous pouvez configurer un exemple simple, où vous hébergez une instance de création et deux instances de publication :

* Auteur —> localhost:4502
* Publier 1 (pub1) —> localhost:4503
* Publier (pub2) —> localhost:4504

### Configuration des agents de réplication en mode de création {#setting-up-replication-agents-on-author}

Pour créer des agents de réplication, vous devez apprendre à créer un agent de réplication standard.

Trois agents de réplication sont nécessaires pour les écrans :

1. **Agent de réplication par défaut ***(spécifié comme***Agent de réplication standard**)

1. **Agent de réplication Screens**
1. **Agent de réplication inverse**

Suivez les mêmes étapes pour créer un agent de réplication inverse.

1. Accédez à votre instance AEM —> icône marteau —> **Opérations** —> **Configuration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Sélectionnez la **Réplication** dans l’arborescence de navigation de gauche.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Sélectionnez les **Agents sur l’auteur** dans le dossier **Réplication** et cliquez sur **Nouveau** pour créer un agent de réplication standard.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Saisissez le **Titre** et le **Nom** pour créer l’agent de réplication, puis cliquez sur **Créer**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Cliquez avec le bouton droit sur l’agent de réplication et cliquez sur **Ouvrir** pour modifier les paramètres.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Paramètres d’agent** afin de saisir les détails.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Accédez à l’onglet **Transport** et saisissez l’**URI**, l’**Utilisateur** et le **Mot de passe**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Vous pouvez également copier et renommer un agent de réplication par défaut existant.

#### Création d’agents de réplication standard {#creating-standard-replication-agents}

1. Créez un agent de réplication standard pour pub1 (l’agent par défaut prêt à l’emploi devrait déjà être configuré) (par exemple, *https://&lt;nom_hôte>:4503/bin/receive?sling:authRequestLogin=1*)

1. Créez un agent de réplication standard pour pub2. Vous pouvez copier l’agent rep pour pub1 et mettre à jour le transport à utiliser pour pub2 en modifiant le port dans la configuration du transport. (par exemple, *https://&lt;nom_hôte>:4504/bin/receive?sling:authRequestLogin=1*)

#### Création d’agents de réplication Screens {#creating-screens-replication-agents}

1. Créez l’agent de réplication AEM Screens pour pub1. Par défaut, il existe un agent de réplication Screens qui pointe vers le port 4503. Ce paramètre doit être activé.
1. Créez l’agent de réplication AEM Screens pour pub2. Copiez l’agent de réplication Screens pour pub1 et modifiez le port afin qu’il pointe sur 4504 pour pub2.

#### Création d’agents de réplication inverse Screens {#creating-screens-reverse-replication-agents}

1. Créez un agent de réplication inverse standard pour pub1.
1. Créez un agent de réplication inverse standard pour pub2. Vous pouvez copier l’agent rep pour pub1 et mettre à jour le transport à utiliser pour pub2 en modifiant le port dans la configuration du transport.

## Configuration de la topologie de publication {#setting-up-publish-topology}

### Étape 1 : configuration de la détection Apache Sling basée sur Oak {#step-configure-apache-sling-oak-based-discovery}

Configurez la détection Apache Sling basée sur Oak pour toutes les instances de publication dans la topologie

Pour chaque instance de publication :

1. Accédez à https://&lt;hôte>:&lt;port>/system/console/configMgr
1. Sélectionnez la Configuration du **Service de détection Apache Sling basé sur Oak** .
1. Mettez à jour les URL des connecteurs de topologie : ajouter les URL de toutes les instances de publication participantes, à savoir [http://localhost:4502/libs/sling/topology/connector](http://localhost:4502/libs/sling/topology/connector)
1. Liste blanche des connecteurs de topologie : à adapter aux adresses IP ou aux sous-réseaux couvrant les instances de publication
1. Activez **Arrêt automatique des boucles locales**

La configuration doit être identique pour chaque instance de publication et l’arrêt automatique des boucles locales empêche la création d’une boucle infinie.

### Étape 2 : vérification de la topologie de publication {#step-verify-publish-topology}

Pour toutes les instances de publication, accédez à https://&lt;hôte>:&lt;port>/system/console/topology. Chaque instance de publication doit être représentée dans la topologie.

### Étape 3 : configuration d’un cluster ActiveMQ Artemis {#step-setup-activemq-artemis-cluster}

Cette étape vous permet de créer un mot de passe chiffré pour le cluster ActiveMQ Artemis.\
L’utilisateur de du cluster et le mot de passe de toutes les instances de publication de la topologie doivent être identiques. Le mot de passe de la configuration ActiveMQ Artemis doit être chiffré. Chaque instance ayant sa propre clé de chiffrement, il est nécessaire d’utiliser la prise en charge de Crypto pour créer une chaîne de mot de passe chiffrée. Le mot de passe chiffré sera ensuite utilisé dans la configuration OSGi pour ActiveMQ.

Sur chaque instance de publication :

1. Dans la console OSGi, accédez à **PRINCIPAL** —> **Prise en charge de Crypto** (*https://&lt;hôte>:&lt;port>/system/console/crypto*).

1. Saisissez le mot de passe en texte brut (identique pour toutes les instances) dans **Texte brut**
1. Cliquez sur **Protéger**.
1. Copiez la valeur **Texte protégé** dans le bloc-notes ou l’éditeur de texte. Cette valeur sera utilisée dans la configuration OSGi pour ActiveMQ.

Comme chaque instance de publication possède par défaut des clés de chiffrement uniques, vous devez effectuer cette étape sur chaque instance pub et enregistrer la clé unique pour la configuration suivante.

*Par exemple*,

Pub1 - {1ec346330f1c26b5c4825084c3b7272a5e85260322edd59119828d1fa0a6 10e}\
Pub2 - {8d3d113c834cc4f52c2daee0da3cb0a21122a31f0138bfe4b70c9ead79415f41}

### Étape 4 : activation du cluster Artemis ActiveMQ {#step-activate-activemq-artemis-cluster}

Sur chaque instance de publication :

1. Accédez au gestionnaire de configuration OSGi *https://&lt;hôte>:&lt;port>/system/console/configMgr*
1. Sélectionnez la Configuration du **Fournisseur JMS Apache ActiveMQ Artemis**
1. Mettez à jour les éléments suivants :

* ***Mot de passe du cluster*** : (utilisez la valeur chiffrée de l’étape précédente pour chaque instance)
* ***Rubriques*** : {name : ’commands’, address : ’com.adobe.cq.screens.commands’, maxConsumers : 50}

### Vérifiez le cluster d’artéfacts ActiveMQ Artemis {#verify-activemq-artemis-cluster}

Suivez les étapes ci-dessous sur chaque instance de publication :

1. Accédez à la console OSGi -> Main > Artémis ActiveMQ ([http://localhost:4505/system/console/mq](http://localhost:4505/system/console/mq)).
1. Vérifiez et contrôlez afin d’afficher les ports des autres instances sous Informations sur le cluster > Topologie > nœuds=2, membres=2.
1. Envoyez un message de test (en haut de l’écran sous Informations sur le courtier)
1. Entrez les modifications suivantes dans les champs :

   1. **Destination** : /com.adobe.cq.screens/devTestTopic
   1. **Texte** : Hello World
   1. Affichez le fichier error.log de chaque instance pour vérifier que le message a été envoyé et reçu par l’ensemble de du cluster.

>[!NOTE]
>
>La navigation vers la console OSGI peut prendre quelques secondes après l’enregistrement de la configuration à l’étape précédente. Vous pouvez également consulter le fichier error.log pour plus de détails.

Par exemple, l’image suivante s’affiche lors d’une configuration réussie d’ActiveMQ Artemis Server.

Si vous ne voyez pas la configuration suivante de */system/console/mq*, accédez à */system/console/mq* et cliquez sur **Redémarrer** pour redémarrer le courtier.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

### Suppression des exigences d’en-tête de référent {#remove-referrer-header-requirement}

Suivez les étapes de chaque instance de publication :

1. Accédez à **Configuration Manager** à partir de la console **** OSGi.
1. Sélectionnez **Filtre de référent Apache Sling**.
1. Mettez à jour la configuration et **cochez Autoriser valeur vide**.

## Configuration des instances de création et de publication {#configuring-author-and-publish-instance}

Une fois que vous aurez configuré la stratégie de publication, vous devez configurer les instances de création et de publication afin d’afficher les résultats concrets de l’implémentation :

>[!NOTE]
>
>**Conditions préalables**
>
>Pour commencer avec cet exemple, créez un projet AEM Screens, puis créez un emplacement, un affichage et un canal dans votre projet. Ajoutez du contenu à votre canal et affectez-le à un affichage.

### Étape 1 : démarrage d’un lecteur AEM Screens (périphérique) {#step-starting-an-aem-screens-player-device}

1. Lancez une fenêtre du navigateur distincte.
1. Accédez au lecteur Screens à l’aide du [navigateur web](http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html)  ou lancez l’application AEM Screens. Lorsque vous ouvrez le périphérique, vous remarquez que son état est non enregistré.

>[!NOTE]
>
>Vous pouvez ouvrir un lecteur AEM Screens en utilisant l’application que vous avez téléchargée ou le navigateur web.

### Étape 2 : enregistrement d’un périphérique sur l’Auteur {#step-registering-a-device-on-author}

1. Accédez à [http://localhost:4502/screens.html/content/screens/we-retail](http://localhost:4502/screens.html/content/screens/we-retail) ou sélectionnez votre projet et accédez à Périphériques > Gestionnaire de périphériques.
1. Sélectionnez **Enregistrer le périphérique**.
1. Cliquez sur **Enregistrement du périphérique** pour afficher le périphérique.
1. Sélectionnez le périphérique que vous voulez enregistrer et cliquez ensuite sur **Enregistrer le périphérique**.
1. Vérifiez le code d’enregistrement et cliquez sur **Valider**.
1. Saisissez un titre pour votre périphérique et cliquez sur **Enregistrer**.

#### Étape 3 : attribution du périphérique à un affichage {#step-assigning-the-device-to-display}

1. Cliquez sur **Attribuer l’affichage** dans la boîte de dialogue de l’étape précédente.
1. Sélectionnez le chemin d’affichage de votre canal dans le dossier **Emplacements**.
1. Cliquez sur **Attribuer**.
1. Cliquez sur **Terminer** pour achever le processus. Le périphérique est désormais attribué.

Vérifiez votre lecteur et vous verrez le contenu que vous avez ajouté à votre canal.

### Étape 4 : publication de la configuration du périphérique sur les instances de publication {#step-publishing-device-configuration-to-publish-instances}

**Vérification du périphérique**

Avant d’effectuer les étapes ci-dessous, veillez à vérifier l’ID du périphérique. Pour vérifier, recherchez l’ID du périphérique dans CRXDELite, en utilisant comme chemin d’accès */home/users/screens/{projet}/devices*.

Pour répliquer l’utilisateur du périphérique, procédez comme suit :

1. Accédez à la page d’administration des utilisateurs (par ex. : [http://localhost:4502/useradmin](http://localhost:4502/useradmin)).
1. Recherchez le groupe **screens-devices-master**
1. Cliquez avec le bouton droit sur le groupe, puis cliquez sur **Activer**

>[!CAUTION]
>
>N’activez pas le service author-publish-screens-service, car il s’agit d’un utilisateur système utilisé par la tâche de création.

Vous pouvez également activer le périphérique à partir de la console de gestion des périphériques. Suivez les étapes ci-dessous :

1. Accédez à votre projet Screens —> **Périphériques**.
1. Cliquez sur **Gestionnaire de périphériques** dans la barre d’actions.
1. Sélectionnez le périphérique et cliquez sur **Activer** dans la barre d’actions, comme illustré dans la figure ci-dessous.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Une fois que vous aurez activé le périphérique, vous pourrez également modifier ou mettre à jour l’URL du serveur en cliquant sur **Modifier l’URL du serveur** dans la barre d’actions, comme illustré dans la figure ci-dessous, et vos modifications seront propagées au lecteur AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

## Liste de contrôle de publication {#publishing-check-list}

Les points suivants récapitulent la Liste de contrôle de publication :

* *Utilisateur du périphérique Screens* : stocké en tant qu’utilisateur AEM, il est activé à partir de **Outils** > **Sécurité** > **Utilisateurs**. L’utilisateur comportera le préfixe &quot;screens&quot; avec une longue chaîne sérialisée.

* *Projet* : le projet AEM Screens.

* *Emplacement* : emplacement auquel le périphérique est connecté.
* *Canaux* : un ou plusieurs canaux affichés à l’emplacement
* *Planification* : si vous utilisez une planification, veillez à ce qu’elle soit publiée.
* *Dossier Emplacement, Planifications et Canal* : si les ressources correspondantes se trouvent dans un dossier.

Une fois la liste de contrôle vérifiée, vous devez vérifier les changements/comportements suivants dans votre canal :

* Après avoir publié la configuration du périphérique, ouvrez la configuration du lecteur Screens et pointez-la vers l’instance de publication. Vous pouvez également activer le périphérique à partir de la console de gestion des périphériques.
* Mettez à jour le contenu d’un canal sur l’auteur, puis publiez-le et vérifiez que le canal mis à jour s’affiche désormais sur le lecteur AEM Screens.
* Connectez le lecteur Screens à une autre instance de publication et vérifiez le comportement ci-dessus.

### Étape 5 : pointage du périphérique vers l’instance de publication dans le panneau d’administration {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Affichez l’interface utilisateur d’administration du lecteur Screens en appuyant longuement dans l’angle supérieur gauche afin d’ouvrir le menu Admin sur votre lecteur AEM Screens, avec fonction tactile activée, ou en utilisant la souris.
1. Cliquez sur l’option **Configuration **dans le panneau latéral.
1. Modifiez l’instance d’auteur en instance de publication dans **Serveur**.

Affichez les modifications dans votre lecteur AEM Screens.

Vous pouvez également mettre à jour/modifier l’URL du serveur à partir de la console de gestion des périphériques en procédant comme suit :

1. Accédez à votre projet AEM Screens et sélectionnez le dossier **Périphériques**.
1. Cliquez sur **Gestionnaire de périphériques** dans la barre d’actions.
1. Sélectionnez le périphérique et cliquez sur **Modifier l’URL du serveur** dans la barre d’actions, comme illustré dans la figure ci-dessous. Vos modifications seront propagées au lecteur AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

## Gestion de la publication : diffusion des mises à jour de contenu de l’auteur à la publication sur le périphérique {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Vous pouvez publier et annuler la publication de contenu à partir d’AEM Screens. La fonction Gérer les publications vous permet de diffuser des mises à jour de contenu de l’auteur à publier sur le périphérique. Vous pouvez publier/annuler la publication de contenu pour l’ensemble de votre projet AEM Screens ou uniquement pour l’un de vos canaux, emplacements, périphériques, applications ou plannings.

### Gestion de la publication pour un projet AEM Screens {#managing-publication-for-an-aem-screens-project}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu de l’auteur à publier sur le périphérique pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le projet vers l’instance de publication.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. L’assistant de **Gestion de publication** démarre. Vous pouvez sélectionner l’**Action** et programmer l’heure de publication sur maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cochez la case pour sélectionner l’intégralité du projet dans l’assistant de **Gestion de publication**.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Cliquez sur **+ Inclure les enfants** dans la barre d’actions et désactivez toutes les options pour publier tous les modules de votre projet, puis cliquez sur **Ajouter** pour publier.

   >[!NOTE]
   >
   >Par défaut, toutes les cases seront cochées et vous devrez les décocher manuellement pour publier tous les modules de votre projet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

1. Click **Publish** from the **Manage **Publication wizard**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.
   >
   >La **gestion de la publication** avec mise à jour du contenu hors ligne est un processus en deux étapes et les étapes doivent être dans l’ordre correct.
   >
   > 1. Le processus ne fonctionne pas si la **mise à jour du contenu hors ligne** est déclenchée avant la publication à l’aide de la fonction **Gérer la publication**.
   > 1. Le processus ne fonctionne pas si le projet ne contient aucune modification et qu&#39;il n’y a pas lieu de **mettre à jour le contenu hors ligne**.
   > 1. Le processus ne fonctionne pas si l’auteur n’effectue pas le processus de réplication (le contenu est toujours téléchargé vers l’instance de publication) après avoir cliqué sur le bouton **Publier** dans le processus de gestion de la publication.


1. Une fois que vous avez terminé le processus de gestion de la publication, vous devez déclencher la mise à jour du contenu hors ligne dans l’Auteur, ce qui crée la mise à jour hors ligne sur l’instance de l’Auteur.

   Accédez au projet et cliquez sur **Mettre à jour le contenu hors ligne** dans la barre d’actions. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur l’instance de publication.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)

   >[!CAUTION]
   >
   >Vous devez d’abord publier, puis déclencher la mise à jour du contenu hors ligne, comme indiqué dans les étapes précédentes.

### Gestion des publications pour un canal {#managing-publication-for-a-channel}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu de l’Auteur à publier sur le périphérique pour un canal dans un projet AEM Screens :

>[!NOTE]
>
>Suivez cette section uniquement si un canal contient des modifications. Si un canal ne comporte aucune modification après le contenu hors ligne de la mise à jour précédente, le processus de gestion des publications pour un canal individuel ne fonctionne pas.

1. Accédez à votre projet Screens et sélectionnez le canal.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le canal vers l’instance de publication.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. L’assistant de **Gestion de publication** démarre. Vous pouvez sélectionner l’**Action** et programmer l’heure de publication sur maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Click **Publish **from the** Manage **Publication wizard.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.

1. Une fois que vous avez terminé le processus de gestion de la publication, vous devez déclencher la mise à jour du contenu hors ligne dans l’Auteur, ce qui crée la mise à jour hors ligne sur l’instance de l’Auteur.

   Accédez au tableau de bord du canal et cliquez sur **Mettre à jour le contenu hors ligne**. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur l’instance de publication.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Vous devez d’abord publier, puis déclencher la mise à jour du contenu hors ligne, comme indiqué dans les étapes précédentes.

### Réaffectation de canal et de périphérique : {#channel-and-device-re-assignment}

Si vous avez réaffecté un périphérique, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois le périphérique réaffecté au nouvel affichage.

De même, si vous avez réaffecté un canal, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois que le canal a été réaffecté au nouvel affichage.
