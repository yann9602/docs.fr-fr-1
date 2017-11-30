---
title: "Comment : modifier la couleur d'un élément à l'aide d'événements Focus"
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
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64b1b788ddebe77704a7d34f31ad82b10da34a5a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="18e11-102">Comment : modifier la couleur d'un élément à l'aide d'événements Focus</span><span class="sxs-lookup"><span data-stu-id="18e11-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="18e11-103">Cet exemple montre comment modifier la couleur d’un élément lorsqu’il obtient et perd le focus à l’aide de la <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> les événements.</span><span class="sxs-lookup"><span data-stu-id="18e11-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="18e11-104">Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="18e11-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e11-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="18e11-105">Example</span></span>  
 <span data-ttu-id="18e11-106">Les éléments suivants [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] crée l’interface utilisateur, qui se compose de deux <xref:System.Windows.Controls.Button> objets et joint les gestionnaires d’événements pour le <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> événements à la <xref:System.Windows.Controls.Button> objets.</span><span class="sxs-lookup"><span data-stu-id="18e11-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="18e11-107">Le code-behind suivant crée le <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="18e11-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="18e11-108">Lorsque le <xref:System.Windows.Controls.Button> gains le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> de la <xref:System.Windows.Controls.Button> est modifié en rouge.</span><span class="sxs-lookup"><span data-stu-id="18e11-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="18e11-109">Lorsque le <xref:System.Windows.Controls.Button> perd le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> de la <xref:System.Windows.Controls.Button> repasse au blanc.</span><span class="sxs-lookup"><span data-stu-id="18e11-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="18e11-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18e11-110">See Also</span></span>  
 [<span data-ttu-id="18e11-111">Vue d’ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="18e11-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
