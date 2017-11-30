---
title: "Comment : utiliser des déclencheurs pour appliquer un style aux éléments sélectionnés d'un ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e86c7f875376a4ab28eec7cd032a165745445441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="a6c5e-102">Comment : utiliser des déclencheurs pour appliquer un style aux éléments sélectionnés d'un ListView</span><span class="sxs-lookup"><span data-stu-id="a6c5e-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="a6c5e-103">Cet exemple montre comment définir <xref:System.Windows.Style.Triggers%2A> pour un <xref:System.Windows.Controls.ListViewItem> contrôle afin que lorsqu’une valeur de propriété d’un <xref:System.Windows.Controls.ListViewItem> modifications, la <xref:System.Windows.Style> de la <xref:System.Windows.Controls.ListViewItem> change en réponse.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6c5e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6c5e-104">Example</span></span>  
 <span data-ttu-id="a6c5e-105">Si vous souhaitez que le <xref:System.Windows.Style> d’un <xref:System.Windows.Controls.ListViewItem> pour modifier en réponse aux modifications de propriété, définissez <xref:System.Windows.Style.Triggers%2A> pour la <xref:System.Windows.Style> modifier.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="a6c5e-106">L’exemple suivant définit un <xref:System.Windows.Trigger> qui définit le <xref:System.Windows.Controls.Control.Foreground%2A> propriété <xref:System.Windows.Media.Brushes.Blue%2A> et modifie le <xref:System.Windows.FrameworkElement.Cursor%2A> pour afficher un <xref:System.Windows.Input.CursorType.Hand> lors de la la <xref:System.Windows.UIElement.IsMouseOver%2A> modifications apportées aux propriétés `true`.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="a6c5e-107">L’exemple suivant définit un <xref:System.Windows.MultiTrigger> qui définit le <xref:System.Windows.Controls.Control.Foreground%2A> propriété d’un <xref:System.Windows.Controls.ListViewItem> à <xref:System.Windows.Media.Brushes.Yellow%2A> lorsque le <xref:System.Windows.Controls.ListViewItem> est l’élément sélectionné et a le focus clavier.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="a6c5e-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6c5e-108">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="a6c5e-109">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a6c5e-109">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="a6c5e-110">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="a6c5e-110">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="a6c5e-111">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="a6c5e-111">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
