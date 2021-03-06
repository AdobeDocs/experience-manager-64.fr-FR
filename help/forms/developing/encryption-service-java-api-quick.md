---
title: API Java du service Encryption QuickStart (SOAP)
seo-title: Encryption Service Java API QuickStart(SOAP)
description: Utilisez l’API Java Encryption Service pour chiffrer un document de PDF, supprimer le chiffrement avec mot de passe, chiffrer un document de PDF avec un certificat, supprimer le chiffrement avec certificat, déverrouiller un document de PDF chiffré et déterminer le type de chiffrement.
seo-description: Use the Encryption Service Java API to encrypt a PDF document, remove password-based encryption, encrypt a PDF document with a certificate, remove certificate-based encryption, unlock an encrypted PDF document, and determine encryption type.
uuid: 3e29b3e9-340b-4b35-80cc-f0aff4180892
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f12c10c3-1ce6-4415-ba9d-5349d1888237
role: Developer
exl-id: 3f287fb1-b1bb-4494-ad66-5addcc6ef2a8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Démarrage rapide de l’API Java Encryption Service (SOAP) {#encryption-service-java-api-quickstart-soap}

[Démarrage rapide (mode SOAP) : Chiffrement d’un document de PDF à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Démarrage rapide (mode SOAP) : Suppression du chiffrement avec mot de passe à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

[Démarrage rapide (mode SOAP) : Chiffrement d’un document de PDF avec un certificat à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Démarrage rapide (mode SOAP) : Suppression d’un chiffrement avec certificat à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Démarrage rapide (mode SOAP) : Déverrouillage d’un document de PDF chiffré à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api)

[Démarrage rapide (mode SOAP) : Détermination du type de chiffrement à l’aide de l’API Java](encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

Les opérations AEM Forms peuvent être effectuées à l’aide de l’API fortement typée d’AEM Forms et le mode de connexion doit être défini sur SOAP.

>[!NOTE]
>
>Les didacticiels de mise en route situés dans Programmation avec AEM forms reposent sur le serveur Forms déployé sur JBoss Application Server et le système d’exploitation Microsoft Windows. Cependant, si vous utilisez un autre système d’exploitation, comme UNIX, remplacez les chemins spécifiques à Windows par les chemins pris en charge par le système d’exploitation approprié. De même, si vous utilisez un autre serveur d’applications J2EE, veillez à spécifier des propriétés de connexion valides. Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Démarrage rapide (mode SOAP) : Chiffrement d’un document de PDF à l’aide de l’API Java {#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api}

L’exemple de code Java suivant chiffre un document PDF nommé *Loan.pdf* avec la valeur de mot de passe de `OpenPassword`. Le mot de passe principal est `PermissionPassword`. Le document du PDF sécurisé est enregistré en tant que fichier de PDF nommé *EncryptLoan.pdf*. (Voir [Chiffrement de documents PDF avec un mot de passe](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.ArrayList; 
 import java.util.List; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class PasswordEncryptPDFSoap{ 
  
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create an EncryptionServiceClient object 
         EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
         //Specify the PDF document to encrypt with a password 
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");     
         Document inDoc = new Document (fileInputStream);  
  
         //Create a PasswordEncryptionOptionSpec object that stores encryption run-time values 
         PasswordEncryptionOptionSpec passSpec = new PasswordEncryptionOptionSpec(); 
          
         //Specify the PDF document resource to encrypt 
         passSpec.setEncryptOption(PasswordEncryptionOption.ALL); 
          
         //Specify the permission associated with the password 
         //These permissions enable data to be extracted from a password 
         //protected PDF form 
         List<PasswordEncryptionPermission> encrypPermissions = new ArrayList<PasswordEncryptionPermission>();  
         encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_ADD); 
         encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_MODIFY); 
         passSpec.setPermissionsRequested(encrypPermissions); 
          
         //Specify the Acrobat version 
         passSpec.setCompatability(PasswordEncryptionCompatability.ACRO_7); 
          
         //Specify the password values 
         passSpec.setDocumentOpenPassword("OpenPassword"); 
         passSpec.setPermissionPassword("PermissionPassword"); 
          
         //Encrypt the PDF document 
         Document encryptDoc = encryptClient.encryptPDFUsingPassword(inDoc,passSpec);  
          
         //Save the password-encrypted PDF document 
         File outFile = new File("C:\\Adobe\EncryptLoan.pdf"); 
         encryptDoc.copyToFile (outFile); 
  
         }catch (Exception e) { 
             e.printStackTrace(); 
         } 
     } 
 }
```

## Démarrage rapide (mode SOAP) : Suppression du chiffrement avec mot de passe à l’aide de l’API Java {#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api}

L’exemple de code Java suivant supprime le chiffrement avec mot de passe d’un document PDF nommé *EncryptLoan.pdf*. La valeur du mot de passe principal utilisé pour supprimer le chiffrement avec mot de passe est : *PermissionPassword*. Le document de PDF non sécurisé est enregistré en tant que fichier de PDF nommé *noEncryptionLoan.pdf*. (Voir [Suppression du chiffrement de mot de passe](/help/forms/developing/encrypting-decrypting-pdf-documents.md#removing-password-encryption).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class RemovePasswordFromPDFSOAP { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                                      
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create an EncryptionServiceClient object 
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
             //Get the encrypted PDF from which to remove password-based encryption 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");     
             Document inDoc = new Document (fileInputStream); 
          
             //Remove password-based encryption from the PDF document  
             Document encryptDoc = encryptClient.removePDFPasswordSecurity(inDoc,"PermissionPassword"); 
  
             //Save the unsecured PDF document 
             File outFile = new File("C:\\Adobe\noEncryptionLoan.pdf"); 
             encryptDoc.copyToFile (outFile); 
              
         }catch (Exception e) { 
             e.printStackTrace();  
         }     
     } 
 }
```

## Démarrage rapide (mode SOAP) : Chiffrement d’un document de PDF avec un certificat à l’aide de l’API Java {#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api}

L’exemple de code Java suivant chiffre un document PDF nommé *Loan.pdf* avec un certificat nommé *Encryption.cer*. Le document de PDF chiffré est enregistré en tant que fichier de PDF nommé *EncryptLoanCert.pdf*. (Voir [Chiffrement de documents de PDF avec des certificats](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.ArrayList; 
 import java.util.List; 
 import java.util.Properties; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class PKIEncryptPDFSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
             //Create a ServiceClientFactory instance 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create an EncryptionServiceClient object 
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
             //Specify the PDF document to encrypt with a certificate 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");     
             Document inDoc = new Document (fileInputStream);  
  
             //Set the List that stores PKI information 
             List pkiIdentities = new ArrayList();  
                  
             //Set the Permission List 
             List permList = new ArrayList(); 
             permList.add(CertificateEncryptionPermissions.PKI_ALL_PERM) ; 
                  
             //Create a Recipient object to store certificate information 
             Recipient recipient = new Recipient(); 
                  
             //Specify the private key that is used to encrypt the document 
             FileInputStream fileInputStreamCert = new FileInputStream("C:\\Adobe\Encryption.cer");     
             Document privateKey = new Document (fileInputStreamCert);  
             recipient.setX509Cert(privateKey); 
                                          
             //Create an EncryptionIdentity object 
             CertificateEncryptionIdentity encryptionId = new CertificateEncryptionIdentity();  
             encryptionId.setPerms(permList); 
             encryptionId.setRecipient(recipient); 
                  
             //Add the EncryptionIdentity to the list 
             pkiIdentities.add(encryptionId); 
              
             //Set encryption run-time options 
             CertificateEncryptionOptionSpec certOptionsSpec = new CertificateEncryptionOptionSpec();  
             certOptionsSpec.setOption(CertificateEncryptionOption.ALL); 
             certOptionsSpec.setCompat(CertificateEncryptionCompatibility.ACRO_7); 
                              
             //Encrypt the PDF document with a certificate 
             Document encryptDoc = encryptClient.encryptPDFUsingCertificates(inDoc,pkiIdentities, certOptionsSpec);  
          
             //Save the encrypted PDF document 
             File outFile = new File("C:\\Adobe\EncryptLoanCert.pdf"); 
             encryptDoc.copyToFile (outFile); 
  
             }catch (Exception e) { 
                 e.printStackTrace(); 
             } 
     } 
 } 
 
```

## Démarrage rapide (mode SOAP) : Suppression d’un chiffrement avec certificat à l’aide de l’API Java {#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api}

L’exemple de code Java suivant supprime un chiffrement avec certificat d’un document de PDF nommé *EncryptLoanCert.pdf*. L’alias de la clé publique utilisée pour supprimer le chiffrement est `Encryption`. Le document de PDF non sécurisé est enregistré en tant que fichier de PDF nommé *noEncryptionLoan.pdf*. (Voir [Suppression d’un chiffrement avec certificat](/help/forms/developing/encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class RemovePKIFromPDFSOAP { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                             
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create an EncryptionServiceClient object 
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
             //Get the encrypted PDF document  
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoanCert.pdf");     
             Document inDoc = new Document (fileInputStream); 
          
             //Remove certificate-based encryption from the PDF document  
             Document encryptDoc = encryptClient.removePDFCertificateSecurity(inDoc, "Encryption"); 
  
             //Save the unsecured PDF document 
             File outFile = new File("C:\\Adobe\noEncryptionLoan.pdf"); 
             encryptDoc.copyToFile (outFile); 
              
         }catch (Exception e) { 
                 e.printStackTrace();  
             }     
     } 
 }
```

## Démarrage rapide (mode SOAP) : Déverrouillage d’un document de PDF chiffré à l’aide de l’API Java {#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api}

L’exemple de code Java suivant déverrouille un document de PDF chiffré par mot de passe nommé *EncryptLoan.pdf*. (Voir [Déverrouillage de documents PDF chiffrés](/help/forms/developing/encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class UnlockPDFSOAP { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create an EncryptionServiceClient object 
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
             //Get the password-encrypted PDF document to unlock 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");     
             Document inDoc = new Document (fileInputStream); 
  
             //Specify the password to open the password-encrypted PDF document 
             String openPassword = "OpenPassword" ;  
  
             //Unlock the password-encrypted PDF document 
             Document unlockedDoc = encryptClient.unlockPDFUsingPassword(inDoc,openPassword); 
          
         }catch (Exception e) { 
                 System.out.println("The following error occurred during this operation " +e.getMessage()); 
         }     
     } 
 } 
 
```

## Démarrage rapide (mode SOAP) : Détermination du type de chiffrement à l’aide de l’API Java {#quick-start-soap-mode-determining-encryption-type-using-the-java-api}

L’exemple de code Java suivant détermine le type de chiffrement qui protège un document de PDF nommé *EncryptLoan.pdf*. (Voir [Définition du type de chiffrement](/help/forms/developing/encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.encryption.client.*; 
  
 public class GetEncryptionTypeSOAP { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                             
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a EncryptionServiceClient object 
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);  
          
             //Get the PDF document 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");     
             Document inDoc = new Document (fileInputStream); 
  
             //Determine the type of encryption of the PDF document 
             EncryptionTypeResult encryptTypeResult = encryptClient.getPDFEncryption(inDoc); 
                          
             if (encryptTypeResult.getEncryptionType() == EncryptionType.PASSWORD) 
                 System.out.println("The PDF document is protected with password-based encryption"); 
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.POLICY_SERVER)     
                 System.out.println("The PDF document is protected with policy"); 
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.CERTIFICATE)     
                 System.out.println("The PDF document is protected with certificate-based encryption"); 
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.OTHER)     
                 System.out.println("The PDF document is protected with another type of encryption");     
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.NONE)     
                 System.out.println("The PDF document is not protected.");         
         }catch (Exception e) { 
                 e.printStackTrace(); 
         }     
     } 
 } 
  
  
 
```
