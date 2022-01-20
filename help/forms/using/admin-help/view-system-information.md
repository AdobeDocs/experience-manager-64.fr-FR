---
title: Affichage des informations du système
seo-title: View system information
description: Découvrez comment vous pouvez afficher les graphiques de contrôle des ressources et les informations sur le serveur exécutant AEM Forms.
seo-description: Learn how you can view resource monitoring charts and information about the server that is running AEM forms.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
exl-id: e4542335-fcee-4506-965a-5bfe79f4b29a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 35%

---

# Affichage des informations du système {#view-system-information}

L’onglet Système affiche des graphiques de contrôle des ressources ainsi que des informations sur le serveur exécutant AEM Forms. Pour accéder à ces informations, cliquez sur Health Monitor dans l’angle supérieur droit de la page. Si vous exécutez AEM Forms dans un environnement en grappe, les informations affichées concernent le nœud sélectionné dans la liste des serveurs.

Pour enregistrer les informations du système actuel en tant que fichier de propriétés, cliquez sur Enregistrer.

Le volet droit de l’onglet Système affiche une représentation graphique des éléments suivants :

* dénombrement des tâches et travaux ;
* utilisation du tas et du tas validé ;
* utilisation du non-tas et du non-tas validé.

Déplacez le curseur pour obtenir les valeurs d’un moment particulier.

>[!NOTE]
>
>les données graphiques, les valeurs d’information sur le serveur et l’heure de l’horloge sont mises à jour toutes les dix minutes. L’information n’est pas affichée en temps réel.

Le volet gauche de l’onglet Système affiche des renseignements relatifs au serveur et au nœud :

**Machine virtuelle :** Version de la machine virtuelle Java (JVM) sur le serveur.

**Fournisseur de la machine virtuelle :** Fabricant de la JVM.

**Version de la machine virtuelle :** Numéro de version JVM

**Nom de la machine :** Nom d’hôte du serveur sur lequel AEM forms est installé.

**Durée de disponibilité :** Heure (en heures et minutes) pendant laquelle le serveur a été exécuté.

**Compilateur juste à temps :** Nom du compilateur utilisé.

**Temps de compilation :** Durée de la compilation.

**Nombre de threads actifs :** Nombre total de threads actuellement présents dans le système AEM forms.

**Pic du nombre de threads :** Le plus grand nombre de threads en direct jamais enregistrés sur le système.

**Nombre de classes chargées :** Nombre de classes chargées dans la JVM.

**Nombre de classes déchargées :** Nombre de classes déchargées de la JVM.

**Tas minimal :** La quantité minimale de tas utilisée.

**Maximum Heap :** La quantité maximale de tas utilisée.

**Nom du système d’exploitation :** Nom du système d’exploitation exécuté sur le serveur d’AEM forms.

**Version du système d’exploitation :** Numéro de version du système d’exploitation s’exécutant sur le serveur AEM forms.

**Arche du système d’exploitation :** Architecture du système d’exploitation sur lequel la JVM est en cours d’exécution.

**Nombre de processeurs :** Nombre de processeurs sur le système.

**Arguments de la machine virtuelle :** Argument utilisé par la JVM.

**Chemin de la classe :** Chemin de classe utilisé par la JVM.

**Chemin de la bibliothèque :** Chemin d’accès à la bibliothèque utilisé par la JVM.

**Chemin de la classe de démarrage :** Chemin de classe de démarrage utilisé par la JVM.

**Type de serveur d’applications :** Type de serveur d’applications utilisé pour exécuter AEM forms.

**Version du serveur d’applications :** Numéro de version du serveur d’applications utilisé pour exécuter AEM forms.

**Fournisseur du serveur d’applications :** Fabricant du serveur d’applications utilisé pour exécuter AEM forms.

**Date d’installation :** Date d’installation AEM forms (au format aaaa-mm-jj).

**AEM forms Version :** Version d’AEM forms installé.

**Version du correctif :** AEM numéro du correctif des formulaires.

**Nom de la base de données :** Type de base de données utilisée par AEM forms.

**Version de la base de données :** Numéro de version de la base de données utilisée par AEM forms.

**Database Drive Name :** Nom du pilote utilisé par la JVM pour se connecter à la base de données.

**Version du pilote de base de données :** Version du pilote utilisé par la JVM pour se connecter à la base de données.

Le bouton **Enregistrer** permet d’enregistrer ces informations système dans un fichier de propriétés.
