---
title: "Comment : incliner un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="b8739-102">Comment : incliner un élément</span><span class="sxs-lookup"><span data-stu-id="b8739-102">How to: Skew an Element</span></span>
<span data-ttu-id="b8739-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.SkewTransform> pour incliner un élément.</span><span class="sxs-lookup"><span data-stu-id="b8739-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="b8739-104">Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme.</span><span class="sxs-lookup"><span data-stu-id="b8739-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="b8739-105">Une utilisation typique d’un <xref:System.Windows.Media.SkewTransform> est la simulation [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] profondeur dans [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="b8739-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="b8739-106">Utilisez le <xref:System.Windows.Media.SkewTransform.CenterX%2A> et <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriétés pour spécifier le centre du point de la <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="b8739-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="b8739-107">Utilisez le <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriétés pour spécifier l’angle d’inclinaison de l’axe des abscisses et l’axe des y et pour incliner le système de coordonnées actuel le long de ces axes.</span><span class="sxs-lookup"><span data-stu-id="b8739-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="b8739-108">Pour prévoir l’effet d’une transformation d’inclinaison, tenez compte des points <xref:System.Windows.Media.SkewTransform.AngleX%2A> inclinaisons de valeurs de l’axe x par rapport au repère d’origine.</span><span class="sxs-lookup"><span data-stu-id="b8739-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="b8739-109">Par conséquent, pour un <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, l’axe y pivote de 30 degrés via l’origine et inclinaisons les valeurs x-de 30 degrés à partir de cette origine.</span><span class="sxs-lookup"><span data-stu-id="b8739-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="b8739-110">De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 inclinaisons de valeurs y de la forme de 30 degrés à partir de l’origine.</span><span class="sxs-lookup"><span data-stu-id="b8739-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="b8739-111">Notez que l’effet produit est différent de celui obtenu lorsque l’on déplace le système de coordonnées de 30 degrés sur l’axe des x ou l’axe des y.</span><span class="sxs-lookup"><span data-stu-id="b8739-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="b8739-112">L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="b8739-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8739-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8739-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="b8739-114">L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central (25,25).</span><span class="sxs-lookup"><span data-stu-id="b8739-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="b8739-115">L’exemple suivant applique une inclinaison verticale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central (25,25).</span><span class="sxs-lookup"><span data-stu-id="b8739-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="b8739-116">L’illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b8739-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="b8739-117">![Exemples de SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="b8739-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="b8739-118">Les trois exemples SkewTransform illustrés</span><span class="sxs-lookup"><span data-stu-id="b8739-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="b8739-119">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="b8739-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8739-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8739-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="b8739-121">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="b8739-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="b8739-122">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="b8739-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
