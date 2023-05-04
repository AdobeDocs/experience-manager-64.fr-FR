---
title: Considérations sur le réseau d’Assets
description: Décrit les considérations relatives au réseau lors de la conception d’une [!DNL Experience Manager] Déploiement des ressources.
contentOwner: AG
feature: Developer Tools
role: Architect,Admin
exl-id: f8f9d86f-a5e3-46ac-8d96-c2e44eac9c93
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 29%

---

# Considérations sur le réseau d’Assets {#assets-network-considerations}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Comprendre votre réseau est aussi important que de comprendre Adobe Experience Manager Assets. Le réseau peut avoir une incidence sur le chargement, le téléchargement et les expériences utilisateur. Le diagramme de votre topologie réseau permet d’identifier les goulots d’étranglement et les zones sous-optimisées du réseau que vous devez corriger pour améliorer les performances du réseau et l’expérience utilisateur.

Veillez à inclure les éléments suivants dans le diagramme de réseau :

* Connectivité de l’appareil client (ordinateur, mobile et tablette, par exemple) au réseau
* La topologie du réseau d’entreprise
* Liaison à Internet à partir du réseau d’entreprise et de [!DNL Experience Manager] environnement
* Topologie de l’environnement [!DNL Experience Manager]
* Définir les consommateurs simultanés de la variable [!DNL Experience Manager] interface réseau
* Les workflows définis de la [!DNL Experience Manager] instance

## Connectivité de l’appareil client au réseau d’entreprise {#connectivity-from-the-client-device-to-the-corporate-network}

Commencez par créer un diagramme de la connectivité entre les différents appareils clients et le réseau d’entreprise. À ce stade, identifiez les ressources partagées, telles que les connexions Wi-Fi, où plusieurs utilisateurs accèdent au même point ou commutateur Ethernet pour charger et télécharger des ressources.

![chlimage_1-353](assets/chlimage_1-353.png)

Les périphériques client se connectent au réseau d’entreprise de différentes façons, telles que le wi-fi, Ethernet sur un commutateur partagé et le VPN. L’identification et la connaissance des goulots d’étranglement sur ce réseau sont importantes pour la planification d’Assets et pour modifier le réseau.

En haut à gauche du diagramme, trois périphériques sont représentés comme partageant un point d’accès Wi-Fi de 48 Mbit/s. Si tous les appareils se chargent simultanément, la bande passante du réseau Wi-Fi est partagée entre les appareils. Par rapport au système dans son ensemble, un utilisateur peut rencontrer un goulot d’étranglement différent pour les trois clients sur ce canal divisé.

Il est difficile de mesurer la vitesse réelle d’un réseau Wi-Fi, car un appareil lent peut avoir un impact sur d’autres clients sur le point d’accès. Si vous prévoyez d’utiliser le Wi-Fi pour les interactions de ressources, effectuez simultanément un test de vitesse auprès de plusieurs clients afin d’évaluer le débit.

Le coin inférieur gauche du diagramme représente deux appareils connectés au réseau d’entreprise par le biais de canaux indépendants. Par conséquent, chaque appareil peut atteindre une vitesse minimale de 10 Mbit/s et 100 Mbit/s.

L&#39;ordinateur affiché à droite a une limite en amont du réseau d&#39;entreprise sur un VPN avec une vitesse de 1 Mbit/s. L’expérience utilisateur pour la connexion de 1 Mbit/s diffère considérablement de celle de l’utilisateur pour la connexion de 1 Gbit/s. En fonction de la taille des ressources avec lesquelles les utilisateurs interagissent, leur lien de liaison VPN peut être inadapté à la tâche.

## La topologie du réseau d’entreprise  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Le diagramme affiche des vitesses de liaison montante plus élevées au sein du réseau d’entreprise que celles généralement utilisées. Ces canaux sont des ressources partagées. Si le commutateur partagé doit gérer 50 clients, il peut s’agir d’un goulot d’étranglement. Dans le diagramme initial, seuls deux ordinateurs partagent la connexion.

## Liaison montante à Internet à partir du réseau d’entreprise et de l’environnement [!DNL Experience Manager] {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Il est important de tenir compte de facteurs inconnus sur Internet et de la connexion VPC, car la bande passante sur Internet peut être altérée en raison de la charge maximale ou de pannes de fournisseur à grande échelle. En général, la connexion à Internet est fiable. Cependant, il peut parfois introduire des goulots d’étranglement.

