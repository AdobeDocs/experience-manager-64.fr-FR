---
title: Présentation de l’API Java QuickStart
seo-title: Introducing Java API QuickStart
description: Les programmes de démarrage rapide de l’API Java vous aident à accélérer le développement des programmes qui interagissent avec les services AEM Forms. Vous pouvez utiliser les programmes de démarrage rapide de l’API Java dans votre projet comme point de départ et les personnaliser.
seo-description: Java API Quick Start programs help you expedite the development of programs that interact with AEM Forms services. You can use the Java API Quick Start programs in your project as a starting point and customize it.
uuid: 480e1809-f789-4ad8-b5d5-2d97aba8411a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, develop
discoiquuid: 38fd51ec-347e-4ae3-86d4-9d2429f79bdd
role: Developer
exl-id: 8a3f2eb9-d686-49d4-baa4-c0921622d01a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Présentation du démarrage rapide de l’API Java {#introducing-java-api-quickstart}

Le démarrage rapide de l’API AEM Forms Adobe peut vous aider à accélérer vos efforts de développement de programmes qui interagissent avec les services AEM Forms. *Démarrage rapide* s sont des programmes complets que vous pouvez copier et coller dans vos propres projets et utiliser comme point de départ. Vous pouvez exécuter un didacticiel de mise en route pour voir comment il se comporte et le modifier en fonction de vos besoins.

Les opérations AEM Forms peuvent être effectuées à l’aide de l’API fortement typée d’AEM Forms et le mode de connexion doit être défini sur SOAP.

Le didacticiel de mise en route de l’API Java, très typé, fournit une liste des fichiers JAR requis pour exécuter l’application Java. La plupart des didacticiels Java sont des applications de console qui s’exécutent dans `main`. Toutefois, le démarrage rapide de l’API Java Forms est mis en oeuvre sous la forme d’une servlet Java s’exécutant dans une application web.

La liste des fichiers JAR se trouve dans une section de commentaire située au début du didacticiel de mise en route. Par exemple, le commentaire suivant se trouve dans un fichier de démarrage rapide de Output et est une liste de fichiers JAR standard qui se trouve dans chaque démarrage rapide de Java.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-output-client.jar 
     * 2. adobe--client.jar 
     * 3. adobe-usermanager-client.jar 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client 
     * 
     * If you want to invoke a remote AEM Forms instance and there is a 
     * firewall between the client application and AEM Forms, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms library files" in Programming  
     * with AEM Forms 
     */
```

## Démarrage rapide de plusieurs services {#multiple-services-quick-start}

Les démarrages les plus rapides se trouvant dans *Programmation avec AEM Forms* appeler un service spécifique pour effectuer une opération ; Cependant, certains didacticiels de mise en route invoquent plusieurs services AEM Forms pour exécuter un workflow donné. La liste suivante fournit des démarrages rapides Java qui appellent plusieurs services AEM Forms :

[Démarrage rapide (mode SOAP) : Transmission d’un document situé dans le référentiel AEM Forms au service Output à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (appelle le service Repository et Output)

[Démarrage rapide (mode SOAP) : Création d’un document de PDF basé sur des fragments à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (appelle le service Assembler et Output)

[Démarrage rapide (mode SOAP) : Création de documents PDF avec des données XML envoyées à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (appelle le service Forms, Output et Document Management)

[Démarrage rapide (mode SOAP) : Transmission de documents au service Forms à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (appelle le service Forms et Document Management)

[Démarrage rapide (mode SOAP) : Signature numérique d’un formulaire XFA à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (appelle le service Forms et Signature)

[Démarrage rapide (mode SOAP) : Gestion des rôles et des autorisations à l’aide de l’API Java](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (appelle DirectoryManager et le service AuthorizationManager )

[Démarrage rapide (mode SOAP) : Transmission de documents à Output Service à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (appel du service Output et Document Management)

>[!NOTE]
>
>Les didacticiels de mise en route situés dans Programmation avec AEM Forms sont basés sur le déploiement d’AEM Forms sur JBoss® Application Server et le système d’exploitation Microsoft® Windows®. Cependant, si vous utilisez un autre système d’exploitation, comme UNIX®, remplacez les chemins spécifiques à Windows par les chemins pris en charge par le système d’exploitation approprié. De même, si vous utilisez un autre serveur d’applications J2EE, veillez à spécifier des propriétés de connexion valides. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>La plupart des didacticiels de mise en route des services Web sont écrits en C# et utilisent le framework .NET. Cependant, vous pouvez créer une logique d’application cliente capable d’appeler les services AEM Forms dans n’importe quel environnement de développement prenant en charge les normes SOAP. (Voir [Appel d’AEM Forms à l’aide de services web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
