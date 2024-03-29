---
title: Conseils de dépannage pour l’espace de travail AEM Forms
seo-title: Troubleshooting guidelines for AEM Forms workspace
description: Activez les journaux et utilisez le débogueur dans le navigateur pour résoudre les problèmes liés à l’espace de travail AEM Forms.
seo-description: Enable logs and use debugger in browser to troubleshoot AEM Forms workspace.
uuid: 07b8c8ed-f1ff-4be5-8005-251ff7b2ac85
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 5dae9ed9-77a3-44f5-a94d-ca5c355c8730
exl-id: 210cb5f2-cc5c-4664-b324-5c6f70f7b593
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 34%

---

# Conseils de dépannage pour l’espace de travail AEM Forms {#troubleshooting-guidelines-for-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cet article explique comment déboguer l’espace de travail AEM Forms en activant la journalisation et en utilisant le débogueur dans un navigateur. Il explique également certains problèmes courants que vous pouvez rencontrer lors de l’utilisation de l’espace de travail AEM Forms et leurs solutions.

## Impossible d’installer le package de l’espace de travail AEM Forms {#unable-to-install-aem-forms-workspace-package}

Après avoir installé le correctif, ouvrez l’espace de travail AEM Forms. Si vous rencontrez l’erreur « Aucune ressource trouvée », ouvrez le gestionnaire de packages CRX, puis réinstallez le package `adobe-lc-workspace-pkg-<version>.zip`.

Lors de l’installation du package, si vous rencontrez une erreur `javax.jcr.nodetype.ConstraintViolationException: OakConstraint0025: Authorizable property rep:authorizableId may not be removed`, procédez comme suit :

1. Connectez-vous à CRX DE Lite. L’URL par défaut est `https://[localhost]:[port]/lc/crx/de/index.jsp`
1. Supprimez le nœud suivant :

   `/home/groups/P/PERM_WORKSPACE_USER`

1. Accédez au gestionnaire de packages. L’URL par défaut est `https://[localhost]:[port]/lc/crx/packmgr/index.jsp.`
1. Recherchez et installez le package `adobe-lc-workspace-pkg-[version].zip`.
1. Redémarrez le serveur d’applications.

## Journalisation de l’espace de travail AEM Forms {#aem-forms-workspace-nbsp-logging}

Vous pouvez générer des journaux à différents niveaux pour la résolution optimale des erreurs. Par exemple, dans une application complexe, la journalisation au niveau du composant permet de déboguer et de résoudre les problèmes liés à des composants spécifiques.

Dans l’espace de travail AEM Forms :

* Pour obtenir les informations de journalisation sur un fichier de composant spécifique, ajoutez `/log/<ComponentFile>/<LogLevel>` dans l’URL, puis appuyez sur `Enter`. Toutes les informations de journalisation pour le fichier de composant au niveau spécifié de journal sont imprimées sur la console.

* Pour obtenir des informations de journalisation tous les fichiers de composant, ajoutez `/log/all/trace` dans l’URL, puis appuyez sur `Enter`.

* Format du journal : `<Component file> <Date>:<Time>: <Log Level> : <Log Message>`

>[!NOTE]
>
>Par défaut, le niveau de journal de tous les composants est défini sur INFO.

* Le niveau de journal défini par l’utilisateur est conservé uniquement pour cette session de navigateur. Lorsque l’utilisateur actualise la page, le niveau de journal est défini sur sa valeur initiale pour tous les composants.

### Liste des fichiers de composant dans l’espace de travail AEM Forms {#list-of-component-files-in-nbsp-aem-forms-workspace}

<table> 
 <tbody> 
  <tr> 
   <td><p>allcategoryModel</p> </td> 
   <td><p>processinstanceModel</p> </td> 
   <td><p>tasklistModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>appnavigationModel</p> </td> 
   <td><p>processInstanceView</p> </td> 
   <td><p>tasklistView</p> </td> 
  </tr> 
  <tr> 
   <td><p>appnavigationView</p> </td> 
   <td><p>processnamelistModel</p> </td> 
   <td><p>taskModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>categorylistModel</p> </td> 
   <td><p>processnamelistView</p> </td> 
   <td><p>taskView</p> </td> 
  </tr> 
  <tr> 
   <td><p>categorylistView</p> </td> 
   <td><p>processnameModel</p> </td> 
   <td><p>teamqueuesView</p> </td> 
  </tr> 
  <tr> 
   <td><p>categoryModel</p> </td> 
   <td><p>processnameView</p> </td> 
   <td><p>todoView</p> </td> 
  </tr> 
  <tr> 
   <td><p>categoryView</p> </td> 
   <td><p>searchtemplatedetailsView</p> </td> 
   <td><p>trackingView</p> </td> 
  </tr> 
  <tr> 
   <td><p>favoritecategoryModel</p> </td> 
   <td><p>sharequeueModel</p> </td> 
   <td><p>uisettingsModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>filterlistView</p> </td> 
   <td><p>sharequeueView</p> </td> 
   <td><p>uisettingsView</p> </td> 
  </tr> 
  <tr> 
   <td><p>filterView</p> </td> 
   <td><p>startpointlistModel</p> </td> 
   <td><p>userinfoModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>outofofficeModel</p> </td> 
   <td><p>startpointlistView</p> </td> 
   <td><p>userinfoView</p> </td> 
  </tr> 
  <tr> 
   <td><p>outofofficeView</p> </td> 
   <td><p>startpointModel</p> </td> 
   <td><p>usersearchModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>preferencesView</p> </td> 
   <td><p>startpointView</p> </td> 
   <td><p>usersearchView</p> </td> 
  </tr> 
  <tr> 
   <td><p>processinstancehistoryView</p> </td> 
   <td><p>startProcessView</p> </td> 
   <td><p>wserrorModel</p> </td> 
  </tr> 
  <tr> 
   <td><p>processinstancelistModel</p> </td> 
   <td><p>startprocessView</p> </td> 
   <td><p>wserrorView</p> </td> 
  </tr> 
  <tr> 
   <td><p>processinstancelistView</p> </td> 
   <td><p>taskdetailsView</p> </td> 
   <td><p>wsmessageView</p> </td> 
  </tr> 
 </tbody> 
