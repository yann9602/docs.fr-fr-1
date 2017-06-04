---
title: "Comment&#160;: d&#233;finir les marges d&#39;&#233;l&#233;ments et de contr&#244;les | Microsoft Docs"
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
  - "Margin (propriété), définir"
  - "propriétés, Margin (propriété)"
  - "définir, Margin (propriété)"
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;finir les marges d&#39;&#233;l&#233;ments et de contr&#244;les
Cet exemple indique comment définir la propriété <xref:System.Windows.FrameworkElement.Margin%2A> en modifiant une valeur de propriété existante de la marge dans code\-behind.  La propriété <xref:System.Windows.FrameworkElement.Margin%2A> est une propriété de l'élément de base <xref:System.Windows.FrameworkElement> et divers contrôles et d'autres éléments en héritent donc.  
  
 Cet exemple est écrit dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], avec un fichier code\-behind auquel fait référence [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Le fichier code\-behind est affiché dans [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] et une version de [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)].  
  
## Exemple  
 [!code-xml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]