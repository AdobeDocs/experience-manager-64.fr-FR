---
title: Rendre les polices disponibles
seo-title: Make fonts available
description: Assurez-vous que les polices utilisées dans un formulaire sont disponibles sur le serveur d’applications J2EE hébergeant AEM forms.
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: 33d63ec9-b100-48b4-b84d-a9de82c24f86
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 16%

---

# Rendre les polices disponibles {#make-fonts-available}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Assurez-vous que les polices utilisées dans un formulaire sont disponibles sur le serveur d’applications J2EE hébergeant AEM forms. Prenons l’exemple suivant. Un concepteur de formulaire ajoute une police dans le répertoire des polices utilisé par Designer et crée un formulaire qui l’utilise sur un ordinateur distinct. Pour que le service Output utilise la police, placez-la dans le répertoire des polices du client. Si le répertoire des polices du client n’existe pas, créez-en un sur le serveur d’applications J2EE hébergeant AEM forms.

Pour plus d’informations sur les paramètres de police supplémentaires, voir [Configuration des paramètres généraux d’AEM forms](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Définition de l’emplacement du répertoire des polices du client**

1. Dans Administration Console, cliquez sur Paramètres > Paramètres de Core Systems > Configurations.
1. Dans la zone Emplacement du répertoire des polices système, saisissez le chemin d’accès au répertoire des polices du client. Vous pouvez ajouter plusieurs répertoires en les séparant par des points-virgules **;**
1. Cliquez sur OK.
1. Redémarrez le système sur lequel AEM forms est installé.

>[!NOTE]
>
>Les polices sont sélectionnées à partir du cache des polices du système Windows et un redémarrage du système est nécessaire pour mettre à jour le cache. Après avoir spécifié le répertoire des polices du client, assurez-vous de redémarrer le système sur lequel AEM Forms est installé.