Au niveau de la liaison montante entre un réseau d’entreprise et Internet, il peut y avoir d’autres services utilisant la bande passante. Il est important de connaître la quantité de bande passante pouvant être dédiée ou donnée en priorité à [!DNL Assets]. Par exemple, si un lien de 1 Gbit/s est déjà utilisé à 80 %, vous ne pouvez allouer qu’un maximum de 20 % de la bande passante pour [!DNL Experience Manager] ressources.

Les pare-feu et les proxys de l’entreprise peuvent également influencer la bande passante de différentes manières. Ce type d’appareil peut donner la priorité à la bande passante en utilisant la qualité du service, les limitations de bande passante par utilisateur ou les limitations de débit binaire par hôte. Il s’agit de points d’étranglement importants à examiner, car ils peuvent avoir un impact significatif sur l’expérience utilisateur d’Assets.

Dans cet exemple, l’entreprise dispose d’une liaison de 10 Gbps. Il doit être assez grand pour plusieurs clients. De plus, le pare-feu impose une limite de débit d’hôte de 10 Mbit/s. Cette limitation peut limiter le trafic sur un seul hôte à 10 Mbit/s, même si la liaison montante à Internet est de 10 Gbit/s.

Il s’agit du plus petit goulot d’étranglement orienté client. Cependant, vous pouvez évaluer une modification ou une liste autorisée avec le groupe d’opérations réseau responsable de ce pare-feu.

À partir des exemples de diagrammes, vous pouvez conclure que six appareils partagent un canal conceptuel de 10 Mbit/s. En fonction de la taille des ressources exploitées, cela peut s’avérer insuffisant pour répondre aux attentes des utilisateurs.

## Topologie de l’environnement [!DNL Experience Manager] {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

La conception de la topologie de l’environnement [!DNL Experience Manager] nécessite une connaissance détaillée de la configuration du système et de la manière dont le réseau est connecté à l’environnement de l’utilisateur.

L’exemple de scénario comprend une ferme de publication avec cinq serveurs, un magasin de fichiers binaires S3 et Dynamic Media configurés.

Dispatcher partage une connexion de 100 Mbit/s avec deux entités, le monde extérieur et le [!DNL Experience Manager] instance. Pour les opérations simultanées de téléchargement et de chargement, vous devez diviser ce nombre par deux. Le stockage externe joint utilise une connexion distincte.

Le [!DNL Experience Manager] l’instance partage une connexion de 1 Gbit/s avec plusieurs services. Du point de vue de la topologie du réseau, cela équivaut à partager un seul canal avec plusieurs services.

Vérification du réseau depuis l’appareil client vers l’ [!DNL Experience Manager] Par exemple, le plus petit goulot d’étranglement semble être la limitation de pare-feu d’entreprise de 10 Mbit. Vous pouvez utiliser ces valeurs dans le calcul de dimensionnement du [Guide du dimensionnement des ressources](assets-sizing-guide.md) pour déterminer l’expérience de l’utilisateur.

## Les workflows définis de la [!DNL Experience Manager] instance {#defined-workflows-of-the-aem-instance}

En tenant compte des performances du réseau, il peut être important de prendre en considération les workflows et la publication qui auront lieu dans le système. De plus, S3 ou tout autre stockage connecté au réseau que vous utilisez et les demandes d’E/S consomment de la bande passante du réseau. Par conséquent, même dans un réseau entièrement optimisé, la performance peut être limitée par les E/S du disque.

Pour simplifier les processus d’assimilation des ressources (notamment lors du chargement d’un grand nombre de ressources), vous devez explorer leurs workflows et en savoir plus sur leur configuration.

Lors de l’évaluation de la topologie de workflow interne, vous devez analyser les éléments suivants :

* Procédures d’écriture d’une ressource
* Les workflows/événements qui se déclenchent lorsqu’une ressource ou une métadonnée est modifiée
* Procédures de lecture d’une ressource

Voici quelques éléments à vérifier :

* XMP des métadonnées lues/écrites en écriture différée
* Activation et réplication automatiques
* Application d’un filigrane
* Ingestion de sous-ressources/extraction de page
* Chevauchement des workflows.

Voici un exemple client pour la définition d’un workflow de ressource.

![chlimage_1-357](assets/chlimage_1-357.png)
