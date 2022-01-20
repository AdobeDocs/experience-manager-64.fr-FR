---
title: Partage de dossiers Experience Manager Assets avec Creative Cloud
description: Configuration et bonnes pratiques pour permettre aux utilisateurs d’Adobe Experience Manager Assets d’échanger des dossiers de ressources avec les utilisateurs de Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 16%

---

# [!DNL Experience Manager] to [!DNL Creative Cloud] Bonnes pratiques relatives au partage de dossiers {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>La fonction Partage de dossiers du Experience Manager vers le Creative Cloud est obsolète. Adobe recommande vivement d’utiliser des fonctionnalités plus récentes, telles que [Adobe d’un lien de ressource](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) ou [application de bureau Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr). En savoir plus dans [Bonnes pratiques d’intégration Experience Manager et Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager peut être configuré pour permettre aux utilisateurs de Experience Manager Assets de partager des dossiers avec des utilisateurs Creative Cloud afin qu’ils soient disponibles en tant que dossiers partagés dans le service Assets Creative Cloud. Cette fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs de Experience Manager Assets, en particulier lorsque les utilisateurs créatifs n’ont pas accès à l’instance Experience Manager Assets (ils ne se trouvent pas sur le réseau d’entreprise).

Ce type d’intégration peut être utilisé dans les deux cas d’utilisation, en particulier lorsque vous travaillez avec des utilisateurs qui n’ont pas d’accès direct à Experience Manager Assets :

* Partage d’un ensemble de ressources spécifiques de Experience Manager Assets avec des utilisateurs de fichiers de Creative Cloud (par exemple, un résumé créatif et un ensemble de ressources approuvées pour le travail de conception d’une nouvelle activité marketing)
* Réception de nouveaux fichiers d’utilisateurs Creative Cloud.

>[!NOTE]
>
>Avant de lire ce document, vous pouvez consulter [Bonnes pratiques d’intégration Experience Manager et Creative Cloud](aem-cc-integration-best-practices.md) pour un aperçu général de la rubrique.

## Présentation {#overview}

Le partage de dossiers entre les Experience Manager et les Creative Cloud repose sur le partage côté serveur de dossiers et de fichiers entre Experience Manager Assets et les comptes Creative Cloud. Les professionnels de la création, qui utilisent l’application de bureau Creative Cloud sur leur bureau, peuvent également rendre les dossiers partagés disponibles directement sur leurs disques à l’aide de la technologie Adobe CreativeSync.

Le diagramme suivant offre une vue d’ensemble du processus d’intégration.

![chlimage_1-406](assets/chlimage_1-406.png)

L’intégration comprend les éléments suivants :

* **[!DNL Assets]server** déployé dans le réseau d’entreprise (services gérés ou on-premise) : Le partage de dossiers est lancé ici.
* **Service principal Adobe Marketing Cloud Assets**: sert d’intermédiaire entre les services de stockage Experience Manager et Creative Cloud. L’administrateur de la société qui utilise l’intégration doit établir une relation de confiance entre l’organisation du Marketing Cloud et l’instance Experience Manager Assets. Elles aussi [définir une liste des collaborateurs Creative Cloud approuvés ;](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), afin que les utilisateurs d’Assets puissent partager des dossiers pour plus de sécurité.
* **Services web Creative Cloud Assets** (IU Web des fichiers de stockage et de Creative Cloud) : C’est là que des utilisateurs Creative Cloud spécifiques, avec lesquels un dossier de ressources a été partagé, peuvent accepter l’invitation et voir le dossier dans le stockage de leur compte de Creative Cloud.
* **application de bureau Creative Cloud**: (Facultatif) Permet un accès direct aux dossiers/fichiers partagés depuis le bureau de l’utilisateur créatif via une synchronisation avec le stockage des ressources du Creative Cloud.

## Caractéristiques et limites {#characteristics-and-limitations}

* **Diffusion unidirectionnelle des modifications :** Les modifications de fichier sont propagées dans une seule direction à partir du système (ressources du Experience Manager ou du Creative Cloud), où la ressource a été créée à l’origine (téléchargée). L’intégration ne fournit pas de synchronisation entièrement automatisée et bidirectionnelle entre les deux systèmes.

