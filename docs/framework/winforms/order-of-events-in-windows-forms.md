---
title: "Ordre des &#233;v&#233;nements dans les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ordre des événements d'arrêt de l'application"
  - "ordre des événements de démarrage de l'application"
  - "événements (Windows Forms), ordre de"
  - "ordre des événements de focus"
  - "séquence, des événements"
  - "événements de validation, ordre de"
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Ordre des &#233;v&#233;nements dans les Windows Forms
L'ordre dans lequel les événements sont déclenchés dans les applications Windows Forms est particulièrement intéressant pour les développeurs soucieux de gérer chacun de ces événements tour à tour.  Quand une situation nécessite une gestion méticuleuse des événements, par exemple quand vous redessinez certaines parties du formulaire, une connaissance de l'ordre exact dans lequel les événements sont déclenchés au moment de l'exécution est nécessaire.  Cette rubrique fournit des détails sur l'ordre des événements durant plusieurs phases importantes de la durée de vie des applications et des contrôles.  Pour obtenir des détails spécifiques sur l'ordre des événements d'entrée de souris, consultez [Événements liés à la souris dans les Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  Pour obtenir une vue d'ensemble des événements dans les Windows Forms, consultez [Vue d'ensemble des événements](../../../docs/framework/winforms/events-overview-windows-forms.md).  Pour plus d'informations sur la composition des gestionnaires d'événements, consultez [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
## Événements de démarrage et d'arrêt des applications  
 Les classes <xref:System.Windows.Forms.Form> et <xref:System.Windows.Forms.Control> exposent un ensemble d'événements liés au démarrage et à l'arrêt de l'application.  Lors du démarrage d'une application Windows Forms, les événements de démarrage du formulaire principal sont déclenchés dans l'ordre suivant :  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=fullName>  
  
 Lors de la fermeture d'une application, les événements d'arrêt du formulaire principal sont déclenchés dans l'ordre suivant :  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=fullName>  
  
 L'événement <xref:System.Windows.Forms.Application.ApplicationExit> de la classe <xref:System.Windows.Forms.Application> est déclenché après les événements d'arrêt du formulaire principal.  
  
> [!NOTE]
>  Visual Basic 2005 fournit des événements d'application supplémentaires, tels que <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=fullName> et <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=fullName>.  
  
## Événements de focus et de validation  
 Quand vous modifiez le focus à l'aide du clavier \(Tab, Maj\+Tab, etc.\) en appelant la méthode <xref:System.Windows.Forms.Control.Select%2A> ou <xref:System.Windows.Forms.Control.SelectNextControl%2A> ou en affectant le formulaire actuel comme valeur de la propriété <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 Quand vous modifiez le focus à l'aide de la souris ou en appelant la méthode <xref:System.Windows.Forms.Control.Focus%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)