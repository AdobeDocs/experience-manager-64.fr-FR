---
title: 'Définition des emplacements de fichiers pour Output '
seo-title: Specify file locations for Output
description: Découvrez comment indiquer les emplacements de fichier pour Output.
seo-description: Learn how to specify file locations for Output.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 5b8f04dd-6781-4126-8bb2-5d8b7a2f19c8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 71%

---

# Définition des emplacements de fichiers pour Output {#specify-file-locations-for-output}

Vous pouvez spécifier les emplacements dans lesquels Output recherche certains types de fichiers requis.

1. Dans Administration Console, cliquez sur Services > Output.
1. Sous Emplacements, définissez les options appropriées.
1. Cliquez sur Enregistrer.

## Paramètres des emplacements {#locations-settings}

**URI racine du contenu :** URI ou emplacement absolu du référentiel à partir duquel les formulaires sont récupérés. Cette valeur est combinée avec le paramètre sForm, indiqué via l’API, pour construire l’URL absolue vers le formulaire à récupérer. Cette valeur peut faire référence à un répertoire ou à un emplacement Web accessible par HTTP.

La valeur par défaut est une chaîne vide.

**Fichier de configuration XCI :** Emplacement relatif ou absolu du fichier de configuration XCI utilisé par le service Output pour le rendu. Si la valeur est relative, il est supposé que le fichier XCI réside dans le fichier EAR déployable d’AEM forms.

La valeur par défaut est `com/adobe/formServer/PA/pa_output.xci`.

**Emplacement du cache :** Indique l’emplacement du cache disque de sortie. Lorsque ce paramètre est modifié, toutes les informations concernant le cache de l’emplacement courant sont réinitialisées et un nouveau cache est créé dans le nouveau répertoire. Sélectionnez l’une des options suivantes :

**Emplacement par défaut :** Il s’agit de la sélection par défaut. Lorsque cette option est sélectionnée, le cache est créé à un emplacement différent selon le serveur d’applications utilisé :

* **JBoss :**`[JBoss Home]\server\[install type]\svcdata\Output\Cache` 
* **WebLogic :**`[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere :**`[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**Répertoire temporaire LC :** Le cache est créé dans un sous-répertoire du répertoire temporaire d’AEM forms, qui est spécifié dans Administration Console sous Paramètres > Paramètres de Core System > Configurations > Emplacement du répertoire temporaire. Le sous-répertoire est nommé `adobeoutput_[servername]`.

>[!NOTE]
>
>Si vous utilisez un utilitaire de nettoyage des répertoires temporaires, sachez que si la suppression de ces répertoires n’affecte pas les fonctionnalités, elle réduit considérablement les performances pendant une courte période, jusqu’à ce que le nouveau cache soit reconstitué. Pour éviter ce problème, ne supprimez pas ces répertoires lorsque vous videz le répertoire temporaire d’AEM forms.
