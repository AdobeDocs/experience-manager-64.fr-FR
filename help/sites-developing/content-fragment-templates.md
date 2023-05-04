---
title: Modèles de fragment de contenu
seo-title: Content Fragment Templates
description: Les modèles sont sélectionnés lors de la création d’un fragment de contenu et fournissent au nouveau fragment la structure de base, l’élément et la variation
seo-description: Templates are selected when creating a content fragmen and provide the new fragment with the basic structure, element, and variation
uuid: 74675e82-26b4-4105-8031-21de51131236
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 8c399a27-abdb-41fb-bd76-f30d22f1d68f
exl-id: fdf1aba8-17fa-473a-9c32-7189d0628927
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 87%

---

# Modèles de fragment de contenu{#content-fragment-templates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

>[!CAUTION]
>
>Les [modèles de fragment de contenu](/help/assets/content-fragments-models.md) sont désormais recommandés pour créer tous les fragments.
>
>Les modèles de fragment de contenu sont utilisés pour tous les exemples dans We.Retail.

Les modèles sont sélectionnés lors de la création d’un fragment de contenu. Ils fournissent au nouveau fragment la structure de base, les éléments et la variation. Les modèles utilisés pour les fragments de contenu sont soumis au gestionnaire de configuration Granite.

Les modèles prêts à l’emploi sont stockés sous :

* `/libs/settings/dam/cfm/templates`

Vous pouvez créer des modèles spécifiques à vos sites pour les fragments de contenu sous :

* `/apps/settings/dam/cfm/templates`

   Emplacement servant à stocker des modèles prêts à l’emploi ou fournir à l’application des modèles spécifiques qui ne sont pas censés être étendus/modifiés au moment de l’exécution.

* `/conf/global/settings/dam/cfm/templates`

   Emplacement des modèles spécifiques au client à l’échelle de l’instance et qui doivent être modifiés au moment de l’exécution.

L’ordre de priorité est (dans l’ordre décroissant) `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>En effet, le contenu de `/libs` est remplacé dès que vous mettez à niveau votre instance (et risque de l’être si vous appliquez un correctif ou un Feature Pack).
>
>La méthode recommandée pour la configuration et d’autres modifications est la suivante :
>
>1. Recréez l’élément requis (tel qu’il existe dans `/libs`) sous `/apps`.
>
>1. Apportez les modifications désirées dans `/apps`.

>


La structure de base d’un modèle est conservée sous :

```xml
conf
  global
    settings
      dam
        cfm
          templates
            <template-name>
              ...
```

Avec la structure spécifique :

```xml
+ <template-name>
    - jcr:primaryType
    - jcr:title
    - jcr:description
    - initialAssociatedContent
    - precreateElements
    - version 
    + elements
        - jcr:primaryType
        + <element-name>
            - jcr:primaryType
            - jcr:title 
            - defaultContent 
            - initialContentType 
            - name 
        ... + other element definitions
    + variations
        - jcr:primaryType 
        + <variation-name>
            - jcr:primaryType 
            - jcr:title 
            - jcr:description
            - name 
        ... + other variation definitions 
