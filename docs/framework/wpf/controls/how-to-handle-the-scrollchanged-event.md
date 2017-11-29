---
title: "Comment : gérer l'événement ScrollChanged"
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
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b8a4f4831b8ed25eb900692e78b5e28bccb86a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-the-scrollchanged-event"></a><span data-ttu-id="a700e-102">Comment : gérer l'événement ScrollChanged</span><span class="sxs-lookup"><span data-stu-id="a700e-102">How to: Handle the ScrollChanged Event</span></span>
## <a name="example"></a><span data-ttu-id="a700e-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="a700e-103">Example</span></span>  
 <span data-ttu-id="a700e-104">Cet exemple montre comment gérer les <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> événements d’un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="a700e-104">This example shows how to handle the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event of a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 <span data-ttu-id="a700e-105">A <xref:System.Windows.Documents.FlowDocument> élément avec <xref:System.Windows.Documents.Paragraph> parties est défini dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a700e-105">A <xref:System.Windows.Documents.FlowDocument> element with <xref:System.Windows.Documents.Paragraph> parts is defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="a700e-106">Lorsque le <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> événement se produit en raison d’une intervention de l’utilisateur, un gestionnaire est appelé et le texte est écrit pour un <xref:System.Windows.Controls.TextBlock> indiquant que l’événement s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a700e-106">When the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event occurs due to user interaction, a handler is invoked, and text is written to a <xref:System.Windows.Controls.TextBlock> indicating that the event has occurred.</span></span>  
  
 [!code-xaml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a700e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a700e-107">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>  
 <xref:System.Windows.Controls.ScrollChangedEventHandler>  
 <xref:System.Windows.Controls.ScrollChangedEventArgs>
