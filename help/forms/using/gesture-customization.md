---
title: Personnalisation de mouvement
seo-title: Gesture customization
description: Personnaliser les mouvements sur votre application AEM Forms
seo-description: Customize the gestures on your AEM Forms app
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 238410e0-1623-49dc-b2fc-b5b2d5fb362b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 42%

---

# Personnalisation de mouvement {#gesture-customization}

Vous pouvez personnaliser les mouvements de l’application AEM Forms afin de fournir une méthode distincte d’interaction avec l’application. Par exemple, vous pouvez ajouter de nouveaux mouvements pour ouvrir/fermer une tâche ou un point de départ.

## Personnalisation des mouvements dans l’application AEM Forms {#to-customize-gestures-in-aem-forms-app}

Dans l’application AEM Forms, un glissement vers la gauche permet d’ouvrir une nouvelle tâche ou un nouveau point de départ, tandis qu’un glissement vers la droite n’active aucune commande. L’exemple suivant décrit les étapes à suivre pour ouvrir une nouvelle tâche ou un nouveau point de départ en effectuant un glissement vers la droite dans l’application AEM Forms.

1. Ouvrez votre projet.

   * Pour iOS, ouvrez `Capture.xcodeproj` dans Xcode
   * Pour Android, ouvrez le projet Android dans Eclipse.
   * Pour Windows, ouvrez `MWSWindows.sln` dans Visual Studio.

1. Accédez au dossier des vues et ouvrez le `task.js` pour modification.

   * Dans Xcode, accédez au **Capture > www > wsmobile > js > runtime > vues** dossier.
   * Dans Eclipse, accédez au **ressources > www > wsmobile > js > runtime > vues** dossier.
   * Dans Visual Studio, accédez au **MWSWindows > www > wsmobile > js > runtime > views** dossier.

   >[!NOTE]
   >
   >Le fichier task.js contient la vue Backbone associée à chaque tâche ou point de départ, tel que répertorié dans les listes de tâches ou de points de départ.

1. Dans le `task.js` , recherchez la propriété events de la vue.

   La propriété events est une map avec chaque entrée au format :

   `"EventName Selector": "Function"`

   Lorsque vous déclenchez un événement JavaScript nommé `EventName`sur un élément de HTML spécifié par `Selector`, la variable `Function`est appelée.

1. Rechercher

   * &quot;appuyez sur .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;appuyez sur .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;appuyez sur .task-content&quot; : &quot;onTaskClick&quot;,

      &quot;appuyez sur .last_empty_div&quot; : &quot;onTaskClick&quot;,
   et remplacer par

   * &quot;swipe .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .task-content&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot; : &quot;onTaskClick&quot;,


1. Enregistrez et fermez le fichier `task.js`.
1. Générez et exécutez l’application AEM Forms. Vous pouvez désormais ouvrir une tâche en faisant glisser votre doigt vers la gauche et la droite.

De même, vous pouvez apporter des modifications dans les autres vues pour différentes combinaisons de mouvements, d’éléments HTML et de fonctions.
