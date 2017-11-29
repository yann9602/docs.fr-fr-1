---
title: "Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d1b22babcc653f999ff500a5e52a12616fc1ae4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="0e849-102">Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles</span><span class="sxs-lookup"><span data-stu-id="0e849-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="0e849-103">La double mise en mémoire tampon utilise une mémoire tampon pour résoudre les problèmes de scintillement associés aux opérations de dessin multiples.</span><span class="sxs-lookup"><span data-stu-id="0e849-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="0e849-104">Quand la double mise en mémoire tampon est activée, toutes les opérations de dessin sont d’abord rendues dans une mémoire tampon au lieu de l’être sur la surface de dessin à l’écran.</span><span class="sxs-lookup"><span data-stu-id="0e849-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="0e849-105">Une fois que toutes les opérations de dessin sont terminées, la mémoire tampon est copiée directement sur la surface de dessin qui y est associée.</span><span class="sxs-lookup"><span data-stu-id="0e849-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="0e849-106">Les graphiques qu’une seule opération sur l’écran, le scintillement d’image associé aux opérations de peinture complexes est éliminé. Pour la plupart des applications, le double tampon par défaut fourni par le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournissent les meilleurs résultats.</span><span class="sxs-lookup"><span data-stu-id="0e849-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="0e849-107">Contrôles Windows Forms standard sont doubles tampon par défaut.</span><span class="sxs-lookup"><span data-stu-id="0e849-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="0e849-108">Vous pouvez activer la double mise en mémoire tampon dans les formulaires par défaut et créé des contrôles de deux manières.</span><span class="sxs-lookup"><span data-stu-id="0e849-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="0e849-109">Vous pouvez soit définir la <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriété `true`, ou vous pouvez appeler la <xref:System.Windows.Forms.Control.SetStyle%2A> pour définir le <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true`.</span><span class="sxs-lookup"><span data-stu-id="0e849-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="0e849-110">Les deux méthodes Active double tampon par défaut pour votre formulaire ou contrôle et fournir un rendu graphique sans scintillement.</span><span class="sxs-lookup"><span data-stu-id="0e849-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="0e849-111">Appel de la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode est recommandée uniquement pour les contrôles personnalisés pour lequel vous avez écrit tout le code de rendu.</span><span class="sxs-lookup"><span data-stu-id="0e849-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="0e849-112">Pour les scénarios doubles mise en mémoire tampon plus avancés, tels que l’animation ou la gestion de mémoire avancée, vous pouvez implémenter votre propre logique de mise en mémoire tampon double.</span><span class="sxs-lookup"><span data-stu-id="0e849-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="0e849-113">Pour plus d’informations, consultez [Comment : gérer manuellement mis en mémoire tampon des graphiques](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="0e849-113">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="0e849-114">Pour réduire le scintillement</span><span class="sxs-lookup"><span data-stu-id="0e849-114">To reduce flicker</span></span>  
  
-   <span data-ttu-id="0e849-115">Affectez à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0e849-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="0e849-116">\- ou -</span><span class="sxs-lookup"><span data-stu-id="0e849-116">\- or -</span></span>  
  
-   <span data-ttu-id="0e849-117">Appelez le <xref:System.Windows.Forms.Control.SetStyle%2A> pour définir le <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true`.</span><span class="sxs-lookup"><span data-stu-id="0e849-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="0e849-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e849-118">See Also</span></span>  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [<span data-ttu-id="0e849-119">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="0e849-119">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="0e849-120">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e849-120">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
