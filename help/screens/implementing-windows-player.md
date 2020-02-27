---
title: Mise en œuvre du lecteur Windows 10
seo-title: Mise en œuvre du lecteur Windows 10
description: 'Suivez cette page pour en savoir plus sur la configuration du lecteur AEM Screens Windows 10. '
seo-description: 'Suivez cette page pour en savoir plus sur la configuration du lecteur AEM Screens Windows 10. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Mise en œuvre du lecteur Windows 10{#implementing-windows-player}

Cette section décrit la configuration du lecteur AEM Screens Windows 10. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

## Installation du lecteur Windows {#installing-windows-player}

Pour mettre en œuvre le lecteur Windows pour AEM Screens, installez le lecteur Windows pour AEM Screens.

Consultez la page [**Téléchargements du lecteur AEM 6.4 **](https://download.macromedia.com/screens/).

### Méthode ad hoc {#ad-hoc-method}

Méthode ad hoc pour installer le dernier lecteur Windows (*.exe*), consultez la page de téléchargement [**du lecteur **](https://download.macromedia.com/screens/)AEM 6.4.

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** depuis le menu d’actions de gauche et saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.

1. Click on the **Registration** link from the left action menu to complete the device registation process.

### Enregistrement de plusieurs lecteurs Windows 10 avec une configuration {#registering-multiple-windows-players-with-one-configuration}

Une fois le lecteur Windows installé, vous pouvez enregistrer plusieurs lecteurs avec une seule configuration.

>[!NOTE]
>
>**Enregistrement groupé du lecteur Windows**
>
>Lors de la mise en œuvre du lecteur Windows, vous n’avez pas besoin de configurer manuellement chaque lecteur. À la place, vous pouvez mettre à jour le fichier JSON de configuration une fois qu’il a été testé et qu’il est prêt pour le déploiement.
>
>La configuration garantit que tous les lecteurs envoient un ping au même serveur spécifié dans le fichier de configuration. Vous devez encore enregistrer manuellement chaque lecteur.

Suivez les étapes ci-dessous pour configurer le lecteur Windows 10 :

1. Installez le lecteur Windows.
1. Recherchez le fichier de configuration sous ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Mettez à jour le fichier JSON de configuration en utilisant les informations ci-dessous, puis copiez le même dossier sur tous les systèmes où réside le lecteur.

### Attributs de règle    {#policy-attributes}

Le tableau suivant récapitule les attributs de règle et fournit un exemple de fichier JSON de règle pour référence :

| **Nom de la règle** | **Objectif** |
|---|---|
| server | URL du serveur Adobe Experience Manager (AEM). |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification de redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Lorsque la valeur est définie sur false, il est entièrement configuré et en production. |
| enableOSD | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur false lorsqu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez-la pour résoudre les incidents et désactivez-la une fois que l’interface est entièrement configurée et en production. |

#### Exemple de fichier JSON de règles    {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

