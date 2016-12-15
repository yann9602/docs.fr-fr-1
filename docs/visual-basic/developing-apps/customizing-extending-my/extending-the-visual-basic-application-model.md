---
title: "Extending the Visual Basic Application Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic Application Model, extending"
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Extending the Visual Basic Application Model
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez ajouter des fonctionnalités au modèle d'application en substituant les membres `Overridable` de la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.  Cette technique permet de personnaliser le comportement du modèle d'application et d'ajouter des appels à vos propres méthodes au moment du démarrage ou de l'arrêt de l'application.  
  
## Vue d'ensemble visuelle du modèle d'application  
 Cette section présente visuellement la séquence des appels de fonction dans le modèle d'application Visual Basic.  La section suivante décrit en détail l'objectif de chaque fonction.  
  
 Le graphique suivant illustre la séquence des appels du modèle d'application dans une application Windows Forms Visual Basic normale.  La séquence commence lorsque la procédure `Sub Main` appelle la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.  
  
 ![Modèle d'application Visual Basic &#45;&#45; Exécution](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB\_ModelRun")  
  
 Le modèle d'application Visual Basic fournit également les événements <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> et <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  Les graphiques suivants illustrent le mécanisme de déclenchement de ces événements.  
  
 ![Modèle d'application Visual Basic &#45;&#45; Instance suivante](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB\_ModelNext")  
  
 ![Exception non gérée du modèle d'application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB\_UnhandEx")  
  
## Substitution des méthodes de base  
 La méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> définit l'ordre dans lequel les méthodes `Application` s'exécutent.  Par défaut, la procédure `Sub Main` d'une application Windows Forms appelle la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.  
  
 Si l'application est une application normale \(application multi\-instances\), ou la première instance d'une application à instance unique, la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> exécute les méthodes `Overridable` dans l'ordre suivant :  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>.  Par défaut, cette méthode définit les styles visuels, les styles d'affichage du texte et l'entité de sécurité en cours pour le thread d'application principal \(si l'application utilise l'authentification Windows\) et appelle `ShowSplashScreen` si ni `/nosplash` ni `-nosplash` n'est utilisé comme argument de ligne de commande.  
  
     La séquence de démarrage de l'application est annulée si cette fonction retourne `False`.  Cela peut être utile si l'application ne doit pas s'exécuter dans certaines circonstances.  
  
     La méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> appelle les méthodes suivantes :  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>.  Détermine si un écran de démarrage est défini pour l'application et, le cas échéant, l'affiche dans un thread séparé.  
  
         La méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> contient le code qui affiche l'écran de démarrage pendant au moins le nombre de millisecondes qui est spécifié par la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  Pour utiliser ces fonctionnalités, vous devez ajouter l'écran de démarrage à votre application à l'aide du **Concepteur de projets** \(qui affecte à la propriété `My.Application.MinimumSplashScreenDisplayTime` une durée de deux secondes\) ou définir la propriété `My.Application.MinimumSplashScreenDisplayTime` dans une méthode qui substitue la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.  Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.  Permet à un concepteur d'émettre du code qui initialise l'écran de démarrage.  
  
         Par défaut, cette méthode ne fait rien.  Si vous sélectionnez un écran de démarrage pour votre application dans le **Concepteur de projets** de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], le concepteur substitue la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> par une autre qui définit la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> à une nouvelle instance du formulaire d'écran de démarrage.  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>.  Fournit un point d'extensibilité pour déclencher l'événement `Startup`.  La séquence de démarrage de l'application s'arrête si cette fonction retourne `False`.  
  
     Par défaut, cette méthode déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>.  Si le gestionnaire d'événements affecte à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de l'argument d'événement la valeur `True`, la méthode retourne `False` pour annuler le démarrage de l'application.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>.  Fournit le point de départ lorsque l'application principale est prête à commencer son exécution, une fois l'initialisation faite.  
  
     Par défaut, avant d'entrer dans la boucle de message Windows Forms, cette méthode appelle les méthodes `OnCreateMainForm` \(pour créer le formulaire principal de l'application\) et `HideSplashScreen` \(pour fermer l'écran de démarrage\) :  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>.  Permet à un concepteur d'émettre du code qui initialise le formulaire principal.  
  
         Par défaut, cette méthode ne fait rien.  Toutefois, lorsque vous sélectionnez un formulaire principal pour votre application dans le **Concepteur de projets** de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], le concepteur substitue la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> à une méthode qui définit la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> comme étant une nouvelle instance du formulaire principal.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>.  Si un écran de démarrage est défini pour l'application et qu'il est ouvert, cette méthode le ferme.  
  
         Par défaut, cette méthode ferme l'écran de démarrage.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>.  Permet de personnaliser le comportement d'une application à instance unique lorsqu'une autre instance de l'application démarre.  
  
     Par défaut, cette méthode déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>.  Fournit un point d'extensibilité pour déclencher l'événement `Shutdown`.  Cette méthode ne s'exécute pas si une exception non gérée se produit dans l'application principale.  
  
     Par défaut, cette méthode déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>.  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>.  Méthode exécutée si une exception non gérée se produit dans l'une des méthodes répertoriées ci\-dessus.  
  
     Par défaut, cette méthode déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> tant qu'un débogueur n'est pas attaché et que l'application gère l'événement `UnhandledException`.  
  
 Si l'application est une application à instance unique, et qu'elle est déjà en cours d'exécution, son instance suivante appelle la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> de l'instance d'origine de l'application, puis se ferme.  
  
 Le constructeur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> appelle la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> pour déterminer le moteur de rendu de texte à utiliser pour les formulaires de l'application.  Par défaut, la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> retourne la valeur `False`, ce qui indique que le moteur de rendu de texte GDI doit être utilisé \(il s'agit de la valeur par défaut dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]\).  Vous pouvez substituer la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> pour retourner la valeur `True`, ce qui indique que le moteur de rendu de texte GDI\+ doit être utilisé \(il s'agit de la valeur par défaut dans Visual Basic .NET 2002 et Visual Basic .NET 2003\).  
  
## Configuration de l'application  
 Dans le modèle d'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fournit des propriétés protégées qui configurent l'application.  Ces propriétés doivent être définies dans le constructeur de la classe d'implémentation.  
  
 Dans un projet Windows Forms par défaut, le **Concepteur de projets** crée du code pour définir les propriétés avec les paramètres du concepteur.  Les propriétés sont utilisées uniquement lorsque le démarrage de l'application est en cours ; il ne sert à rien de les utiliser après le démarrage de l'application.  
  
||||  
|-|-|-|  
|Propriété|Détermine|Définition dans le volet d'application du Concepteur de projets|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Si l'application s'exécute comme une application à instance unique ou comme une application multi\-instances.|Case à cocher de**Définissez la demande d'instance unique**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Si l'application utilise les styles visuels qui correspondent à Windows XP.|Case à cocher de**Activez les styles visuels XP**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Si l'application enregistre automatiquement les modifications des paramètres utilisateur lorsqu'elle se ferme.|Case à cocher de**Enregistrez My.Settings sur l'arrêt**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Ce qui provoque l'arrêt de l'application, par exemple lorsque le formulaire de démarrage se ferme ou lorsque le dernier formulaire se ferme.|Liste de**mode d'arrêt**|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)