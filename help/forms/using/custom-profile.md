---
title: Création d’un profil personnalisé pour HTML5 forms
seo-title: Creating a custom profile for HTML5 forms
description: Un profil HTML5 forms est un nœud de ressources dans Apache Sling. Il représente une version personnalisée du service de rendu HTML5 forms.
seo-description: A HTML5 forms profile is a resource node in Apache Sling. It represents a customized version of HTML5 forms Render service.
uuid: b9938280-a92c-4dde-b465-04372db3ca8d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
feature: Mobile Forms
exl-id: 4630c43f-5b47-435c-8ce5-b4e0d986ec02
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 60%

---

# Création d’un profil personnalisé pour HTML5 forms {#creating-a-custom-profile-for-html-forms}

Un profil est un noeud de ressource dans [Apache Sling](https://sling.apache.org/). Il représente une version personnalisée du service de rendu HTML5 forms. Vous pouvez utiliser le service de rendu de HTML5 forms pour personnaliser l’apparence, le comportement et les interactions des HTMLS5. Un noeud de profil existe dans la variable `/content` dans le référentiel JCR. Vous pouvez placer le noeud directement sous le noeud `/content` dossier ou tout sous-dossier de `/content` dossier.

Le nœud de profil présente la propriété **sling:resourceSuperType** et la valeur par défaut est **xfaforms/profile**. Le script de rendu du noeud se trouve à l’emplacement /libs/xfaforms/profile.

Les scripts Sling sont des scripts JSP. Ces scripts JSP servent de conteneurs pour rassembler le code HTML du formulaire demandé et les artefacts JS/CSS requis. Ces scripts Sling sont également appelés des **scripts de rendu de profil.** Le moteur de rendu de profil appelle le service Forms OSGi pour effectuer le rendu du formulaire demandé.

Le script de profil se trouve dans html.jsp et html.POST.jsp pour les requêtes de GET et de POST. Vous pouvez copier et modifier un ou plusieurs fichiers à remplacer pour y ajouter vos personnalisations. N’effectuez aucune modification statique, la mise à jour du correctif remplace ces modifications.

Un profil comporte divers modules : les modules formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp, et footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

Les modules formRuntime.jsp contiennent des références aux bibliothèques clientes. Il décrit également des méthodes pour extraire des informations sur les paramètre régionaux dans la demande et inclure les messages dans la demande. Vous pouvez inclure des bibliothèques ou des styles JavaScript personnalisés dans le fichier formRuntime.jsp.

## config.jsp {#config-jsp}

Le module config.jsp contient les différentes configurations telles que les services de journalisation, de proxy, et la version du comportement. Dans config.jsp, vous pouvez personnaliser les configurations et les widgets. Vous pouvez également ajouter des configurations telles que l’enregistrement de widgets personnalisés au module config.jsp.

## toolbar.jsp {#toolbar-jsp}

Le fichier toolbar.jsp contient le code pour créer la barre d’outils colorée. Pour supprimer la barre d’outils, supprimez toolbar.jsp du module HTML.jsp

## formBody.jsp {#formbody-jsp}

Le module formBody.jsp sert à la représentation par HTML du formulaire XFA.

## nav_footer.jsp {#nav-footer-jsp}

HTML5 forms commence par générer uniquement la première page du formulaire. Lorsqu’un utilisateur fait défiler le formulaire, le reste des formulaires est chargé. La vitesse de chargement est ainsi optimisée. Le composant nav_footer.jsp contient tous les styles et éléments requis pour faciliter le chargement des pages dans le défilement.

## footer.jsp  {#footer-jsp}

Le module footer.jsp est vide. Il vous permet d’ajouter des scripts qui ne sont utilisés que pour les interactions utilisateur.

## Création de profils personnalisés {#creating-custom-profiles}

Pour créer un profil personnalisé, procédez comme suit :

### Créez un nœud de profil {#create-profile-node}

1. Accédez à l’interface CRX DE à l’adresse URL : `https://[server]:[port]/crx/de` et connectez-vous à l’interface avec les informations d’identification de l’administrateur.

1. Dans le panneau de gauche, rendez-vous à l’emplacement suivant : */content/xfaforms/profiles*.

1. Copiez le paramètre par défaut du nœud et collez le nœud dans un autre dossier(*/content/profiles*) intitulé *hrform*.

1. Sélectionnez le nouveau nœud, *hrform*, puis ajoutez une propriété de chaîne : *sling:resourceType* avec la valeur : *hrform/demo*.

1. Cliquez sur Enregistrer tout dans le menu de la barre d’outils pour enregistrer les modifications.

### Créez un script de rendu de profil {#create-the-profile-renderer-script}

Après la création d’un profil personnalisé, ajoutez les informations de rendu à ce profil. Lorsqu’il reçoit une demande pour le nouveau profil, CRX vérifie l’existence du dossier/apps pour la page JSP à générer. Créez la page JSP dans le dossier /apps.

1. Dans le volet de gauche, accédez au `/apps` dossier.
1. Cliquez avec le bouton droit de la souris sur le `/apps` et choisissez de créer un dossier portant le nom **hrform**.
1. Insider la variable **hrform** créer un dossier nommé **demo**.
1. Cliquez sur le bouton **Enregistrer tout**.
1. Accédez à `/libs/xfaforms/profile/html.jsp` et copiez le noeud **html.jsp**.
1. Coller **html.jsp** dans le noeud `/apps/hrform/demo` dossier créé ci-dessus avec le même nom **html.jsp** et cliquez sur **Enregistrer**.
1. Si vous rencontrez d’autres composants du script de profil, suivez les étapes 1 à 6 pour copier les composants dans le dossier /apps/hrform/demo.

1. Pour vérifier que le profil est créé, ouvrez l’URL `https://[server]:[port]/content/xfaforms/profiles/hrform.html`

Pour vérifier les formulaires, [Importez les formulaires](/help/forms/using/get-xdp-pdf-documents-aem.md) de votre système de fichiers local vers AEM Forms et [affichez l’aperçu du formulaire](/help/forms/using/previewing-forms.md) sur l’instance d’auteur du serveur AEM.
