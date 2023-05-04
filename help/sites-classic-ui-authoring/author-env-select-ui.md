---
title: Choisir votre interface utilisateur
seo-title: Selecting your UI
description: Pour offrir davantage de confort aux auteurs et autrices, l’IU destinée aux écrans tactiles permet de basculer vers l’IU classique lorsque cela s’avère nécessaire.
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 997040d4-cf8f-4240-8423-a98d562aae02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 67%

---

# Choisir votre interface utilisateur{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’interface utilisateur activée pour les écrans tactiles remplace l’IU classique, il appartient donc à l’utilisateur ou à l’administrateur de l’instance AEM de choisir explicitement s’il faut continuer à utiliser cette dernière. Étant donné que l’IU classique n’est plus gérée, il n’est plus possible pour l’auteur de basculer simplement de l’IU classique vers son équivalent dans l’IU activée pour les écrans tactiles.

Pour offrir davantage de confort à ces utilisateurs, l’IU destinée aux écrans tactiles permet de basculer vers l’IU classique lorsque cela s’avère nécessaire. Voir [Sélection de l’interface utilisateur](/help/sites-authoring/select-ui.md) pour plus d’informations, voir la documentation de création standard .

>[!NOTE]
>
>Les instances mises à niveau à partir d’une version précédente conservent l’IU classique pour la création de pages.
>
>Après la mise à niveau, la création de pages ne bascule pas automatiquement vers l’IU tactile. Vous pouvez cependant configurer ce basculement à l’aide de la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) du **service Mode d’IU de création de la gestion de contenu web** (service `AuthoringUIMode`). Consultez la section [IU par défaut en fonction de l’éditeur](#uioverridesfortheeditor).

## Configuration de l’interface utilisateur par défaut pour votre instance {#configuring-the-default-ui-for-your-instance}

Un administrateur système peut configurer l’interface utilisateur qui s’affiche au démarrage et lors de la connexion à l’aide de [Mappage racine](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Il peut être remplacé par les paramètres par défaut de l’utilisateur ou les paramètres de session.
