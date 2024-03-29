---
title: Extraire des chaînes pour la traduction
seo-title: Extracting Strings for Translating
description: Utilisez xgettext-maven-plugin pour extraire du code source des chaînes qui doivent être traduites.
seo-description: Use xgettext-maven-plugin to extract strings from your source code that need translating
uuid: 2c586ecb-8494-4f8f-b31a-1ed73644d611
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: components
discoiquuid: 034f70f1-fbd2-4f6b-b07a-5758f0461a5b
exl-id: 50c2479b-72b6-42fa-8e48-45c8e9596161
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 57%

---

# Extraire des chaînes pour la traduction{#extracting-strings-for-translating}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez xgettext-maven-plugin pour extraire du code source les chaînes qui doivent être traduites. Le module externe Maven extrait les chaînes dans un fichier XLIFF que vous envoyez pour traduction. Les chaînes sont extraites à partir des emplacements suivants :

* Fichiers source Java
* Fichiers source JavaScript
* Représentations XML des ressources SVN (noeuds JCR)

## Configuration de l’extraction de chaînes {#configuring-string-extraction}

Configurez la manière dont l’outil xgettext-maven-plugin extrait les chaînes pour votre projet.

```xml
/filter { }
/parsers {
   /vaultxml { }
   /javascript { }
   /regexp {
      /files {
         /java { } 
         /jsp { }
         /extjstemplate { }
      }
   }
}
/potentials { }
```

| Section | Description |
|---|---|
| /filter | Identifie les fichiers qui sont analysés. |
| /parsers/vaultxml | Configure l’analyse des fichiers Vault. Identifie les noeuds JCR qui contiennent des chaînes externalisées et des indices de localisation. Identifie également les noeuds JCR à ignorer. |
| /parsers/javascript | Identifie les fonctions JavaScript qui externalisent les chaînes. Il n’est pas nécessaire de modifier cette section. |
| /parsers/regexp | Configure l’analyse de fichiers de modèle ExtJS, Java et JSP. Il n’est pas nécessaire de modifier cette section. |
| /potentials | Formule de détection des chaînes à internationaliser. |

### Identification des fichiers à analyser {#identifying-the-files-to-parse}

La section /filter du fichier i18n.any identifie les fichiers analysés par l’outil xgettext-maven-plugin. Ajoutez plusieurs règles d’inclusion et d’exclusion qui identifient les fichiers qui sont analysés et ignorés, respectivement. Vous devez inclure tous les fichiers, puis exclure ceux que vous ne souhaitez pas analyser. En règle générale, vous excluez les types de fichiers qui ne contribuent pas à l’interface utilisateur ou les fichiers qui définissent l’interface utilisateur mais ne sont pas traduits. Les règles d’inclusion et d’exclusion ont le format suivant :

```
{ /include "pattern" }
{ /exclude "pattern" }
```

La partie &quot;pattern&quot; d’une règle est utilisée pour faire correspondre les noms des fichiers à inclure ou à exclure. Le préfixe de modèle indique si vous faites correspondre un noeud JCR (sa représentation dans Vault) ou le système de fichiers.

| Préfixe | Effet |
|---|---|
| / | Indique un chemin JCR. Par conséquent, ce préfixe correspond aux fichiers situés dans le répertoire jcr_root. |
| &amp;ast; | Indique un fichier ordinaire sur le système de fichiers. |
| aucune | L’absence de préfixe, ou un motif commençant par un nom de dossier ou de fichier, indique un fichier ordinaire sur le système de fichiers. |

Lorsqu’il est utilisé dans un motif, le caractère / indique un sous-répertoire et le caractère &amp;ast; correspond à tous les éléments. Le tableau suivant répertorie plusieurs exemples de règles.

<table> 
 <tbody> 
  <tr> 
   <th>Exemple de règle</th> 
   <th>Effet</th> 
  </tr> 
  <tr> 
   <td><code>{ /include "*" }</code></td> 
   <td>Inclure tous les fichiers.</td> 
  </tr> 
  <tr> 
   <td><code>{ /exclude "*.pdf" }</code></td> 
   <td>Exclure tous les fichiers du PDF.</td> 
  </tr> 
  <tr> 
   <td><code> { /exclude "*/pom.xml" }</code></td> 
   <td>Exclure les fichiers POM.</td> 
  </tr> 
  <tr> 
   <td><code class="code">{ /exclude "/content/*" }
      { /include "/content/catalogs/geometrixx/templatepages" }
      { /include "/content/catalogs/geometrixx/templatepages/*" }</code></td> 
   <td><p>Excluez tous les fichiers sous le nœud /content.</p> <p>Inclure le nœud /content/catalogs/geometrixx/templatepages.</p> <p>Inclure tous les nœuds enfants /content/catalogs/geometrixx/templatepages.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Extraction des chaînes  {#extracting-the-strings}

aucun POM :

```shell
mvn -N com.adobe.granite.maven:xgettext-maven-plugin:1.2.2:extract  -Dxgettext.verbose=true -Dxgettext.target=out -Dxgettext.rules=i18n.any -Dxgettext.root=.
```

Avec POM : Ajoutez ceci au POM :

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.adobe.granite.maven</groupId>
            <artifactId>xgettext-maven-plugin</artifactId>
            <version>1.1</version>
            <configuration>
                <rules>i18n.any</rules>
                <root>jcr_root</root>
                <xliff>cq.xliff</xliff>
                <verbose>true</verbose>
            </configuration>
        </plugin>
    </plugins>
</build>
```

La commande :

```shell
mvn xgettext:extract
```

### Fichiers de sortie {#output-files}

* `raw.xliff` : chaînes extraites
* `warn.log` : avertissements (le cas échéant), si l’API `CQ.I18n.getMessage()` est utilisée de manière incorrecte. Une correction est toujours nécessaire, suivie d’une nouvelle exécution.

* `parserwarn.log` : avertissements de l’analyseur (le cas échéant) ; problèmes de l’analyseur js, par exemple
* `potentials.xliff` : candidats « potentiels » qui ne sont pas extraits, mais il peut s’agir de chaînes lisibles qui doivent être traduites (peuvent être ignorées ; produisent toujours un grand nombre de faux positifs).
* `strings.xliff` : fichier xliff aplati, à importer dans ALF
* `backrefs.txt` : permet de rechercher rapidement une chaîne donnée dans des emplacements de code source.
