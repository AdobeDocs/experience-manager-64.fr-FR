---
title: '[!DNL Experience Manager Assets] Expérience de page d’accueil'
description: Personnalisez la page d’accueil des ressources pour bénéficier d’une expérience d’écran de bienvenue enrichie, y compris un instantané des activités récentes concernant les ressources.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 41%

---

# [!DNL Adobe Experience Manager Assets] Expérience de page d’accueil {#aem-assets-home-page-experience}

Personnalisez le [!DNL Experience Manager Assets] Page d’accueil pour une expérience d’écran de bienvenue riche, avec un instantané des activités récentes concernant les ressources.

Le [!DNL Adobe Experience Manager Assets] La page d’accueil offre une expérience d’écran de bienvenue riche et personnalisée, qui inclut un instantané des activités récentes, telles que les ressources récemment affichées ou chargées.

La page d’accueil d’Assets est désactivée par défaut. Pour l’activer, procédez comme suit :

1. Pour accéder à [!DNL Experience Manager] Configuration Manager, cliquez sur **[!UICONTROL Outils > Opération > Console web]**.
1. Ouvrez le **Enregistreur d’événements DAM Day CQ** service.
1. Sélectionnez la **[!UICONTROL Activer ce service]** pour activer l’enregistrement des activités.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Dans la **Types d’événement** sélectionnez les événements à enregistrer et enregistrez les modifications.

   >[!CAUTION]
   >
   >Activer les options Ressource affichée, Projets affichés et Collections affichées augmente significativement le nombre d’événements enregistrés.

1. Ouvrez le **[!UICONTROL Indicateur de fonction de la page d’accueil des ressources DAM]** à partir de Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Sélectionnez la **[!UICONTROL isEnabled.name]** pour activer la fonction Page d’accueil des ressources. Enregistrez les modifications.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Ouvrez le **[!UICONTROL Préférences utilisateur]** et sélectionnez **[!UICONTROL Activer la page d’accueil des ressources]**. Enregistrez les modifications.

   ![user_preferences](assets/user_preferences.png)

Après avoir activé la page d’accueil des ressources, accédez à l’interface utilisateur d’Assets à partir de la page Navigation .

![home_page](assets/home_page.png)

Appuyez/cliquez sur le bouton **[!UICONTROL Cliquez ici pour configurer le lien de votre expérience]** pour ajouter votre nom d’utilisateur, votre image d’arrière-plan et votre image de profil.

La page d’accueil des ressources inclut les sections suivantes :

* Section Bienvenue
* Section Widget

**Section Bienvenue**

Si votre profil existe, la section Bienvenue affiche pour vous un message de bienvenue. En outre, il affiche votre image de profil et une image de bienvenue (si elle est déjà configurée).

Si votre profil est incomplet, la section Bienvenue affiche un message de bienvenue générique et un espace réservé pour votre image de profil.

**Section Widget**

Cette section s’affiche sous la section Bienvenue et contient des widgets prêts à l’emploi dans les sections suivantes :

* Activité
* Récent
* Découvrez

**Activité**: Dans cette section, la variable **Mon activité** Le widget affiche les activités récentes effectuées par l’utilisateur connecté avec des ressources (y compris des ressources sans rendu), par exemple les chargements, téléchargements, création de ressources, modifications, commentaires, annotations et partages de ressources.

**Récent**: Le **Récemment consultés** sous cette section, le widget affiche les entités récemment consultées par l’utilisateur connecté, y compris les dossiers, les collections et les projets.

**Discover**: Le **Nouveau** Le widget situé sous cette section affiche les ressources et les rendus récemment chargés dans le [!DNL Assets] instance.

Pour activer la purge des données d’activité de l’utilisateur, activez l’option **Service de purge des événements de la gestion des actifs numériques** à partir de Configuration Manager. Une fois que vous avez activé ce service, les activités de l’utilisateur connecté dépassant le nombre spécifié sont supprimées par le système.

L’écran de bienvenue fournit des outils d’aide à la navigation, comme des icônes sur la barre d’outils afin d’accéder aux dossiers, aux collections et aux catalogues.

>[!NOTE]
>
>L’activation des services Enregistreur d’événements de la gestion des actifs numériques Day CQ et Purge d’événements de la gestion des actifs numériques augmente les opérations d’écriture sur JCR et l’indexation de recherche, ce qui augmente considérablement la charge sur le [!DNL Experience Manager] serveur. La charge supplémentaire sur le [!DNL Experience Manager] peut avoir un impact sur ses performances.

>[!CAUTION]
>
>Les activités de collecte, de filtrage et de purge effectuées par l’utilisateur, requises pour la page d’accueil des ressources, génèrent une charge qui peut affecter les performances. Par conséquent, les administrateurs doivent configurer la page d’accueil de manière efficace pour les utilisateurs cibles.
>
>Adobe recommande que les administrateurs et les utilisateurs qui effectuent des opérations en masse évitent d’utiliser la fonction de la page d’accueil des ressources pour empêcher l’augmentation des activités de l’utilisateur.  De plus, les administrateurs peuvent exclure les activités d’enregistrement de certains utilisateurs en configurant **l’enregistreur d’événement Day CQ DAM** à partir du gestionnaire de configuration.
>
>Si vous utilisez la fonction, Adobe recommande que vous planifiez la fréquence de purge par rapport à la charge du serveur.
