---
title: "Comment : utiliser un MatrixTransform pour créer des transformations personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1414ae590be10c3adcc6857492e23bf659beec67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="90a5a-102">Comment : utiliser un MatrixTransform pour créer des transformations personnalisées</span><span class="sxs-lookup"><span data-stu-id="90a5a-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="90a5a-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.MatrixTransform> pour traduire (déplacer) la position, stretch et l’inclinaison d’un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="90a5a-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90a5a-104">Utilisez le <xref:System.Windows.Media.MatrixTransform> classe pour créer des transformations personnalisées qui ne sont pas fournies par le <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> classes.</span><span class="sxs-lookup"><span data-stu-id="90a5a-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90a5a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="90a5a-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="90a5a-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90a5a-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="90a5a-107">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="90a5a-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="90a5a-108">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="90a5a-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="90a5a-109">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="90a5a-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
