---
title: "Comment&#160;: ajouter la gestion de classe d&#39;un &#233;v&#233;nement rout&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestionnaires de classes, événements routés"
  - "événements routés, gestionnaires de classes"
  - "task_core_add_class_handling_routed_event"
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: ajouter la gestion de classe d&#39;un &#233;v&#233;nement rout&#233;
Les événements routés peuvent être gérés par des gestionnaires de classes ou d'instances sur un nœud donné de l'itinéraire.  Les gestionnaires de classes sont appelés en premier et peuvent être utilisés par des implémentations de classe pour supprimer des événements de la gestion d'instances ou pour introduire d'autres comportements spécifiques des événements dans les événements détenus par les classes de base.  Cet exemple illustre deux techniques étroitement liées permettant d'implémenter des gestionnaires de classes.  
  
## Exemple  
 Cet exemple utilise une classe personnalisée basée sur le panneau <xref:System.Windows.Controls.Canvas>.  Le principe de base de l'application est que la classe personnalisée introduit des comportements sur ses éléments enfants, notamment l'interception des clics sur le bouton gauche de la souris et leur marquage comme gérés, avant d'appeler la classe d'élément enfant ou un gestionnaire d'instances correspondant.  
  
 La classe <xref:System.Windows.UIElement> expose une méthode virtuelle qui permet la gestion de classe de l'événement <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>, par simple substitution de l'événement.  Il s'agit de la méthode la plus simple pour implémenter la gestion de classe si cette méthode virtuelle est disponible dans la hiérarchie de la classe.  Le code suivant affiche l'implémentation de <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> dans le "MyEditContainer" dérivé de <xref:System.Windows.Controls.Canvas>.  L'implémentation marque l'événement comme géré dans les arguments, puis ajoute du code pour fournir une modification visible de base à l'élément source.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Si aucun élément virtuel n'est disponible dans les classes de base ou pour cette méthode particulière, la gestion de classe peut être directement ajoutée à l'aide d'une méthode utilitaire de la classe <xref:System.Windows.EventManager>, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.  Cette méthode doit être appelée uniquement dans l'initialisation statique des classes qui ajoutent la gestion de classe.  Cet exemple ajoute un autre gestionnaire pour <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> ; dans ce cas, la classe inscrite correspond à la classe personnalisée.  Par opposition, en cas d'utilisation d'éléments virtuels, la classe inscrite correspond réellement à la classe de base <xref:System.Windows.UIElement>.  Si les classes de base et les sous\-classes inscrivent la gestion de classe, les gestionnaires de sous\-classes sont appelés en premier lieu.  D'après le comportement d'une application, ce gestionnaire affiche d'abord sa boîte de message puis la modification visuelle s'affiche dans le gestionnaire de la méthode virtuelle.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## Voir aussi  
 <xref:System.Windows.EventManager>   
 [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [Gérer un événement routé](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)