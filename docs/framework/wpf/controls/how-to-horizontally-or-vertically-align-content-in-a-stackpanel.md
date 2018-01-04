---
title: "Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel"
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
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad3252b249c716d59b72a6c5af7bd96f2d058126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="a0786-102">Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel</span><span class="sxs-lookup"><span data-stu-id="a0786-102">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="a0786-103">Cet exemple montre comment ajuster le <xref:System.Windows.Controls.StackPanel.Orientation%2A> du contenu dans un <xref:System.Windows.Controls.StackPanel> élément et comment ajuster le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> du contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="a0786-103">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0786-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0786-104">Example</span></span>  
 <span data-ttu-id="a0786-105">L’exemple suivant crée trois <xref:System.Windows.Controls.ListBox> éléments [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0786-105">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="a0786-106">Chaque <xref:System.Windows.Controls.ListBox> représente les valeurs possibles de la <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriétés d’un <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="a0786-106">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="a0786-107">Lorsqu’un utilisateur sélectionne une valeur dans un de la <xref:System.Windows.Controls.ListBox> éléments, la propriété associée de la <xref:System.Windows.Controls.StackPanel> et de ses enfants <xref:System.Windows.Controls.Button> modifier des éléments.</span><span class="sxs-lookup"><span data-stu-id="a0786-107">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a0786-108">Le fichier code-behind suivant définit les modifications apportées aux événements qui sont associés les <xref:System.Windows.Controls.ListBox> sélection change.</span><span class="sxs-lookup"><span data-stu-id="a0786-108">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="a0786-109"><xref:System.Windows.Controls.StackPanel>est identifié par le <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span><span class="sxs-lookup"><span data-stu-id="a0786-109"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a0786-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0786-110">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [<span data-ttu-id="a0786-111">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="a0786-111">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
