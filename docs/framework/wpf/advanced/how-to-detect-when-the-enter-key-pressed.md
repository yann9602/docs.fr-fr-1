---
title: "Comment&#160;: effectuer une d&#233;tection en cas d&#39;appui sur la touche Entr&#233;e | Microsoft Docs"
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
  - "Entrée (touche), détecter"
  - "clés, Entrée"
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: effectuer une d&#233;tection en cas d&#39;appui sur la touche Entr&#233;e
Cet exemple montre comment détecter lorsque la touche <xref:System.Windows.Input.Key> est enfoncée sur le clavier.  
  
 Cet exemple comprend un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et un fichier code\-behind.  
  
## Exemple  
 Lorsque l'utilisateur appuie sur la touche <xref:System.Windows.Input.Key> dans la <xref:System.Windows.Controls.TextBox>, l'entrée contenue dans la zone de texte apparaît dans une autre zone de l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Le [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l'interface utilisateur, qui se compose d'un <xref:System.Windows.Controls.StackPanel>, d'un <xref:System.Windows.Controls.TextBlock> et d'une <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Le code\-behind suivant crée le gestionnaire d'événements <xref:System.Windows.UIElement.KeyDown>.  Si la touche enfoncée est la touche <xref:System.Windows.Input.Key>, un message s'affiche dans le <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## Voir aussi  
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)