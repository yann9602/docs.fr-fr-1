---
title: "Comment : animer la taille d'un FrameworkElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf31fa1a10748c3c2f6d239d041c72c57a148e1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="baf05-102">Comment : animer la taille d'un FrameworkElement</span><span class="sxs-lookup"><span data-stu-id="baf05-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="baf05-103">Pour animer la taille d’un <xref:System.Windows.FrameworkElement>, vous pouvez animer ses <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés ou utilisez un animé <xref:System.Windows.Media.ScaleTransform>.</span><span class="sxs-lookup"><span data-stu-id="baf05-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="baf05-104">Dans l’exemple suivant réalise une animation de la taille des deux boutons à l’aide de ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="baf05-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="baf05-105">Un bouton est redimensionné en animation son <xref:System.Windows.FrameworkElement.Width%2A> propriété et l’autre est redimensionnée par l’animation un <xref:System.Windows.Media.ScaleTransform> appliquée à ses <xref:System.Windows.UIElement.RenderTransform%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="baf05-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="baf05-106">Chaque bouton contient du texte.</span><span class="sxs-lookup"><span data-stu-id="baf05-106">Each button contains some text.</span></span> <span data-ttu-id="baf05-107">Initialement, le texte est le même dans les deux boutons, mais que les boutons sont redimensionnés, le texte dans le deuxième bouton est déformé.</span><span class="sxs-lookup"><span data-stu-id="baf05-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf05-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="baf05-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="baf05-109">Lorsque vous transformez un élément, l’élément tout entier et son contenu est transformés.</span><span class="sxs-lookup"><span data-stu-id="baf05-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="baf05-110">Lorsque vous modifiez directement la taille d’un élément, comme dans le cas du premier bouton, contenu de l’élément n’est pas redimensionné à moins que leur taille et la position dépendent de la taille de leur élément parent.</span><span class="sxs-lookup"><span data-stu-id="baf05-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="baf05-111">Animation de la taille d’un élément en appliquant une transformation animée à sa <xref:System.Windows.UIElement.RenderTransform%2A> propriété fournit de meilleures performances que sa <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> directement, car le <xref:System.Windows.UIElement.RenderTransform%2A> propriété ne déclenche pas une passe de disposition.</span><span class="sxs-lookup"><span data-stu-id="baf05-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="baf05-112">Pour plus d’informations sur les propriétés d’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="baf05-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="baf05-113">Pour plus d’informations sur les transformations, consultez la [transforme une vue d’ensemble](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="baf05-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
