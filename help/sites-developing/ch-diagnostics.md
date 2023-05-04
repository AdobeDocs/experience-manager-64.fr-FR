---
title: Diagnostic ContextHub
seo-title: ContextHub Diagnostics
description: ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 66%

---

# Diagnostics ContextHub {#contexthub-diagnostics}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

ContextHub fournit une page de diagnostics qui affiche un aperçu de sa structure. Pour ouvrir la page, accédez à la page `contexthub.diagnostics.html` de votre instance de création AEM par exemple :

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

La page Diagnostics ContextHub fournit des informations sur les magasins et les modules d’IU créés, les dossiers de bibliothèques clientes chargés et les liens vers des pages utiles.

>[!NOTE]
>
>Pour que les informations de diagnostic soient renvoyées, le mode de débogage doit être activé, sinon la page de diagnostic est vide. Reportez-vous à ce [document](/help/sites-administering/contexthub-config.md#debugging-contexthub) pour plus de détails sur l’activation du mode débogage.

>[!NOTE]
>
>Pour les configurations ContextHub toujours situées sous leurs chemins hérités, l’emplacement où définir la page de diagnostics est `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Magasins {#stores}

La section Magasins répertorie tous les magasins ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de magasin](/help/sites-developing/ch-samplestores.md) sur lequel le magasin est basé.
* **path:** Le chemin d’accès au noeud du référentiel qui contient la configuration.
* **resourceType:** Chemin d’accès du noeud du référentiel où le type de magasin est défini.
* **clientlibs :** Les catégories des bibliothèques clientes chargées qui implémentent le type de magasin.

## Modules {#modules}

La section Modules répertorie tous les modules d’IU ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de module d’IU](/help/sites-developing/ch-samplemodules.md) sur lequel le module d’IU est basé.
* **path:** Le chemin d’accès au noeud du référentiel qui contient la configuration.
* **resourceType:** Chemin d’accès du noeud du référentiel où le type de module d’IU est défini.
* **clientlibs :** Les catégories des bibliothèques clientes chargées qui implémentent le type de module d’IU.

## Clientlibs {#clientlibs}

La section Clientlibs répertorie tous les dossiers de bibliothèque cliente chargés par ContextHub. Les bibliothèques clientes sont classées :

* **kernel.js :** bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de stockage.
* **ui.js :** bibliothèques clientes qui implémentent les types de modules d’IU et l’IU ContextHub.
* **style.css :** Fichiers CSS chargés à partir des bibliothèques clientes.

## URL {#urls}

La section URL contient des liens vers les fonctionnalités de ContextHub :

* **Éditeur de configuration :** ouvre la [page de configuration ContextHub](/help/sites-administering/contexthub-config.md) où vous pouvez configurer les magasins, les modes IU et les modules d’IU.

* **Configuration des modules ContextHub :** ouvre le fichier /etc/cloudsettings/default/contexthub.config.kernel.js, qui contient la représentation de l’objet Javascript des configurations du magasin ContextHub.
* **Configuration de l’IU ContextHub :** ouvre le fichier /etc/cloudsettings/default/contexthub.config.ui.js, qui contient la représentation de l’objet Javascript des configurations du mode d’IU ContextHub.
* **kernel.js :** ouvre le fichier /etc/cloudsettings/default/contexthub.kernel.js contenant le code source des bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de magasin.
* **ui.js :** ouvre le fichier /etc/cloudsettings/default/contexthub.ui.js contenant le code source des bibliothèques clientes qui implémentent l’IU et les types de module d’IU ContextHub.
* **style.css :** ouvre le fichier /etc/cloudsettings/default/contexthub.styles.css, qui contient les styles CSS des modules d’IU et l’IU ContextHub.
