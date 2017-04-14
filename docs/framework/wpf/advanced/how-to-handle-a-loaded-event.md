---
title: "Comment&#160;: g&#233;rer un &#233;v&#233;nement charg&#233; | Microsoft Docs"
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
  - "événements, Chargé"
  - "événements Loaded"
  - "XAML, événements Loaded"
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: g&#233;rer un &#233;v&#233;nement charg&#233;
Cet exemple indique comment gérer l'événement <xref:System.Windows.FrameworkElement.Loaded?displayProperty=fullName> et fournit un scénario approprié pour gérer cet événement.  Le gestionnaire crée un <xref:System.Windows.Controls.Button> lors du chargement de la page.  
  
## Exemple  
 L'exemple suivant utilise le langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] avec un fichier code\-behind.  
  
 [!code-xml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement>   
 [Événements de la durée de vie d'un objet](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)