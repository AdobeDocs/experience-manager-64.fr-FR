---
title: Utilisation de l’espace de travail AEM Forms
seo-title: Working with AEM Forms workspace
description: Commencez avec l’espace de travail AEM Forms à l’aide de cette présentation rapide des flux de processus.
seo-description: Get started with AEM Forms workspace with this quick overview of the process workflows.
uuid: fac103bd-142b-46cc-9db7-22d1880260f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ebabecb9-91c4-4991-8f5b-d27f940d2ecb
exl-id: b5ca864c-0895-4c83-a8f6-1913452b1b01
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 99%

---

# Utilisation de l’espace de travail AEM Forms {#working-with-aem-forms-workspace}

## Présentation {#introduction}

L’espace de travail AEM Forms fait partie d’AEM Forms. L’espace de travail facilite le rendu de formulaires HTML, en plus des formulaires PDF. Vous pouvez désormais vous lancer dans des processus d’entreprise à partir d’interfaces mobiles et d’applications Web.

En outre, l’espace de travail AEM Forms est hautement personnalisable à l’aide de la norme HTML et des méthodologies de développement JavaScript™. Il s’agit d’un composant logiciel qui s’intègre facilement avec vos autres applications Web.

Pour en savoir plus, voir [Présentation de l’espace de travail AEM Forms](/help/forms/using/introduction-html-workspace.md).

## Se familiariser {#getting-familiar}

