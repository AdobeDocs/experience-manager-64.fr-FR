---
title: "[!DNL Experience Manager Assets] Expérience de page d’accueil"
description: Personnalisez la page d’accueil des ressources pour bénéficier d’une expérience d’écran de bienvenue enrichie, y compris un instantané des activités récentes concernant les ressources.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 47%

---

# Expérience de page d’accueil d’[!DNL Adobe Experience Manager Assets] {#aem-assets-home-page-experience}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Personnalisez la page d’accueil d’[!DNL Experience Manager Assets] afin d’enrichir l’expérience de l’écran de bienvenue, avec notamment un instantané des activités récentes concernant les ressources.

Le [!DNL Adobe Experience Manager Assets] La page d’accueil offre une expérience d’écran de bienvenue riche et personnalisée, qui inclut un instantané des activités récentes, telles que les ressources récemment affichées ou chargées.

La page d’accueil des ressources est désactivée par défaut. Pour l’activer, procédez comme suit :

1. Pour accéder à [!DNL Experience Manager] Configuration Manager, cliquez sur **[!UICONTROL Outils > Opération > Console web]**.
1. Ouvrez le service **Enregistreur d’événement de gestion des ressources numériques Day CQ**.
1. Sélectionnez l’option **[!UICONTROL Activer ce service]** pour activer l’enregistrement des activités.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Dans la liste **Types d’événement**, sélectionnez les événements à enregistrer et enregistrez les modifications.

   >[!CAUTION]
   >
   >Activer les options Ressource affichée, Projets affichés et Collections affichées augmente significativement le nombre d’événements enregistrés.

1. Ouvrez l’**[!UICONTROL Indicateur de fonctionnalité de la page d’accueil des ressources de gestion des ressources numériques]** à partir de Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Sélectionnez la **[!UICONTROL isEnabled.name]** pour activer la fonction Page d’accueil des ressources. Enregistrez les modifications.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Ouvrez la boîte de dialogue **[!UICONTROL Préférences utilisateur]** et sélectionnez **[!UICONTROL Activer la page d’accueil des ressources]**. Enregistrez les modifications.

   ![user_preferences](assets/user_preferences.png)

Après avoir activé la page d’accueil des ressources, accédez à l’interface utilisateur d’Assets à partir de la page Navigation .

![home_page](assets/home_page.png)

Appuyez/cliquez sur le bouton **[!UICONTROL Cliquez ici pour configurer le lien de votre expérience]** pour ajouter votre nom d’utilisateur, votre image d’arrière-plan et votre image de profil.

La page d’accueil des ressources comprend les sections suivantes :

* Section d’accueil
* Section Widget

**Section d’accueil**

Si votre profil existe, la section Bienvenue vous affiche un message de bienvenue. Elle affiche également votre image de profil et une image de bienvenue (si celle-ci est déjà configurée).

Si votre profil est incomplet, la section Bienvenue affiche un message de bienvenue générique et un espace réservé pour votre image de profil.

**Section Widget**

Cette section apparaît sous la section Bienvenue et affiche des widgets prêts à l’emploi sous les sections suivantes :

* Activité
* Récent
* Découvrez

**Activité** : dans cette section, le widget **Mon activité** affiche les activités récentes effectuées avec les ressources (y compris les ressources sans rendu) par l’utilisateur connecté (par exemple, les transferts de ressources, les téléchargements, la création de ressources, les modifications, les commentaires, les annotations et les partages).

**Récent** : le widget **Récemment consultés** de cette section affiche les entités auxquelles l’utilisateur connecté a récemment accédé, y compris les dossiers, les collections et les projets.

**Discover**: Le **Nouveau** Le widget situé sous cette section affiche les ressources et les rendus récemment chargés dans le [!DNL Assets] instance.

Pour permettre la purge des données d’activité d’utilisateur, activez le **service de purge d’événement de gestion des ressources numériques** dans le gestionnaire de configuration. Une fois ce service activé, les activités de l’utilisateur connecté dépassant un nombre spécifié sont supprimées par le système.

L’écran de bienvenue fournit des aides à la navigation simples, par exemple des icônes dans la barre d’outils pour accéder aux dossiers, aux collections et aux catalogues.

>[!NOTE]
>
>Activer les services Enregistreur d’événement de gestion des ressources numériques Day CQ et de purge d’événement de gestion des ressources numériques augmente les opérations d’écriture vers JCR et l’indexation des recherches, ce qui accroît significativement la charge sur le serveur [!DNL Experience Manager]. La charge supplémentaire sur le serveur [!DNL Experience Manager] peut en affecter les performances.

>[!CAUTION]
>
>La capture, le filtrage et la purge des activités utilisateur requises pour la page d’accueil des ressources imposent une surcharge de performances. Par conséquent, les administrateurs doivent configurer efficacement la page d’accueil pour les utilisateurs cibles.
>
>Adobe recommande aux administrateurs et aux utilisateurs qui effectuent des opérations en bloc d’éviter d’utiliser la fonction Page d’accueil des ressources pour éviter d’augmenter les activités des utilisateurs. De plus, les administrateurs peuvent exclure les activités d’enregistrement de certains utilisateurs en configurant l’**Enregistreur d’événement de gestion des ressources numériques Day CQ** à partir du gestionnaire de configuration.
>
>Si vous utilisez la fonction, Adobe recommande de planifier la fréquence de purge par rapport à la charge du serveur.
