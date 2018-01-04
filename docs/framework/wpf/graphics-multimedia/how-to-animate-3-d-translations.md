---
title: "Comment : animer des translations 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d49ad52906787eed9ab115adeb763b89b2ea38e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="00c86-102">Comment : animer des translations 3D</span><span class="sxs-lookup"><span data-stu-id="00c86-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="00c86-103">Cette rubrique montre comment animer une transformation de translation définie sur un [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modèle.</span><span class="sxs-lookup"><span data-stu-id="00c86-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="00c86-104">Le code ci-dessous montre l’application d’un <xref:System.Windows.Media.Media3D.TranslateTransform3D> de l’objet à la <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriété d’un <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="00c86-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="00c86-105">Le <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriété de ce <xref:System.Windows.Media.Media3D.TranslateTransform3D> objet s’anime à l’aide du code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="00c86-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="00c86-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="00c86-106">Example</span></span>  
 <span data-ttu-id="00c86-107">Le code suivant montre l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="00c86-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="00c86-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00c86-108">See Also</span></span>  
 [<span data-ttu-id="00c86-109">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="00c86-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="00c86-110">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="00c86-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="00c86-111">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="00c86-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="00c86-112">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="00c86-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
