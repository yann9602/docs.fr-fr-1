---
title: "Comment : ajouter du texte à un Visual"
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
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 735a84a034587b1433403a45edc7c2f459340273
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="32425-102">Comment : ajouter du texte à un Visual</span><span class="sxs-lookup"><span data-stu-id="32425-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="32425-103">L’exemple suivant montre comment dessiner du texte à un <xref:System.Windows.Media.DrawingVisual> à l’aide un <xref:System.Windows.Media.DrawingContext> objet.</span><span class="sxs-lookup"><span data-stu-id="32425-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="32425-104">Un contexte de dessin est retourné en appelant le <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> méthode d’un <xref:System.Windows.Media.DrawingVisual> objet.</span><span class="sxs-lookup"><span data-stu-id="32425-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="32425-105">Vous pouvez dessiner des graphiques et du texte dans un contexte de dessin.</span><span class="sxs-lookup"><span data-stu-id="32425-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="32425-106">Pour dessiner le texte dans le contexte de dessin, utilisez la <xref:System.Windows.Media.DrawingContext.DrawText%2A> méthode d’un <xref:System.Windows.Media.DrawingContext> objet.</span><span class="sxs-lookup"><span data-stu-id="32425-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="32425-107">Lorsque vous avez terminé de dessiner le contenu dans le contexte de dessin, appelez le <xref:System.Windows.Media.DrawingContext.Close%2A> méthode pour fermer le contexte de dessin et de conserver le contenu.</span><span class="sxs-lookup"><span data-stu-id="32425-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32425-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="32425-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="32425-109">Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994) (Test de positionnement à l’aide d’exemples de DrawingVisuals).</span><span class="sxs-lookup"><span data-stu-id="32425-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
