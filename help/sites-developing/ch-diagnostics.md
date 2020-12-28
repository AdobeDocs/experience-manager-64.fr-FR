---
title: Diagnostic ContextHub
seo-title: Diagnostic ContextHub
description: ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub
seo-description: ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 72%

---


# Diagnostic ContextHub {#contexthub-diagnostics}

ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub. Pour ouvrir la page, accédez à la page `contexthub.diagnostics.html` de votre instance de création AEM par exemple :

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

La page de diagnostic de ContextHub présente des informations sur les magasins et les modules d’IU qui ont été créés, les dossiers de bibliothèque cliente chargés et les liens vers des pages utiles.

>[!NOTE]
>
>Pour que les informations de diagnostic soient renvoyées, le mode de débogage doit être activé, sinon la page de diagnostic est vide. Reportez-vous à ce [document](/help/sites-administering/contexthub-config.md#debugging-contexthub) pour plus de détails sur l’activation du mode débogage.

>[!NOTE]
>
>Pour les configurations ContextHub toujours situées sous leurs chemins d’accès hérités, l’emplacement de la page de diagnostics est `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Magasins  {#stores}

La section Magasins répertorie tous les magasins ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de magasin](/help/sites-developing/ch-samplestores.md) sur lequel le magasin est basé.
* **path :** chemin d’accès au nœud du référentiel contenant la configuration.
* **resourceType :** chemin du nœud du référentiel où le type de magasin est défini.
* **clientlibs :** catégories des bibliothèques clientes chargées qui implémentent le type de magasin.

## Modules  {#modules}

La section Modules répertorie tous les modules d’IU ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de module d’IU](/help/sites-developing/ch-samplemodules.md) sur lequel le module d’IU est basé.
* **path :** chemin d’accès au nœud du référentiel contenant la configuration.
* **resourceType :** chemin du nœud du référentiel où le type de module d’IU est défini.
* **clientlibs :** catégories des bibliothèques clientes chargées qui implémentent le type de module d’IU.

## Clientlibs  {#clientlibs}

La section Clientlibs répertorie tous les dossiers de bibliothèque cliente chargés par ContextHub. Les bibliothèques clientes sont catégorisées :

* **kernel.js :** bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de stockage.
* **ui.js :** bibliothèques clientes qui implémentent les types de modules d’IU et l’IU ContextHub.
* **style.css :** fichiers CSS chargés à partir des bibliothèques clientes.

## URL  {#urls}

La section URL contient des liens vers les fonctionnalités de ContextHub :

* **Éditeur de configuration :** ouvre la [page de configuration ContextHub](/help/sites-administering/contexthub-config.md) où vous pouvez configurer les magasins, les modes IU et les modules d’IU.

* **Configuration des modules ContextHub :** ouvre le fichier /etc/cloudsettings/default/contexthub.config.kernel.js, qui contient la représentation d’objet Javascript des configurations de stockage ContextHub.
* **Configuration de l’interface utilisateur ContextHub :** ouvre le fichier /etc/cloudsettings/default/contexthub.config.ui.js, qui contient la représentation de l’objet Javascript des configurations du mode d’interface utilisateur ContextHub.
* **kernel.js :** ouvre le fichier /etc/cloudsettings/default/contexthub.kernel.js, qui contient le code source des bibliothèques clientes qui implémentent la structure ContextHub, le moteur de segments et les types de stockage.
* **ui.js :** ouvre le fichier /etc/cloudsettings/default/contexthub.ui.js, qui contient le code source des bibliothèques clientes qui implémentent les types d’interface utilisateur et de module d’interface utilisateur ContextHub.
* **style.css:** Ouvre le fichier /etc/cloudsettings/default/contexthub.styles.css, qui contient les styles CSS pour l’interface utilisateur et les modules d’interface utilisateur ContextHub.
