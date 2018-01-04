---
title: "Comment : utiliser un élément mis en cache comme pinceau"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f463c15855e267a4c246625a8d06e627852f48a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="131a4-102">Comment : utiliser un élément mis en cache comme pinceau</span><span class="sxs-lookup"><span data-stu-id="131a4-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="131a4-103">Utilisez la <xref:System.Windows.Media.BitmapCacheBrush> classe pour réutiliser efficacement un élément mis en cache.</span><span class="sxs-lookup"><span data-stu-id="131a4-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="131a4-104">Pour mettre en cache un élément, créer une nouvelle instance de la <xref:System.Windows.Media.BitmapCache> de classe et l’affecter à l’élément <xref:System.Windows.UIElement.CacheMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="131a4-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="131a4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="131a4-105">Example</span></span>  
 <span data-ttu-id="131a4-106">L’exemple de code suivant montre comment réutiliser un élément mis en cache.</span><span class="sxs-lookup"><span data-stu-id="131a4-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="131a4-107">L’élément mis en cache est un <xref:System.Windows.Controls.Image> contrôle qui affiche une grande image.</span><span class="sxs-lookup"><span data-stu-id="131a4-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="131a4-108">Le <xref:System.Windows.Controls.Image> contrôle est mis en cache sous forme de bitmap à l’aide de la <xref:System.Windows.Media.BitmapCache> classe et le cache est réutilisé en l’assignant à une <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="131a4-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="131a4-109">Le pinceau est assigné à l’arrière-plan de vingt-cinq boutons pour une réutilisation efficace.</span><span class="sxs-lookup"><span data-stu-id="131a4-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="131a4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="131a4-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="131a4-111">Guide pratique pour améliorer les performances de rendu en mettant en cache un élément</span><span class="sxs-lookup"><span data-stu-id="131a4-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
