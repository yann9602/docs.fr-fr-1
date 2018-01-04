---
title: "Comment : modifier l'embout à la fin d'une ligne ou d'un segment"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d2cd55de403b766344749259068ccd313558f89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Comment : modifier l'embout à la fin d'une ligne ou d'un segment
Cet exemple montre comment modifier la forme au début ou à la fin d’open <xref:System.Windows.Shapes.Shape> élément. Pour modifier l’embout au début de l’open <xref:System.Windows.Shapes.Shape>, utilisez son <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriété. Pour modifier l’embout à la fin d’open <xref:System.Windows.Shapes.Shape>, utilisez son <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriété. Pour afficher les embouts de ligne disponibles, consultez le <xref:System.Windows.Media.PenLineCap> énumération.  
  
> [!NOTE]
>  Cette propriété affecte uniquement une forme ouverte, comme un <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>, ou open <xref:System.Windows.Shapes.Path> élément.  
  
 L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Polyline> éléments et utilise un autre ensemble de formes à la fin de chacun.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
