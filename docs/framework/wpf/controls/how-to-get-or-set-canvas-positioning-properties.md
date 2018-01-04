---
title: "Comment : obtenir ou définir des propriétés de positionnement de la zone de dessin"
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
helpviewer_keywords: Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2b01657088c388ad09037716278dc0788de2abb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="f13aa-102">Comment : obtenir ou définir des propriétés de positionnement de la zone de dessin</span><span class="sxs-lookup"><span data-stu-id="f13aa-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="f13aa-103">Cet exemple montre comment utiliser les méthodes de positionnement de la <xref:System.Windows.Controls.Canvas> élément pour positionner le contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="f13aa-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="f13aa-104">Cet exemple utilise le contenu d’un <xref:System.Windows.Controls.ListBoxItem> pour représenter les valeurs de positionnement et convertit les valeurs en instances de <xref:System.Double>, qui est un argument requis pour le positionnement.</span><span class="sxs-lookup"><span data-stu-id="f13aa-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="f13aa-105">Les valeurs sont ensuite converties en chaînes et affichées sous forme de texte dans un <xref:System.Windows.Controls.TextBlock> élément à l’aide de la <xref:System.Windows.Controls.Canvas.GetLeft%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="f13aa-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f13aa-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f13aa-106">Example</span></span>  
 <span data-ttu-id="f13aa-107">L’exemple suivant crée un <xref:System.Windows.Controls.ListBox> élément qui possède onze sélectionnable <xref:System.Windows.Controls.ListBoxItem> éléments.</span><span class="sxs-lookup"><span data-stu-id="f13aa-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="f13aa-108">Le <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> les déclencheurs d’événements le `ChangeLeft` méthode personnalisée, qui le bloc de code suivant définit.</span><span class="sxs-lookup"><span data-stu-id="f13aa-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="f13aa-109">Chaque <xref:System.Windows.Controls.ListBoxItem> représente un <xref:System.Double> valeur, qui est un des arguments qui la <xref:System.Windows.Controls.Canvas.SetLeft%2A> méthode <xref:System.Windows.Controls.Canvas> accepte.</span><span class="sxs-lookup"><span data-stu-id="f13aa-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="f13aa-110">Pour pouvoir utiliser un <xref:System.Windows.Controls.ListBoxItem> pour représenter une instance de <xref:System.Double>, vous devez d’abord convertir le <xref:System.Windows.Controls.ListBoxItem> pour le type de données correct.</span><span class="sxs-lookup"><span data-stu-id="f13aa-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="f13aa-111">Lorsqu’un utilisateur modifie le <xref:System.Windows.Controls.ListBox> selection, il appelle la `ChangeLeft` méthode personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f13aa-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="f13aa-112">Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.LengthConverter> objet, qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.ListBoxItem> à une instance de <xref:System.Double> (Notez que cette valeur a déjà été convertie en un <xref:System.String> à l’aide de la <xref:System.Windows.Controls.Control.ToString%2A> méthode).</span><span class="sxs-lookup"><span data-stu-id="f13aa-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="f13aa-113">Cette valeur est ensuite transmise à la <xref:System.Windows.Controls.Canvas.SetLeft%2A> et <xref:System.Windows.Controls.Canvas.GetLeft%2A> méthodes de <xref:System.Windows.Controls.Canvas> afin de modifier la position de la `text1` objet.</span><span class="sxs-lookup"><span data-stu-id="f13aa-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f13aa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f13aa-114">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [<span data-ttu-id="f13aa-115">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="f13aa-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
