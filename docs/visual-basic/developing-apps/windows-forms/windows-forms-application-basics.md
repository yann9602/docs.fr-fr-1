---
title: "Windows Forms Application Basics (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Windows applications"
  - "Windows Forms, Visual Basic"
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Windows Forms Application Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La possibilité de créer des applications Windows Forms qui s'exécutent localement sur les ordinateurs des utilisateurs constitue un élément essentiel de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Vous pouvez utiliser Visual Studio pour créer l'application et l'interface utilisateur à l'aide de Windows Forms.  Une application Windows Forms repose sur les classes de l'espace de noms <xref:System.Windows.Forms>.  
  
## Conception d'applications Windows Forms  
 Vous pouvez créer des applications de service Windows Forms et Windows à l'aide de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Mise en route des Windows Forms](../Topic/Getting%20Started%20with%20Windows%20Forms.md).  Fournit des informations sur la manière de créer et de programmer des Windows Forms.  
  
-   [Windows Forms Walkthroughs](http://msdn.microsoft.com/fr-fr/fd44d13d-4733-416f-aefc-32592e59e5d9).  Répertorie les rubriques qui permettent de développer pas à pas les applications Windows Forms les plus fréquemment créées, basées sur les Windows Forms.  
  
-   [contrôles Windows Forms](../Topic/Windows%20Forms%20Controls.md).  Collection de rubriques expliquant en détail l'utilisation des contrôles Windows Forms.  
  
-   [Windows Service Applications](../Topic/Developing%20Windows%20Service%20Applications.md).  Répertorie les rubriques qui expliquent comment créer des services Windows.  
  
## Génération d'interfaces utilisateur complètes et interactives  
 Windows Forms est le composant client intelligent du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)], un ensemble de bibliothèques managées qui autorisent des tâches d'application courantes telles que la lecture et l'écriture dans le système de fichiers.  Grâce à un environnement de développement comme [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)], vous pouvez créer des applications Windows Forms qui affichent des informations, demandent des entrées de données aux utilisateurs et communiquent avec les ordinateurs distants sur un réseau.  
  
 Dans Windows Forms, un formulaire est une surface visuelle sur laquelle vous affichez des informations à l'intention de l'utilisateur.  Généralement, vous créez des applications Windows Forms en plaçant des contrôles sur les formulaires et en développant des réponses aux actions des utilisateurs telles les clics de souris ou les pressions sur les touches.  Un *contrôle* est un élément d'interface utilisateur discret qui affiche des données ou accepte une entrée de données.  
  
### Événements  
 Lorsqu'un utilisateur effectue une action sur votre formulaire ou sur un de ses contrôles, il génère un événement.  Votre application réagit à ces événements en utilisant du code et traite les événements lorsqu'ils se produisent.  Pour plus d'informations, consultez [Création de gestionnaires d'événements dans les Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
### Contrôles  
 Windows Forms contient de nombreux contrôles que vous pouvez placer sur les formulaires : contrôles qui affichent des zones de texte, des boutons, zones déroulantes, des cases d'option et même des pages Web.  Pour obtenir la liste de tous les contrôles que vous pouvez utiliser sur un formulaire, consultez [Contrôles à utiliser dans les Windows Forms](../Topic/Controls%20to%20Use%20on%20Windows%20Forms.md).  Si un contrôle existant ne satisfait pas vos besoins, Windows Forms prend également en charge la création de vos propres contrôles personnalisés à l'aide de la classe <xref:System.Windows.Forms.UserControl>.  
  
 Windows Forms possède des contrôles d'interface utilisateur complets qui émulent des fonctions dans des applications haut de gamme comme Microsoft Office.  À l'aide du contrôle <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.MenuStrip>, vous pouvez créer des barres d'outils et des menus qui contiennent du texte et des images, afficher des sous\-menus et héberger d'autres contrôles tels que des zones de texte et des zones de liste déroulante.  
  
 À l'aide du Concepteur de formulaires de glisser\-déplacer [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)], vous pouvez facilement créer des applications Windows Forms : sélectionnez simplement les contrôles avec votre curseur et placez\-les sur le formulaire à l'emplacement de votre choix.  Le concepteur fournit des outils tels que le quadrillage et des « lignes d'alignement » pour résoudre le problème d'alignement des contrôles.  Lorsque vous utilisez [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] ou effectuez une compilation sur la ligne de commande, vous pouvez utiliser les contrôles <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> et <xref:System.Windows.Forms.SplitContainer> pour créer des dispositions de formulaire avancées avec un minimum de temps et d'effort.  
  
