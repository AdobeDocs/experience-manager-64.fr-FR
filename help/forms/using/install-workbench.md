---
title: Installer Workbench
seo-title: Install workbench
description: Installez Workbench.
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
source-git-commit: 19dcda357b34e7160792d43cb9335fc3be0dedbc
workflow-type: tm+mt
source-wordcount: '2743'
ht-degree: 88%

---


# Installer Workbench {#install-workbench}

Ce document fournit des instructions d’installation et de configuration de Workbench. Le programme d’installation installe également  Designer.

## À propos {#about}

Ce document est destiné aux administrateurs ou développeurs chargés de l’installation, de la configuration, de l’administration ou du déploiement de Workbench.
Il contient aussi les informations permettant de configurer votre système pour prendre en charge vos processus Adobe® AEM forms® Enterprise Suite (ES) Update 1 (8.2.x) et Adobe® AEM forms® Enterprise Suite 2 (ES2) mis à niveau.
Le présent guide s’adresse par conséquent à un public familiarisé avec le système d’exploitation Microsoft® Windows®.

## Informations complémentaires {#additional-information}

Les ressources indiquées dans le tableau ci-dessous peuvent vous aider à en savoir davantage sur AEM Forms et à démarrer avec cette application.
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Pour plus d’informations sur</strong></p> </td> 
   <td><p><strong>Voir</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Informations de procédure pour Workbench</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61_fr">Aide de Workbench</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Informations générales sur AEM Forms et la manière dont il s’intègre avec d’autres produits Adobe</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65_fr">Présentation d’AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Tutoriel pour créer une application AEM Forms et la tester dans Workspace</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">Création de votre première application AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Toute la documentation disponible relative à AEM Forms</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Documentation dʼAEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Autres services et produits qui s’intègrent à AEM Forms</p> </td> 
   <td><p><a href="http://www.adobe.com/fr/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Les mises à jour des correctifs, les explications techniques et les informations complémentaires sur cette version du produit</p> </td> 
   <td><p><a href="https://www.adobe.com/account/sign-in.supportportal.html">Contactez le support aux entreprises d’Adobe</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Workspace Flex est obsolète et est remplacé par AEM Forms. Il est disponible pour la version AEM Forms.

## Avant l’installation {#before-you-install}

### Présentation de l’installation de Workbench {#workbench-installation-overview}

Workbench est un environnement de développement intégré (IDE) que les développeurs et les auteurs de formulaires utilisent pour créer des processus et des formulaires d’entreprise automatisés. Il permet aussi de gérer les ressources et les services que les processus et les formulaires utilisent.

L’illustration suivante illustre l’installation de Workbench, notamment :
* Création de processus via Workbench
* Conception de formulaire dans Designer

>[!NOTE]
>
>Le serveur AEM Forms nécessite un programme d’installation distinct. Pour plus d’informations, consultez la documentation relative à l’installation d’AEM Forms sur JEE.

## Configuration système requise {#system-prerequisites}

Cette section décrit le configuration matérielle et logicielle requise et les plateformes prises en charge.

### Configuration matérielle et logicielle minimale {#minimum-hardware-software-requirements}

**Workbench**
La configuration minimale recommandée est la suivante :
Espace disque pour l’installation :
* 680 Mo pour Workbench seul.
* 2.15 Go sur un seul disque pour une installation complète de Workbench , Designer et des exemples.
* 400 Mo pour les répertoires d’installation temporaires (200 Mo dans le répertoire utilisateur temporaire et 200 Mo dans le répertoire temporaire de Windows).

>[!NOTE]
>
>Si l’ensemble de ces emplacements se trouve sur un seul disque, vous devez disposer dʼun total de 1,5 Go dʼespace libre lors de l’installation. Les fichiers copiés dans les répertoires temporaires sont supprimés à la fin de l’installation.

