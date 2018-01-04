---
title: "Comment : tester l'égalité et l'inégalité de structures Point4D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac69ec232485ebd3097f2db3b31d3fd43d0ccc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="6b567-102">Comment : tester l'égalité et l'inégalité de structures Point4D</span><span class="sxs-lookup"><span data-stu-id="6b567-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="6b567-103">Cet exemple montre comment tester <xref:System.Windows.Media.Media3D.Point4D> structures pour l’égalité et d’inégalité.</span><span class="sxs-lookup"><span data-stu-id="6b567-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="6b567-104">Le code suivant illustre comment tester <xref:System.Windows.Media.Media3D.Point4D> l’égalité et d’inégalité à l’aide de structures le <xref:System.Windows.Media.Media3D.Point4D> méthodes d’égalité.</span><span class="sxs-lookup"><span data-stu-id="6b567-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="6b567-105">Le <xref:System.Windows.Media.Media3D.Point4D> structures sont testées pour l’égalité à l’aide de l’égalité surchargée (`==`) (opérateur), puis d’inégalité à l’aide de l’inégalité surchargée (`!=`) (opérateur) et enfin une <xref:System.Windows.Media.Media3D.Point3D> structure et un <xref:System.Windows.Media.Media3D.Point4D> structure sont vérifiées pour l’égalité à l’aide de la méthode statique <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6b567-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b567-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b567-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="6b567-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b567-107">See Also</span></span>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
