---
title: Exécution d’AEM en mode Prêt pour la production
seo-title: Running AEM in Production Ready Mode
description: Découvrez comment exécuter AEM en mode Prêt pour la production.
seo-description: Learn how to run AEM in Production Ready Mode.
uuid: f48c8bae-c72f-4772-967e-f1526f096399
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 32da99f0-f058-40ae-95a8-2522622438ce
exl-id: 2ab55a72-2eb2-49dc-8716-0a8a4d0c4b73
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 73%

---

# Exécution d’AEM en mode Prêt pour la production{#running-aem-in-production-ready-mode}

Avec AEM 6.1, Adobe introduit la nouvelle `"nosamplecontent"` runmode visant à automatiser les étapes nécessaires à la préparation d’une instance AEM pour le déploiement dans un environnement de production.

Le nouveau mode d’exécution configure non seulement automatiquement l’instance pour qu’elle soit conforme aux meilleures pratiques de sécurité décrites dans la liste de contrôle de sécurité, mais en plus supprime tous les exemples d’applications et de configurations geometrixx dans le processus.

>[!NOTE]
>
>Puisque, pour des raisons pratiques, le mode Prêt pour la production d’AEM couvre uniquement une majorité de tâches requises pour sécuriser une instance, il est vivement conseillé de consulter la [liste de contrôle de sécurité](/help/sites-administering/security-checklist.md) avant de passer à la publication dans votre environnement de production.
>
>De plus, notez qu’exécuter AEM en mode Prêt pour la production aura pour effet de désactiver l’accès à CRXDE Lite. Si vous en avez besoin à des fins de débogage, voir la section [Activation de CRXDE Lite dans AEM](/help/sites-administering/enabling-crxde-lite.md).

![chlimage_1-83](assets/chlimage_1-83.png)

Pour exécuter l’AEM en mode prêt pour la production, il vous suffit d’ajouter le `nosamplecontent` via le `-r` runmode basculez vers vos arguments de démarrage existants :

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

Par exemple, vous pouvez utiliser le mode Prêt pour la production afin de lancer une instance de création avec la persistance MongoDB comme suit :

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Modifications faisant partie du mode Prêt pour la production {#changes-part-of-the-production-ready-mode}

Plus spécifiquement, les modifications de configuration suivantes seront effectuées lorsque AEM est exécuté en mode Prêt pour la production :

1. Le **lot de prise en charge CRXDE** (`com.adobe.granite.crxde-support`) est désactivé par défaut dans le mode Prêt pour la production. Il peut être installé à tout moment à partir du référentiel Maven public Adobe. La version 3.0.0 est requise pour AEM 6.1.

1. Le lot **Accès WebDAV simple Apache Sling aux référentiels** (`org.apache.sling.jcr.webdav`) ne sera disponible que sur les instances de **création**.

1. Les utilisateurs nouvellement créés devront changer de mot de passe à la première connexion. Ceci ne s’applique pas à l’administrateur.
1. **Génération des informations de débogage** est désactivé pour la variable **Gestionnaire de script Java Apache Sling**.

1. Les options **Contenu mappé** et **Générer les informations de débogage** sont désactivées pour le **gestionnaire de script JSP Apache Sling**.

1. Le **Filtre WCM Day CQ** est défini sur `edit` on **author** et `disabled` on **publier** instances.

1. Le **Gestionnaire de bibliothèques de HTMLS Adobe Granite** est configuré avec les paramètres suivants :

   1. **Minimiser :** `enabled`
   1. **Déboguer:** `disabled`
   1. **Gzip :** `enabled`
   1. **Minutage :** `disabled`

1. Le servlet **Apache Sling GET** est configuré pour prendre en charge les configurations sécurisées par défaut, comme suit :

| **Configuration** | **Auteur** | **Publication** |
|---|---|---|
| Rendu TXT | disabled | disabled |
| Rendu HTML | disabled | disabled |
| Rendu JSON | enabled | enabled |
| Rendu XML | disabled | disabled |
| json.maximumresults | 1000 | 100 |
| Index automatique | disabled | disabled |