* Configuration matérielle requise : Processeur Intel® Pentium® 4 ou AMD équivalent, processeur cadencé à 1 GHz.
* Téléchargez et installez la dernière version d’Adobe AIR (à partir de <a href="http://www.adobe.com/">www.adobe.com</a>) requis pour le client d’aide de la communauté, intégré à Workbench.
* Mise à jour 22 ou ultérieure de l’environnement d’exécution Java™ (JRE) 6.0 vers la version 6.0 *Nouveautés de la version 10*.
* Résolution d’affichage de 1024 X 768 pixels au minimum, écran couleur de 16 bits minimum.
* Connexion réseau via le protocole TCP/IPv4 ou TCP/IPv6 au serveur AEM Forms.
* Installez les packages d’exécution redistribuables Visual C++ 2012 32 bits.
* Installez les packages d’exécution redistribuables Visual C++ 2013 32 bits.

>[!NOTE]
>
>Si Adobe® Acrobat® X est installé sur votre ordinateur, veillez à le désinstaller avant d’installer Workbench. Vous pouvez réinstaller Acrobat après l’installation de Workbench.

>[!NOTE]
>
>Vous devez disposer des droits d’administrateur pour pouvoir installer Workbench. Si vous effectuez une installation à partir d’un compte non administrateur, le programme d’installation vous demandera les informations d’identification d’un compte administrateur.

### Plateformes prises en charge {#supported-platforms}

