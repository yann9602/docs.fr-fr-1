---
title: "Comment : énumérer le contenu de dessin d'un Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c97926286076149a6eedf34bb70bbc76b2e0d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="9026c-102">Comment : énumérer le contenu de dessin d'un Visual</span><span class="sxs-lookup"><span data-stu-id="9026c-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="9026c-103">Le <xref:System.Windows.Media.Drawing> objet fournissent un modèle d’objet pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="9026c-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9026c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9026c-104">Example</span></span>  
 <span data-ttu-id="9026c-105">L’exemple suivant utilise le <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> pour récupérer le <xref:System.Windows.Media.DrawingGroup> valeur d’un <xref:System.Windows.Media.Visual> et énumérer.</span><span class="sxs-lookup"><span data-stu-id="9026c-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9026c-106">Lorsque vous énumérez le contenu de l’élément visuel, vous récupérez <xref:System.Windows.Media.Drawing> objets et pas la représentation sous-jacente des données rendues comme liste d’instructions graphiques vectorielles.</span><span class="sxs-lookup"><span data-stu-id="9026c-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="9026c-107">Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9026c-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="9026c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9026c-108">See Also</span></span>  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="9026c-109">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="9026c-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="9026c-110">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="9026c-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