```

Plus de détails sur les nœuds et leurs propriétés : 

* **Modèle**

<table> 
 <tbody> 
  <tr> 
   <th>Nom</th> 
   <th>Type</th> 
   <th>Valeur</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<em>template-name</em>&gt;</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Ce nœud est la racine de chaque modèle. Il est obligatoire et doit avoir un nom unique.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>obligatoire<br /> </p> </td> 
   <td>Le titre du modèle (affiché dans l’assistant <strong>Créer un fragment</strong>).</td> 
  </tr> 
  <tr> 
   <td><code>jcr:description</code></td> 
   <td><p><code>String</code></p> <p>facultatif</p> </td> 
   <td>Un texte qui décrit l’objet du modèle (affiché dans l’assistant <strong>Créer un fragment</strong>).</td> 
  </tr> 
  <tr> 
   <td><code>initialAssociatedContent</code></td> 
   <td><p><code>String[]</code></p> <p>facultatif</p> </td> 
   <td>Un tableau avec les chemins d’accès aux collections qui doivent être associées par défaut à un fragment de contenu nouvellement créé.</td> 
  </tr> 
  <tr> 
   <td><code>precreateElements</code></td> 
   <td><p><code>Boolean</code></p> <p>obligatoire</p> </td> 
   <td><p><code>true</code>, si les sous-ressources représentant les éléments (à l’exception de l’élément principal) du fragment de contenu doivent être créées lors de la création du fragment de contenu ; <em>false</em> si elles doivent être créées « à la volée ».</p> <p><strong>Remarque</strong> : actuellement, ce paramètre doit être défini sur <code>true</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><code>version</code></td> 
   <td><p><code>Long</code></p> <p>obligatoire</p> </td> 
   <td><p>Version de la structure de contenu ; actuellement pris en charge :</p> <p><strong>Remarque</strong> : actuellement, ce paramètre doit être défini sur <code>2</code>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

* **Éléments**

<table> 
 <tbody> 
  <tr> 
   <th>Nom</th> 
   <th>Type</th> 
   <th>Valeur</th> 
  </tr> 
  <tr> 
   <td><code>elements</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>obligatoire</p> </td> 
   <td><p>Nœud contenant la définition des éléments du fragment de contenu. Il est obligatoire et doit contenir au moins un nœud enfant pour l’élément <strong>Principal</strong> mais peut contenir [1..n] nœuds enfants.</p> <p>Lorsque le modèle est utilisé, la sous-branche des éléments est copiée dans la sous-branche de modèle du fragment.</p> <p>Le premier élément (affiché dans CRXDE Lite) est automatiquement considéré comme l’élément <i>Principal</i> ; le nom du nœud n’a pas d’importance et le nœud lui-même n’a pas de signification particulière, mis à part le fait qu’il est représenté par la ressource principale ; les autres éléments sont traités comme des sous-ressources.</p> </td> 
  </tr> 
 </tbody> 
</table>

* **Nom de l’élément**

<table> 
 <tbody> 
  <tr> 
   <th>Nom</th> 
   <th>Type</th> 
   <th>Valeur</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<i>element-name</i>&gt;</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Ce nœud définit un élément. Il est obligatoire et doit avoir un nom unique.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>obligatoire</p> </td> 
   <td>Titre de l’élément (affiché dans le sélecteur d’éléments de l’éditeur de fragments).</td> 
  </tr> 
  <tr> 
   <td><code>defaultContent</code></td> 
   <td><p><code>String</code></p> <p>facultatif</p> <p>par défaut : ""</p> </td> 
   <td>Contenu initial de l’élément ; utilisé uniquement si <code>precreateElements</code><i> = </i><code>true</code></td> 
  </tr> 
  <tr> 
   <td><code>initialContentType</code></td> 
   <td><p><code>String</code></p> <p>facultatif</p> <p>par défaut : <code>text/html</code></p> </td> 
   <td><p>Type de contenu initial de l’élément ; utilisé uniquement si <code>precreateElements</code><i> = </i><code>true</code> ; actuellement pris en charge :</p> 
    <ul> 
     <li><code>text/html</code></li> 
     <li><code>text/plain</code></li> 
     <li><code>text/x-markdown</code></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>name</code></td> 
   <td><p><code>String</code></p> <p>obligatoire</p> </td> 
   <td>Nom interne de l’élément ; doit être unique pour le type de fragment.</td> 
  </tr> 
 </tbody> 
</table>

* **Variations**

<table> 
 <tbody> 
  <tr> 
   <th>Nom</th> 
   <th>Type</th> 
   <th>Valeur</th> 
  </tr> 
  <tr> 
   <td><code>variations</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>facultatif</p> </td> 
   <td>Ce nœud facultatif contient la définition des variantes initiales du fragment de contenu.</td> 
  </tr> 
 </tbody> 
</table>

* **Nom de la variation**

<table> 
 <tbody> 
  <tr> 
   <th>Nom</th> 
   <th>Type</th> 
   <th>Valeur</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<i>variation-name</i>&gt;</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>requis si un nœud de variation est présent</p> </td> 
   <td><p>Définit une variation initiale.<br /> La variation est ajoutée à tous les éléments du fragment de contenu par défaut.</p> <p>La variation aura le même contenu initial que l’élément correspondant (voir <code class="code">defaultContent/
       initialContentType</code>).</p> </td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>obligatoire</p> </td> 
   <td>Titre de la variation (affiché dans la <strong>Variation</strong> de l’éditeur de fragments (rail de gauche)).</td> 
  </tr> 
  <tr> 
   <td><code>jcr:desciption</code></td> 
   <td><p><code>String</code></p> <p>facultatif</p> <p>par défaut : ""</p> </td> 
   <td>Texte qui fournit une description de la variation <span>(affichée dans l’onglet <strong>Variation</strong> de l’éditeur de fragments (rail de gauche)).</span></td> 
  </tr> 
 </tbody> 
</table>
