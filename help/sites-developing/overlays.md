---
title: Recouvrements
seo-title: Overlays
description: AEM applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
seo-description: AEM uses the principle of overlays to allow you to extend and customize the consoles and other functionality
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
exl-id: c0678bb6-5e57-4ebb-b6dc-5240bafbc79e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 64%

---

# Recouvrements{#overlays}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM (et auparavant, CQ) a longtemps utilisé le principe des recouvrements pour vous permettre d’étendre et de personnaliser le [consoles](/help/sites-developing/customizing-consoles-touch.md) et d’autres fonctionnalités (par exemple, [création de pages](/help/sites-developing/customizing-page-authoring-touch.md)).

Recouvrement est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte (extension d’AEM), une superposition signifie prendre la fonctionnalité prédéfinie et y imposer vos propres définitions (pour personnaliser la fonctionnalité standard).

Dans une instance standard, la fonctionnalité prédéfinie est conservée sous `/libs` et il est conseillé de définir votre incrustation (personnalisations) sous la branche `/apps`. AEM utilise un chemin de recherche pour localiser une ressource, en commençant par la branche `/apps`, puis la branche `/libs` (le [chemin de recherche peut être configuré](#configuring-the-search-paths)). Ce mécanisme signifie que votre recouvrement (et les personnalisations qui y sont définies) sera prioritaire.

Depuis AEM 6.0, des modifications ont été apportées à la manière dont les superpositions sont implémentées et utilisées :

* AEM 6.0 et versions ultérieures : pour les incrustations liées à [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) (interface utilisateur tactile)

   * Méthode

      * Recréez la structure `/libs` appropriée sous `/apps`.

         Cela ne nécessite aucune copie 1:1 ; [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) est utilisé pour effectuer des références croisées avec les définitions d’origine qui sont requises. Sling Resource Merger propose des services pour accéder à des ressources et les fusionner par le biais de mécanismes de différenciation (diff).

      * Le cas échéant, effectuez des modifications sous `/apps`.
   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Vous ne devez redéfinir que ce qui est réellement nécessaire.


* Recouvrements autres que Granite et antérieurs à AEM 6.0

   * Méthode

      * Copiez le contenu de `/libs` vers `/apps`.

         Vous devez copier la sous-branche entière, y compris les propriétés.

      * Le cas échéant, effectuez des modifications sous `/apps`.
   * Inconvénients

      * La modification d’un élément sous `/libs` n’entraînera pas la perte des changements effectués. Cependant, il se peut que vous deviez recréer certaines modifications affectant votre recouvrement sous `/apps`.


>[!CAUTION]
>
>Le [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) et les méthodes associées ne peuvent être utilisées qu’avec [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html). Cela signifie que la création d’un recouvrement avec une ossature n’est appropriée que pour l’interface utilisateur (IU) tactile standard.
>
>Les superpositions pour d’autres zones (y compris l’IU classique) impliquent de copier le noeud approprié et la sous-structure entière, puis d’apporter les modifications requises.

Les recouvrements sont la méthode recommandée pour de nombreuses modifications, telles que [configuration des consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) ou [création de votre catégorie de sélection dans l’explorateur de ressources dans le panneau latéral](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (utilisé lors de la création de pages). Ils sont requis pour les raisons suivantes :

* Vous ***ne devez pas* effectuer de modifications dans la branche `/libs`**Les modifications que vous effectuez risquent d’être perdues, car cette branche est sensible aux modifications lorsque vous :

   * mise à niveau sur votre instance
   * appliquer un correctif ;
   * installation d’un Feature Pack ;

* Ils centralisent vos modifications dans un seul emplacement ; ils facilitent le suivi, la migration, la sauvegarde et/ou le débogage de vos modifications, suivant les besoins.

## Configuration des chemins de recherche {#configuring-the-search-paths}

Pour les superpositions, la ressource diffusée est un agrégat des ressources et propriétés récupérées, en fonction des chemins de recherche qui peuvent être définis :

* La ressource **Resolver Search Path**, telle qu’elle est définie dans la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) pour **Apache Sling Resource Resolver Factory**.

   * L’ordre descendant des chemins de recherche indique leurs priorités respectives.
   * Dans une installation standard, les principales valeurs par défaut sont les suivantes : `/apps`, `/libs`. Par conséquent, le contenu de `/apps` a une priorité supérieure à celui de `/libs` (en d’autres termes, il le *recouvre*).

* Deux utilisateurs du service ont besoin d’un accès JCR:READ à l’emplacement de stockage des scripts. Ces utilisateurs sont : components-search-service (utilisé par les composants de cache et d’accès com.day.cq.wcm.coreto) et sling-scripting (utilisé par org.apache.sling.servlets.resolver pour rechercher des servlets).
* La configuration suivante doit également être définie en fonction de l’emplacement de stockage des scripts (dans cet exemple sous /etc, /libs ou /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Enfin, le Servlet Resolver doit également être configuré (dans cet exemple, pour ajouter également /etc).

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver  
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

## Exemple d’utilisation {#example-of-usage}

Voici quelques exemples présentés dans les cas suivants :

* [Personnalisation des consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Personnalisation de la création de pages](/help/sites-developing/customizing-page-authoring-touch.md)
