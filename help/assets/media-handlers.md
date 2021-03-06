---
title: Traitement des ressources à l’aide des workflows et des gestionnaires de médias
description: En savoir plus sur les différents gestionnaires de médias et sur la façon de les utiliser dans les workflows afin d’effectuer des tâches sur les ressources.
contentOwner: AG
feature: Workflow,Renditions
role: User
exl-id: 7694c68d-0a17-4052-8fbe-9bf45b229e81
source-git-commit: bc27dee618ee57dc188c7f35a1af4d1dba80cf1b
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 45%

---

# Traitement des ressources à l’aide des workflows et des gestionnaires de médias {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager Assets fournit un ensemble de workflows et de gestionnaires de médias par défaut pour traiter les ressources. Un workflow définit une tâche type de gestion et de traitement des ressources, puis délègue les tâches spécifiques aux gestionnaires de médias, par exemple la génération de miniatures ou l’extraction de métadonnées.

Un workflow peut être défini de manière à s’exécuter automatiquement lorsqu’une ressource d’un type ou d’un format particulier est chargée sur le serveur. Les étapes de traitement sont définies sous la forme d’une série de gestionnaires de médias Experience Manager Assets. Adobe Experience Manager fournit quelques [gestionnaires intégrés,](#default-media-handlers) et plus peuvent être [développé personnalisé](#creating-a-new-media-handler) ou défini en déléguant le processus à une [outil de ligne de commande](#command-line-based-media-handler).

Les gestionnaires de médias sont des services de Experience Manager Assets qui effectuent des actions spécifiques sur les ressources. Par exemple, lorsqu’un fichier audio MP3 est téléchargé dans Experience Manager, un workflow déclenche un gestionnaire MP3 qui extrait les métadonnées et génère une miniature. Les gestionnaires de médias sont utilisés avec des workflows. La plupart des types MIME courants sont pris en charge dans Experience Manager. Vous pouvez exécuter des tâches spécifiques sur les ressources en effectuant l’une des opérations suivantes :

* Extension ou création de workflows.
* Extension ou création de gestionnaires de médias.
* Désactivation ou activation des gestionnaires de médias.

>[!NOTE]
>
>Voir [Formats pris en charge par Assets](assets-formats.md) pour obtenir une description de tous les formats pris en charge par Experience Manager Assets et des fonctionnalités prises en charge pour chaque format.

## Gestionnaires de médias par défaut {#default-media-handlers}

Les gestionnaires de médias suivants sont disponibles dans Experience Manager Assets et gèrent les types MIME les plus courants :

| Nom du gestionnaire | Nom du service (dans la console système) | Types MIME pris en charge |
|---|---|---|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg<br><b>Important</b> - Lorsque vous téléchargez un fichier MP3, il s’agit de [traité à l’aide d’une bibliothèque tierce](https://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html). La bibliothèque calcule une longueur approximative non précise si le MP3 a un débit variable (VBR). |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | Solution de secours au cas où aucun autre gestionnaire n’aurait été trouvé pour extraire des données d’une ressource |

Tous les gestionnaires effectuent les tâches suivantes :

* extraction de toutes les métadonnées disponibles dans la ressource.
* création d’une miniature à partir de la ressource.

Il est possible d’afficher les gestionnaires de médias actifs :

1. Dans votre navigateur, accédez à la page suivante : `http://localhost:4502/system/console/components`.
1. Cliquez sur le lien `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Une liste comportant tous les gestionnaires de médias actifs est affichée. Par exemple :

![chlimage_1-437](assets/chlimage_1-437.png)

## Utilisation des gestionnaires de médias dans les workflows pour effectuer des tâches sur Assets {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Les gestionnaires de médias sont des services utilisés avec des workflows.

Experience Manager dispose de workflows par défaut pour traiter les ressources. Pour les afficher, ouvrez la console Processus et cliquez sur le bouton **[!UICONTROL Modèles]** tab : les titres de workflow commençant par Experience Manager Assets sont spécifiques aux ressources.

Les workflows existants peuvent être étendus et de nouveaux workflows peuvent être créés pour gérer les ressources en fonction d’exigences spécifiques.

L’exemple suivant montre comment améliorer la variable **[!UICONTROL Synchronisation AEM Assets]** de sorte que les sous-ressources soient générées pour toutes les ressources, à l’exception des documents de PDF.

### Désactivation/activation d’un gestionnaire de médias {#disabling-enabling-a-media-handler}

Les gestionnaires de médias peuvent être désactivés ou activés par le biais de la console de gestion web Apache Felix. Lorsque le gestionnaire de médias est désactivé, ses tâches ne sont pas réalisées sur les ressources.

Pour activer/désactiver un gestionnaire de médias :

1. Dans votre navigateur, accédez à la page suivante : `https://<host>:<port>/system/console/components`.
1. Cliquez sur **[!UICONTROL Désactiver]** en regard du nom du gestionnaire de médias. Par exemple : `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Actualisez la page : une icône s’affiche en regard du gestionnaire de médias pour indiquer qu’il est désactivé.
1. Pour activer le gestionnaire de médias, cliquez sur le bouton **[!UICONTROL Activer]** en regard de son nom.

### Création d’un gestionnaire de médias {#creating-a-new-media-handler}

Pour prendre en charge un nouveau type de média ou exécuter des tâches spécifiques sur une ressource, il est nécessaire de créer un gestionnaire de médias. Cette section décrit la procédure à suivre.

#### Classes et interfaces importantes  {#important-classes-and-interfaces}

La meilleure façon de démarrer une implémentation est d’hériter d’une implémentation abstraite fournie qui prend en charge l’essentiel du traitement et qui fournit un comportement par défaut raisonnable : à savoir la classe `com.day.cq.dam.core.AbstractAssetHandler`.

Cette classe fournit déjà un descripteur de service abstrait. Donc, si vous héritez de cette classe et que vous utilisez le plug-in maven-sling-plugin, assurez-vous que vous avez défini l’indicateur inherit sur `true`.

Implémentez les méthodes suivantes :

* `extractMetadata()` : extraction de toutes les métadonnées disponibles.
* `getThumbnailImage()` : création d’une miniature à partir de la ressource transmise.
* `getMimeTypes()` : renvoi des types MIME de la ressource.

Voici un exemple de modèle :

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

L’interface et les classes sont les suivantes :

* `com.day.cq.dam.api.handler.AssetHandler` : cette interface décrit le service qui ajoute la prise en charge de types MIME spécifiques. L’ajout d’un type MIME nécessite l’implémentation de cette interface. L’interface contient des méthodes pour importer et exporter les documents spécifiques, pour créer des miniatures et extraire des métadonnées.
* `com.day.cq.dam.core.AbstractAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes.
* Classe `com.day.cq.dam.core.AbstractSubAssetHandler` :
   * Cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes, ainsi que la fonctionnalité commune d’extraction de sous-ressources.
   * La meilleure façon de démarrer une implémentation est d’hériter d’une implémentation abstraite fournie qui prend en charge la plupart des éléments et qui fournit un comportement par défaut raisonnable : la classe com.day.cq.dam.core.AbstractAssetHandler .
   * Cette classe fournit déjà un descripteur de service abstrait. Donc, si vous héritez de cette classe et que vous utilisez le plug-in maven-sling-plugin, assurez-vous que vous avez défini l’indicateur inherit sur true.

Les méthodes suivantes doivent être implémentées :

* `extractMetadata()` : cette méthode extrait toutes les métadonnées disponibles.
* `getThumbnailImage()` : cette méthode crée une miniature de la ressource transmise.
* `getMimeTypes()`: cette méthode renvoie les types MIME de la ressource.

Voici un exemple de modèle :

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts }

L’interface et les classes sont les suivantes :

* `com.day.cq.dam.api.handler.AssetHandler` : cette interface décrit le service qui ajoute la prise en charge de types MIME spécifiques. L’ajout d’un type MIME nécessite l’implémentation de cette interface. L’interface contient des méthodes pour importer et exporter les documents spécifiques, pour créer des miniatures et extraire des métadonnées.
* `com.day.cq.dam.core.AbstractAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes.
* `com.day.cq.dam.core.AbstractSubAssetHandler` : cette classe sert de base pour toutes les autres implémentations de gestionnaires de ressources et fournit des fonctionnalités communes, ainsi que la fonctionnalité commune d’extraction de sous-ressources.

#### Exemple : créer un gestionnaire de texte spécifique {#example-create-a-specific-text-handler}

Dans cette section, vous allez créer un gestionnaire de texte spécifique qui génère des miniatures avec un filigrane.

Procédez comme suit :

Voir [Outils de développement](../sites-developing/dev-tools.md) pour installer et configurer Eclipse avec un module externe Maven et configurer les dépendances nécessaires au projet Maven.

Après avoir exécuté la procédure suivante, lorsque vous téléchargez un fichier texte dans Experience Manager, les métadonnées du fichier sont extraites et deux miniatures avec un filigrane sont générées.

1. Dans Eclipse, créez `myBundle` Projet Maven :

   1. Dans la barre de menus, cliquez sur **[!UICONTROL Fichier > Nouveau > Autre]**.
   1. Dans la boîte de dialogue, développez le dossier Maven, sélectionnez Projet Maven, puis cliquez sur **[!UICONTROL Suivant]**.
   1. Vérifiez les **[!UICONTROL Création d’un projet simple]** et le **[!UICONTROL Utilisation des emplacements de Workspace par défaut]** , puis cliquez sur **[!UICONTROL Suivant]**.
   1. Définissez le projet Maven avec les valeurs suivantes :

      * Id de groupe : com.day.cq5.myhandler
      * Id d’artefact : myBundle
      * Nom : Mon lot de Experience Manager
      * Description : Ceci est mon lot de Experience Manager
   1. Cliquez sur **[!UICONTROL Finish]** (Terminer). 


1. Définissez le compilateur Java™ sur la version 1.5 :

   1. Cliquez avec le bouton droit de la souris sur le `myBundle` projet, sélectionnez Propriétés.
   1. Sélectionnez Compilateur Java™ et définissez les propriétés suivantes sur 1.5 :

      * Niveau de conformité du compilateur
      * Compatibilité des fichiers .class générés
      * Compatibilité source
   1. Cliquez sur **[!UICONTROL OK]**. Dans la boîte de dialogue, cliquez sur Oui.


1. Remplacez le code du fichier pom.xml par le code suivant :

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion> 
    <!-- ====================================================================== --> 
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent> 
    <!-- ====================================================================== --> 
    <!-- P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging> 
    <!-- ====================================================================== --> 
    <!-- B U I L D D E F I N I T I O N --> 
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build> 
    <!-- ====================================================================== --> 
    <!-- D E P E N D E N C I E S --> 
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. Créer le package `com.day.cq5.myhandler` qui contient les classes Java™ sous `myBundle/src/main/java`:

   1. Sous myBundle, cliquez avec le bouton droit de la souris. `src/main/java`, sélectionnez Nouveau, puis Package.
   1. Nommez-le `com.day.cq5.myhandler` et cliquez sur Terminer.

1. Création de la classe Java™ `MyHandler`:

   1. Dans Eclipse, sous `myBundle/src/main/java`, cliquez avec le bouton droit de la souris sur le `com.day.cq5.myhandler` module, sélectionnez Nouveau, puis Classe.
   1. Dans la boîte de dialogue, nommez la classe Java™ MyHandler et cliquez sur Terminer. Eclipse crée le fichier MyHandler.java et l’ouvre.
   1. Dans `MyHandler.java` remplacez le code existant par le code suivant, puis enregistrez les modifications :

   ```java
   package com.day.cq5.myhandler; 
   import java.awt.Color; 
   import java.awt.Rectangle; 
   import java.awt.image.BufferedImage; 
   import java.io.IOException; 
   import java.io.InputStream; 
   import java.io.InputStreamReader; 
   import javax.jcr.Node; 
   import javax.jcr.RepositoryException; 
   import javax.jcr.Session; 
   import org.apache.commons.io.IOUtils; 
   import org.slf4j.Logger; 
   import org.slf4j.LoggerFactory; 
   import com.day.cq.dam.api.metadata.ExtractedMetadata; 
   import com.day.cq.dam.core.AbstractAssetHandler; 
   import com.day.image.Font; 
   import com.day.image.Layer; 
   import com.day.cq.wcm.foundation.ImageHelper; 
   
   /** 
    * The <code>MyHandler</code> can extract text files 
    * @scr.component inherit="true" immediate="true" metatype="false" 
    * @scr.service 
    * 
    **/ 
   
   public class MyHandler extends AbstractAssetHandler { 
    /** * Logger instance for this class. */ 
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class); 
    /** * Music icon margin */ 
    private static final int MARGIN = 10; 
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */ 
    public String[] getMimeTypes() {
     return new String[] {"text/plain"}; 
    }
   
    public ExtractedMetadata extractMetadata(Node asset) { 
     ExtractedMetadata extractedMetadata = new ExtractedMetadata(); 
     InputStream data = getInputStream(asset); 
     try { 
      // read text data 
      InputStreamReader reader = new InputStreamReader(data); 
      char[] buffer = new char[4096]; 
      String text = ""; 
      while (reader.read(buffer) != -1) { 
       text += new String(buffer); 
      } 
      reader.close(); 
      long wordCount = this.wordCount(text); 
      extractedMetadata.setProperty("text", text); 
      extractedMetadata.setMetaDataProperty("Word Count",wordCount); 
      setMimetype(extractedMetadata, asset); 
     } catch (Throwable t) { 
      log.error("handling error: " + t.toString(), t); 
     } finally { 
      IOUtils.closeQuietly(data); 
     } 
     return extractedMetadata; } 
    // ----------------------< helpers >---------------------------------------- 
    protected BufferedImage getThumbnailImage(Node node) { 
     ExtractedMetadata metadata = extractMetadata(node); 
     final String text = (String) metadata.getProperty("text"); 
     // create text layer 
     final Layer layer = new Layer(500, 600, Color.WHITE); 
     layer.setPaint(Color.black); 
     Font font = new Font("Arial", 12); 
     String displayText = this.getDisplayText(text, 600, 12); 
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text 
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0); 
     } 
     // create watermark and merge with text layer 
     Layer watermarkLayer; 
     try { 
      final Session session = node.getSession(); 
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png"); 
      watermarkLayer.setX(MARGIN); 
      watermarkLayer.setY(MARGIN); 
      layer.merge(watermarkLayer); 
     } catch (RepositoryException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); 
     } catch (IOException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); } 
     layer.crop(new Rectangle(510, 600)); 
     return layer.getImage(); } 
    // ---------------< private >----------------------------------------------- 
    /** 
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px) 
     * * @return the text which will fit into the box 
     */ 
    private String getDisplayText(String text, int height, int fontheight) { 
     String trimmedText = text.trim(); 
     int numOfLines = height / fontheight; 
     String lines[] = trimmedText.split("\n"); 
     if (lines.length <= numOfLines) { 
      return trimmedText; 
     } else { 
      String cuttetText = ""; 
      for (int i = 0; i < numOfLines; i++) { 
       cuttetText += lines[i] + "\n"; 
      } 
      return cuttetText; 
     } 
    } 
    /**
     * * This method counts the number of words in a string 
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */ 
    private long wordCount(String text) { 
     // We need to keep track of the last character, if we have two whitespace in a row we don't want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true; 
     boolean currentWhiteSpace = true; 
     char c; long numwords = 0; 
     int j = text.length(); 
     int i = 0; 
     while (i < j) { 
      c = text.charAt(i++); 
      if (c == 0) { break; } 
      currentWhiteSpace = Character.isWhitespace(c); 
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; } 
      prevWhiteSpace = currentWhiteSpace; 
     } 
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; } 
     return numwords; 
    } 
   }
   ```

1. Compilez la classe Java™ et créez le lot :

   1. Cliquez avec le bouton droit sur le projet myBundle, puis sélectionnez **[!UICONTROL Exécutez comme]**, puis **[!UICONTROL Installation de Maven]**.
   1. Le lot `myBundle-0.0.1-SNAPSHOT.jar` (contenant la classe compilée) est créé sous `myBundle/target`.

1. Dans l’Explorateur CRX, créez un noeud sous `/apps/myApp`. Nom = `install`, Type = `nt:folder`.
1. Copier le lot `myBundle-0.0.1-SNAPSHOT.jar` et stockez-le sous `/apps/myApp/install` (par exemple avec WebDAV). Le nouveau gestionnaire de texte est désormais principal en Experience Manager.
1. Dans votre navigateur, ouvrez la console de gestion web Apache Felix. Sélectionnez l’onglet Composants et désactivez le gestionnaire de texte par défaut. `com.day.cq.dam.core.impl.handler.TextHandler`.

## Gestionnaire de médias en ligne de commande {#command-line-based-media-handler}

Experience Manager vous permet d’exécuter n’importe quel outil de ligne de commande dans un workflow pour convertir des ressources (comme ImageMagick) et ajouter le nouveau rendu à la ressource. Installez l’outil de ligne de commande sur le disque hébergeant le serveur Experience Manager et ajoutez et configurez une étape de processus au workflow. Le processus appelé, appelé `CommandLineProcess`, filtre en fonction de types MIME spécifiques et crée plusieurs miniatures en fonction du nouveau rendu.

Les conversions suivantes peuvent être automatiquement exécutées et stockées dans [!DNL Experience Manager Assets]:

* Transformation EPS et AI à l’aide d’[ImageMagick](https://www.imagemagick.org/script/index.php) et de [Ghostscript](https://www.ghostscript.com/)
* Transcodage vidéo FLV à l’aide de [FFmpeg](https://ffmpeg.org/)
* Encodage MP3 à l’aide de [LAME](https://lame.sourceforge.io)
* Traitement audio à l’aide de [SOX](https://sox.sourceforge.io)

>[!NOTE]
>
>Sur les systèmes autres que Windows, l’outil FFMpeg renvoie une erreur lors de la génération de rendus pour une ressource vidéo dont le nom de fichier contient une apostrophe (’). Si le nom de votre fichier vidéo comporte un guillemet simple, supprimez-le avant de le charger dans Experience Manager.

Le processus `CommandLineProcess` effectue les opérations suivantes par ordre d’apparition dans la liste :

* Filtre le fichier en fonction des types MIME indiqués, le cas échéant.
* Crée un répertoire temporaire sur le disque hébergeant le serveur Experience Manager.
* Diffuse le fichier d’origine vers le répertoire temporaire.
* Exécute la commande définie par les arguments de l’étape. La commande est exécutée dans le répertoire temporaire avec les autorisations de l’utilisateur exécutant Experience Manager.
* Renvoie le résultat dans le dossier de rendu du serveur de Experience Manager.
* Supprime le répertoire temporaire.
* Crée des miniatures basées sur ces rendus, si spécifié. Le nombre et les dimensions des miniatures sont définis par les arguments de l’étape.

### Exemple utilisant ImageMagick {#an-example-using-imagemagick}

L’exemple suivant montre comment configurer l’étape de processus de ligne de commande. Chaque fois qu’une ressource de type MIME gif ou tiff est ajoutée à `/content/dam` sur le serveur Experience Manager, une image inversée de l’original est créée avec trois miniatures supplémentaires (140x100, 48x48 et 10x250).

Pour effectuer cette étape de processus, utilisez ImageMagick. Installez ImageMagick sur le disque hébergeant le serveur Experience Manager :

1. Installation d’ImageMagick. Voir [Documentation d’ImageMagick](https://www.imagemagick.org/script/download.php) pour plus d’informations.
1. Configurez l’outil pour pouvoir exécuter `convert` sur la ligne de commande.
1. Pour vérifier si cet outil est installé correctement, exécutez la commande `convert -h` sur la ligne de commande.

   Il affiche un écran d’aide avec toutes les options possibles de l’outil de conversion.

   >[!NOTE]
   >
   >Dans certaines versions de Windows® (par exemple, Windows® SE), la commande convert ne s’exécute pas, car elle entre en conflit avec l’utilitaire de conversion natif qui fait partie de l’installation de Windows®. Dans ce cas, indiquez le chemin complet de l’utilitaire ImageMagick utilisé pour convertir les fichiers image en miniatures. Par exemple, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Pour vérifier si l’outil s’exécute correctement, ajoutez une image de JPG dans le répertoire de travail et exécutez la commande . `convert <image-name>.jpg -flip <image-name>-flipped.jpg` sur la ligne de commande.

   Une image inversée est ajoutée au répertoire.

Ajoutez ensuite l’étape de processus de ligne de commande au workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** :

1. Accédez à la console **[!UICONTROL Workflow]**.
1. Dans l’onglet **[!UICONTROL Modèles]**, modifiez le modèle **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**.
1. Modifiez les paramètres de l’étape **[!UICONTROL Rendu Web]** comme suit :

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Enregistrez le workflow.

Pour tester le workflow modifié, ajoutez une ressource à `/content/dam`.

1. Dans le système de fichiers, obtenez une image TIFF de votre choix. Renommez-la `myImage.tiff` et copiez-la dans `/content/dam` en utilisant, par exemple, WebDAV.
1. Accédez à la console **[!UICONTROL CQ5 DAM]**, par exemple `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Ouvrez la ressource `myImage.tiff` et vérifiez que l’image inversée et les trois miniatures ont bien été créées.

