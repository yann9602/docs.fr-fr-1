---
title: "Comment : améliorer les performances de défilement d'un contrôle ListBox"
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
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 46a54c9ed1dff9796506df78d07d7506dfd29cbf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="2bdda-102">Comment : améliorer les performances de défilement d'un contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="2bdda-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="2bdda-103">Si un <xref:System.Windows.Controls.ListBox> contient de nombreux éléments, la réponse de l’interface utilisateur peut être lente lorsqu’un utilisateur fait défiler le <xref:System.Windows.Controls.ListBox> à l’aide de la roulette de la souris ou en faisant glisser le curseur d’une barre de défilement.</span><span class="sxs-lookup"><span data-stu-id="2bdda-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="2bdda-104">Vous pouvez améliorer les performances de la <xref:System.Windows.Controls.ListBox> lorsque l’utilisateur fait défiler en définissant le `VirtualizingStackPanel.VirtualizationMode` propriété attachée <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bdda-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bdda-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bdda-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="2bdda-106">Description</span><span class="sxs-lookup"><span data-stu-id="2bdda-106">Description</span></span>  
<span data-ttu-id="2bdda-107">L’exemple suivant crée un <xref:System.Windows.Controls.ListBox> et définit les `VirtualizingStackPanel.VirtualizationMode` propriété attachée <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> pour améliorer les performances pendant le défilement.</span><span class="sxs-lookup"><span data-stu-id="2bdda-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="2bdda-108">Code</span><span class="sxs-lookup"><span data-stu-id="2bdda-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="2bdda-109">L’exemple suivant montre les données que l’exemple précédent utilise.</span><span class="sxs-lookup"><span data-stu-id="2bdda-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
