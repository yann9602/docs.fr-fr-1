---
title: "Vue d&#39;ensemble de TextBlock | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles TextBlock"
  - "TextBlock (contrôle)"
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Vue d&#39;ensemble de TextBlock
Le <xref:System.Windows.Controls.TextBlock> contrôle prend en charge de texte flexible pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications. L’élément cible principalement basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénarios qui ne nécessitent pas plus d’un paragraphe de texte. Il prend en charge un nombre de propriétés qui permettent un contrôle précis de présentation, telles que <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, et <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Contenu de texte peut être ajouté à l’aide de la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété. Lorsqu’il est utilisé dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], contenu entre l’ouverture et la balise de fermeture est ajouté implicitement comme texte de l’élément.  
  
 A <xref:System.Windows.Controls.TextBlock> élément peut être instancié très simplement à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 De même, l’utilisation de la <xref:System.Windows.Controls.TextBlock> élément dans le code est relativement simple.  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Label>