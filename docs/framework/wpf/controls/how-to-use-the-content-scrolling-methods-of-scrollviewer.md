---
title: "Comment : utiliser les méthodes de défilement du contenu de ScrollViewer"
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
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5911d8e36b82aa44a1fdadfa60d422c894b4fc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="9a721-102">Comment : utiliser les méthodes de défilement du contenu de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="9a721-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="9a721-103">Cet exemple montre comment utiliser les méthodes de défilement de la <xref:System.Windows.Controls.ScrollViewer> élément.</span><span class="sxs-lookup"><span data-stu-id="9a721-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="9a721-104">Ces méthodes fournissent un défilement incrémentiel du contenu, par ligne ou par page, dans un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9a721-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a721-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a721-105">Example</span></span>  
 <span data-ttu-id="9a721-106">L’exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> nommé `sv1`, qui héberge un enfant <xref:System.Windows.Controls.TextBlock> élément.</span><span class="sxs-lookup"><span data-stu-id="9a721-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="9a721-107">Étant donné que la <xref:System.Windows.Controls.TextBlock> est plus grand que le parent <xref:System.Windows.Controls.ScrollViewer>, barres de défilement s’affichent pour permettre le défilement.</span><span class="sxs-lookup"><span data-stu-id="9a721-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="9a721-108"><xref:System.Windows.Controls.Button>les éléments qui représentent les différentes méthodes de défilement sont ancrés sur la gauche dans une fonction <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9a721-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9a721-109">Chaque <xref:System.Windows.Controls.Button> dans les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier appelle une méthode personnalisée associée qui contrôle le comportement de défilement dans <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9a721-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="9a721-110">L’exemple suivant utilise le <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> et <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="9a721-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9a721-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a721-111">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
