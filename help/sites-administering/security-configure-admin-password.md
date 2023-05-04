---
title: Configurer le mot de passe d’administrateur sur l’installation
seo-title: Configure the Admin Password on Installation
description: Découvrez comment modifier le mot de passe administrateur lors de l’installation d’AEM.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 33%

---

# Configurer le mot de passe d’administrateur sur l’installation{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Depuis la version 6.3, AEM permet de définir le mot de passe administrateur à l’aide de la ligne de commande lors de l’installation d’une nouvelle instance.

Avec les versions précédentes d’AEM, le mot de passe du compte administrateur, ainsi que le mot de passe de diverses autres consoles, devaient être modifiés après l’installation.

Cette fonctionnalité ajoute la possibilité de définir un nouveau mot de passe administrateur pour le référentiel et le moteur de servlet lors de l’installation d’une instance AEM, éliminant ainsi la nécessité de le faire manuellement par la suite.

>[!CAUTION]
>
>Notez que la fonction ne couvre pas la console Felix, dont le mot de passe doit être modifié manuellement. Pour plus d’informations, voir [Section Liste de contrôle de sécurité](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Comment Puis-Je L’Utiliser ? {#how-do-i-use-it}

Cette fonctionnalité se déclenche automatiquement si vous choisissez d&#39;installer AEM via la ligne de commande, au lieu de double-cliquer sur le fichier JAR depuis un explorateur de système de fichiers.

La syntaxe générale pour exécuter une instance AEM à partir de la ligne de commande est la suivante :

```shell
java -jar aem6.3.jar
```

Lors de l’exécution de l’instance à partir de la ligne de commande, vous aurez la possibilité de modifier le mot de passe administrateur lors du processus d’installation :

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>L’invite de modification du mot de passe administrateur s’affiche uniquement lors de l’installation d’une nouvelle instance AEM.

## Utilisation de l’indicateur -nointeractive {#using-the-nointeractive-flag}

Vous pouvez également choisir de spécifier le mot de passe dans un fichier de propriétés. Pour ce faire, utilisez la méthode `-nointeractive` l’indicateur associé au `-Dadmin.password.file` propriété système.

Voici un exemple :

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Le mot de passe dans le fichier `passwordfile.properties` doit avoir le format suivant :

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Si vous utilisez simplement le paramètre `-nointeractive` sans la propriété système `-Dadmin.password.file`, AEM utilise le mot de passe administrateur par défaut sans vous demander de le modifier, répliquant essentiellement le comportement des versions antérieures. Ce mode non interactif peut être utilisé pour les installations automatisées via l’option de ligne de commande dans un script d’installation.
