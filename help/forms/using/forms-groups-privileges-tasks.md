---
title: AEM Forms sur les groupes et privilèges OSGi
seo-title: AEM Forms sur les groupes et privilèges OSGi
description: Affecter des utilisateurs aux groupes pour gérer AEM Forms sur OSGi
seo-description: Affecter des utilisateurs aux groupes pour gérer AEM Forms sur OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
translation-type: tm+mt
source-git-commit: f87d70515a385fb23b36797e468325fa1a5e9ff4
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 99%

---


# AEM Forms sur les groupes et privilèges OSGi  {#aem-forms-on-osgi-groups-and-privileges}

Affecter des utilisateurs aux groupes pour gérer AEM Forms sur OSGi

Vous pouvez [créer des groupes](/help/sites-administering/user-group-ac-admin.md#group-administration) et affecter des stratégies et des [utilisateurs](/help/sites-administering/user-group-ac-admin.md#user-administration) aux groupes dans AEM. Ces stratégies contrôlent les privilèges des utilisateurs qui font partie du groupe.

Une fois que vous avez installé le [package du module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md), les groupes mentionnés dans cet article, tels que forms-user et forms-power-user, sont automatiquement disponibles pour affectation. Le tableau suivant répertorie les tâches qu’un utilisateur peut effectuer pour AEM Forms sur OSGi en fonction des affectations de groupe :

<table> 
 <tbody>
  <tr>
   <td>Groupe</td> 
   <td>Tâches</td> 
  </tr>
  <tr>
   <td>utilisateur de formulaires <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Créer, prévisualiser, publier et soumettre des formulaires adaptatifs</li> 
     <li>Créer, prévisualiser et publier des communications interactives et des fragments de document</li> 
     <li>Charger les ressources vers une instance AEM</li> 
     <li>Créer des thèmes</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-user</td> 
   <td>
    <ul> 
     <li>Créer, prévisualiser, publier et soumettre des formulaires adaptatifs</li> 
     <li>Créer, prévisualiser et publier des communications interactives et des fragments de document</li> 
     <li>Créer des scripts pour les formulaires adaptatifs à l’aide de l’éditeur de code</li> 
     <li>Charger des ressources, y compris des scripts</li> 
     <li>Créer des thèmes</li> 
     <li>Importer des packages contenant des données XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Examiner les envois</li> 
     <li>Approuver ou refuser des envois</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
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
     <li>Accéder aux lettres ou aux communications interactives de Correspondence Management à l’aide de l’interface utilisateur de l’agent</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Créer une application de boîte de réception</li> 
     <li>Créer un modèle de processus</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Utiliser les applications de boîte de réception AEM</li> 
     <li>Gérer les instances de processus</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Configurer PDF Generator</li> 
     <li>Configurer Watched folder</li> 
     <li>Gérer les applications de processus</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. L’utilisateur disposant des privilèges du groupe forms-user ne peut pas écrire de scripts pour les formulaires adaptatifs.
1. L’utilisateur disposant des privilèges template-authors ne peut pas écrire de scripts pour les modèles.

