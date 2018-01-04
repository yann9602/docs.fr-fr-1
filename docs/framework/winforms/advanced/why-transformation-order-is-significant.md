---
title: Importance de l'ordre des transformations
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
helpviewer_keywords: transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd3363a1afb8658ed3bb27359259cb752464507d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="why-transformation-order-is-significant"></a>Importance de l'ordre des transformations
Un seul <xref:System.Drawing.Drawing2D.Matrix> objet peut stocker une seule transformation ou une séquence de transformations. Celle-ci est appelée une transformation composite. La matrice d’une transformation composite est obtenue en multipliant les matrices des différentes transformations.  
  
## <a name="composite-transform-examples"></a>Exemples de transformations composites  
 Dans une transformation composite, l’ordre des différentes transformations est important. Par exemple, si vous tout d’abord faire pivoter, mettre à l’échelle, puis traduisez, vous obtenez un résultat différent que si vous convertissez tout d’abord, faire pivoter, puis mettre à l’échelle. Dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], transformations composites sont construites de gauche à droite. Si S, R et T sont respectivement des matrices de mise à l’échelle, de rotation et de traduction, puis le produit SRT (dans cet ordre) est la matrice de la transformation composite qui échelles en premier, puis fait pivoter, puis traduit. La matrice produite par le produit SRT est différente de la matrice produite par le produit TRS.  
  
 Un ordre est important parce que les transformations comme la rotation et de mise à l’échelle s’effectuent par rapport à l’origine du système de coordonnées. Mise à l’échelle d’un objet qui est centré à l’origine de produit le même résultat que la mise à l’échelle d’un objet qui a été déplacé en dehors de l’origine. De même, la rotation d’un objet qui est centré à l’origine produit le même résultat que la rotation d’un objet qui a été déplacé en dehors de l’origine.  
  
 L’exemple suivant combine une mise à l’échelle, de rotation et de translation (dans cet ordre) pour former une transformation composite. L’argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passé à la <xref:System.Drawing.Graphics.RotateTransform%2A> méthode indique que la rotation suivra la mise à l’échelle. De même, l’argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passé à la <xref:System.Drawing.Graphics.TranslateTransform%2A> méthode indique que la traduction suivra la rotation. <xref:System.Drawing.Drawing2D.MatrixOrder.Append>et <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> sont membres de la <xref:System.Drawing.Drawing2D.MatrixOrder> énumération.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 L’exemple suivant appelle la même méthode que dans l’exemple précédent, mais l’ordre des appels est inversé. L’ordre des opérations est tout d’abord traduire, faire pivoter, puis de l’échelle, ce qui produit un résultat très différent de la première échelle, puis de faire pivoter, puis traduire.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Permet d’inverser l’ordre des transformations individuelles dans une transformation composite est pour inverser l’ordre d’une séquence d’appels de méthode. Pour contrôler l’ordre des opérations, une seconde consiste à modifier l’argument de commande de matrice. L’exemple suivant est identique à l’exemple précédent, à ceci près que <xref:System.Drawing.Drawing2D.MatrixOrder.Append> a été remplacé par <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. La multiplication des matrices s’effectue dans l’ordre SRT, où S, R et T sont les matrices d’échelle, de rotation et traduire, respectivement. L’ordre de la transformation composite est la première échelle, faire pivoter, puis traduire.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Le résultat de l’exemple précédent est le même que le résultat du premier exemple dans cette rubrique. Il s’agit, car nous avons inversé l’ordre des appels de méthode et l’ordre de la multiplication de matrice.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Utilisation des transformations dans GDI+ managé](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
