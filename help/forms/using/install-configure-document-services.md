---
title: Installation et configuration des services de document
seo-title: Installing and configuring document services
description: Installez les services de documents d’AEM Forms pour créer, assembler, publier, archiver des documents PDF, ajouter des signatures numériques afin de limiter l’accès aux documents et de décoder les formulaires à code-barres.
seo-description: Install AEM Forms document services to create, assemble, distribute, archive PDF documents, add digital signatures to limit access to documents, and decode barcoded forms.
uuid: 908806a9-b0d4-42d3-9fe4-3eae44cf4326
topic-tags: installing
discoiquuid: b53eae8c-16ba-47e7-9421-7c33e141d268
role: Admin
exl-id: b3eea94d-87f1-49b3-aabc-cdb32629ef20
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '4251'
ht-degree: 100%

---

# Installation et configuration des services de document {#installing-and-configuring-document-services}

AEM Forms fournit un ensemble de services OSGi pour exécuter différentes opérations au niveau du document, par exemple, des services pour créer, assembler, publier et archiver des documents PDF, pour ajouter des signatures numériques afin de limiter l’accès aux documents et de décoder les formulaires à code-barres. Ces services sont inclus dans le package du module complémentaire AEM Forms. Ces services sont collectivement désignés par Services de document. Les services de document disponibles et leurs fonctionnalités principales sont les suivants :

* **Service Assembler :** permet de combiner, d’organiser et d’étendre vos documents aux formats PDF et XDP et d’obtenir des informations sur les documents PDF. Ce service permet également de convertir et de valider des documents PDF au format PDF/A standard, il convertit les formulaires PDF et XML aux formats PDF/A-1b, PDF/A-2b et PDFA/A-3b. Pour plus d’informations, consultez la section [Service Assembler](/help/forms/using/assembler-service.md).

* **Service ConvertPDF :** permet de convertir des documents PDF en fichiers PostScript ou en images (aux formats JPEG, JPEG 2000, PNG et TIFF). Pour plus d’informations, consultez la section [Service ConvertPDF](/help/forms/using/using-convertpdf-service.md).

* **Service Barcoded Forms :** permet d’extraire des données depuis des images électroniques de code-barres. Il accepte en entrée des fichiers PDF et TIFF qui contiennent un ou plusieurs codes à barres et extrait les données de code à barres. Pour plus d’informations, consultez la section [Service Barcoded Forms](/help/forms/using/using-barcoded-forms-service.md).

* **Service DocAssurance :** permet de chiffrer et de déchiffrer des documents, d’ajouter des droits d’utilisation aux fonctionnalités d’Adobe Reader ou encore d’ajouter des signatures numériques à vos documents. Le service Doc Assurance se compose en fait de trois services : Signature, Encryption et Reader Extensions. Pour plus d’informations, consultez la section [Service DocAssurance](/help/forms/using/overview-aem-document-services.md).

