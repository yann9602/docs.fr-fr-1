---
title: "Extension du modèle d’Application Visual Basic | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9752cdfa79d3db4c8b07daa95aea2c842e06cc36
ms.lasthandoff: 03/13/2017

---
# <a name="extending-the-visual-basic-application-model"></a>Extension du modèle d'application Visual Basic
Vous pouvez ajouter des fonctionnalités au modèle d’application en substituant les `Overridable` les membres de la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Cette technique vous permet de personnaliser le comportement du modèle d’application et ajouter des appels à vos propres méthodes lorsque l’application démarre et s’arrête.  
  
## <a name="visual-overview-of-the-application-model"></a>Présentation visuelle du modèle d’Application  
 Cette section présente visuellement la séquence des appels de fonction dans le modèle d’Application Visual Basic. La section suivante décrit l’objectif de chaque fonction en détail.  
  
 Le graphique suivant illustre la séquence d’appels du modèle application dans une application Visual Basic Windows Forms normale. La séquence commence lorsque la `Sub Main` les appels de procédure du <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>méthode.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
 ![Modèle d’Application Visual Basic--Exécution](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 Le modèle d’Application Visual Basic fournit également les <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>et <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Les graphiques suivants illustrent le mécanisme de déclenchement de ces événements.  
  
 ![Modèle d’Application Visual Basic--Instance suivante](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Exception non gérée du modèle d’Application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Substituer les méthodes de Base  
 Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>méthode définit l’ordre dans lequel les `Application` méthodes exécuter.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Par défaut, le `Sub Main` procédure pour une application Windows Forms appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>méthode.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
 Si l’application est une application normale (plusieurs instances d’application) ou la première instance d’une application à instance unique, la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>méthode s’exécute le `Overridable` méthodes dans l’ordre suivant :</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Par défaut, cette méthode définit les styles visuels, styles d’affichage du texte et principal actuel pour le thread d’application principal (si l’application utilise l’authentification Windows) et les appels `ShowSplashScreen` si aucun `/nosplash` ni `-nosplash` est utilisé comme un argument de ligne de commande.  
  
     La séquence de démarrage d’application est annulée si cette fonction renvoie `False`. Cela peut être utile s’il existe des circonstances dans lesquelles l’application ne doit pas exécutée.  
  
     Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>méthode appelle les méthodes suivantes :</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Détermine si l’application a un écran de démarrage défini et si c’est le cas, affiche l’écran de démarrage sur un thread distinct.  
  
         Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>méthode contient le code qui affiche l’écran d’accueil de l’écran au moins le nombre de millisecondes spécifié par le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>propriété.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Pour utiliser cette fonctionnalité, vous devez ajouter l’écran de démarrage à votre application à l’aide de la **Concepteur de projets** (qui affecte le `My.Application.MinimumSplashScreenDisplayTime` deux secondes à la propriété), ou définir le `My.Application.MinimumSplashScreenDisplayTime` propriété dans une méthode qui substitue le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>(méthode).</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> Permet à un concepteur d’émettre du code qui initialise l’écran de démarrage.  
  
         Par défaut, cette méthode ne fait rien. Si vous sélectionnez un écran de démarrage pour votre application dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Concepteur de projets**, le concepteur substitue la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>par une méthode qui définit le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>propriété à une nouvelle instance de la forme de l’écran de démarrage.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A> Fournit un point d’extensibilité pour déclencher le `Startup` événement. La séquence de démarrage de l’application s’arrête si cette fonction retourne `False`.  
  
     Par défaut, cette méthode déclenche la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> Si le Gestionnaire d’événements définit les @System.ComponentModel.CancelEventArgs.Cancel propriété de l’argument d’événement pour `True`, la méthode retourne `False` pour annuler le démarrage de l’application.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A> Fournit le point de départ lorsque l’application principale est prête à s’exécuter, une fois l’initialisation terminée.  
  
     Par défaut, avant d’entrer dans la boucle de message Windows Forms, cette méthode appelle la `OnCreateMainForm` (pour créer le formulaire principal de l’application) et `HideSplashScreen` (pour fermer l’écran de démarrage) méthodes :  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> Offre un moyen pour un concepteur d’émettre du code qui initialise le formulaire principal.  
  
         Par défaut, cette méthode ne fait rien. Toutefois, lorsque vous sélectionnez un formulaire principal pour votre application dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Concepteur de projet**, le concepteur substitue la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>par une méthode qui définit la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>propriété vers une nouvelle instance du formulaire principal.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A> Si l’application a un écran de démarrage défini et ouvert, cette méthode ferme l’écran de démarrage.  
  
         Par défaut, cette méthode ferme l’écran de démarrage.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> Fournit un moyen de personnaliser le comportement d’une application à instance unique lorsqu’une autre instance de l’application démarre.  
  
     Par défaut, cette méthode déclenche la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A> Fournit un point d’extensibilité pour déclencher le `Shutdown` événement. Cette méthode ne s’exécute pas si une exception non gérée se produit dans l’application principale.  
  
     Par défaut, cette méthode déclenche la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A> Exécuté si une exception non gérée se produit dans une des méthodes répertoriées ci-dessus.  
  
     Par défaut, cette méthode déclenche la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>événement tant qu’un débogueur n’est pas attaché et que l’application gère le `UnhandledException` événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
  
 Si l’application est une application à instance unique et que l’application est déjà en cours d’exécution, l’instance suivante de l’application appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>méthode sur l’instance d’origine de l’application, puis se ferme.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>  
  
 Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>constructeur appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>propriété pour déterminer le moteur de rendu de texte à utiliser pour les formulaires de l’application.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Par défaut, le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>propriété renvoie `False`, indiquant que le moteur de rendu de texte GDI est utilisé, qui est la valeur par défaut dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> Vous pouvez remplacer le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>propriété à retourner `True`, ce qui signifie que le moteur de rendu de texte GDI + est utilisé, qui est la valeur par défaut dans Visual Basic .NET 2002 et Visual Basic .NET 2003.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>  
  
## <a name="configuring-the-application"></a>Configuration de l’Application  
 Dans le cadre de la [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modèle d’Application, la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe fournit des propriétés protégées qui configurent l’application.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Ces propriétés doivent être définies dans le constructeur de la classe d’implémentation.  
  
 Dans un projet Windows Forms par défaut, le **Concepteur de projet** crée du code pour définir les propriétés avec les paramètres du concepteur. Les propriétés sont utilisées uniquement au démarrage de l’application ; leur définition après le démarrage de l’application n’a aucun effet.  
  
|Propriété|Détermine|Dans le volet Application du Concepteur de projets|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Si l’application s’exécute comme une application à instance unique ou à plusieurs instances.|**Application à instance unique** case à cocher|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Si l’application utilise des styles visuels qui correspond à Windows XP.|**Activer des styles visuels XP** case à cocher|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Si l’application enregistre automatiquement les modifications des paramètres utilisateur de l’application lors de la fermeture de l’application.|**Enregistrer My.Settings lors de l’arrêt** case à cocher|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Ce qui entraîne l’application à arrêter, par exemple lorsque le formulaire de démarrage ferme ou lorsque le dernier formulaire.|**En mode arrêt** liste|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Vue d’ensemble du modèle d’Application Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [Page Application, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)