### Éléments d'interface personnalisés  
 Enfin, si vous devez créer vos propres éléments d'interface personnalisés, l'espace de noms <xref:System.Drawing> contient toutes les classes nécessaires pour rendre des lignes, des cercles et d'autres formes directement sur un formulaire.  
  
 Pour des informations pas à pas sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes.  
  
|Pour|Consultez|  
|----------|---------------|  
|Créer une application Windows Forms avec [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].|[Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/fr-fr/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Utiliser des contrôles sur les formulaires|[Comment : ajouter des contrôles à des Windows Forms](../Topic/How%20to:%20Add%20Controls%20to%20Windows%20Forms.md)|  
|Gérer des événements à partir d'un formulaire et de ses contrôles|[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/fr-fr/8461e9b8-14e8-406f-936e-3726732b23d2)|  
|Utilisez le contrôle <xref:System.Windows.Forms.ToolStrip>|[Comment : créer un ToolStrip de base avec des éléments standard à l'aide du concepteur](../Topic/How%20to:%20Create%20a%20Basic%20Windows%20Forms%20ToolStrip%20with%20Standard%20Items%20Using%20the%20Designer.md)|  
|Créer des graphiques à l'aide de <xref:System.Drawing>|[Mise en route de la programmation graphique](../Topic/Getting%20Started%20with%20Graphics%20Programming.md)|  
|Créer des contrôles personnalisés|[Comment : hériter de la classe UserControl](../Topic/How%20to:%20Inherit%20from%20the%20UserControl%20Class.md)|  
  
## Affichage et manipulation de données  
 De nombreuses applications doivent afficher les données à partir d'une base de données, d'un fichier XML, d'un service Web XML ou d'une autre source de données.  Windows Forms fournit un contrôle souple appelé contrôle <xref:System.Windows.Forms.DataGridView> pour rendre ces données tabulaires dans un format de ligne et de colonne traditionnel de sorte que chaque donnée occupe sa propre cellule.  À l'aide de <xref:System.Windows.Forms.DataGridView>, vous pouvez personnaliser l'apparence des cellules, verrouiller les lignes et les colonnes arbitraires en place et afficher des contrôles complexes dans les cellules, entre autres fonctionnalités.  
  
 La connexion aux sources de données sur un réseau est une tâche simple dans les clients intelligents Windows Forms.  Le composant <xref:System.Windows.Forms.BindingSource>, nouveau avec Windows Forms dans [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong-md.md)] et le [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)], représente une connexion à une source de données et expose des méthodes pour lier des données aux contrôles, naviguer jusqu'aux enregistrements précédents et suivants, modifier les enregistrements et réenregistrer les modifications dans la source d'origine.  Le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit une interface simple sur le composant <xref:System.Windows.Forms.BindingSource> afin que les utilisateurs puissent naviguer entre les enregistrements.  
  
### Contrôles liés aux données  
 Vous pouvez créer facilement des contrôles liés aux données à l'aide de la fenêtre Sources de données qui affiche des sources de données telles que des bases de données, des services Web et des objets dans votre projet.  Vous pouvez créer des contrôles liés aux données en faisant glisser des éléments depuis cette fenêtre jusqu'à votre projet.  Vous pouvez également connecter des contrôles existants à des données en faisant glisser des objets depuis la fenêtre Sources de données jusqu'à des contrôles existants.  
  
### Paramètres  
 Les paramètres constituent un autre type de liaison de données que vous pouvez gérer dans Windows Forms.  La plupart des applications clientes intelligentes doivent conserver des informations sur leur état à l'exécution, telles que la dernière taille des formulaires, et conserver des données sur les préférences de l'utilisateur, telles que les emplacements par défaut des fichiers enregistrés.  La fonction des paramètres d'application prend en charge ces conditions en fournissant un moyen facile de stocker les deux types de paramètres sur l'ordinateur client.  Une fois définis à l'aide de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] ou d'un éditeur de code, ces paramètres sont rendus persistants au format XML et automatiquement reconvertis dans la mémoire au moment de l'exécution.  
  
 Pour des informations pas à pas sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes.  
  
