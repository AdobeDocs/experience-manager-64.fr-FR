---
title: Créer des apparences personnalisées dans les formulaires HTML5
seo-title: Create custom appearances in HTML5 forms
description: Vous pouvez ajouter des widgets personnalisés à une Forms mobile. Vous pouvez étendre les widgets jQuery existants ou développer vos propres widgets personnalisés.
seo-description: You can plug in custom widgets to a Mobile Forms. You can extend existing jQuery Widgets or develop your own custom widgets.
uuid: afb16f42-e404-478b-82dd-4b5b59c4f184
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5d860f05-3257-4cf7-93dd-77d226d59b39
feature: Mobile Forms
exl-id: e9e53b6d-6403-4d37-bac1-efaff0317f34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 43%

---

# Créer des apparences personnalisées dans les formulaires HTML5 {#create-custom-appearances-in-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez ajouter des widgets personnalisés à une Forms mobile. Vous pouvez étendre les widgets jQuery existants ou développer vos propres widgets personnalisés à l’aide de la structure des aspects. Le moteur XFA utilise différents widgets. Consultez la section [Framework d’apparence pour les formulaires adaptatifs et HTML5](/help/forms/using/introduction-widgets.md) pour obtenir des informations détaillées.

![Exemple d’un widget par défaut et d’un widget personnalisé](assets/custom-widgets.jpg)
**Figure :** *Exemple de widget par défaut et personnalisé*

## Intégration de widgets personnalisés à des formulaires HTML5 {#integrating-custom-widgets-with-html-forms}

### Création d’un profil  {#create-a-profile-nbsp}

Vous pouvez créer un profil ou choisir un profil existant pour ajouter un widget personnalisé. Pour plus d’informations sur la création de profils, voir [Création d’un profil personnalisé](/help/forms/using/custom-profile.md).

### Création d’un widget {#create-a-widget}

Les formulaires HTML5 fournissent une implémentation du framework des widgets qui peut être étendu pour créer d’autres widgets. L’implémentation est un widget jQuery *abstractWidget* qui peut être étendu pour écrire un nouveau widget. Le nouveau widget peut être rendu fonctionnel uniquement en étendant/remplaçant les fonctions mentionnées ci-dessous.

<table> 
 <tbody> 
  <tr> 
   <td>Fonction/classe</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td>render</td> 
   <td>La fonction de rendu renvoie l’objet jQuery pour l’élément de HTML par défaut du widget. L’élément de HTML par défaut doit être de type pouvant faire l’objet d’un focus. Par exemple : &lt;a&gt;, &lt;input&gt;, et &lt;li&gt;. L’élément renvoyé est utilisé comme $userControl. Si $userControl indique la contrainte ci-dessus, les fonctions de la classe AbstractWidget fonctionnent comme prévu. Dans le cas contraire, une partie des API communes (focus, clic) nécessitent des modifications. </td> 
  </tr> 
  <tr> 
   <td>getEventMap</td> 
   <td>Renvoie un mappage pour convertir les événements HTML en événements XFA. <br /> {<br /> blur: XFA_EXIT_EVENT,<br /> }<br /> Cet exemple indique que le flou est un événement HTML et que XFA_EXIT_EVENT est l’événement XFA correspondant. </td> 
  </tr> 
  <tr> 
   <td>getOptionsMap</td> 
   <td>Renvoie un mappage qui fournit des détails sur l’action à effectuer lors de la modification d’une option. Les clés sont les options fournies au widget et les valeurs sont les fonctions qui sont appelées lorsqu’une modification de cette option est détectée. Le widget fournit des gestionnaires pour toutes les options courantes (à l’exception de value et displayValue).</td> 
  </tr> 
  <tr> 
   <td>getCommitValue</td> 
   <td>La structure du widget charge la fonction chaque fois que la valeur du widget est enregistrée dans XFAModel (par exemple sur l’événement exit d’un textField). L’implémentation doit renvoyer la valeur qui est enregistrée dans le widget. Le gestionnaire s’accompagne de la nouvelle valeur de l’option.</td> 
  </tr> 
  <tr> 
   <td>showValue</td> 
   <td>Par défaut, dans XFA lors de l’événement enter, la rawValue du champ s’affiche. Cette fonction est appelée pour afficher la rawValue à l’utilisateur. </td> 
  </tr> 
  <tr> 
   <td>showDisplayValue</td> 
   <td>Par défaut, dans XFA lors de l’événement de sortie, la valeur formattedValue du champ s’affiche. Cette fonction est appelée pour afficher la formattedValue à l’utilisateur. </td> 
  </tr> 
 </tbody> 
</table>

Pour créer votre propre widget, dans le profil créé précédemment, ajoutez les références du fichier Javascript qui contient les fonctions remplacées et les nouvelles fonctions ajoutées. Par exemple, le widget *sliderNumericFieldWidget* est un widget pour les champs numériques. Pour utiliser le widget dans votre profil, dans la section d’en-tête, insérez la ligne suivante :

```
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Enregistrement du widget personnalisé avec le moteur de script XFA  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Lorsque le code d’un widget personnalisé est prêt, enregistrez le widget avec le moteur de script à l’aide de l’API `registerConfig` pour [Form Bridge](/help/forms/using/form-bridge-apis.md). widgetConfigObject est utilisé comme entrée.

```
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

La configuration du widget est fournie sous la forme d’un objet JSON (ensemble de paires clé-valeur), où la clé identifie les champs et la valeur représente le widget à utiliser avec ces champs. Voici un exemple de configuration :

```
*{*

*“identifier1” : “customwidgetname”,  
“identifier2” : “customwidgetname2”,  
..  
}*
```

où « identifiant » est un sélecteur CSS jQuery qui représente un champ spécifique, un ensemble de champs d’un type particulier ou tous les champs. La liste suivante regroupe les valeurs de l’identifiant dans différents cas :

| Type d’identificateur | formulaire | Description |
|---|---|---|
| Champ particulier avec le nom fieldname | Identifiant :&quot;div.fieldname&quot; | Tous les champs portant le nom &quot;fieldname&quot; sont générés à l’aide du widget. |
| Tous les champs de type « type » (où type est NumericField, DateField, etc.). : | Identifiant : &quot;div.type&quot; | Dans Timefield et DateTimeField, le type est textfield, ces champs n’étant plus pris en charge. |
| Tous les champs | Identifiant : « div.field » |  |