Pour consulter la liste complète des plateformes prises en charge pour Workbench, reportez-vous à la section [Plateformes prises en charge par AEM Forms](http://adobe.com/go/learn_aemforms_supportedplatforms_65_fr).

## Considérations sur l’installation de Designer {#designer-installation-considerations}

Par défaut, l’installation de Workbench comprend une version correspondante de Designer uniquement en anglais. Si le programme d’installation de Workbench détecte une version existante de Designer sur votre ordinateur, l’installation peut s’arrêter et vous devrez supprimer la version actuelle de Designer pour pouvoir continuer.
Le tableau ci-dessous contient une liste complète des scénarios possibles d’installation de Designer que vous pouvez rencontrer, ainsi que des mesures à prendre lorsque vous installez Workbench.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Version de Designer installée</strong></p> </td> 
   <td><p><strong>Actions requises</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro ou Acrobat Pro Extended (comprend Designer)</p> </td> 
   <td><p>Aucune. L’installation de Workbench détecte une instance de Designer sur votre ordinateur qui a été installée avec Acrobat Pro ou Acrobat Pro Extended.
Différentes versions de Designer peuvent coexister sur le même système (par exemple, Designer 8.2.x et 9.0.x). Il n’est pas nécessaire de désinstaller la version de Designer installée avec Acrobat 10 Pro or Acrobat 10 Pro Extended.
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Designer (autonome)</p> </td> 
   <td><p>Aucune. La version de Designer incluse avec Workbench est en anglais uniquement. Le programme d’installation de Workbench ne réinstallera pas une nouvelle version de Designer. À la place, une version mise à jour, fournie avec le programme d’installation de Workbench, est corrigée. Cela vous permet également d’utiliser votre version traduite de Designer dans Workbench.<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### Pour désinstaller Designer (autonome) {#uninstall-designer-standalone}

1. Accédez à **Panneau de configuration > Programmes > Programmes et fonctionnalités**
1. Dans la liste Programmes actuellement installés, sélectionnez **Adobe Designer**.
1. Cliquez sur **Désinstaller**, puis sur **Oui**.

### Pour désinstaller Designer (autonome) sous Windows 10, procédez comme suit : {#uninstall-designer-standalone-windows10}

1. Accédez à **Panneau de configuration > Programmes > Programmes et fonctionnalités**
1. Dans la liste Programmes actuellement installés, sélectionnez **Adobe Designer**.
1. Cliquez sur **Désinstaller**, puis sur **Oui**.

### Pour désinstaller Designer fourni avec Acrobat Pro ou Acrobat Pro Extended {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. Accédez à **Panneau de configuration > Programmes > Programmes et fonctionnalités**
1. Dans la liste Programmes actuellement installés, sélectionnez **Adobe Acrobat Pro** ou **Adobe Acrobat Pro Extended**.
1. Cliquez sur **Modifier** puis cliquez sur **Suivant**.
1. Sélectionner **Modifier** puis cliquez sur **Suivant**.
1. Sélectionnez **Adobe Designer**, **Ce composant ne sera pas disponible**, puis cliquez sur **Suivant**
1. Cliquez sur **Mettre à jour** puis sur **Terminer**

### Pour désinstaller Designer fourni avec Acrobat Pro ou Acrobat Pro Extended sous Windows 10 {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. Accédez à **Panneau de configuration > Programmes > Programmes et fonctionnalités**
1. Dans la liste Programmes actuellement installés, sélectionnez **Adobe Acrobat Pro** ou **Adobe Acrobat Pro Extended**.
1. Cliquez sur **Modifier** puis cliquez sur **Suivant**.
1. Sélectionner **Modifier** puis cliquez sur **Suivant**.
1. Sélectionnez **Adobe Designer**, **Ce composant ne sera pas disponible**, puis cliquez sur **Suivant**
1. Cliquez sur **Mettre à jour** puis sur **Terminer**

## Installation de Workbench {#installing-workbench}

Ce chapitre explique comment installer Workbench.

### Installation et exécution de Workbench {#installing-and-running-workbench}

Avant d’installer Workbench, vérifiez que votre environnement inclut les logiciels et le matériel nécessaires pour l’exécuter (consultez la section : **Avant lʼinstallation**).

**Pour installer et exécuter Workbench :**

1. Effectuez l’une des tâches suivantes :
   * Accédez au répertoire \workbench sur le support d’installation et cliquez deux fois sur le fichier run_windows_installer.bat.
   * Téléchargez et décompressez Workbench sur votre système de fichiers. Une fois Workbench téléchargé, accédez au répertoire \workbench et cliquez deux fois sur le fichier run_windows_installer.bat.

   >[!IMPORTANT]
   >
   >Le programme d’installation de Workbench ne fonctionne qu’à partir d’un DVD ou d’un lecteur local. Il ne peut pas être exécutée à partir d’un site distant.

   >[!NOTE]
   >
   >Si vous rencontrez une erreur « Impossible de créer la machine virtuelle Java », créez une variable d’environnement nommée _JAVA_OPTIONS avec la valeur -Xmx512M et exécutez le programme d’installation.

1. Dans l’écran d’introduction, cliquez sur Suivant.
1. Lisez le contrat de licence du produit, cochez la case J’accepte les termes du contrat, puis cliquez sur Suivant.
1. (Facultatif) Sélectionnez Installer Adobe Designer si vous avez besoin de cet outil pour créer et modifier des formulaires.

   >[!NOTE]
   >
   >Vous pouvez continuer à utiliser Designer installé avec Acrobat 10 en laissant cette option désactivée.

1. Acceptez le répertoire par défaut proposé comme indiqué ou cliquez sur Choisir et accédez au répertoire dans lequel vous allez installer Workbench, puis cliquez sur Suivant.

   >[!NOTE]
   >
   >Le chemin d’accès du répertoire d’installation ne doit pas contenir les caractères # (livre) et $ (dollar).

1. Vérifiez le compte-rendu de préinstallation, puis cliquez sur Installer. Le programme d’installation affiche la progression de l’installation.
1. Vérifiez le récapitulatif de l’installation. Sélectionnez Démarrer AEM Forms Workbench pour lancer Workbench, puis cliquez sur Suivant.
1. Passez en revue les notes de mise à jour, puis cliquez sur Terminé.
1. Les éléments suivants sont désormais installés sur votre ordinateur :
   * **Workbench** : pour exécuter Workbench via le menu Démarrer, sélectionnez Tous les programmes > AEM Forms > Workbench, si vous avez choisi d’y stocker le dossier de raccourci. Pour plus d’informations, consultez la documentation sur lʼUtilisation de Workbench.
   * **Designer** : vous pouvez accéder à Designer depuis Workbench. Pour plus d’informations, consultez la section Prise en main de l’aide de Designer.
   * **Module externe Workbench**: Suivez les instructions de la section &quot;3.3 Installation de la fonction Workbench Eclipse&quot; à la page 6.
   * **SDK AEM Forms** : pour plus d’informations sur l’utilisation du SDK, consultez la section <a href="http://www.adobe.com/go/learn_lc_programming_10_fr">Programmer avec AEM Forms</a>.

## Processus de mise à niveau {#upgrading-processes}

Les processus AEM Forms Update 1 et LiveCycle ES2 peuvent être mis à niveau vers les applications AEM Forms à l’aide de l’assistant de mise à niveau. Pour plus d’informations, consultez la documentation sur la Mise à niveau des artefacts hérités dans l’aide de Workbench.

### Installation de la fonction Workbench Eclipse {#installing-workbench-eclipse-feature}

Si vous le souhaitez, vous pouvez ajouter la fonction Workbench à Eclipse. Vous pouvez ajouter Workbench après avoir installé Workbench. Par exemple, pour JBoss, l’emplacement suivant contient le fichier :

* Workbench_DVD/additional/eclipse Téléchargez et installez Eclipse 3.6 à partir de <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### Configuration de la fonction de mise à jour d’Eclipse pour Workbench {#configuring-eclipse-update-feature-for-workbench}

Workbench prend en charge la fonction de mise à jour afin que vous soyez sûr d’utiliser la version d’Eclipse la plus à jour. Toutefois, vous devez vous assurer que certains modules supplémentaires sont inclus avec chaque téléchargement :

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Version d’Eclipse</strong></p> </td> 
   <td><p><strong>Modules requis Workbench</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* Graphical Editing Framework (FEM) [org.eclipse.gef.feature.group]: Contenu dans le &quot;SDK Graphical Modeling Framework&quot; [org.eclipse.gmf.sdk.feature.group]

* WST XML Core [org.eclipse.wst.xml_core.feature.feature.group]: Il est contenu dans &quot;Eclipse XML Editors and Tools&quot; [org.eclipse.wst.xml_ui.feature.feature.group]

* Plug-in &#39;org.apache.commons.lang_2.3.0&#39; [n/a]: Il est contenu dans la &quot;Liste des tâches Mylyn (obligatoire)&quot; [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**Installation et déploiement de la fonction Workbench sur Eclipse**:
1. Démarrez Eclipse.
1. Sélectionnez Aide > Installer un nouveau logiciel , puis cliquez sur Ajouter pour ouvrir la boîte de dialogue Ajouter un référentiel.
1. Dans la boîte de dialogue Ajouter un référentiel, cliquez sur Local, accédez au répertoire dans lequel le programme d’installation de Workbench a enregistré le fichier ZIP du module externe, sélectionnez workbench-updatesite.zip, puis cliquez sur Ouvrir.
1. Suivez les instructions des écrans suivants pour déployer la fonction Workbench vers Eclipse.

   >[!NOTE]
   >
   >Ignorez le message « Avertissement : Vous êtes sur le point d’installer une fonction non signée », puis cliquez sur Installer   pour continuer. 

   >[!NOTE]
   >
   >Le module externe Adobe AEM Forms Discovery pour Flash Builder vous permet de créer rapidement des applications Adobe Flex et AIR qui appellent un service faisant partie d’AEM Forms par le biais de ses points de terminaison distants. Des informations sur l’installation et la mise à jour du module externe sont disponibles sur le site web Adobe à l’adresse **Lien requis**.

### Configuration et connexion au serveur {#configuring-and-logging-server}

Pour utiliser Workbench, vous devez disposer d’une instance AEM Forms en cours d’exécution, généralement sur un ordinateur distinct. Vous devez disposer d’un nom d’utilisateur et d’un mot de passe pour vous connecter à AEM Forms, ainsi que des détails concernant l’emplacement du serveur.

>[!NOTE]
>
>Si vous avez configuré AEM Forms pour utiliser le fournisseur de référentiels EMC Documentum ou IBM FileNet et que vous voulez vous connecter à un référentiel autre que le référentiel configuré par défaut dans la console d’administration d’AEM Forms, indiquez le nom de l’utilisateur au format nom_utilisateur@Repository.

### Configuration des paramètres de délai d’expiration {#configuring-timeout-settings}

Par défaut, Workbench arrive à expiration après deux heures, peu importe l’activité ou l’inactivité. Pour modifier le paramètre de délai d’expiration, reportez-vous à la section « Configuration de la gestion des utilisateurs > Configurer les attributs système avancés » de l’aide de la console d’administration.

### Configuration de Workbench pour une connexion via HTTPS {#configuring-workbench-to-connect-over-HTTPS}

Pour connecter Workbench à un serveur AEM Forms via HTTPS, vous devez vous assurer que l’autorité de certification qui a émis la clé publique sera reconnue comme étant approuvée par Workbench. Si le certificat n’est pas reconnu comme provenant d’une source approuvée, vous devez mettre à jour le fichier cacert situé dans le répertoire [Workbench_EMPLACEMENT]/workbench/jre/lib/security.

>[!NOTE]
>
>[Workbench_EMPLACEMENT] représente le répertoire où vous avez installé Workbench. L’emplacement par défaut est C:\Program Files (x86)\Adobe Experience Manager Forms Workbench.

Assurez-vous que vous vous connectez à HTTPS en utilisant le nom spécifié dans le certificat. Ce nom est généralement le nom d’hôte complet.

**Pour mettre à jour le fichier cacert**, procédez comme suit :
1. Assurez-vous que vous disposez d’une copie du certificat SSL (Secure Sockets Layer). Contactez l’administrateur qui a configuré le serveur SSL ou exportez le certificat à l’aide d’un navigateur Web.

   >[!NOTE]
   >
   >Pour exporter le certificat, ouvrez un navigateur web et connectez-vous à la console d’administration, installez le certificat dans le navigateur, puis exportez-le du navigateur vers un emplacement de stockage temporaire (ou directement dans le répertoire [Workbench_EMPLACEMENT]/workbench/jre/lib/security).

1. Copiez le certificat dans le répertoire [Workbench_EMPLACEMENT]/workbench/jre/lib/security.

1. Ouvrez une fenêtre d’invite de commande, accédez à [Workbench_EMPLACEMENT]/workbench/jre/bin, puis tapez la commande suivante :
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Où :
   * changeit est le mot de passe par défaut du stockage des clés cacerts.
   * certname est le certificat sélectionné à l’étape 1.
   * example est l’alias que vous avez choisi pour le certificat. Cette valeur peut être changée

1. Une fois invité à approuver le certificat, tapez Oui et appuyez sur la touche Entrée. Le stockage des clés importe le fichier cacerts dans le répertoire [Workbench_EMPLACEMENT]/workbench/jre/lib/security.

1. Fermez et redémarrez Workbench pour appliquer les modifications.

### Configuration des paramètres du cache pour les modèles générés dynamiquement {#configuring-cache-settings-for-dynamically-generated-templates}

Les aspects suivants du fonctionnement du cache doivent être pris en compte si votre application génère des modèles uniques à la volée en mettant automatiquement à jour le contenu XFA. En effet, chaque transaction utilise un modèle nouveau et unique.

Lorsque le générateur ou la sortie des formulaires recherche ou met à jour les entrées du cache pour un modèle de formulaire spécifique, il utilise plusieurs valeurs clés pour localiser l’entrée de cache spécifique à laquelle il sera fait accès.

* **Nom de fichier modèle** : Emplacement et nom du modèle utilisé comme identifiant unique principal du formulaire mis en cache.
* **Horodatage** : Le fichier modèle contient un horodatage utilisé pour déterminer l’heure de la dernière mise à jour du formulaire.
* **UUID modèle** : Designer insère dans chaque modèle un identifiant unique (UUID) pour le formulaire et sa version. Chaque fois que le formulaire est mis à jour, l’identifiant UUID incorporé est mis à jour. Par exemple, un modèle XDP peut afficher le contenu suivant :

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **Options de rendu** : Dans le cache de formulaire rendu, les contenus de cache sont stockés séparément pour chaque ensemble d’options de rendu uniques.


Le service Forms reçoit des modèles par référence au nom de fichier ou à l’emplacement de référentiel ou par valeur en tant qu’objet XML en mémoire.
* **Modèles transmis par référence** : Utilise la racine de contenu et le nom de formulaire. Si des modèles uniques avec différents noms de fichier sont transmis dans chaque requête à l’aide de cette méthode, le cache de disque grandit sans fin et n’est jamais réutilisé. Pour éviter cela, les modèles uniques doivent être transmis avec le même nom de fichier pour garantir que le même cache est mis à jour pour toutes les requêtes.
* **Modèles transmis par valeur** : Utilise les octets de modèle transmis avec les données à l’aide du paramètre theinDataDoc. Si des modèles uniques avec un identifiant UUID différent sont transmis à l’aide de cette méthode, le cache de disque grandit sans fin et n’est jamais réutilisé. Pour éviter ceci, l’attribut UUID doit être supprimé de tous les modèles afin de garantir qu’aucun cache n’est créé pour le modèle. Sinon, transmettre le même identifiant UUID non nul permet de créer les objets de cache, mais garantit que le même cache est mis à jour à chaque demande.

Pour empêcher le cache de grandir sans fin, tenez compte des facteurs suivants afin de rendre les modèles générés de manière dynamique à l’aide des nouvelles API AEM Forms, qui sont renderHTMLForm2 et renderPDFForm2.

Lorsque vous utilisez les nouvelles API, le modèle est transmis en tant qu’objet document, qui est géré par le service Forms selon qu’il est passivé on non.

Pour les documents passivés dans lesquels l’identifiant UUID et la racine de contenu font office de clé de cache, tenez compte des points suivants :
* Le cache n’est pas créé pour les modèles d’entrée passivés sans identifiant UUID.
* Si plusieurs modèles d’entrée passivés portant le même identifiant UUID et la même racine de contenu sont transmis, le même cache est remplacé.

Pour les documents non passivés dans lesquels le nom de fichier et la racine de contenu font office de clé de cache, considérez l’aspect suivant :
* Pour les modèles d’entrée non passivés, la mise en cache dépend de la racine de contenu et du nom de fichier à partir desquels le document a été généré.
Le même cache sera utilisé uniquement pour les requêtes présentant la même racine de contenu et le même nom de fichier de modèle.
Les meilleures pratiques suivantes garantissent que le cache ne grandit pas sans fin lorsque des modèles générés de manière dynamique sont transmis au service Forms :
   * Éliminez l’identifiant UUID ou transmettez le même identifiant UUID dans tous les modèles générés dynamiquement.
   * Générez le document à partir des octets de modèle ou du même nom de fichier sur disque.

### Désinstallation de Workbench {#uninstalling-workbench}

Utilisez l’outil d’ajout ou de suppression de programmes du Panneau de configuration pour lancer le programme de désinstallation. Les applications Workbench et Designer ont des programmes de désinstallation distincts.

## Configurer AEM Forms XDC Editor {#configuring-aem-forms-xdc-editor}

Avec XDC Editor, les administrateurs d’imprimantes réseau peuvent créer et modifier des fichiers XML Forms Architecture Device Configuration (XDC). Les fichiers XDC décrivent les fonctionnalités des imprimantes, telles que la langue d’imprimante ou la corrélation entre le format de papier et l’emplacement du bac.

Pour que votre administrateur d’imprimantes réseau utilise XDC Editor, déplacez les fichiers XDC échantillons et reportez-vous à la section Création de profils de périphériques à l’aide de XDC Editor.

**Pour obtenir les fichiers XDC échantillons, procédez comme suit** :
1. Sur le serveur AEM Forms, localisez le dossier XDC dans [répertoire racine AEM Forms]\sdk\samples\Output\IVS.
1. Copiez le contenu de ce dossier dans un répertoire accessible à partir du système Workbench ou Eclipse.

**Pour accéder à l’aide de XDC Editor, procédez comme suit** :
1. Visitez le site web de documentation d’AEM Forms.
1. Cliquez sur l’onglet Développer et accédez à Création de profils de périphériques à l’aide de XDC Editor. Téléchargez le fichier xdc_editor_help_web.zip et installez les fichiers d’aide en suivant les instructions fournies dans le fichier Lisez-moi.