|Pour|Consultez|  
|----------|---------------|  
|Utiliser un composant <xref:System.Windows.Forms.BindingSource>|[Comment : lier des contrôles Windows Forms au composant BindingSource à l'aide du concepteur](../Topic/How%20to:%20Bind%20Windows%20Forms%20Controls%20with%20the%20BindingSource%20Component%20Using%20the%20Designer.md)|  
|Utiliser des sources de données [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)]|[Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)|  
|Ouvrir la fenêtre Sources de données|[Procédure pas à pas : affichage de données sur un Windows Form](../Topic/Walkthrough:%20Displaying%20Data%20on%20a%20Windows%20Form.md)|  
|Utiliser les paramètres d'application|[How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/fr-fr/53b3af80-1c02-4e35-99c6-787663148945)|  
  
## Déploiement d'applications sur les ordinateurs clients  
 Une fois que vous avez écrit votre application, vous devez l'envoyer à vos utilisateurs afin qu'ils puissent l'installer et l'exécuter sur leurs propres ordinateurs clients.  À l'aide de la technologie [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)], quelques clics suffisent à déployer vos applications depuis [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] et à fournir aux utilisateurs une URL pointant vers votre application sur le Web.  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] gère tous les éléments et dépendances dans votre application et vérifie que l'application est correctement installée sur l'ordinateur client.  
  
 Les applications [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] peuvent être configurées pour s'exécuter uniquement lorsque l'utilisateur est connecté au réseau, ou pour s'exécuter en mode connexion et en mode hors connexion.  Lorsque vous spécifiez qu'une application doit prendre en charge une opération hors connexion, [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] ajoute un lien à votre application dans le menu **Démarrer** de l'utilisateur afin que ce dernier puisse l'ouvrir sans utiliser l'URL.  
  
 Lorsque vous mettez à jour votre application, vous publiez un nouveau manifeste de déploiement et une nouvelle copie de votre application sur votre serveur Web.  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] détecte les mises à jour disponibles et met à niveau l'installation de l'utilisateur ; aucune programmation personnalisée n'est requise pour mettre à jour les anciens assemblys.  
  
 Pour une introduction complète à [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)], consultez [ClickOnce Security and Deployment](/visual-studio/deployment/clickonce-security-and-deployment).  Pour des informations pas à pas sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes :  
  
|Pour|Consultez|  
|----------|---------------|  
|Déployer une application avec [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)]|[How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)<br /><br /> [Walkthrough: Manually Deploying a ClickOnce Application](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)|  
|Mettre à jour un déploiement [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)]|[How to: Manage Updates for a ClickOnce Application](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)|  
|Gérer la sécurité avec [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)]|[How to: Enable ClickOnce Security Settings](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)|  
  
## Autres contrôles et fonctionnalités  
 Il existe de nombreuses autres fonctionnalités dans Windows Forms qui rendent l'implémentation des tâches courantes rapide et facile, par exemple la prise en charge de la création de boîtes de dialogue, de l'impression, de l'ajout d'une aide et d'une documentation et de la traduction de votre application en plusieurs langues.  Windows Forms s'appuie en outre sur le système de sécurité fiable du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)], ce qui vous permet de publier des applications plus sécurisées pour vos clients.  
  
 Pour des informations pas à pas sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes :  
  
|Pour|Consultez|  
|----------|---------------|  
|Imprimer le contenu d'un formulaire|[Comment : imprimer des graphiques dans Windows Forms](../Topic/How%20to:%20Print%20Graphics%20in%20Windows%20Forms.md)<br /><br /> [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../Topic/How%20to:%20Print%20a%20Multi-Page%20Text%20File%20in%20Windows%20Forms.md)|  
|Globaliser une application Windows Forms|[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5)|  
|En savoir plus sur la sécurité Windows Forms|[Vue d'ensemble de la sécurité dans les Windows Forms](../Topic/Security%20in%20Windows%20Forms%20Overview.md)|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Vue d'ensemble des Windows Forms](../Topic/Windows%20Forms%20Overview.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)