* **Service Encryption :** permet de chiffrer et de déchiffrer des documents. Lorsqu’un document est chiffré, son contenu devient illisible. Un utilisateur autorisé peut déchiffrer le document pour pouvoir accéder à son contenu. Pour plus d’informations, consultez la section [Service Encryption](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **Service Forms :** permet de créer des applications clientes interactives de capture de données assurant la validation, le traitement, la transformation et la transmission de formulaires généralement créés dans Forms Designer. Le service Forms restitue sous forme de documents PDF tout type de formulaire que vous créez. Pour plus d’informations, consultez la section [Service Forms](/help/forms/using/forms-service.md).

* **Service Output :** permet de créer des documents dans différents formats, y compris PDF et les formats d’imprimantes laser et d’imprimantes d’étiquettes. Les formats d’imprimantes laser sont les suivants : PostScript et PCL (Printer Control Language). Pour plus d’informations, consultez la section [Service Output](/help/forms/using/output-service.md).

* **Service PDF Generator :** fournit des API pour convertir des formats de fichier natifs en PDF. Il convertit également des fichiers PDF en d’autres formats et optimise la taille des documents PDF. Pour plus d’informations, consultez la section [Service PDF Generator](aem-document-services-programmatically.md#pdfgeneratorservice).

* **Service Reader Extension :** permet à votre organisation de partager facilement des documents PDF interactifs en ajoutant des droits dʼutilisation aux fonctionnalités dʼAdobe Reader. Ce service active des fonctionnalités indisponibles à l’ouverture d’un document PDF dans Adobe Reader, comme l’ajout de commentaires dans un document, le remplissage de formulaires et l’enregistrement du document. Pour plus d’informations, consultez la section [Service Reader Extensions](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **Service Signature :** permet d’utiliser des documents et des signatures numériques sur le serveur AEM. Par exemple, le service Signature est généralement utilisé dans les situations suivantes :

   * Le serveur AEM certifie un formulaire avant que ce dernier ne soit envoyé à un utilisateur et ouvert avec Acrobat ou Adobe Reader.
   * Le serveur AEM valide la signature apposée sur un formulaire via Acrobat ou Adobe Reader.
   * Le serveur AEM signe un formulaire au nom d’un notaire.

   Le service Signature accède aux certificats et aux informations d’identification stockées dans le Trust Store. Pour plus d’informations, consultez la section [Service Signature](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms est une plateforme d’entreprise performante et les services de documents ne sont quʼune des fonctionnalités proposées. Pour obtenir la liste complète des fonctionnalités, voir [Présentation d’AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Topologie de déploiement {#deployment-topology}

Le package du module complémentaire AEM Forms est une application déployée sur AEM. En général, une seule instance AEM (de création ou de publication) suffit pour exécuter les services de document AEM Forms. La topologie suivante est recommandée pour exécuter les services de document d’AEM Forms. Pour plus d’informations sur les topologies, voir [Topologies d’architecture et de déploiement pour AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![Topologies d’architecture et de déploiement pour AEM Forms](do-not-localize/document-services.png)

>[!NOTE]
>
>Bien qu’AEM Forms vous permette de configurer et d’exécuter toutes les fonctionnalités à partir d’un seul serveur, vous devez planifier la capacité, équilibrer la charge et configurer des serveurs dédiés pour des fonctionnalités spécifiques dans un environnement de production. Par exemple, pour un environnement utilisant le service PDF Generator pour convertir des milliers de pages par jour et plusieurs formulaires adaptatifs pour capturer des données, configurez des serveurs AEM Forms distincts pour le service PDF Generator et les fonctionnalités de formulaires adaptatifs. Cela permet de fournir des performances optimales et de dimensionner les serveurs indépendamment les uns des autres.

## Configuration requise {#system-requirements}

Avant de commencer à installer et configurer les services de document AEM Forms, assurez-vous que :

* Le matériel et l’infrastructure logicielle sont en place. Pour obtenir une liste détaillée des matériels et logiciels pris en charge, voir [Conditions techniques applicables](/help/sites-deploying/technical-requirements.md).

* Le chemin d’installation de l’instance AEM ne contient aucun espace blanc.
* Une instance AEM est en cours d’utilisation. Dans la terminologie AEM, une « instance » est une copie d’AEM s’exécutant sur un serveur en mode de création ou de publication. En général, une seule instance AEM (création ou publication) suffit pour exécuter les services de document AEM Forms :

   * **Création** : instance AEM utilisée pour créer, télécharger et modifier du contenu et assurer l’administration du site Web. Une fois que le contenu est publié, il est répliqué sur l’instance de publication.
   * **Publication** : instance AEM qui diffuse le contenu publié au public sur Internet ou sur un réseau interne.

* Les besoins en mémoire sont satisfaits. Le module complémentaire AEM Forms nécessite :

   * 15 Go d’espace temporaire pour les installations Microsoft Windows.
   * 6 Go d’espace temporaire pour les installations Unix.

* Les logiciels client requis pour que PDF Generator effectue la conversion sous Microsoft Windows et Linux sont installés :

   * **Microsoft Windows** : installez [Microsoft Office](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) ou [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator).
   * **Linux** : installez [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p).

>[!NOTE]
>
>* Sous Microsoft Windows, PDF Generator prend en charge les itinéraires de conversion WebKit, Acrobat WebCapture et PhantomJS pour convertir des fichiers HTML en documents PDF.
>* Sur les systèmes dʼexploitation UNIX, PDF Generator prend en charge les itinéraires de conversion WebKit et PhantomJS pour convertir des fichiers HTML en documents PDF.
>


### Exigences supplémentaires pour les systèmes d’exploitation UNIX {#extrarequirements}

Si vous utilisez un système d’exploitation UNIX, installez les packages suivants des supports d’installation du système d’exploitation correspondant :

<table> 
 <tbody> 
  <tr> 
   <td> 
    <ul> 
     <li>expat</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libxcb</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>freetype</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXau</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>libSM</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>zlib</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libICE</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libuuid</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>glibc</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXext</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>nss-softokn-freebl</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>fontconfig</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>libX11</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXrender</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXrandr</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXinerama</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

* **(PDF Generator uniquement**) Installez la version 32 bits des bibliothèques libcurl, libcrypto et libssl et créez les liens symboliques ci-dessous. Les liens symboliques pointent vers la dernière version des bibliothèques respectives :

   * /usr/lib/libcurl.so
   * /usr/lib/libcrypto.so
   * /usr/lib/libssl.so

* **(PDF Generator uniquement)** Le service PDF Generator prend en charge les itinéraires WebKit et PhantomJS pour convertir des fichiers HTML en documents PDF. Pour activer la conversion pour l’itinéraire PhantomJS, installez les bibliothèques 64 bits répertoriées ci-dessous. Ces bibliothèques sont généralement déjà installées. Si une bibliothèque est manquante, installez-la manuellement :

   * linux-gate.so.1
   * libz.so.1
   * libfontconfig.so.1
   * libfreetype.so.6
   * libdl.so.2
   * librt.so.1
   * libpthread.so.0
   * libstdc++.so.6
   * libm.so.6
   * libgcc_s.so.1
   * libc.so.6
   * ld-linux.so.2
   * libexpat.so.1

## Configurations de pré-installation {#preinstallationconfigurations}

Les configurations répertoriées dans la section Configurations de pré-installation s’appliquent uniquement au service PDF Generator. Si vous ne configurez pas le service PDF Generator, vous pouvez ignorer la section Configurations de pré-installation.

### Installation d’Adobe Acrobat et d’applications tierces {#install-adobe-acrobat-and-third-party-applications}

Si vous prévoyez d’utiliser le service PDF Generator pour convertir des formats de fichiers natifs tels que Microsoft Word, Microsoft Excel, Microsoft PowerPoint, OpenOffice, WordPerfect X7 et Adobe Acrobat en documents PDF, assurez-vous que ces applications sont installées sur le serveur AEM Forms.

>[!NOTE]
>
>* Adobe Acrobat, Microsoft Word, Excel et PowerPoint sont disponibles uniquement pour Microsoft Windows. Si vous utilisez le système d’exploitation UNIX, installez OpenOffice pour convertir les fichiers RTF et les fichiers Microsoft Office pris en charge en documents PDF.
>* Fermez toutes les boîtes de dialogue qui s’affichent après l’installation d’Adobe Acrobat et d’un logiciel tiers pour tous les utilisateurs configurés pour utiliser le service PDF Generator.
>* Démarrez tous les logiciels installés au moins une fois. Fermez toutes les boîtes de dialogue pour tous les utilisateurs configurés pour utiliser le service PDF Generator.
>


Après l’installation d’Acrobat, ouvrez Microsoft Word. Sur l’onglet **Acrobat**, cliquez sur **Créer un fichier PDF** et convertissez un fichier .doc ou.docx disponible sur votre ordinateur en document PDF. Si la conversion fonctionne, AEM Forms est prêt à utiliser Acrobat avec le service PDF Generator.

### Définition des variables d’environnement {#setup-environment-variables}

Définissez des variables d’environnement pour Java Development Kit 32 bits et 64 bits, des applications tierces et Adobe Acrobat. Les variables d’environnement doivent contenir le chemin d’accès absolu de l’exécutable utilisé pour démarrer l’application correspondante, par exemple, le tableau ci-dessous répertorie les variables d’environnement pour quelques applications :

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Application</strong></p> </td> 
   <td><p><strong>Variable d’environnement</strong></p> </td> 
   <td><p><strong>Exemple</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>JDK (64 bits)</strong></p> </td> 
   <td><p>JAVA_HOME</p> </td> 
   <td><p>C:\Program Files\Java\jdk1.8.0_74</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>JDK (32 bits)</strong></p> </td> 
   <td><p>JAVA_HOME_32</p> </td> 
   <td><p>C:\Program Files (x86)\Java\jdk1.8.0_74</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>Adobe Acrobat</strong></p> </td> 
   <td><p>Acrobat_PATH</p> </td> 
   <td><p>C:\Program Files (x86)\Adobe\Acrobat 2015\Acrobat\Acrobat.exe</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>Bloc-notes</strong></p> </td> 
   <td><p>Notepad_PATH</p> </td> 
   <td><p>C:\WINDOWS\notepad.exe<br /> <strong></strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>OpenOffice </strong></p> </td> 
   <td><p>OpenOffice_PATH</p> </td> 
   <td><p>C:\Program Files (x86)\OpenOffice.org 4</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Toutes les variables d’environnement et leurs chemins respectifs sont sensibles à la casse.
>* JAVA_HOME, JAVA_HOME_32 et Acrobat_PATH (Windows uniquement) sont des variables d’environnement obligatoires.
>* La variable d’environnement OpenOffice_PATH est définie sur le dossier d’installation et non pas sur le chemin d’accès au fichier exécutable.
>* Ne définissez pas de variables d’environnement pour des applications Microsoft Office telles que Word, PowerPoint, Excel et Project, ni pour des applications AutoCAD. Si ces applications sont installées sur le serveur, le service Generate PDF les démarre automatiquement.
>* Sur les plates-formes UNIX, installez OpenOffice en tant que /root. Si OpenOffice n’est pas installé en tant qu’utilisateur root, le service PDF Generator ne parvient pas à convertir les documents OpenOffice en documents PDF. Si vous devez installer et exécuter OpenOffice en tant qu’utilisateur non root, indiquez les droits sudo pour l’utilisateur non-root.
>* Si vous utilisez OpenOffice sur une plateforme UNIX, exécutez la commande suivante pour définir la variable de chemin :
>
>  `export OpenOffice_PATH=/opt/openoffice.org4`


### (Uniquement pour IBM WebSphere) Configuration du fournisseur de socket SSL IBM {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Pour configurer le fournisseur de socket SSL IBM, procédez comme suit :

1. Créez une copie du fichier java.security. L’emplacement par défaut du fichier est `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Ouvrez le fichier java.security copié pour le modifier.
1. Modifiez les fabriques de socket SSL par défaut pour utiliser les fabriques JSSE2 au lieu des fabriques IBM WebSphere par défaut :

   **Contenu par défaut:**

   ```shell
   #ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   #ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   #WebSphere socket factories (in cryptosf.jar)
   ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

   **Contenu modifié :**

   ```shell
   ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   
   #WebSphere socket factories (in cryptosf.jar)
   #ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   #ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

1. Pour activer le serveur AEM Forms pour utiliser le fichier java.security mis à jour, lors du démarrage du serveur AEM Forms, ajoutez l’argument java suivant :

   `-Djava.security.properties= [path of newly created Java.security file].`

### (Windows uniquement) Configurer et installer le service d’encre et de reconnaissance de l’écriture manuscrite {#configure-install-ink-and-handwriting-service}

Si vous exécutez Microsoft Windows Server, configurez le service d’encre et de reconnaissance de l’écriture manuscrite. Ce service est nécessaire pour ouvrir des fichiers Microsoft PowerPoint qui utilisent des fonctions d’encre de Microsoft Office :

1. Ouvrez le gestionnaire de serveur. Cliquez sur l’icône du **[!UICONTROL gestionnaire de serveur]** sur la barre de lancement rapide.
1. Cliquez sur **[!UICONTROL Ajouter des fonctions]** dans le menu **[!UICONTROL Fonctions]**. Cochez la case **[!UICONTROL Services d’encre et de reconnaissance de l’écriture manuscrite.]**
1. Boîte de dialogue **[!UICONTROL Sélectionner des fonctionnalités]** avec l’option **[!UICONTROL Services d’encre et de reconnaissance de l’écriture manuscrite]** cochée. Cliquez sur **[!UICONTROL Installer]** pour installer le service.

### (Windows uniquement) Configurer les paramètres de blocage des fichiers pour Microsoft Office {#configure-the-file-block-settings-for-microsoft-office}

Modifiez les paramètres du Centre de gestion de la confidentialité Microsoft Office pour permettre au service PDF Generator de convertir des fichiers créés avec des versions précédentes de Microsoft Office.

1. Ouvrez une application Microsoft Office. Par exemple, Microsoft Word. Accédez à **[!UICONTROL Fichier]** >**[!UICONTROL Options]**. La boîte de dialogue Options s’affiche.

1. Cliquez sur **[!UICONTROL Centre de gestion de la confidentialité]**, puis sur **[!UICONTROL Paramètres du Centre de gestion de la confidentialité]**.
1. Dans les **[!UICONTROL Paramètres du Centre de gestion de la confidentialité]**, cliquez sur **[!UICONTROL Paramètres de blocage des fichiers]**.
1. Dans la liste **[!UICONTROL Type de fichier]**, désélectionnez l’option **[!UICONTROL Ouvrir]** pour le type de fichier que le service PDF Generator devrait être autorisé à convertir en documents PDF.

### (Windows uniquement) Accorder le droit Remplacer un jeton de niveau processus {#grant-the-replace-a-process-level-token-privilege}

Le compte utilisateur utilisé pour démarrer le serveur d’applications doit avoir le droit de **Remplacer un jeton de niveau processus**. Le compte système local possède le droit de **Remplacer un jeton de niveau processus** par défaut. Pour les serveurs s’exécutant avec un utilisateur du groupe des administrateurs locaux, le droit doit être accordé explicitement. Effectuez les étapes suivantes pour accorder le droit :

1. Ouvrez l’éditeur de stratégie de groupe de Microsoft Windows. Pour ouvrir l’éditeur de stratégie de groupe, cliquez sur **[!UICONTROL Démarrer]**, saisissez **gpedit.msc** dans la zone Lancer la recherche, puis cliquez sur **[!UICONTROL Éditeur de stratégie de groupe]**.
1. Accédez à **[!UICONTROL Stratégie d’ordinateur local]** > **[!UICONTROL Configuration d’ordinateur]** > **[!UICONTROL Paramètres Windows]** > **[!UICONTROL Paramètres de sécurité]** > **[!UICONTROL Stratégies locales]** > **[!UICONTROL Attribution des droits utilisateur]** et modifiez la stratégie **[!UICONTROL Remplacer un jeton de niveau processus]** pour y inclure le groupe Administrateurs.
1. Ajoutez l’utilisateur à l’entrée Remplacer un jeton de niveau processus.

### (Windows uniquement) Activer le service PDF Generator pour les utilisateurs non-administrateurs {#enable-the-pdf-generator-service-for-non-administrators}

Vous pouvez permettre à un utilisateur non-administrateur d’utiliser le service PDF Generator. Normalement, seuls les utilisateurs disposant de droits d’administrateur peuvent utiliser le service :

1. Créez une variable d’environnement PDFG_NON_ADMIN_ENABLED.
1. Définissez la valeur de la variable d’environnement sur TRUE.
1. Redémarrez l’instance AEM Forms.

### (Windows uniquement) Désactiver le contrôle de compte d’utilisateur (UAC) {#disable-user-account-control-uac}

1. Pour accéder à l’utilitaire de configuration système, sélectionnez **[!UICONTROL Démarrer > Exécuter]** et saisissez **[!UICONTROL MSCONFIG]**.
1. Cliquez sur l’onglet **[!UICONTROL Outils]**, faites défiler l’écran vers le bas, puis sélectionnez **[!UICONTROL Modifier les paramètres de contrôle de compte d’utilisateur]**. Cliquez sur **[!UICONTROL Démarrer]** pour lancer la commande dans une nouvelle fenêtre.
1. Déplacez le curseur sur le niveau Ne jamais m’avertir. Cela fait, fermez la fenêtre de commande, puis celle de la configuration du système.
1. Vérifiez que le paramètre de registre pour l’UAC est défini sur 0 (zéro). Pour vérifier, procédez comme suit :

   1. Microsoft recommande de sauvegarder le registre avant de le modifier. Pour obtenir la procédure détaillée, voir [Comment sauvegarder et restaurer le registre dans Windows](https://support.microsoft.com/fr-fr/help/322756).
   1. Ouvrez l’éditeur de registre Microsoft Windows. Pour ouvrir l’éditeur de registre, accédez à Démarrer > Exécuter, saisissez regedit, puis cliquez sur OK.
   1. Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Assurez-vous que la valeur de EnableLUA est définie sur 0 (zéro).
   1. Assurez-vous que la valeur de **EnableLUA** est définie sur 0 (zéro). Si la valeur n’est pas 0, remplacez-la par 0. Fermez l’éditeur du registre.

1. Redémarrez l’ordinateur.

### (Windows uniquement) Désactiver le service de rapport d’erreur {#disable-error-reporting-service}

Lors de la conversion d’un document au format PDF à l’aide du service PDF Generator sous Windows Server, ce dernier signale parfois que le fichier exécutable a rencontré un problème et doit se fermer. La conversion au format PDF n’est toutefois pas affectée et se poursuit en arrière-plan.

Pour éviter de recevoir cette erreur, vous pouvez désactiver le rapport d’erreurs Windows. Pour en savoir plus sur la désactivation des rapports d’erreur, consultez la section [https://technet.microsoft.com/en-us/library/cc754364.aspx](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### (Windows uniquement) Configurer la conversion de fichiers HTML en PDF {#configure-html-to-pdf-conversion}

Le service PDF Generator fournit des méthodes ou des itinéraires WebKit, WebCapture et PhantomJS pour convertir des fichiers HTML en documents PDF. Sous Windows, pour activer la conversion des itinéraires WebKit et Acrobat WebCapture, copiez la police Unicode vers le répertoire %windir%\fonts.

>[!NOTE]
>
>À chaque installation de nouvelles polices dans le dossier de polices, redémarrez l’instance AEM Forms.

### (Plateformes UNIX uniquement) Configurations supplémentaires pour la conversion de fichiers HTML en PDF  {#extra-configurations-for-html-to-pdf-conversion}

Sur les plates-formes UNIX, le service PDF Generator prend en charge les itinéraires WebKit et PhantomJS pour convertir des fichiers HTML en documents PDF. Pour activer la conversion de fichiers HTML en PDF, effectuez les configurations suivantes, applicables à l’itinéraire de conversion de votre choix :

### (Plateformes UNIX uniquement) Activer la prise en charge des polices Unicode (WebKit uniquement) {#enable-support-for-unicode-fonts-webkit-only}

Copiez la police Unicode vers l’un des répertoires suivants, en fonction de votre système d’exploitation :

* /usr/lib/X11/fonts/TrueType
* /usr/share/fonts/default/TrueType
* /usr/X11R6/lib/X11/fonts/ttf
* /usr/X11R6/lib/X11/fonts/truetype
* /usr/X11R6/lib/X11/fonts/TrueType
* /usr/X11R6/lib/X11/fonts/TTF
* /usr/openwin/lib/X11/fonts/TrueType (Solaris)

>[!NOTE]
>
>* Sous RedHat Enterprise Linux 6.x et versions ultérieures, les polices Courier ne sont pas disponibles. Pour installer les polices Courier, téléchargez l’archive font-ibm-type1-1.0.3.zip. Extrayez le fichier d’archive vers /usr/share/fonts. Créez un lien symbolique de /usr/share/X11/fonts vers /usr/share/fonts.
>* Supprimez tous les fichiers de mémoire cache des polices .lst dans les répertoires Html2PdfSvc/bin et /usr/share/fonts.
>* Vérifiez que les répertoires /usr/lib/X11/fonts et /usr/share/fonts existent. Si les répertoires n’existent pas, utilisez la commande ln pour créer un lien symbolique à partir de /usr/share/X11/fonts vers /usr/lib/X11/fonts et un autre lien symbolique à partir de /usr/share/fonts vers /usr/share/X11/fonts. Vérifiez également que les polices Courier sont disponibles à l’emplacement /usr/lib/X11/fonts.
>* Vérifiez que toutes les polices (Unicode et non Unicode) sont disponibles dans le répertoire /usr/share/fonts ou /usr/share/X11/fonts.
>* Lorsque vous exécutez le service PDF Generator en tant qu’utilisateur non root, donnez à l’utilisateur non root un accès en lecture et en écriture à tous les répertoires de polices.
>* À chaque installation de nouvelles polices dans le dossier de polices, redémarrez l’instance AEM Forms.
>


## Installation du module complémentaire AEM Forms {#install-aem-forms-add-on-package}

Le package du module complémentaire AEM Forms est une application déployée sur AEM. Le package contient des services de document AEM Forms et d’autres fonctionnalités AEM Forms. Pour installer le package, procédez comme suit : 

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
1. Dans la section **[!UICONTROL Filtres]** :
   1. Sélectionnez **[!UICONTROL Formulaires]** dans la liste déroulante **[!UICONTROL Solution]**.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
1. Appuyez sur le nom applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis appuyez sur **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](https://docs.adobe.com/content/help/fr/experience-manager-65/administering/contentmanagement/package-manager.html) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

   Vous pouvez également télécharger le package via le lien direct répertorié dans l’article [Version d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).

1. Une fois le package installé, vous êtes invité à redémarrer l’instance AEM. **N’arrêtez pas le serveur immédiatement.** Avant d’arrêter le serveur AEM Forms, attendez que les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED cessent d’apparaître dans le fichier `[AEM-Installation-Directory]/crx-quickstart/logs/error`.log et que le journal soit stable.

## Configurations post-installation {#post-installation-configurations}

### Configuration de Boot Delegation pour les bibliothèques RSA/BouncyCastle  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Désactivez l’instance AEM. Accédez au dossier [Répertoire d’installation AEM]\crx-quickstart\conf\. Ouvrez le fichier sling.properties pour modification.

   Si vous utilisez `[AEM installation directory]\crx-quickstart\bin\start.bat` pour démarrer une instance AEM, modifiez le fichier sling.properties situé à l’emplacement suivant :`[AEM_root]\crx-quickstart\`.

1. Ajoutez les propriétés suivantes au fichier sling.properties :

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (AIX uniquement) Ajoutez les propriétés suivantes au fichier sling.properties :

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Enregistrez et fermez le fichier.

### Configuration du service de gestion de polices  {#configuring-the-font-manager-service}

1. Connectez-vous à [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) en tant qu’administrateur.
1. Recherchez et ouvrez le service **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]**. Indiquez le chemin d’accès des répertoires des polices système, Adobe Server et client. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >les droits d’utilisation relatifs aux polices fournies par des sociétés autres qu’Adobe sont régis par les contrats de licence accompagnant ces polices. Ils ne sont pas couverts par la licence d’utilisation du logiciel Adobe qui vous est concédée. Adobe vous recommande de vous assurer que vous agissez en conformité avec tous les contrats de licence de sociétés tierces applicables avant d’utiliser des polices non-Adobe avec des logiciels Adobe, notamment en ce qui concerne l’utilisation de polices dans des environnements de serveurs.
   > Lorsque vous installez de nouvelles polices dans le dossier de polices, redémarrez l’instance AEM Forms.

### Configuration d’un compte d’utilisateur local pour exécuter le service PDF Generator  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Un compte d’utilisateur local est requis pour exécuter le service PDF Generator. Pour les étapes de création d’un utilisateur local, voir [Créer un compte d’utilisateur dans Windows](https://support.microsoft.com/fr-fr/help/13951/windows-create-user-account) ou créer un compte d’utilisateur sur des plateformes UNIX.

1. Ouvrez la page [Configuration de PDF Generator dans AEM Forms.](http://localhost:4502/libs/fd/pdfg/config/ui.html)

1. Dans l’onglet **[!UICONTROL Comptes d’utilisateurs]**, saisissez les informations d’identification d’un compte d’utilisateur local, puis cliquez sur **[!UICONTROL Envoyer]**. Si Microsoft Windows vous y invite, autorisez l’accès à l’utilisateur. Une fois ajouté, l’utilisateur configuré est affiché sous la section **[!UICONTROL Vos comptes d’utilisateurs]** dans l’onglet **[!UICONTROL Comptes d’utilisateurs]**.

### Configuration des paramètres de délai d’expiration {#configure-the-time-out-settings}

1. Dans [AEM Configuration Manager](http://localhost:4502/system/console/configMgr), recherchez et ouvrez le service **[!UICONTROL Jacorb ORB Provider]**.

   Ajoutez l’élément suivant au champ **[!UICONTROL Properties.name personnalisé]** et cliquez sur **[!UICONTROL Enregistrer]**. Il définit le délai de la réponse en attente (également appelé délai d’attente du client CORBA) à 600 secondes.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Connectez-vous à l’instance de création AEM et accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Outils]** > **[!UICONTROL Forms]** > **[!UICONTROL Configuration de PDF Generator]**. L’URL par défaut est http://localhost:4502/libs/fd/pdfg/config/ui.html.

   Ouvrez l’onglet **[!UICONTROL Configuration générale]** et modifiez la valeur des champs suivants pour votre environnement :

<table> 
 <tbody> 
  <tr> 
   <td>Champ</td> 
   <td>Description</td> 
   <td>Valeur par défaut</td> 
  </tr> 
  <tr> 
   <td>Expiration de conversion sur le serveur</td> 
   <td>Une conversion PDFG reste active pendant le nombre de secondes définies dans le délai de conversion du serveur.</td> 
   <td>270 secondes<br /> </td> 
  </tr> 
  <tr> 
   <td>Secondes d’analyse de nettoyage PDFG</td> 
   <td>Nombre de secondes requises pour exécuter des opérations après la conversion.<br /> </td> 
   <td>3600 secondes</td> 
  </tr> 
  <tr> 
   <td>Secondes avant expiration de la tâche</td> 
   <td>Durée pendant laquelle le service PDF Generator peut exécuter une conversion. Assurez-vous que la valeur de Secondes avant expiration de la tâche est supérieure à celle de Secondes d’analyse de nettoyage PDFG.</td> 
   <td>7200 secondes</td> 
  </tr> 
 </tbody> 
</table>

### (Windows uniquement) Configurer Acrobat pour le service PDF Generator {#configure-acrobat-for-the-pdf-generator-service}

Sous Microsoft Windows, le service PDF Generator utilise Adobe Acrobat pour convertir les formats de fichiers pris en charge en document PDF. Pour configurer Adobe Acrobat pour le service PDF Generator, procédez comme suit :

1. Ouvrez Acrobat et sélectionnez **[!UICONTROL Modifier]** > **[!UICONTROL Préférences]** > **[!UICONTROL Mises à jour]**. Dans Rechercher les mises à jour maintenant, décochez **[!UICONTROL Installer automatiquement les mises à jour]** et cliquez sur **[!UICONTROL OK]**. Fermez Acrobat.
1. Cliquez deux fois sur un document PDF sur votre système. Lors du premier démarrage d’Acrobat, les boîtes de dialogue de connexion, l’écran de bienvenue et le CLUF s’affichent. Fermez ces boîtes de dialogue pour tous les utilisateurs configurés pour utiliser PDF Generator.
1. Exécutez le fichier de commandes de l’utilitaire PDF Generator pour configurer Acrobat pour le service PDF Generator :

   1. Ouvrez [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) et téléchargez le fichier `adobe-aemfd-pdfg-common-pkg-[version].zip` depuis le gestionnaire de packages.
   1. Décompressez le fichier .zip téléchargé. Ouvrez l’invite de commande avec des droits d’administrateurs.
   1. Accédez au répertoire `[extracted-zip-file]\jcr_root\etc\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\scripts`. Exécutez le fichier de commandes suivant :

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat est configuré pour s’exécuter avec le service PDF Generator.

1. Exécutez l’outil de préparation du système pour valider l’installation d’Acrobat. L’outil vérifie que l’ordinateur est correctement configuré pour exécuter les conversions PDF Generator et génère un rapport au chemin indiqué:

   1. Ouvrez une invite de commandes et accédez au dossier `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\etc\fd\ pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\srt`. Exécutez la commande suivante à partir de l’invite de commande :

      `cscript SystemReadinessTool.vbs [Path_of_reports_folder] en`

      >[!NOTE]
      >
      >Si l’outil System Readiness signale que le fichier pdfgen.api n’est pas disponible dans le dossier des plug-ins Acrobat, copiez le fichier pdfgen.api du répertoire `[extracted-adobe-aemfd-pdfg-common-pkg]\plugins\x86_win32` au répertoire `[Acrobat_root]\Acrobat\plug_ins`.

   1. Accédez à `[Path_of_reports_folder]`. Ouvrez le fichier SystemReadinessTool.html. Vérifiez le rapport et résolvez les problèmes mentionnés.

### (Windows uniquement) Configurer l’itinéraire principal pour la conversion de fichiers HTML en PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

Le service PDF Generator fournit plusieurs itinéraires pour convertir des fichiers HTML en documents PDF : WebKit, Acrobat WebCapture (Windows uniquement) et PhantomJS. Adobe recommande d’utiliser l’itinéraire PhantomJS, car il peut gérer le contenu dynamique, ne dépend pas des bibliothèques 32 bits, JDK 32 bits et ne nécessite aucune police supplémentaire. En outre, l’itinéraire PhantomJS ne requiert pas d’accès sudo ou root pour exécuter la conversion.

L’itinéraire principal par défaut pour les conversions HTML en PDF est WebKit. Pour modifier l’itinéraire de conversion :

1. Sur l’instance de création AEM, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Forms]** > **[!UICONTROL Configuration de PDF Generator]**.

1. Dans l’onglet **[!UICONTROL Configuration générale]**, sélectionnez l’itinéraire de votre choix dans le menu déroulant **[!UICONTROL Itinéraire principal pour les conversions HTML en PDF]**.

### Initialisez Global Trust Store {#intialize-global-trust-store}

Trust Store Management vous permet d’importer, de modifier et de supprimer des certificats de confiance sur le serveur pour valider des signatures numériques et l’authentification de certificats. Vous pouvez en importer et en exporter autant que vous le souhaitez. Une fois qu’un certificat a été importé, vous pouvez modifier les paramètres d’approbation et le type de Trust Store. Pour initialiser un Trust Store, procédez comme suit :

1. Connectez-vous à une instance AEM Forms en tant qu’administrateur.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Trust Store]**.
1. Cliquez sur **[!UICONTROL Créer un Trust Store]**. Définissez le mot de passe, puis cliquez sur **[!UICONTROL Enregistrer]**.

### Configuration des certificats pour le service Encryption et l’extension Reader {#set-up-certificates-for-reader-extension-and-encryption-service}

Le service DocAssurance peut appliquer des droits d’utilisation aux documents PDF. Pour appliquer des droits d’utilisation aux documents PDF, configurez les certificats :

Avant de configurer des certificats, assurez -vous que vous disposez des éléments suivants :

* Fichier de certificat (.pfx).

* Mot de passe de la clé privée, fourni avec le certificat.

* Alias de la clé privée. Vous pouvez exécuter la commande Java keytool pour afficher l’alias de la clé privée :
   `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Mot de passe du fichier KeyStore. Si vous utilisez le certificat Reader Extensions d’Adobe, le mot de passe du fichier Key Store est toujours identique au mot de passe de la clé privée.

Pour configurer les certificats, procédez comme suit :

1. Connectez-vous à l’instance Auteur AEM en tant qu’administrateur. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]**.
1. Cliquez sur le champ **[!UICONTROL nom]** du compte d’utilisateur. La page **[!UICONTROL Modifier les paramètres utilisateur]** s’affiche. Sur l’instance d’auteur AEM, les certificats résident dans un KeyStore. Si vous n’avez pas créé de KeyStore précédemment, cliquez sur **[!UICONTROL Créer KeyStore]** et définissez un nouveau mot de passe pour le KeyStore. Si le serveur contient déjà un KeyStore, ignorez cette étape.  Si vous utilisez le certificat Reader Extensions d’Adobe, le mot de passe du fichier Key Store est toujours identique au mot de passe de la clé privée.
1. Sur la page **[!UICONTROL Modifier les paramètres utilisateur]**, sélectionnez lʼonglet **[!UICONTROL KeyStore]**. Développez l’option **[!UICONTROL Ajouter la clé privée à partir du fichier de magasin de clés]**, puis fournissez un alias. L’alias est utilisé pour effectuer l’opération Reader Extensions.
1. Pour télécharger le fichier de certificat, cliquez sur **[!UICONTROL Sélectionner le fichier du magasin de clés]**, puis téléchargez un fichier &lt;filename>.pfx.

   Ajoutez les **[!UICONTROL mot de passe du magasin de clés]**, **[!UICONTROL mot de passe de la clé privée]** et **[!UICONTROL alias de la clé privée]** associés au certificat dans les champs respectifs. Cliquez sur **[!UICONTROL Envoyer]**.

   >[!NOTE]
   >
   >Dans l’environnement de production, remplacez les informations d’identification d’évaluation par celles de production. Veillez à supprimer vos anciennes informations d’identification Reader Extensions avant de mettre à jour des informations d’identification expirées ou d’évaluation.

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]** sur la page **[!UICONTROL Modifier les paramètres utilisateur]**.

### Activation du chiffrement AES-256 {#enable-aes}

Pour utiliser le chiffrement AES 256 pour les fichiers PDF, récupérez et installez les fichiers Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy. Remplacez les fichiers local_policy.jar et US_export_policy.jar dans le dossier jre/lib/security. Par exemple, si vous utilisez Sun JDK, copiez les fichiers téléchargés dans le dossier `[JAVA_HOME]/jre/lib/security`.

Le service Assembler dépend des services Reader Extensions, Signatures, Forms et Output. Pour vérifier que les services requis sont opérationnels, procédez comme suit :

1. Connectez-vous à lʼadresse `https://'[server]:[port]'/system/console/bundles` en tant qu’administrateur.
1. Recherchez les services suivants et vérifiez qu’ils sont en cours d’exécution :

<table> 
 <tbody> 
  <tr> 
   <th>Nom du service</th> 
   <th>Nom du lot</th> 
  </tr> 
  <tr> 
   <td>Service Signatures</td> 
   <td>adobe-aemfd-signatures</td> 
  </tr> 
  <tr> 
   <td>Service Reader Extensions</td> 
   <td>com.adobe.aemfd.adobe-aemfd-readerextensions<br /> </td> 
  </tr> 
  <tr> 
   <td>Service Forms</td> 
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector<br /> </td> 
  </tr> 
  <tr> 
   <td>Service Output</td> 
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector</td> 
  </tr> 
 </tbody> 
</table>

## Problèmes connus et dépannage {#known-issues-and-troubleshooting}

* La conversion de fichiers HTML au format PDF échoue si un fichier d’entrée compressé comprend des fichiers HTML dont le nom contient des caractères à deux octets. Pour éviter ce problème, n’utilisez aucun caractère à deux octets dans le nom des fichiers HTML.

* Sur les systèmes d’exploitation UNIX, effectuez les opérations suivantes pour rechercher les bibliothèques manquantes :

1. Accéder à `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/`.

1. Exécutez la commande suivante pour répertorier toutes les bibliothèques requises par PhantomJS pour convertir un fichier HTML en PDF.

   `ldd phantomjs`

   Exécutez la commande suivante pour répertorier les bibliothèques manquantes.

   `ldd phantomjs | grep not`

1. Installez manuellement les bibliothèques manquantes.

## Étapes suivantes {#next-steps}

Vous disposez d’un environnement de documents de services AEM Forms fonctionnel. Vous pouvez utiliser les services de document via :

* [Processus basés sur l’utilisation de Forms on OSGi](/help/forms/using/aem-forms-workflow.md)
* [Dossiers de contrôle](/help/forms/using/watched-folder-in-aem-forms.md)
* [API de services de document](/help/forms/using/aem-document-services-programmatically.md)
