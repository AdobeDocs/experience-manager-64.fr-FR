---
title: Activer la journalisation des formulaires au format HTML5
seo-title: Enable logging for HTML5 forms
description: L’utilitaire de journalisation permet la journalisation d’un formulaire et vous aide à déboguer les problèmes liés aux formulaires.
seo-description: The logger utility enables logging for a form and helps you debug form-related issues.
uuid: d6279092-57f3-4fc6-b41b-9caf65459d4d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 23bc7cd2-7d06-4ef8-977a-778e290daef9
feature: Mobile Forms
exl-id: c7953d1b-a332-4138-b744-516f3881cd4d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 57%

---

# Activer la journalisation des formulaires au format HTML5 {#enable-logging-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez configurer l’utilitaire de journalisation pour commencer à créer des journaux pour les formulaires HTML5. L’utilitaire de journalisation comporte plusieurs niveaux. Vous pouvez définir un niveau en fonction de vos besoins. HTML5 forms comporte des composants serveur et client. Vous pouvez configurer des journaux pour chaque composant.

## Configuration de la journalisation côté serveur {#configuring-server-side-logging}

Effectuez les étapes suivantes pour configurer les journaux côté serveur :

1. Accédez à `https://[server]:[port]/system/console/configMgr`. Recherchez et ouvrez l’option *Configuration des journaux de journalisation Apache Sling*. Une boîte de dialogue s’affiche:

   ![ Boîte de dialogue des options de configuration des journaux de journalisation](assets/logconfig.png)

   Option de configuration des journaux de journalisation Apache Sling

1. Remplacez le **Niveau de journal** par **Débogage**.

1. Spécifiez le chemin et le nom du **fichier journal**.

   >[!NOTE]
   >
   >Pour générer des journaux dans le répertoire de formulaires HTML5, ajoutez ../logs/ avant le nom de fichier.

1. Modifiez **Logger** en **HTMLFormsPerfLogger.** Cliquez sur **Enregistrer**.

## Configuration de la journalisation du client {#configuring-client-logging}

Vous pouvez utiliser les méthodes suivantes pour activer la connexion côté client dans les formulaires HTML5 :

* A l’aide du paramètre de requête nommé `log`
* Utilisation de CQ Configuration Manager

### Activation de la journalisation à l’aide du paramètre de requête {#enabling-logging-using-request-parameter}

Grâce à cette méthode, vous pouvez générer des journaux pour une requête spécifique. Le nom du paramètre de requête est **log**. L’URL du journal se présente comme suit :

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

La configuration du journal comprend le niveau et la catégorie de journalisation.

#### Destination du journal {#log-destination}

<table> 
 <tbody> 
  <tr> 
   <th><strong>Destination du journal</strong></th> 
   <th><strong>Description</strong></th> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Les journaux sont dirigés vers le navigateur. <strong>Console</strong></td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Les journaux sont collectés dans un objet JavaScript côté client et peuvent être publiés sur le <strong>serveur</strong> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Les deux options ci-dessus<br /> </td> 
  </tr> 
 </tbody> 
</table>

#### Niveaux de journal {#log-levels}

<table> 
 <tbody> 
  <tr> 
   <th>Niveau de journal</th> 
   <th>Description</th> 
  </tr> 
  <tr> 
   <td>0</td> 
   <td>DÉSACTIVÉ<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>FATAL<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>ERROR<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>WARN<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>INFO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>DEBUG<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>TRACE<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>7</td> 
   <td>TOUT<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Catégories de journalisation {#logger-categories}

<table> 
 <tbody> 
  <tr> 
   <th>Catégorie de journal</th> 
   <th>Description</th> 
  </tr> 
  <tr> 
   <td>une</td> 
   <td>xfa (journaux liés au moteur de script)</td> 
  </tr> 
  <tr> 
   <td>b</td> 
   <td>xfaView (journaux liés au moteur de mise en page)<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>c</td> 
   <td>xfaPerf (journaux liés aux performances)<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Configuration du journal {#log-configuration}

Dans l’URL du journal, le paramètre de chaîne de requête de configuration du journal est défini comme suit :

`{destination}-{a level}-{b level}-{c level}`

Par exemple :

<table> 
 <tbody> 
  <tr> 
   <th>Configuration du journal</th> 
   <th>Description</th> 
  </tr> 
  <tr> 
   <td>2-a4-b5-c6<br type="_moz" /> </td> 
   <td>Destination : Serveur<br /> niveau xfa : INFO<br /> niveau xfaView : DEBUG<br /> niveau xfaPerf : TRACE</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Le niveau de journalisation par défaut pour chaque catégorie de logs a (xfa), b (xfaView) et c (xfaPerf) est de 2 (ERROR). En conséquence, pour la configuration des logs : 2-b6, les niveaux de journal des différentes catégories sont les suivants :\
>a (xfa) : 2 (niveau par défaut ERROR)\
>b (xfaView) : 6 (TRACE spécifié par l’utilisateur)\
>a (xfaPerf) : 2 (niveau par défaut ERROR)

### Activation de la journalisation à l’aide de Configuration Manager {#enabling-logging-using-configuration-manager}

Si vous utilisez Configuration Manager pour activer la journalisation, les journaux sont générés pour chaque demande de rendu jusqu’à ce que la journalisation soit de nouveau désactivée.

1. Connectez-vous à CQ Configuration Manager à l’adresse `https://[server]:[port]/system/console/configMgr` à lʼaide de vos informations d’identification d’administrateur.
1. Recherchez et cliquez sur **Configurations de Mobile Forms**.
1. Dans la zone de texte Options de débogage , saisissez les configurations de journal, comme décrit dans la section précédente, par exemple : **2-a4-b5-c6**

   ![Configuration de formulaires](assets/forms_configuration.png)

   Configuration de formulaires

## Chargement des logs {#uploading-logs}

Si la destination est définie sur 1, tous les messages du journal de script client sont dirigés vers la console. Si un administrateur a besoin de ces journaux ainsi que des journaux de serveur, définissez le niveau de destination sur 2. À ce niveau, tous les journaux sont rassemblés dans un objet JS côté client et, si le formulaire est généré avec le profil par défaut, un bouton **Envoyer des journaux** apparaît à gauche du bouton **Mettre les champs existants en surbrillance** dans la barre d’outils. Lorsque l’utilisateur clique sur le lien, tous les journaux rassemblés sont publiés sur le serveur et consignés dans le fichier de journalisation des erreurs configuré sur le serveur.

Par défaut, toutes les informations sont ajoutées dans le fichier error.log du répertoire /crx-repository/logs/.

Pour modifier l’emplacement et le nom du fichier journal :

1. Connectez-vous à Configuration Manager en tant qu’administrateur. L’URL de Configuration Manager définie par défaut est `https://[*Server*]:[*Port*]/system/console/configMgr`.
1. Cliquez sur **Configuration des journaux de journalisation Sling d’Apache**. Une boîte de dialogue s’affiche.

   ![logconfig-1](assets/logconfig-1.png)

1. Remplacez le **Niveau de journal** par Débogage.

1. Spécifiez le chemin d’accès et le nom du **fichier journal**.

   >[!NOTE]
   >
   >Pour créer des journaux dans le répertoire où les autres fichiers journaux sont conservés, spécifiez ../logs/&lt;nom_fichier> dans la propriété Fichiers journaux.

1. Modifiez **Logger** en **HTMLFormsPerfLogger** et cliquez sur **Enregistrer**.
