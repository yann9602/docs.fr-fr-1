---
title: "Comment : transformer l'échelle d'un modèle 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f650d968ca715e47269e0765d791856b681237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="0e2e5-102">Comment : transformer l'échelle d'un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="0e2e5-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="0e2e5-103">Cet exemple montre comment mettre à l’échelle un objet 3D.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="0e2e5-104">Pour mettre à l’échelle un objet 3D, vous devez utiliser un <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="0e2e5-105">Le <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, et <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> propriétés redimensionnent l’élément selon le facteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="0e2e5-106">Par exemple, un <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> valeur de 1.5 étire un objet à 150 % de sa largeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="0e2e5-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valeur de 0.5 réduit la hauteur d’un objet de 50 pour cent.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="0e2e5-108">Le code ci-dessous montre comment utiliser un <xref:System.Windows.Media.Media3D.ScaleTransform3D> en tant que la transformation pour un <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="0e2e5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e2e5-109">Example</span></span>  
 <span data-ttu-id="0e2e5-110">Le code suivant montre l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="0e2e5-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0e2e5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e2e5-111">See Also</span></span>  
 [<span data-ttu-id="0e2e5-112">Animer des translations 3D</span><span class="sxs-lookup"><span data-stu-id="0e2e5-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [<span data-ttu-id="0e2e5-113">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="0e2e5-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="0e2e5-114">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="0e2e5-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
