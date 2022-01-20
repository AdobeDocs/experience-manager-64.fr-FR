---
title: Appel de processus pour des intervenants humains de longue durée
seo-title: Invoking Human-Centric Long-Lived Processes
description: Appelez par programmation des processus de longue durée pour des intervenants humains créés dans Workbench à l’aide d’une application cliente Java web qui utilise l’API d’appel, d’une application ASP.NET qui utilise des services web et d’une application cliente créée avec Flex qui utilise Remoting.
seo-description: Programmatically invoke human-centric long-lived processes created in Workbench using a Java web-based client application that uses the Invocation API, an ASP.NET application that uses web services, and a client application built with Flex that uses Remoting.
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
role: Developer
exl-id: 4f581af8-9c1a-4e80-b459-a83a1dab3b01
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3712'
ht-degree: 4%

---

# Appel de processus pour des intervenants humains de longue durée {#invoking-human-centric-long-lived-processes}

Vous pouvez appeler par programmation des processus de longue durée pour des intervenants humains créés dans Workbench à l’aide des applications client suivantes :

* Application cliente Java web qui utilise l’API d’appel. (Voir [Appel d’AEM Forms à l’aide de l’API Java](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).
* Une application ASP.NET qui utilise des services web. (Voir [Appel d’AEM Forms à l’aide de services web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Application cliente créée avec Flex qui utilise le service Remoting. (Voir [Appel d’AEM Forms à l’aide d’AEM Forms Remoting (obsolète pour AEM forms)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Le processus de longue durée appelé est nommé *FirstAppSolution/PreLoanProcess*. Vous pouvez créer ce processus en suivant le tutoriel spécifié dans [Création de votre première application AEM Forms](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).

Un processus pour des intervenants humains implique une tâche à laquelle un utilisateur peut répondre à l’aide de Workspace. Par exemple, avec Workbench, vous pouvez créer un processus qui permet à un gestionnaire de banque d’approuver ou de refuser une demande de prêt. L’illustration suivante présente le processus *FirstAppSolution/PreLoanProcess*.

Le processus* FirstAppSolution/PreLoanProcess* accepte un paramètre d’entrée nommé* formData* dont le type de données est XML. Les données XML sont fusionnées avec une conception de formulaire nommée *PreLoanForm.xdp*. L’illustration suivante présente un formulaire qui représente une tâche affectée à un utilisateur pour approuver ou refuser une demande de prêt. L’utilisateur approuve ou refuse la demande à l’aide de Workspace. L’utilisateur de Workspace peut approuver la demande de prêt en cliquant sur le bouton Approuver illustré ci-dessous. De même, l’utilisateur peut refuser la demande de prêt en cliquant sur le bouton de refus.

Un processus de longue durée est appelé de manière asynchrone et ne peut pas être appelé de manière synchrone en raison des facteurs suivants :

* Un processus peut s’étendre sur un temps considérable.
* Un processus peut dépasser les limites organisationnelles.
* Un processus a besoin d’une entrée externe pour se terminer. Prenons l’exemple d’un formulaire envoyé à un responsable absent du bureau. Dans ce cas, le processus n’est pas terminé tant que le gestionnaire ne retourne pas et ne remplit pas le formulaire.

Lorsqu’un processus de longue durée est appelé, AEM Forms crée une valeur d’identifiant d’appel dans le cadre de la création d’un enregistrement. L’enregistrement suit l’état du processus de longue durée et est stocké dans la base de données AEM Forms. La valeur de l’identifiant d’appel vous permet de suivre l’état du processus de longue durée. En outre, vous pouvez utiliser la valeur de l’identifiant d’appel de processus pour effectuer des opérations Process Manager, telles que l’arrêt d’une instance de processus en cours d’exécution.

>[!NOTE]
>
>AEM Forms ne crée pas de valeur d’identifiant d’appel ni d’enregistrement lorsqu’un processus de courte durée est appelé.

Le `FirstAppSolution/PreLoanProcess` est appelé lorsqu’un demandeur envoie une demande, qui est représentée sous la forme de données XML. Le nom de la variable de processus d’entrée est `formData` et son type de données est XML. Dans le cadre de cette discussion, supposons que les données XML suivantes soient utilisées comme entrée de la variable `FirstAppSolution/PreLoanProcess` processus.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <LoanApp> 
 <Name>Sam White</Name> 
 <LoanAmount>250000</LoanAmount> 
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail> 
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
 </LoanApp>
```

Les données XML transmises à un processus doivent correspondre aux champs situés dans le formulaire utilisé dans le processus. Dans le cas contraire, les données ne s’affichent pas dans le formulaire. Toutes les applications qui invoquent la variable `FirstAppSolution/PreLoanProcess` doit transmettre cette source de données XML. Les applications créées dans *Appel de processus pour des intervenants humains de longue durée* créer dynamiquement la source de données XML à partir des valeurs saisies par un utilisateur dans un client web ;

A l’aide d’une application cliente, vous pouvez envoyer le *FirstAppSolution/PreLoanProcess *traitez les données XML requises. Un processus de longue durée renvoie une valeur d’identifiant d’appel comme valeur renvoyée. L’illustration suivante présente les applications clientes appelant le* Processus de longue durée FirstAppSolution/PreLoanProcess. Les applications clientes envoient des données XML et récupèrent une valeur string qui représente la valeur de l’identifiant d’appel.

**Voir également**

[Création d’une application Web Java qui appelle un processus pour des intervenants humains de longue durée](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Création d’une application web ASP.NET qui appelle un processus de longue durée pour des intervenants humains](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Création d’une application client créée avec Flex qui appelle un processus de longue durée pour des intervenants humains](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Création d’une application Web Java qui appelle un processus pour des intervenants humains de longue durée {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

Vous pouvez créer une application web qui utilise un servlet Java pour appeler la variable `FirstAppSolution/PreLoanProcess` processus. Pour appeler ce processus à partir d’une servlet Java, utilisez l’API d’appel dans la servlet Java. (Voir [Appel d’AEM Forms à l’aide de l’API Java](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

L’illustration suivante présente une application cliente web qui publie des valeurs de nom, de téléphone (ou de courrier électronique) et de montant. Ces valeurs sont envoyées à la servlet Java lorsque l’utilisateur clique sur le bouton Envoyer la demande .

Le servlet Java effectue les tâches suivantes :

* Récupère les valeurs publiées de la page HTML dans la servlet Java.
* Crée de manière dynamique une source de données XML à transmettre au processus* FirstAppSolution/PreLoanProcess *. Les valeurs name, phone (ou email) et amount sont spécifiées dans la source de données XML.
* Appelle le *FirstAppSolution/PreLoanProcess* en utilisant l’API d’appel d’AEM Forms.
* Renvoie la valeur de l’identifiant d’appel au navigateur web client.

### Résumé des étapes {#summary-of-steps}

Pour créer une application web Java qui appelle la fonction `FirstAppSolution/PreLoanProcess` effectuez les étapes suivantes :

1. [Création d’un projet web](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Création d’une logique d’application Java pour le servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [Créer la page web de l&#39;application web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Regroupement de l’application web dans un fichier WAR](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Déployez le fichier WAR sur le serveur d’applications J2EE hébergeant AEM Forms.](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms).
1. [Tester votre application web](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Certaines de ces étapes dépendent de l’application J2EE sur laquelle AEM Forms est déployé. Par exemple, la méthode que vous utilisez pour déployer un fichier WAR dépend du serveur d’applications J2EE que vous utilisez. On suppose qu’AEM Forms est déployé sur JBoss®.

### Création d’un projet web {#create-a-web-project}

La première étape pour créer une application web est de créer un projet web. L’IDE Java sur lequel repose ce document est Eclipse 3.3. À l’aide de l’IDE Eclipse, créez un projet web et ajoutez les fichiers JAR requis à votre projet. Ajoutez une page de HTML nommée *index.html *et une servlet Java à votre projet.

La liste suivante indique les fichiers JAR à inclure dans votre projet web :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Pour connaître l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>Le fichier J2EE.jar définit les types de données utilisés par une servlet Java. Vous pouvez obtenir ce fichier JAR à partir du serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un projet web**

1. Démarrez Eclipse et cliquez sur **Fichier** >  **Nouveau projet**.
1. Dans le **Nouveau projet** boîte de dialogue, sélectionnez **Web** > **Projet web dynamique**.
1. Type `InvokePreLoanProcess` pour le nom de votre projet, puis cliquez sur **Terminer**.

**Ajout des fichiers JAR requis à votre projet**

1. Dans la fenêtre Explorateur de projets, cliquez avec le bouton droit sur la `InvokePreLoanProcess` projet et sélectionnez **Propriétés**.
1. Cliquez sur **Chemin de création Java** puis cliquez sur le bouton **Bibliothèques** .
1. Cliquez sur le bouton **Ajout de fichiers JAR externes** et accédez aux fichiers JAR à inclure.

**Ajout d’une servlet Java à votre projet**

1. Dans la fenêtre Explorateur de projets, cliquez avec le bouton droit sur la `InvokePreLoanProcess` projet et sélectionnez **Nouveau** >  **Autre**.
1. Développez l’objet **Web** dossier, sélectionnez **Servlet**, puis cliquez sur **Suivant**.
1. Dans la boîte de dialogue Créer un servlet, saisissez `SubmitXML` pour le nom du servlet, puis cliquez sur **Terminer**.

**Ajout d’une page de HTML à votre projet**

1. Dans la fenêtre Explorateur de projets, cliquez avec le bouton droit sur la `InvokePreLoanProcess` projet et sélectionnez **Nouveau** > **Autre**.
1. Développez l’objet **Web** dossier, sélectionnez **HTML**, puis cliquez sur **Suivant**.
1. Dans la boîte de dialogue Nouveau HTML, saisissez `index.html` pour le nom de fichier, puis cliquez sur **Terminer**.

>[!NOTE]
>
>Pour plus d’informations sur la création de contenu de HTML qui appelle la servlet Java SubmitXML, voir [Créer la page web de l&#39;application web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application).

### Création d’une logique d’application Java pour le servlet {#create-java-application-logic-for-the-servlet}

Création d’une logique d’application Java qui appelle la fonction `FirstAppSolution/PreLoanProcess` processus depuis le servlet Java. Le code suivant affiche la syntaxe de la variable `SubmitXML` Servlet Java :

```as3
     public class SubmitXML extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
         doPost(req,resp); 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
             //Add code here to invoke the FirstAppSolution/PreLoanProcess process 
             }
```

En règle générale, vous ne placez pas de code client dans le code d’une servlet Java. `doGet` ou `doPost` . Une meilleure pratique de programmation consiste à placer ce code dans une classe distincte. Ensuite, instanciez la classe à partir de la fonction `doPost` (ou `doGet` ) et appelez les méthodes appropriées. Toutefois, pour des raisons de concision du code, les exemples de code sont conservés au minimum et sont placés dans la variable `doPost` .

Pour appeler la fonction `FirstAppSolution/PreLoanProcess` effectuez les tâches suivantes à l’aide de l’API d’appel :

1. Incluez les fichiers JAR client, tels que adobe-livecycle-client.jar, dans le chemin de classe de votre projet Java. Pour plus d’informations sur l’emplacement de ces fichiers, voir [Inclusion des fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Récupérez les valeurs name, phone et amount qui sont envoyées à partir de la page HTML. Utilisez ces valeurs pour créer de manière dynamique une source de données XML envoyée à la variable `FirstAppSolution/PreLoanProcess` processus. Vous pouvez utiliser `org.w3c.dom` pour créer la source de données XML (cette logique d’application est illustrée dans l’exemple de code suivant).
1. Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Créez un objet `ServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. Un objet `ServiceClient` vous permet d’appeler une opération de service. Il gère des tâches telles que la localisation, la répartition et le routage des demandes d’appel.
1. Créez un objet `java.util.HashMap` en utilisant son constructeur.
1. Appelez la méthode `java.util.HashMap` de l’objet `put` pour chaque paramètre d’entrée à transmettre au processus de longue durée. Assurez-vous de spécifier le nom des paramètres d’entrée du processus. Parce que la variable `FirstAppSolution/PreLoanProcess` Le processus nécessite un paramètre d’entrée de type `XML` (nommé `formData`), il vous suffit d’appeler la fonction `put` une fois.

   ```as3
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process 
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                 
    //Create a Map object to store the parameter value 
    Map params = new HashMap(); 
    params.put("formData", inXML);
   ```

1. Créez un `InvocationRequest` en appelant le `ServiceClientFactory` de `createInvocationRequest` et transmission des valeurs suivantes :

   * Valeur string qui spécifie le nom du processus de longue durée à appeler. Pour appeler la fonction `FirstAppSolution/PreLoanProcess` processus, spécifiez `FirstAppSolution/PreLoanProcess`.
   * Une valeur string qui représente le nom de l’opération de processus. Le nom de l’opération de processus de longue durée est `invoke`.
   * L’objet `java.util.HashMap` qui contient les valeurs de paramètre requises par l’opération de service.
   * Une valeur booléenne qui spécifie `false`, qui crée une requête asynchrone (cette valeur s’applique pour appeler un processus de longue durée).

   >[!NOTE]
   >
   >*Un processus de courte durée peut être appelé en transmettant la valeur true comme quatrième paramètre de la méthode createInvocationRequest . La transmission de la valeur true crée une requête synchrone.*

1. Envoyez la demande d’appel à AEM Forms en appelant la méthode `ServiceClient` de `invoke` et transmission de la méthode `InvocationRequest` . Le `invoke` renvoie une `InvocationReponse` .
1. Un processus de longue durée renvoie une valeur string qui représente une valeur d’identification d’appel. Récupérez cette valeur en appelant la variable `InvocationReponse` de `getInvocationId` .

   ```as3
    //Send the invocation request to the long-lived process and  
    //get back an invocation response object 
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
    String invocationId = lcResponse.getInvocationId();
   ```

1. Ecrivez la valeur d&#39;identification de l&#39;appel dans le navigateur web client. Vous pouvez utiliser une `java.io.PrintWriter` pour écrire cette valeur dans le navigateur web client.

### Démarrage rapide : Appel d’un processus de longue durée à l’aide de l’API d’appel {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

L’exemple de code Java suivant représente le servlet Java qui appelle la variable `FirstAppSolution/PreLoanProcess` processus.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 
     * (Because this  quick start is implemented as a Java servlet, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     * */ 
 import java.io.ByteArrayOutputStream; 
 import java.io.File; 
 import java.io.IOException; 
 import java.io.PrintWriter; 
  
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import javax.xml.parsers.DocumentBuilder; 
 import javax.xml.parsers.DocumentBuilderFactory; 
 import javax.xml.transform.Transformer; 
 import javax.xml.transform.TransformerFactory; 
 import javax.xml.transform.dom.DOMSource; 
 import javax.xml.transform.stream.StreamResult; 
  
 import com.adobe.idp.dsc.InvocationRequest; 
 import com.adobe.idp.dsc.InvocationResponse; 
 import com.adobe.idp.dsc.clientsdk.ServiceClient; 
 import org.w3c.dom.Element; 
  
     public class SubmitXML extends javax.servlet.http.HttpServlet implements javax.servlet.Servlet { 
       static final long serialVersionUID = 1L; 
      
        public SubmitXML() { 
         super(); 
     }        
      
      
     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
         // TODO Auto-generated method stub 
         doPost(request,response); 
     }       
      
     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
                  
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Create a ServiceClient object 
             ServiceClient myServiceClient = myFactory.getServiceClient(); 
              
             //Get the values that are passed from the Loan HTML page 
             String name = (String)request.getParameter("name"); 
             String phone = (String)request.getParameter("phone"); 
             String amount = (String)request.getParameter("amount"); 
                  
             //Create XML to pass to the FirstAppSolution/PreLoanProcess process 
             org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                                  
             //Create a Map object to store the XML input parameter value 
             Map params = new HashMap(); 
             params.put("formData", inXML);  
              
             //Create an InvocationRequest object 
             InvocationRequest lcRequest =  myFactory.createInvocationRequest( 
                 "FirstAppSolution/PreLoanProcess", //Specify the long-lived process name 
                     "invoke",           //Specify the operation name     
                     params,               //Specify input values 
                     false);               //Create an asynchronous request  
              
             //Send the invocation request to the long-lived process and  
             //get back an invocation response object 
             InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
             String invocationId = lcResponse.getInvocationId(); 
  
             //Create a PrintWriter instance 
             PrintWriter pp = response.getWriter();      
              
             //Write the invocation identifier value back to the client web browser 
             pp.println("The job status identifier value is: " +invocationId); 
              
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
      
      
      //Create XML data to pass to the long-lived process 
      private static org.w3c.dom.Document GetDataSource(String name, String phone, String amount) 
      { 
             org.w3c.dom.Document document = null; 
              
             try 
             { 
                 //Create DocumentBuilderFactory and DocumentBuilder objects 
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                 DocumentBuilder builder = factory.newDocumentBuilder(); 
  
                 //Create a new Document object 
                 document = builder.newDocument();  
  
                 //Create MortgageApp - the root element in the XML  
                 Element root = (Element)document.createElement("LoanApp"); 
                 document.appendChild(root); 
                                              
                 //Create an XML element for Name 
                 Element nameElement = (Element)document.createElement("Name"); 
                 nameElement.appendChild(document.createTextNode(name)); 
                 root.appendChild(nameElement); 
                  
                 //Create an XML element for Phone 
                 Element phoneElement = (Element)document.createElement("PhoneOrEmail"); 
                 phoneElement.appendChild(document.createTextNode(phone)); 
                 root.appendChild(phoneElement); 
                  
                 //Create an XML element for amount 
                 Element loanElement = (Element)document.createElement("LoanAmount"); 
                 loanElement.appendChild(document.createTextNode(amount)); 
                 root.appendChild(loanElement); 
  
                 //Create an XML element for ApprovalStatus 
                 Element approveElement = (Element)document.createElement("ApprovalStatus"); 
                 approveElement.appendChild(document.createTextNode("PENDING APPROVAL")); 
                 root.appendChild(approveElement); 
                                  
               } 
          catch (Exception e) { 
                   System.out.println("The following exception occurred: "+e.getMessage()); 
                } 
         return document; 
          } 
         }
```

### Créer la page web de l&#39;application web {#create-the-web-page-for-the-web-application}

La page web * index.html *fournit un point d’entrée au servlet Java qui appelle la variable `FirstAppSolution/PreLoanProcess` processus. Cette page web est un formulaire de HTML de base qui contient un HTML et un bouton d’envoi. Lorsque l’utilisateur clique sur le bouton d’envoi, les données de formulaire sont publiées sur la variable `SubmitXML` Servlet Java.

Le servlet Java capture les données publiées à partir de la page de HTML à l’aide du code Java suivant :

```as3
 //Get the values that are passed from the Loan HTML page 
 String name = request.getParameter("name"); 
 String phone = request.getParameter("phone"); 
 String amount = request.getParameter("amount");
```

Le code de HTML suivant représente le fichier index.html créé lors de la configuration de l’environnement de développement. (Voir [Création d’un projet web](invoking-human-centric-long-lived.md#create-a-web-project).)

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "https://www.w3.org/TR/html4/loose.dtd"> 
 <html> 
 <head> 
 <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1"> 
 <title>Insert title here</title> 
 </head> 
 <body> 
 <table> 
     <TBODY> 
         <TR> 
             <td><img src="financeCorpLogo.jpg" width="172" height="62"></TD> 
             <td><FONT size="+2"><strong>Java Loan Application Page</strong></FONT></TD> 
             <td> </TD> 
             <td> </TD> 
         </TR> 
          
     </TBODY> 
 </TABLE> 
     <FORM action="https://hiro-xp:8080/PreLoanProcess/SubmitXML" method="post"> 
        <table> 
          <TBODY> 
                <TR> 
                      <td><LABEL for="name">Name: </LABEL></TD> 
                  <td><INPUT type="text" name="name"></TD> 
                  <td><input type="submit" value="Submit Application"></TD> 
                  </TR> 
            <TR> 
                  <td> <LABEL for="phone">Phone/Email: </LABEL></TD> 
              <td><INPUT type="text" name="phone"></TD> 
                  <td></TD> 
              </TR> 
  
            <TR> 
                  <td><LABEL for="amount">Amount: </LABEL></TD> 
              <td><INPUT type="text" name="amount"></TD> 
                 <td></TD> 
             </TR> 
          </TBODY> 
 </TABLE> 
       </FORM> 
 </body> 
 </html>
```

### Regroupement de l’application web dans un fichier WAR {#package-the-web-application-to-a-war-file}

Pour déployer le servlet Java qui appelle la fonction `FirstAppSolution/PreLoanProcess` traitez votre application web dans un fichier WAR. Assurez-vous que les fichiers JAR externes dont dépend la logique métier du composant, tels que adobe-livecycle-client.jar et adobe-usermanager-client.jar, sont également inclus dans le fichier WAR.

L’illustration suivante présente le contenu du projet Eclipse, qui est compressé dans un fichier WAR.

>[!NOTE]
>
>Dans l’illustration précédente, le fichier du JPG peut être remplacé par n’importe quel fichier image du JPG.

**Regroupez une application web dans un fichier WAR :**

1. Dans la **Explorateur de projets** , cliquez avec le bouton droit de la souris sur la fenêtre `InvokePreLoanProcess` projet et sélectionnez **Exporter** > **Fichier WAR**.
1. Dans le **Module web** zone de texte, saisissez `InvokePreLoanProcess` pour le nom du projet Java.
1. Dans le **Destination** zone de texte, saisissez `PreLoanProcess.war`**pour le** nom de fichier, indiquez l’emplacement de votre fichier WAR, puis cliquez sur Terminer.

### Déployez le fichier WAR sur le serveur d’applications J2EE hébergeant AEM Forms. {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Déployez le fichier WAR sur le serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour déployer le fichier WAR sur le serveur d’applications J2EE, copiez le fichier WAR du chemin d’exportation vers *[Installation d’AEM Forms]*\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy.

>[!NOTE]
>
>si AEM Forms n’est pas déployé sur JBoss, vous devez déployer le fichier WAR en conformité avec le serveur d’applications J2EE hébergeant AEM Forms.

### Tester votre application web {#test-your-web-application}

Une fois l’application web déployée, vous pouvez la tester à l’aide d’un navigateur web. En supposant que vous utilisiez le même ordinateur qui héberge AEM Forms, vous pouvez spécifier l’URL suivante :

* http://localhost:8080/PreLoanProcess/index.html

   Saisissez les valeurs dans les champs du HTML de formulaire et cliquez sur le bouton Envoyer la demande . En cas de problème, consultez le fichier journal du serveur d’applications J2EE.

   >[!NOTE]
   >
   >Pour confirmer que l’application Java a appelé le processus, démarrez Workspace et acceptez le prêt.

## Création d’une application web ASP.NET qui appelle un processus de longue durée pour des intervenants humains {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

Vous pouvez créer une application ASP.NET qui appelle la fonction `FirstAppSolution/PreLoanProcess` processus. Pour appeler ce processus à partir d’une application ASP.NET, utilisez les services web. (Voir [Appel d’AEM Forms à l’aide de services web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

L’illustration suivante présente une application cliente ASP.NET obtenant des données d’un utilisateur final. Les données sont placées dans une source de données XML et envoyées à la variable `FirstAppSolution/PreLoanProcess` processus lorsque l’utilisateur clique sur le bouton Envoyer la demande .

Notez qu’une fois le processus appelé, une valeur d’identifiant d’appel s’affiche. Une valeur d’identifiant d’appel est créée dans le cadre d’un enregistrement qui suit l’état du processus de longue durée.

L’application ASP.NET effectue les tâches suivantes :

* Récupère les valeurs saisies par l’utilisateur dans la page web.
* Crée de manière dynamique une source de données XML transmise au processus* FirstAppSolution/PreLoanProcess *. Les trois valeurs sont spécifiées dans la source de données XML.
* Appelle le processus* FirstAppSolution/PreLoanProcess *à l’aide des services web.
* Renvoie la valeur de l’identifiant d’appel et l’état de l’opération de longue durée au navigateur web client.

### Résumé des étapes {#summary_of_steps-1}

Pour créer une application ASP.NET capable d’appeler le processus FirstAppSolution/PreLoanProcess, procédez comme suit :

1. [Création d’une application web ASP.NET](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Créez une page ASP qui appelle FirstAppSolution/PreLoanProcess](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess).
1. [Exécution de l’application ASP.NET](invoking-human-centric-long-lived.md#run-the-asp-net-application).

### Création d’une application web ASP.NET {#create-an-asp-net-web-application}

Créez une application Web Microsoft .NET C# ASP.NET. L’illustration suivante présente le contenu du projet ASP.NET nommé *InvokePreLoanProcess*.

Notez que sous Références du service, il existe deux éléments. Le premier élément s’appelle* JobManager*. Cette référence permet à l’application ASP.NET d’appeler le service Job Manager. Ce service renvoie des informations sur l’état d’un processus de longue durée. Par exemple, si le processus est en cours d’exécution, ce service renvoie une valeur numérique qui spécifie le processus en cours d’exécution. La seconde référence est nommée *PreLoanProcess*. Cette référence de service représente la référence au processus* FirstAppSolution/PreLoanProcess *. Après avoir créé une référence de service, les types de données associés au service AEM Forms peuvent être utilisés dans votre projet .NET.

**Créez un projet ASP.NET :**

1. Démarrez Microsoft Visual Studio 2008.
1. Dans la **Fichier** menu, sélectionnez **Nouveau**, **Site Web**.
1. Dans le **Modèles** list, select **Site web ASP.NET**.
1. Dans le **Emplacement** , sélectionnez un emplacement pour votre projet. Nommage de votre projet *InvokePreLoanProcess*.
1. Dans le **Langue** , sélectionnez Visual C#
1. Cliquez sur OK.

**Ajouter des références de service :**

1. Dans le menu Projet , sélectionnez **Ajouter une référence de service**.
1. Dans le **Adresse** , spécifiez le fichier WSDL dans le service Job Manager.

   ```as3
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Dans le champ Espace de noms , saisissez `JobManager`.
1. Cliquez sur **Aller** puis cliquez sur **OK**.
1. Dans le **Projet** menu, sélectionnez **Ajouter une référence de service**.
1. Dans le **Adresse** , spécifiez le fichier WSDL dans le processus FirstAppSolution/PreLoanProcess.

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Dans le champ Espace de noms , saisissez `PreLoanProcess`.
1. Cliquez sur **Aller** puis cliquez sur **OK**.

>[!NOTE]
>
>Remplacer `hiro-xp` avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. Le `lc_version` permet de s’assurer que la fonctionnalité AEM Forms, telle que MTOM, est disponible. Sans spécifier la variable `lc_version`, vous ne pouvez pas appeler AEM Forms à l’aide de MTOM. (Voir [Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

### Créez une page ASP qui appelle FirstAppSolution/PreLoanProcess {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

Dans le projet ASP.NET, ajoutez un formulaire web (un fichier ASPX) responsable de l’affichage d’une page de HTML au demandeur de prêt. Le formulaire web est basé sur une classe dérivée de `System.Web.UI.Page`. La logique de l’application C# qui appelle `FirstAppSolution/PreLoanProcess` se trouve dans la variable `Button1_Click` (ce bouton représente le bouton Submit Application).

L’illustration suivante présente l’application ASP.NET

Le tableau suivant répertorie les contrôles qui font partie de cette application ASP.NET.

<table> 
 <thead> 
  <tr> 
   <th><p>Nom du contrôle</p></th> 
   <th><p>Description</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>TextBoxName</p></td> 
   <td><p>Indique le prénom et le nom du client. </p></td> 
  </tr> 
  <tr> 
   <td><p>TextBoxPhone</p></td> 
   <td><p>Indique l’adresse électronique ou le téléphone du client. </p></td> 
  </tr> 
  <tr> 
   <td><p>TextBoxAmount</p></td> 
   <td><p>Indique le montant du prêt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Button1</p></td> 
   <td><p>Représente le bouton Envoyer la demande.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelJobID</p></td> 
   <td><p>Contrôle Label qui spécifie la valeur de la valeur de l’identifiant d’appel.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelStatus</p></td> 
   <td><p>Contrôle Label qui spécifie la valeur de l’état de la tâche. Cette valeur est récupérée en appelant le service Job Manager. </p></td> 
  </tr> 
 </tbody> 
</table>

La logique d’application qui fait partie de l’application ASP.NET doit créer de manière dynamique une source de données XML à transmettre à la variable `FirstAppSolution/PreLoanProcess` processus. Les valeurs saisies par le demandeur dans la page de HTML doivent être spécifiées dans la source de données XML. Ces valeurs de données sont fusionnées dans le formulaire lorsque le formulaire est affiché dans Workspace. Les classes situées dans la variable `System.Xml` Les espaces de noms sont utilisés pour créer la source de données XML.

Lors de l’appel d’un processus qui nécessite des données XML d’une application ASP.NET, vous pouvez utiliser un type de données XML. En d’autres termes, vous ne pouvez pas passer une `System.Xml.XmlDocument` au processus. Le nom qualifié complet de cette instance XML à transmettre au processus est `InvokePreLoanProcess.PreLoanProcess.XML`. Convertir la variable `System.Xml.XmlDocument` instance à `InvokePreLoanProcess.PreLoanProcess.XML`. Vous pouvez effectuer cette tâche à l’aide du code suivant.

```as3
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
 XmlDocument myXML = CreateXML(userName, phone, amount); 
      
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance 
 StringWriter sw = new StringWriter(); 
 XmlTextWriter xw = new XmlTextWriter(sw); 
 myXML.WriteTo(xw); 
  
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
 inXML.document = sw.ToString();
```

Pour créer une page ASP qui appelle la fonction `FirstAppSolution/PreLoanProcess` effectuez les tâches suivantes dans le `Button1_Click` method :

1. Créez un `FirstAppSolution_PreLoanProcessClient` en utilisant son constructeur par défaut.
1. Créez un `FirstAppSolution_PreLoanProcessClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms et le type de codage :

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Veillez toutefois à indiquer `?blob=mtom`.

   >[!NOTE]
   >
   >Remplacer `hiro-xp`* avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. *

1. Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` membre de données. Convertissez la valeur de retour en `BasicHttpBinding`.
1. Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` membre de données à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
1. Activez l’authentification HTTP de base en effectuant les tâches suivantes :

   * Attribuer le nom d’utilisateur AEM forms au membre de données `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName`.
   * Attribuer la valeur de mot de passe correspondante au membre de données `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password`.
   * Attribuer la valeur constante `HttpClientCredentialType.Basic` au membre de données `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au membre de données `BasicHttpBindingSecurity.Security.Mode`.

   L’exemple de code suivant illustre ces tâches.

   ```as3
    //Enable BASIC HTTP authentication 
    BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
    b.MessageEncoding = WSMessageEncoding.Mtom; 
    mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
    mortgageClient.ClientCredentials.UserName.Password = "password"; 
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
    b.MaxReceivedMessageSize = 2000000; 
    b.MaxBufferSize = 2000000; 
    b.ReaderQuotas.MaxArrayLength = 2000000;
   ```

1. Récupérez les valeurs de nom, de téléphone et de montant saisies par l’utilisateur dans la page web. Utilisez ces valeurs pour créer de manière dynamique une source de données XML envoyée à la variable `FirstAppSolution/PreLoanProcess` processus. Créez un `System.Xml.XmlDocument` qui représente la source de données XML à transmettre au processus (cette logique d’application est présentée dans l’exemple de code suivant).
1. Convertir la variable `System.Xml.XmlDocument` instance à `InvokePreLoanProcess.PreLoanProcess.XML` (cette logique d’application est illustrée dans l’exemple de code suivant).
1. Appeler la variable `FirstAppSolution/PreLoanProcess` en appelant le `FirstAppSolution_PreLoanProcessClient` de `invoke_Async` . Cette méthode renvoie une valeur string qui représente la valeur de l’identifiant d’appel du processus de longue durée.
1. Créez un `JobManagerClient` en utilisant son constructeur. (Assurez-vous d’avoir défini une référence de service pour le service Job Manager.)
1. Répétez les étapes 1 à 5. Spécifiez l’URL suivante pour l’étape 2 : `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Créez un objet `JobId` en utilisant son constructeur.
1. Définissez la variable `JobId` de `id` membre de données avec la valeur renvoyée de la variable `FirstAppSolution_PreLoanProcessClient` de `invoke_Async` .
1. Attribuez le `value` true à la variable `JobId` de `persistent` membre de données.
1. Créez un `JobStatus` en appelant le `JobManagerService` object’s `getStatus` et transmission de la méthode `JobId` .
1. Obtenez la valeur d’état en récupérant la valeur de la variable `JobStatus` de `statusCode` membre de données.
1. Attribuez la valeur de l’identifiant d’appel à la variable `LabelJobID.Text` champ .
1. Attribuez la valeur d’état à la variable `LabelStatus.Text` champ .

### Démarrage rapide : Appel d’un processus de longue durée à l’aide de l’API de service Web {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

L’exemple de code C# suivant appelle la variable `FirstAppSolution/PreLoanProcess`processus.

```as3
 ???/** 
     * Ensure that you create a .NET project that uses  
     * MS Visual Studio 2008 and version 3.5 of the .NET 
     * framework. This is required to invoke a  
     * AEM Forms service using MTOM. 
      
  
 using System; 
 using System.Collections; 
 using System.Configuration; 
 using System.Data; 
 using System.Linq; 
 using System.Web; 
 using System.ServiceModel; 
 using System.Web.Security; 
 using System.Web.UI; 
 using System.Web.UI.HtmlControls; 
 using System.Web.UI.WebControls; 
 using System.Web.UI.WebControls.WebParts; 
 using System.Xml.Linq; 
 using System.Xml; 
 using System.IO; 
  
 //A reference to FirstAppSolution/PreLoanProcess 
 using InvokePreLoanProcess.PreLoanProcess; 
  
 //A reference to JobManager service 
 using InvokePreLoanProcess.JobManager; 
  
  
 namespace InvokePreLoanProcess 
 { 
        public partial class _Default : System.Web.UI.Page 
        { 
            //This method is called when the Submit Application button is  
            //Clicked 
            protected void Button1_Click(object sender, EventArgs e) 
            { 
                //Create a FirstAppSolution_PreLoanProcessClient object 
                FirstAppSolution_PreLoanProcessClient mortgageClient = new FirstAppSolution_PreLoanProcessClient(); 
                mortgageClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
                b.MessageEncoding = WSMessageEncoding.Mtom; 
                mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
                mortgageClient.ClientCredentials.UserName.Password = "password"; 
                b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b.MaxReceivedMessageSize = 2000000; 
                b.MaxBufferSize = 2000000; 
                b.ReaderQuotas.MaxArrayLength = 2000000; 
      
                //Retrieve values that user entered into the web page 
                String userName = TextBoxName.Text; 
                String phone = TextBoxPhone.Text; 
                String amount = TextBoxAmount.Text; 
  
                //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument myXML = CreateXML(userName, phone, amount); 
      
                StringWriter sw = new StringWriter(); 
                XmlTextWriter xw = new XmlTextWriter(sw); 
                myXML.WriteTo(xw); 
  
                InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
                inXML.document = sw.ToString();  
  
                //INvoke the FirstAppSolution/PreLoanProcess process 
                String invocationID =  mortgageClient.invoke_Async(inXML); 
  
                //Create a JobManagerClient object to obtain the status of the long-lived operation 
                JobManagerClient jobManager = new JobManagerClient(); 
                jobManager.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/JobManager?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b1 = (BasicHttpBinding)jobManager.Endpoint.Binding; 
                b1.MessageEncoding = WSMessageEncoding.Mtom; 
                jobManager.ClientCredentials.UserName.UserName = "administrator"; 
                jobManager.ClientCredentials.UserName.Password = "password"; 
                b1.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b1.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b1.MaxReceivedMessageSize = 2000000; 
                b1.MaxBufferSize = 2000000; 
                b1.ReaderQuotas.MaxArrayLength = 2000000; 
  
  
                //Create a JobID object that represents the status of the  
                //long-lived operation 
                JobId jobId = new JobId(); 
                jobId.id = invocationID; 
                jobId.persistent = true; 
                JobStatus jobStatus = jobManager.getStatus(jobId); 
                System.Int16 val2 = jobStatus.statusCode; 
                LabelJobID.Text = "The job status identifier value is " + invocationID;   
                LabelStatus.Text = "The status of the long-lived operation is " + getJobDescription(val2);  
      
            } 
  
            private static XmlDocument CreateXML(String name, String phone, String amount) 
            { 
                //This method dynamically creates a DDX document  
                //to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument xmlDoc = new XmlDocument(); 
  
                //Create the root element and append it to the XML DOM         
                System.Xml.XmlElement root = xmlDoc.CreateElement("LoanApp"); 
                xmlDoc.AppendChild(root); 
  
                //Create the Name element 
                XmlElement nameElement = xmlDoc.CreateElement("Name"); 
                nameElement.AppendChild(xmlDoc.CreateTextNode(name)); 
                root.AppendChild(nameElement); 
  
                //Create the LoanAmount element 
                XmlElement LoanAmount = xmlDoc.CreateElement("LoanAmount"); 
                LoanAmount.AppendChild(xmlDoc.CreateTextNode(amount)); 
                root.AppendChild(LoanAmount); 
  
                //Create the PhoneOrEmail element 
                XmlElement PhoneOrEmail = xmlDoc.CreateElement("PhoneOrEmail"); 
                PhoneOrEmail.AppendChild(xmlDoc.CreateTextNode(phone)); 
                root.AppendChild(PhoneOrEmail); 
  
                //Create the ApprovalStatus element 
                XmlElement ApprovalStatus = xmlDoc.CreateElement("ApprovalStatus"); 
                ApprovalStatus.AppendChild(xmlDoc.CreateTextNode("PENDING APPROVAL")); 
                root.AppendChild(ApprovalStatus); 
  
                //Return the XmlElement instance 
                return xmlDoc; 
            } 
  
  
            //Returns the String value of the Job Manager status code 
            private String getJobDescription(int val) 
            { 
                switch(val) 
                { 
                    case 0: 
                        return "JOB_STATUS_UNKNOWN"; 
      
                    case 1:  
                        return "JOB_STATUS_QUEUED"; 
  
                    case 2:  
                        return "JOB_STATUS_RUNNING"; 
  
                    case 3:  
                        return "JOB_STATUS_COMPLETED";   
      
                    case 4:  
                        return "JOB_STATUS_FAILED";  
  
                     case 5:  
                        return "JOB_STATUS_COMPLETED";  
      
                    case 6:  
                        return "JOB_STATUS_SUSPENDED"; 
      
                    case 7:  
                        return "JOB_STATUS_COMPLETE_REQUESTED"; 
      
                    case 8:  
                        return "JOB_STATUS_TERMINATE_REQUESTED"; 
  
                     case 9:  
                        return "JOB_STATUS_SUSPEND_REQUESTED"; 
  
                       case 10:  
                        return "JOB_STATUS_RESUME_REQUESTED"; 
                } 
  
                return ""; 
            } 
       } 
 } 
 
```

>[!NOTE]
>
>Les valeurs situées dans la méthode définie par l’utilisateur getJobDescription correspondent aux valeurs renvoyées par le service Job Manager.

### Exécution de l’application ASP.NET {#run-the-asp-net-application}

Après avoir compilé et déployé votre application ASP.NET, vous pouvez l’exécuter à l’aide d’un navigateur web. En supposant que le nom du projet ASP.NET soit *InvokePreLoanProcess*, spécifiez l’URL suivante dans un navigateur web :

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

où localhost est le nom du serveur web hébergeant le projet ASP.NET et 1629 est le numéro de port. Lorsque vous compilez et créez votre application ASP.NET, Microsoft Visual Studio la déploie automatiquement.

>[!NOTE]
>
>Pour confirmer que l’application ASP.NET a appelé le processus, démarrez Workspace et acceptez le prêt.

## Création d’une application client créée avec Flex qui appelle un processus de longue durée pour des intervenants humains {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

Vous pouvez créer une application cliente créée avec Flex pour appeler la méthode *FirstAppSolution/PreLoanProcess* processus. Cette application utilise Remoting pour appeler le *FirstAppSolution/PreLoanProcess* processus. (Voir [Appel d’AEM Forms à l’aide d’AEM Forms Remoting (obsolète pour AEM forms)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

L’illustration suivante présente une application cliente créée avec Flex pour collecter des données d’un utilisateur final. Les données sont placées dans une source de données XML et envoyées au processus.

Notez qu’une fois le processus appelé, une valeur d’identifiant d’appel s’affiche. Une valeur d’identifiant d’appel est créée dans le cadre d’un enregistrement qui suit l’état du processus de longue durée.

L’application cliente créée avec Flex effectue les tâches suivantes :

* Récupère les valeurs saisies par l’utilisateur dans la page web.
* Crée de manière dynamique une source de données XML transmise à la variable *FirstAppSolution/PreLoanProcess* processus. Les trois valeurs sont spécifiées dans la source de données XML.
* Appelle le *FirstAppSolution/PreLoanProcess* traitez à l’aide de Remoting.
* Renvoie la valeur de l’identifiant d’appel du processus de longue durée.

### Résumé des étapes {#summary_of_steps-2}

Pour créer une application cliente créée avec Flex qui peut appeler le processus FirstAppSolution/PreLoanProcess, procédez comme suit :

1. Démarrez un nouveau projet Flex.
1. Incluez le fichier adobe-remoting-provider.swc dans le chemin de classe de votre projet. (Voir [Inclusion du fichier de bibliothèque Flex AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Créez un `mx:RemoteObject` par ActionScript ou MXML. (Voir [Création d’une instance mx:RemoteObject](/help/forms/developing/invoking-aem-forms-using-remoting.md))
1. Configurez une `ChannelSet` pour communiquer avec AEM Forms et l’associer à la fonction `mx:RemoteObject` instance. (Voir [Création d’un canal vers AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Appelez le paramètre `login` ou du service `setCredentials` pour spécifier la valeur de l’identifiant utilisateur et le mot de passe. (Voir [Utilisation de l’authentification unique](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Créez la source de données XML à transmettre au `FirstAppSolution/PreLoanProcess` en créant une instance XML. (Cette logique d’application est illustrée dans l’exemple de code suivant.)
1. Créez un objet de type Objet à l’aide de son constructeur. Affectez le XML à l’objet en spécifiant le nom du paramètre d’entrée du processus, comme illustré dans le code suivant :

   ```as3
    //Get the XML data to pass to the AEM Forms process 
    var xml:XML = createXML(); 
    var params:Object = new Object(); 
    params["formData"]=xml;
   ```

1. Appeler la variable `FirstAppSolution/PreLoanProcess` en appelant la fonction `mx:RemoteObject` de l’instance `invoke_Async` . Transmettez la variable `Object` qui contient le paramètre d’entrée. (Voir [Transmission des valeurs d’entrée](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Récupérez la valeur d’identification d’appel renvoyée par un processus de longue durée, comme illustré dans le code suivant :

   ```as3
    // Handles async call that invokes the long-lived process 
    private function resultHandler(event:ResultEvent):void 
    { 
    ji = event.result as JobId; 
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
    }
   ```

### Appel d’un processus de longue durée à l’aide de l’option Remoting {#invoking-a-long-lived-process-using-remoting}

L’exemple de code Flex suivant appelle la variable `FirstAppSolution/PreLoanProcess` processus.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
  
 <mx:Application  xmlns="*" backgroundColor="#FFFFFF"  
      creationComplete="initializeChannelSet();"> 
  
 <mx:Script> 
          <![CDATA[ 
  
             import mx.controls.Alert; 
             import mx.rpc.events.FaultEvent; 
             import mx.rpc.events.ResultEvent; 
             import flash.net.navigateToURL; 
             import mx.messaging.ChannelSet; 
             import mx.messaging.channels.AMFChannel; 
             import mx.collections.ArrayCollection; 
             import mx.rpc.livecycle.JobId; 
             import mx.rpc.livecycle.JobStatus; 
             import mx.rpc.livecycle.DocumentReference; 
             import mx.formatters.NumberFormatter; 
      
             // Holds the job ID returned by LC.JobManager 
             private var ji:JobId;   
      
             private function initializeChannelSet():void  
              { 
              var cs:ChannelSet= new ChannelSet();  
         cs.addChannel(new AMFChannel("remoting-amf", "https://hiro-xp:8080/remoting/messagebroker/amf"));  
         LC_MortgageApp.setCredentials("tblue", "password"); 
         LC_MortgageApp.channelSet = cs; 
              } 
  
            private function submitApplication():void 
             { 
             //Get the XML data to pass to the AEM Forms process 
             var xml:XML = createXML(); 
             var params:Object = new Object(); 
             params["formData"]=xml; 
             LC_MortgageApp.invoke_Async(params); 
             } 
  
             // Handles async call that invokes the long-lived process 
             private function resultHandler(event:ResultEvent):void 
             { 
                ji = event.result as JobId; 
                jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
             } 
  
             private function createXML():XML 
             { 
                //Calculate the Mortgage value to place in the XML data 
                var propertyPrice:String = txtAmount.text ;  
                var name:String = txtName.text ; 
                var phone:String = txtPhone.text ;;  
      
                var model:XML =  
  
                  <LoanApp> 
                           <Name>{name}</Name> 
                           <LoanAmount>{propertyPrice}</LoanAmount> 
                           <PhoneOrEmail>{phone}</PhoneOrEmail>  
                           <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
                  </LoanApp> 
      
              return model; 
             } 
      
      
          ]]> 
       </mx:Script> 
      
       <!-- Declare the RemoteObject and set its destination to the mortgage-app remoting endpoint defined in AEM Forms. --> 
       <mx:RemoteObject id="LC_MortgageApp" destination="FirstAppSolution/PreLoanProcess" result="resultHandler(event);"> 
          <mx:method name="invoke_Async" result="resultHandler(event)"/> 
      </mx:RemoteObject> 
  
  
     <mx:Grid x="229" y="186"> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Image> 
                     <mx:source>file:///D|/LiveCycle_9/FirstApp/financeCorpLogo.jpg</mx:source> 
                 </mx:Image> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Flex Loan Application Page" fontSize="20"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Name:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtName"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Button label="Submit Application" click="submitApplication()"/> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Phone/Email:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtPhone"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Amount:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtAmount"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Label" id="jobStatusDisplay" enabled="true" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
     </mx:Grid> 
      
 </mx:Application> 
 
```
