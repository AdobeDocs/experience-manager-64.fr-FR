---
title: Développement de projets AEM à l’aide d’Eclipse
seo-title: How to Develop AEM Projects Using Eclipse
description: Ce guide décrit l’utilisation d’Eclipse pour le développement de projets basés sur AEM
seo-description: This guide describes how to use Eclipse for developing AEM based projects
uuid: 79fee76f-6bcc-498f-af46-530816b41bbe
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: aa58cfb8-ec15-4698-a8f0-97683b0de51c
exl-id: 5fae4a4c-c97a-4541-bdc5-63ef4ca0172c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 54%

---

# Développement de projets AEM à l’aide d’Eclipse{#how-to-develop-aem-projects-using-eclipse}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Ce guide explique comment utiliser Eclipse pour développer des projets basés sur AEM.

>[!NOTE]
>
>Adobe fournit désormais les [outils de développement AEM pour Eclipse](/help/sites-developing/aem-eclipse.md) qui vous aident à développer des solutions AEM avec Eclipse.

## Présentation {#overview}

Pour commencer AEM développement sur Eclipse, les étapes suivantes sont nécessaires.

Chacune d’elles est expliquée plus en détail dans le reste de cette rubrique pratique.

* Installation d’Eclipse 4.3 (Kepler)
* Configuration de votre projet AEM basé sur Maven
* Préparation de la prise en charge JSP d’Eclipse dans le fichier POM Maven
* Importation du projet Maven dans Eclipse

>[!NOTE]
>
>Ce guide est basé sur Eclipse 4.3 (Kepler) et AEM 5.6.1.

## Installer Eclipse {#install-eclipse}

Téléchargez l’« IDE Eclipse pour le développement Java EE » depuis la [page des téléchargements d’Eclipse](https://www.eclipse.org/downloads/).

Installez Eclipse en suivant la procédure [Instructions d’installation](https://wiki.eclipse.org/Eclipse/Installation).

## Configuration de votre projet AEM basé sur Maven {#set-up-your-aem-project-based-on-maven}

Ensuite, configurez le projet en utilisant Maven comme décrit dans la rubrique [Création de projets AEM à l’aide d’Apache Maven](/help/sites-developing/ht-projects-maven.md).

## Préparation de la prise en charge JSP pour Eclipse {#prepare-jsp-support-for-eclipse}

Eclipse peut également fournir une assistance lors de l’utilisation de JSP, par exemple

* remplissage automatique des bibliothèques de balises
* Connaissance Eclipse des objets définis par &lt;cq:defineobjects /> et &lt;sling:defineobjects />

Pour que cela fonctionne :

1. Suivez les instructions de la section [Comment travailler avec des JSP](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) de la rubrique [Création de projets AEM à l’aide d’Apache Maven](/help/sites-developing/ht-projects-maven.md).
1. Ajoutez ce qui suit au &lt;build /> dans le POM de votre module de contenu.

   Le module externe de prise en charge Maven d’Eclipse, m2e, ne fournit pas de prise en charge pour le module externe maven-jspc-plugin, et cette configuration indique à m2e d’ignorer le module externe et la tâche connexe de nettoyer les résultats de la compilation temporaire.

   Ce n’est pas un problème : comme indiqué dans la section [Comment travailler avec des JSP](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps), le plugin maven-jspc-plugin de cette configuration n’est utilisé que pour valider la compilation des JSP dans le cadre du processus de création. Eclipse signale déjà les problèmes rencontrés dans les JSP et ne se repose pas sur ce plugin Maven pour le faire.

   **myproject/content/pom.xml**

   ```xml
   <build>
     <!-- ... -->
     <pluginManagement>
       <plugins>
         <!--This plugin's configuration is used to store Eclipse m2e settings only. It has no influence on the Maven build itself.-->
         <plugin>
           <groupId>org.eclipse.m2e</groupId>
           <artifactId>lifecycle-mapping</artifactId>
           <version>1.0.0</version>
           <configuration>
             <lifecycleMappingMetadata>
               <pluginExecutions>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.sling</groupId>
                     <artifactId>maven-jspc-plugin</artifactId>
                     <versionRange>[2.0.6,)</versionRange>
                     <goals>
                       <goal>jspc</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.maven.plugins</groupId>
                     <artifactId>maven-clean-plugin</artifactId>
                     <versionRange>[2.4.1,)</versionRange>
                     <goals>
                       <goal>clean</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
               </pluginExecutions>
             </lifecycleMappingMetadata>
           </configuration>
         </plugin>
       </plugins>
     </pluginManagement>
   </build>
   ```

### Importation du projet Maven dans Eclipse {#import-the-maven-project-into-eclipse}

1. Dans Eclipse, sélectionnez File (Ficher) > Import (Importer)...
1. Dans la boîte de dialogue d’importation, sélectionnez Maven > Existing Maven Projects (Projets Maven existants), puis cliquez sur Next (Suivant).

   ![chlimage_1-41](assets/chlimage_1-41.png)

1. Saisissez le chemin d’accès au dossier de niveau supérieur du projet et cliquez sur « Tout sélectionner » et « Terminer ».

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. Vous êtes à présent prêt à utiliser Eclipse pour développer le projet AEM, notamment la saisie semi-automatique.

   ![chlimage_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Si vous incluez `/libs/foundation/global.jsp` ou d’autres JSP dans `/libs`, vous devez les copier dans le projet afin qu’Eclipse puisse résoudre l’inclusion. En même temps, vous devez vous assurer qu’ils ne sont pas inclus dans le package de contenu Maven. La rubrique [Création de projets AEM à l’aide d’Apache Maven](/help/sites-developing/ht-projects-maven.md) décrit comment réaliser cette opération.
