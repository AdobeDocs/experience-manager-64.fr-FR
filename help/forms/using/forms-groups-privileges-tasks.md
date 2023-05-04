---
title: AEM Forms sur les groupes et privilèges OSGi
seo-title: AEM Forms on OSGi Groups and Privileges
description: Affectez des utilisateurs aux groupes pour gérer AEM Forms sur OSGi.
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 31%

---

# AEM Forms sur les groupes et privilèges OSGi {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Affectez des utilisateurs aux groupes pour gérer AEM Forms sur OSGi.

Vous pouvez [créer des groupes ;](/help/sites-administering/user-group-ac-admin.md#group-administration) et affecter des stratégies ; [utilisateurs](/help/sites-administering/user-group-ac-admin.md#user-administration) aux groupes d’AEM. Ces stratégies contrôlent les privilèges des utilisateurs qui font partie du groupe.

Une fois que vous avez installé [Package de module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md), les groupes mentionnés dans cet article, tels que forms-user et forms-power-user, sont automatiquement disponibles pour attribution. Le tableau suivant répertorie les tâches qu’un utilisateur peut effectuer pour AEM Forms sur OSGi en fonction des affectations de groupe :

<table> 
 <tbody>
  <tr>
   <td>Groupe</td> 
   <td>Tâches</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Créer, prévisualiser, publier et envoyer des formulaires adaptatifs</li> 
     <li>Créer, prévisualiser et publier des communications interactives et des fragments de document</li> 
     <li>Chargement de ressources vers une instance AEM</li> 
     <li>Créer des thèmes</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>Créer, prévisualiser, publier et envoyer des formulaires adaptatifs</li> 
     <li>Créer, prévisualiser et publier des communications interactives et des fragments de document</li> 
     <li>Création de scripts pour les formulaires adaptatifs à l’aide de l’éditeur de code</li> 
     <li>Chargement de ressources, y compris de scripts</li> 
     <li>Créer des thèmes</li> 
     <li>Importer des packages contenant des données XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Vérifier les envois</li> 
     <li>Approuver ou refuser des envois</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Créer et prévisualiser des formulaires adaptatifs ou des modèles de communication interactive</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Créer et modifier un modèle de données de formulaire</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>Accès aux lettres ou aux communications interactives de Correspondence Management à l’aide de l’interface utilisateur de l’agent</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Création d’une application de boîte de réception</li> 
     <li>Créer un modèle de processus</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Utilisation des applications de boîte de réception AEM</li> 
     <li>Gestion des instances de workflow</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Configurer PDF Generator</li> 
     <li>Configuration du dossier de contrôle</li> 
     <li>Gérer les applications de processus</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. L’utilisateur disposant de droits de groupe d’utilisateurs de formulaires ne peut pas écrire de scripts pour les formulaires adaptatifs.
1. L’utilisateur disposant des privilèges template-authors ne peut pas écrire de scripts pour les modèles.