* **Contrôle de version:**

   * Experience Manager ne crée les versions d’une ressource que si le fichier provient de Experience Manager et y est mis à jour.
   * Creative Cloud Assets fournit sa propre [fonctionnalité de création de versions](https://helpx.adobe.com/fr/creative-cloud/help/versioning-faq.html), qui vise les mises à jour de travail en cours (en général, les mises à jour sont conservées 10 jours).

* **Limites d’espace :** La taille et le volume des fichiers échangés sont limités par les [Quota de ressources Creative Cloud](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) pour les utilisateurs créatifs (selon le niveau d’abonnement) et une taille de fichier maximale de 5 Go. L’espace est en outre limité par le quota de ressources que l’organisation possède dans le service principal d’Adobe Marketing Cloud Assets.

* **Exigences d’espace :** Les fichiers des dossiers partagés doivent également être stockés physiquement dans Experience Manager, puis dans un compte de Creative Cloud, avec une copie mise en cache dans le service principal Ressources de Marketing Cloud.
* **Mise en réseau et bande passante :** Les fichiers dans les dossiers partagés et toutes les mises à jour doivent être transportés sur le réseau entre les systèmes. Vous devez vous assurer que seuls les fichiers et les mises à niveau appropriées sont partagés.
* **Type de dossier** : le partage d’un dossier de ressources de type `sling:OrderedFolder` n’est pas pris en charge. Si vous souhaitez partager un dossier, lors de sa création dans Experience Manager Assets, ne sélectionnez pas l’option Ordre .

## Bonnes pratiques {#best-practices}

Les bonnes pratiques pour utiliser le partage de dossiers entre Experience Manager et Creative Cloud sont les suivantes :

* **Considérations relatives au volume :** Le partage de dossiers de Experience Manager et de Creative Cloud doit être utilisé pour partager un plus petit nombre de fichiers, par exemple, pertinents pour une campagne ou une activité spécifique. Pour partager des jeux de ressources plus volumineux, comme toutes les ressources approuvées dans l’entreprise, utilisez d’autres méthodes de distribution (par exemple, Experience Manager Assets Brand Portal) ou l’appli de bureau Experience Manager.
* **Évitez de partager des hiérarchies profondes :** Le partage fonctionne de manière récursive et n’autorise pas l’annulation sélective du partage. En règle générale, seuls les dossiers sans sous-dossiers, ou ayant une hiérarchie très simple, comme 1 niveau de sous-dossiers, doivent être considérés pour le partage.
* **Séparez les dossiers pour un partage unidirectionnel :** Des dossiers distincts doivent être utilisés pour partager des ressources finales de Experience Manager Assets vers des fichiers de Creative Cloud et pour partager des ressources prêtes pour les créatifs à partir de fichiers de Creative Cloud vers [!DNL Assets]. Associé à une bonne convention d’affectation des noms pour ces dossiers, il crée un environnement de travail plus facile à comprendre pour les utilisateurs Experience Manager Assets et les utilisateurs Creative Cloud.
* **Évitez les travaux en cours dans le dossier partagé :** Le dossier partagé ne doit pas être utilisé pour le travail en cours : utilisez un dossier distinct dans les fichiers du Creative Cloud pour effectuer le travail qui nécessite des modifications fréquentes du fichier.
* **Démarrez une nouvelle tâche en dehors du dossier partagé :** Les nouvelles conceptions (fichiers créatifs) doivent être démarrées dans le dossier de travaux en cours distinct dans les fichiers Creative Cloud. Lorsqu’elles sont prêtes à être partagées avec les utilisateurs de Experience Manager Assets, elles doivent être déplacées ou enregistrées dans le dossier partagé.
* **Simplifiez la structure de partage :** Pour une configuration opérationnelle plus gérable, pensez à simplifier la structure de partage. Au lieu de les partager avec tous les utilisateurs créatifs, les dossiers Experience Manager Assets doivent uniquement être partagés avec les représentants de l’équipe, comme un directeur créatif ou un chef d’équipe. Le responsable artistique doit recevoir les ressources finales, déterminer l’attribution des tâches, puis permettre aux concepteurs de travailler sur les ressources de travail en cours sur leurs comptes Creative Cloud respectifs. Ils peuvent utiliser des fonctions de collaboration de Creative Cloud pour coordonner le travail, puis sélectionner et remettre les ressources prêtes à être partagées dans Experience Manager Assets dans leur dossier partagé prêt pour les créatifs.

Le diagramme suivant illustre un exemple de configuration pour la création de conceptions basées sur des ressources finales existantes de Experience Manager Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