</table>

### Niveaux de journal disponibles dans l’espace de travail AEM Forms {#log-levels-available-in-nbsp-aem-forms-workspace}

* FATAL
* ERROR
* WARN
* INFO
* DEBUG
* TRACE
* DÉSACTIVÉ

## Informations de débogage pour les navigateurs {#debugging-information-for-browsers}

Les scripts et les styles peuvent être débogués dans différents navigateurs.

* **Débogage dans IE** : pour déboguer l’espace de travail AEM Forms dans IE, consultez le lien [https://msdn.microsoft.com/fr-fr/library/hh772704(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/hh772704(v=vs.85).aspx).

* **Débogage dans Chrome** : pour ouvrir le débogueur dans Chrome, utilisez le raccourci clavier Ctrl+Maj+I. Pour plus d’informations, consultez le lien [https://developer.chrome.com/extensions/tut_debugging.html](https://developer.chrome.com/extensions/tut_debugging.html).

* **Débogage dans Firefox** : plusieurs modules complémentaires sont disponibles pour déboguer des scripts et des styles dans Firefox. Par exemple, Firebug est un utilitaire de débogage de ce type ([https://getfirebug.com](https://getfirebug.com)).

## FAQ {#faqs}

1. Le formulaire PDF n’est pas rendu ou envoyé dans Google Chrome.

   1. Installez le module externe Adobe® Reader®.
   1. Dans Chrome, ouvrez chrome://plugins pour afficher les modules externes disponibles.
   1. Désactivez le module de visionneuse du PDF Chrome et activez le module externe Adobe Reader.

1. Le formulaire ou le guide du SWF n’est pas rendu dans Google Chrome.

   1. Dans Chrome, ouvrez chrome://plugins pour afficher les modules externes disponibles.
   1. Voir les détails du module externe du lecteur Adobe Flash®.
   1. Désactivez PepperFlash sous le plug-in Adobe Flash Player.

1. J’ai personnalisé l’espace de travail AEM Forms, mais je ne parviens pas à voir les modifications.

   Effacez le cache de votre navigateur, puis accédez à l’espace de travail AEM Forms.

1. Que doit faire l’utilisateur pour permettre le rendu du formulaire en HTML lorsqu’il est ouvert dans le bureau ?

   Sélectionnez le bouton radio HTML du profil par défaut à l’étape Affecter une tâche lors de l’utilisation de Workbench.

1. La pièce jointe ne s’affiche pas lorsque vous cliquez dessus.

   Pour afficher les pièces jointes, activez les fenêtres contextuelles dans votre navigateur.

1. Un utilisateur est connecté à une application de formulaires. Si l’utilisateur tente de se connecter à l’espace de travail, il se peut qu’il ne se charge pas, si l’utilisateur ne dispose pas des autorisations d’espace de travail.

   Déconnectez-vous de l’autre application de formulaires, puis connectez-vous à l’espace de travail.

1. Lorsqu’ils sont rendus dans l’espace de travail AEM Forms, les formulaires de HTML, qui utilisent les propriétés de processus dans leur conception, affichent le bouton Envoyer à l’intérieur du formulaire.

   Lors de la conception de formulaires, lorsque vous utilisez Propriétés du processus, un bouton Envoyer est ajouté à l’intérieur du formulaire. Lorsqu’il est rendu en tant que PDF dans l’espace de travail AEM Forms, le bouton Envoyer n’est pas visible par l’utilisateur final. Cependant, lors du rendu en tant que formulaire de HTML dans l’espace de travail AEM Forms, le bouton Envoyer est visible par l’utilisateur final. Le fait de cliquer sur ce bouton Envoyer à l’intérieur du formulaire ne déclenche aucune action. Cliquez sur le bouton Envoyer au bas de l’espace de travail AEM Forms, en dehors du formulaire, pour terminer la tâche.
