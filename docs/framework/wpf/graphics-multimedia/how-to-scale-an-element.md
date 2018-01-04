---
title: "Comment : mettre à l'échelle un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2bff810dc9b44b25db93c8565da27acc4f0ccc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="9abd3-102">Comment : mettre à l'échelle un élément</span><span class="sxs-lookup"><span data-stu-id="9abd3-102">How to: Scale an Element</span></span>
<span data-ttu-id="9abd3-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.ScaleTransform> à l’échelle d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9abd3-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="9abd3-104">Utilisez le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés pour redimensionner l’élément selon le facteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="9abd3-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="9abd3-105">Par exemple, un <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> valeur de 1.5 étire l’élément à 150 % de sa largeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="9abd3-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="9abd3-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> la valeur 0,5 diminue la hauteur d’un élément de 50 %.</span><span class="sxs-lookup"><span data-stu-id="9abd3-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="9abd3-107">Utilisez le <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A> propriétés pour spécifier le point qui est le centre de l’opération de mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="9abd3-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="9abd3-108">Par défaut, un <xref:System.Windows.Media.ScaleTransform> est centré au point (0,0), qui correspond à l’angle supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="9abd3-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="9abd3-109">Cela a pour effet de déplacement de l’élément et également de paraît plus grand, car lorsque vous appliquez un <xref:System.Windows.Media.Transform>, vous modifiez l’espace de coordonnées dans lequel réside l’objet.</span><span class="sxs-lookup"><span data-stu-id="9abd3-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="9abd3-110">L’exemple suivant utilise un <xref:System.Windows.Media.ScaleTransform> pour doubler la taille de 50 x 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="9abd3-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="9abd3-111">Le <xref:System.Windows.Media.ScaleTransform> a la valeur 0 (valeur par défaut) pour les deux <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="9abd3-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9abd3-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9abd3-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="9abd3-113">En général, vous affectez <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A> au centre de l’objet qui est à l’échelle : (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="9abd3-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="9abd3-114">L’exemple suivant montre une autre <xref:System.Windows.Shapes.Rectangle> qui est doublée taille ; Toutefois, cela <xref:System.Windows.Media.ScaleTransform> a une valeur de 25 pour <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, qui correspond au centre du rectangle.</span><span class="sxs-lookup"><span data-stu-id="9abd3-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="9abd3-115">L’illustration suivante montre la différence entre les deux <xref:System.Windows.Media.ScaleTransform> operations.</span><span class="sxs-lookup"><span data-stu-id="9abd3-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="9abd3-116">La ligne en pointillés affiche la taille et la position du rectangle avant la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="9abd3-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="9abd3-117">![échelles de 2 x avec différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="9abd3-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="9abd3-118">Deux opérations ScaleTransform avec des valeurs ScaleX et ScaleY identiques, mais des centres différents</span><span class="sxs-lookup"><span data-stu-id="9abd3-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="9abd3-119">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="9abd3-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9abd3-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="9abd3-121">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="9abd3-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="9abd3-122">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="9abd3-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