#### Configuration de l’étape de processus CommandLineProcess {#configuring-the-commandlineprocess-process-step}

Cette section décrit la procédure à suivre pour définir les **[!UICONTROL Arguments du processus]** de `CommandLineProcess`. Séparez les valeurs de [!UICONTROL Arguments de processus] utilisez une virgule et ne commencez pas de valeur avec un espace.

| Argument-Format | Description |
|---|---|
| mime:&lt;mime-type> | Argument facultatif. Le processus est appliqué si la ressource a le même type MIME que celui des arguments. <br>Plusieurs types MIME peuvent être définis. |
| tn:&lt;width>:&lt;height> | Argument facultatif. Le processus crée une miniature avec les dimensions définies dans l’argument. <br>Plusieurs miniatures peuvent être définies. |
| cmd: &lt;command> | Définit la commande qui est exécutée. La syntaxe dépend de l’outil de ligne de commande. Une seule commande peut être définie. <br>Les variables suivantes peuvent être utilisées pour créer la commande :<br>`${filename}`: nom du fichier d’entrée, par exemple original.jpg <br> `${file}`: chemin d’accès complet du fichier d’entrée, par exemple /tmp/cqdam0816.tmp/original.jpg <br> `${directory}`: répertoire du fichier d’entrée, par exemple /tmp/cqdam0816.tmp <br>`${basename}`: nom du fichier d’entrée sans son extension, par exemple original <br>`${extension}`: extension du fichier d’entrée, par exemple jpg |

Par exemple, si ImageMagick est installé sur le disque hébergeant le serveur Experience Manager et si vous créez une étape de processus à l’aide de **CommandLineProcess** comme implémentation et les valeurs suivantes comme **Arguments de processus**:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Ensuite, lorsque le workflow s’exécute, l’étape s’applique uniquement aux ressources qui ont `image/gif` ou `mime:image/tiff` comme des types MIME. Il crée une image inversée de l’original, la convertit en .jpg et crée trois miniatures aux dimensions suivantes : 140x100, 48x48 et 10x250.

Utilisez les [!UICONTROL Arguments de processus] suivants pour créer les trois miniatures standards à l’aide d’ImageMagick :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Utilisez les [!UICONTROL Arguments de processus] suivants pour créer le rendu web à l’aide d’ImageMagick :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>Le `CommandLineProcess` s’applique uniquement aux ressources (noeuds de type `dam:Asset`) ou des descendants d’une ressource.