Pour être informé du processus de bout en bout de création d’une application de formulaire afin d’automatiser un processus d’entreprise, suivez la présentation. Vous pouvez créer, gérer et tester une application à l’aide de Workbench, Designer et l’espace de travail AEM Forms après avoir suivi la présentation. Pour plus d’informations sur l’implémentation, voir [Création d’une première application AEM Forms](https://helpx.adobe.com/fr_FR/livecycle/11.0/CreateFirstApp/index.html).

## Présentation fonctionnelle {#functional-overview}

Vous pouvez utiliser l’espace de travail AEM Forms pour effectuer les tâches suivantes :

**Démarrer une gestion commerciale :** l’espace de travail AEM Forms classe les processus comme prévu et défini par l’entreprise. Vous pouvez ajouter aux favoris les catégories fréquemment utilisées pour pouvoir y accéder rapidement. Lors du démarrage d’un processus, vous remplissez généralement un formulaire pour démarrer un processus d’entreprise contrôlé par le flux de travail des formulaires. Pour plus d’informations, voir [Démarrage des processus](/help/forms/using/starting-processes.md).

**Afficher et agir sur les tâches :** lorsque vous affichez les listes de tâches, vous visualisez les tâches de gestion commerciale qui vous sont affectées, ou qui sont affectées à des groupes auxquels vous appartenez, ou qui sont les tâches partagées d’autres utilisateurs. Vous pouvez ouvrir, modifier et effectuer les tâches selon vos besoins. En règle générale, l’exécution d’une tâche implique de fournir des informations, d’approuver ou de rejeter un formulaire. Pour plus d’informations, voir [Utilisation des listes de tâches](/help/forms/using/todo-lists.md).

**Suivi de tâches** : pour effectuer le suivi des tâches, utilisez l’onglet Suivi dans l’espace de travail AEM Forms. Vous pouvez rechercher les processus actifs ou terminés que vous avez démarrés ou modifiés. Vous pouvez afficher les tâches, les affectations et les formulaires qui faisaient partie du processus. Vous pouvez également démarrer de nouveaux processus à l’aide des données de formulaire provenant d’un processus lancé précédemment. Pour plus d’informations, voir [Suivi des processus](/help/forms/using/tracking-processes.md).

## Nouvelle offre de l’espace de travail AEM Forms {#new-offering-of-aem-forms-workspace}

**Prise en charge de l’approbation en bloc des tâches** :

Vous pouvez approuver plusieurs tâches du même type. Une fois que vous sélectionnez une tâche à approuver, seules les tâches avec le même processus, les mêmes noms de tâche et les mêmes options de routage restent activées. Voir [Utilisation de listes de tâches](/help/forms/using/todo-lists.md) pour plus d’informations sur l’implémentation.

## Migration de Workspace Flex vers l’espace de travail AEM Forms {#migrating-from-flex-workspace-to-aem-forms-workspace}

**Ce qui continue de fonctionner**

AEM Forms sur JEE déploie également l’espace de travail Flex par défaut. Il continue de fonctionner comme avant et tous les processus et personnalisations existants continuent à fonctionner.

**Les processus existants de migration vers l’espace de travail AEM Forms :**

Dans l’espace de travail AEM Forms, les services par défaut de rendu et d’envoi associés aux formulaires XDP ont changé, dans le profil d’action par défaut, et de nouveaux services ont été ajoutés. Pour plus d’informations, voir [Nouveau service de rendu et d’envoi](/help/forms/using/new-render-submit-service.md). Pour migrer les processus existants qui fonctionnent avec des formulaires XDP afin de pouvoir bénéficier de ces services, suivez [ces étapes](/help/forms/using/new-render-submit-service.md).

**Mappage des personnalisations de l’espace de travail Flex avec l’espace de travail AEM Forms:**

Le mappage entre différents types de personnalisations dans les deux espaces de travail se présente comme suit.

<table> 
 <tbody>
  <tr>
   <td><strong>Type de personnalisation </strong></td> 
   <td><strong>Personnalisations abordées </strong></td> 
   <td><strong>Scénario de personnalisation de l’espace de travail AEM Forms correspondant</strong></td> 
  </tr>
  <tr>
   <td>Personnalisation de localisation</td> 
   <td>
    <ol> 
     <li>Modification des paramètres régionaux de l’espace de travail</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Modification des paramètres régionaux de l’espace de travail AEM Forms</a></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td>Personnalisation du thème</td> 
   <td>
    <ol> 
     <li>Remplacement des images</li> 
     <li>Modification des couleurs</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/changing-organization-logo-branding.md">Modification du logo de l’organisation</a> </li> 
     <li><a href="/help/forms/using/changing-color-scheme-interface.md">Modification du modèle de couleur </a></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td>Personnalisation de la mise en page</td> 
   <td>
    <ol> 
     <li>Simplification de l’interface utilisateur de l’espace de travail<br />  </li> 
     <li>Création d’un nouvel écran de connexion</li> 
     <li>Création d’un conteneur d’approbation personnalisée</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/description-reusable-components.md">Utilisation de composants réutilisables </a></li> 
     <li><a href="/help/forms/using/creating-new-login-screen.md">Création d’un nouvel écran de connexion</a></li> 
     <li>Le conteneur d’approbation est obsolète.</li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### Restrictions de l’espace de travail AEM Forms {#limitations-of-aem-forms-workspace}

Les caractéristiques suivantes de l’espace de travail Flex ne sont pas disponibles dans l’espace de travail AEM Forms : messages et notification, page d’accueil, conteneur d’approbation et l’option de gestion des en-têtes de colonne. Pour obtenir une liste complète, voir [Fonctions de l’espace de travail Flex non disponibles dans l’espace de travail AEM Forms](/help/forms/using/features-flex-workspace-available-html.md).

## Développement avec l’espace de travail AEM Forms {#developing-with-aem-forms-workspace}

### Architecture {#architecture}

L’espace de travail AEM Forms est une application Web basée sur HTML et JavaScript™ hébergée sur CRX™. Lorsque l’URL de l’espace de travail est ouverte dans un navigateur, une ressource CRX™ est appelée et l’application est rendue en tant que page HTML dans le navigateur. Le code des bibliothèques JavaScript et le code JavaScript personnalisé gèrent le comportement interne et externe de l’application, tel que l’interface utilisateur, l’interaction utilisateur et la communication avec le serveur AEM Forms. Pour plus d’informations, voir [l’architecture](/help/forms/using/html-workspace-architecture.md) de l’espace de travail AEM Forms.

### Personnalisation de l’espace de travail AEM Forms {#aem-forms-workspace-customization}

L’espace de travail AEM Forms prend en charge un large éventail de personnalisations pour mettre à jour la mise en page de l’interface utilisateur, son aspect, sa fonctionnalité et bien plus encore. Les personnalisations impliquent la mise à jour d’un ou plusieurs des éléments suivants :

* l’aspect de l’interface utilisateur ;
* la fonctionnalité à l’aide des personnalisations sémantiques ;
* Réutilisation des composants HTML dans d’autres applications Web.

L’article relatif à la [personnalisation](introduction-customizing-html-workspace.md) décrit les types de ces personnalisations.

### Configuration de l’environnement de développement {#set-up-the-developer-environment}

Les éléments livrables de l’espace de travail AEM Forms comprennent un paquet CRX déployé sur CRX, des archives du SDK contenant le code source complet, des bibliothèques JavaScript tierces et des scripts de génération de l’espace de travail AEM Forms. Utilisez-les pour configurer l’environnement de développement pour l’exécution des personnalisations mentionnées ci-dessus. Pour plus de détails, voir [Génération du code de l’espace de travail AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code).

Vous pouvez personnaliser une grande partie de l’interface et des principales fonctionnalités telles que les polices, le modèle de couleurs, le logo, l’écran de connexion, les boîtes de dialogue d’erreur, l’intégration à des applications tierces et la réutilisation de composants dans une application tierce. Vous pouvez également agrandir le contenu affiché sur la page Résumé de la tâche, afficher les images pour actions d’itinéraire de la tâche, et même modifier les modèles et les vues Backbone de bas niveau qui créent l’application de l’espace de travail AEM Forms.

### Rendu HTML des formulaires XDP {#html-rendering-of-xdp-forms}

Par défaut, pour un nouveau processus, un formulaire XDP est rendu au format PDF sur un bureau d’ordinateur et au format HTML sur une tablette. Il est possible de toujours rendre un formulaire XDP au format HTML. Pour plus d’informations, voir [Nouveaux services de rendu et d’envoi](/help/forms/using/new-render-submit-service.md).

La fonction [Mobile Forms](https://helpx.adobe.com/fr/livecycle/help/mobile-forms/introduction.html), qui fonctionne avec les [profils](https://helpx.adobe.com/fr/livecycle/help/mobile-forms/creating-profile.html), permet le rendu HTML des formulaires XDP. Par défaut, « Rendre le nouveau formulaire HTML » utilise le profil `default.html`, qui peut être modifié. Vous pouvez également ajouter des modifications personnalisées qui surviennent avant le rendu d’un formulaire XDP au format HTML.

## Application de l’espace de travail AEM Forms {#aem-forms-workspace-app}

Pour travailler sur vos processus d’entreprise sur un périphérique mobile, vous pouvez utiliser l’offre de l’application de l’espace de travail AEM Forms qui propose des formulaires AEM. Pour plus d’informations, voir [Présentation de l’application de l’espace de travail AEM Forms](https://helpx.adobe.com/fr/livecycle/help/mobile-workspace/mobile-workspace-overview.html).
