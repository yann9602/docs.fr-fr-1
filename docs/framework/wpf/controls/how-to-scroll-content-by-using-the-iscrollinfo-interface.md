---
title: "Comment : faire défiler le contenu à l'aide de l'interface IScrollInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae6d9439ad76258105d615960bd05ecf458eb613
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Comment : faire défiler le contenu à l'aide de l'interface IScrollInfo
Cet exemple montre comment faire défiler le contenu à l’aide de la <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les fonctionnalités de la <xref:System.Windows.Controls.Primitives.IScrollInfo> interface. L’exemple crée un <xref:System.Windows.Controls.StackPanel> élément [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui est imbriqué dans un parent <xref:System.Windows.Controls.ScrollViewer>. Les éléments enfants de la <xref:System.Windows.Controls.StackPanel> peut défiler logiquement à l’aide des méthodes définies par le <xref:System.Windows.Controls.Primitives.IScrollInfo> interface et le cast de l’instance de <xref:System.Windows.Controls.StackPanel> (`sp1`) dans le code.  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Chaque <xref:System.Windows.Controls.Button> dans les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier déclenche une méthode personnalisée associée qui contrôle le comportement de défilement dans <xref:System.Windows.Controls.StackPanel>. L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> méthodes ; il indique également générique comment utiliser toutes les méthodes de positionnement qui la <xref:System.Windows.Controls.Primitives.IScrollInfo> classe définit.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [Vue d’ensemble de ScrollViewer](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)
