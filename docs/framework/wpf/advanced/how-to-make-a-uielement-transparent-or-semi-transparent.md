---
title: "Comment : rendre un UIElement transparent ou semi-transparent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25245319c02ae376410d71afb7a1e56eda259e99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="9468b-102">Comment : rendre un UIElement transparent ou semi-transparent</span><span class="sxs-lookup"><span data-stu-id="9468b-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="9468b-103">Cet exemple montre comment rendre un <xref:System.Windows.UIElement> transparent ou semi-transparent.</span><span class="sxs-lookup"><span data-stu-id="9468b-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="9468b-104">Pour rendre un élément transparent ou semi-transparent, vous définissez son <xref:System.Windows.UIElement.Opacity%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9468b-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="9468b-105">La valeur `0.0` rend l’élément complètement transparent, alors que la valeur `1.0` rend l’élément complètement opaque.</span><span class="sxs-lookup"><span data-stu-id="9468b-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="9468b-106">La valeur `0.5` rend les 50 % de l’élément opaque et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="9468b-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="9468b-107">D’un élément <xref:System.Windows.UIElement.Opacity%2A> a la valeur `1.0` par défaut.</span><span class="sxs-lookup"><span data-stu-id="9468b-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9468b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9468b-108">Example</span></span>  
 <span data-ttu-id="9468b-109">L’exemple suivant définit la <xref:System.Windows.UIElement.Opacity%2A> d’un bouton `0.25`, sorte que celui-ci et son contenu (dans ce cas, le texte du bouton) sont opaques à 25 %.</span><span class="sxs-lookup"><span data-stu-id="9468b-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="9468b-110">Si le contenu d’un élément ont leurs propres <xref:System.Windows.UIElement.Opacity%2A> paramètres, ces valeurs sont multipliées par les éléments contenant <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9468b-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="9468b-111">L’exemple suivant définit un bouton <xref:System.Windows.UIElement.Opacity%2A> à `0.25`et le <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Controls.Image> contrôle contenu dans le bouton pour `0.5`.</span><span class="sxs-lookup"><span data-stu-id="9468b-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="9468b-112">Par conséquent, l’image apparaît 12,5 % opaque : 0,25 * 0,5 = 0,125.</span><span class="sxs-lookup"><span data-stu-id="9468b-112">As a result, the image appears 12.5% opaque: 0.25 * 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="9468b-113">Une autre façon de contrôler l’opacité d’un élément consiste à définir l’opacité de la <xref:System.Windows.Media.Brush> qui peint l’élément.</span><span class="sxs-lookup"><span data-stu-id="9468b-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="9468b-114">Cette approche vous permet de modifier de manière sélective l’opacité de certaines parties d’un élément et offre des avantages de performances principal à l’aide de l’élément <xref:System.Windows.UIElement.Opacity%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9468b-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="9468b-115">L’exemple suivant définit la <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre du bouton <xref:System.Windows.Controls.Control.Background%2A> a la valeur `0.25`.</span><span class="sxs-lookup"><span data-stu-id="9468b-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="9468b-116">Par conséquent, l’arrière-plan du pinceau est opaque à 25 %, mais son contenu (le texte du bouton) reste opaque à 100 %.</span><span class="sxs-lookup"><span data-stu-id="9468b-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="9468b-117">Vous pouvez également contrôler l’opacité des couleurs individuelles au sein d’un pinceau.</span><span class="sxs-lookup"><span data-stu-id="9468b-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="9468b-118">Pour plus d’informations sur les couleurs et les pinceaux, consultez [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9468b-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="9468b-119">Pour obtenir un exemple montrant comment animer l’opacité d’un élément, consultez [animer l’opacité d’un élément ou un pinceau](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="9468b-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
