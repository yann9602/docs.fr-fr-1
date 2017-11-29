---
title: "Comment : traduire un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 222aebe0ffe3d2bb1d84002a2ad94b0b92ede15b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="01488-102">Comment : traduire un élément</span><span class="sxs-lookup"><span data-stu-id="01488-102">How to: Translate an Element</span></span>
<span data-ttu-id="01488-103">Cet exemple montre comment traduire (déplacer) un élément en utilisant un <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="01488-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="01488-104">La <xref:System.Windows.Media.TranslateTransform> classe s’avère particulièrement utile pour déplacer des éléments à l’intérieur des panneaux qui ne prennent pas en charge le positionnement absolu.</span><span class="sxs-lookup"><span data-stu-id="01488-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="01488-105">Par exemple, en appliquant un <xref:System.Windows.Media.TranslateTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété d’un élément, vous pouvez déplacer un élément dans un <xref:System.Windows.Controls.StackPanel> ou <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="01488-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="01488-106">Utilisez le <xref:System.Windows.Media.TranslateTransform.X%2A> propriété de la <xref:System.Windows.Media.TranslateTransform> pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe des abscisses.</span><span class="sxs-lookup"><span data-stu-id="01488-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="01488-107">Utilisez le <xref:System.Windows.Media.TranslateTransform.Y%2A> propriété pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe des ordonnées.</span><span class="sxs-lookup"><span data-stu-id="01488-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="01488-108">Enfin, appliquez le <xref:System.Windows.Media.TranslateTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="01488-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="01488-109">L’exemple suivant utilise un <xref:System.Windows.Media.TranslateTransform> déplacer un élément 50 pixels vers les droite et de 50 pixels vers le bas.</span><span class="sxs-lookup"><span data-stu-id="01488-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01488-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="01488-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="01488-111">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="01488-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01488-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01488-112">See Also</span></span>  
 [<span data-ttu-id="01488-113">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="01488-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
