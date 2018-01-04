---
title: "Comment : contrôler le remplissage d'une forme composite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb7956ab70dc30c7d090b9616cc603df2dc0b4e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Comment : contrôler le remplissage d'une forme composite
Le <xref:System.Windows.Media.GeometryGroup.FillRule%2A> propriété d’un <xref:System.Windows.Media.GeometryGroup> ou un <xref:System.Windows.Media.PathGeometry>, spécifie une « règle » que la forme composite utilise pour déterminer si un point donné fait partie de la géométrie. Il existe deux valeurs possibles pour <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> et <xref:System.Windows.Media.FillRule.Nonzero>. Les sections suivantes décrivent comment utiliser ces deux règles.  
  
 **EvenOdd :** cette règle détermine si un point se trouve dans la région de remplissage en dessinant un rayon à partir de ce point vers l’infini dans n’importe quelle direction et en comptant le nombre de segments de tracé dans la forme donnée qui sont coupés par le rayon. Si ce nombre est impair, le point est à l’intérieur ; s’il est pair, le point est à l’extérieur.  
  
 Par exemple, le code XAML suivant crée une forme composite constituée d’une série d’anneaux concentriques (cible) avec une <xref:System.Windows.Media.GeometryGroup.FillRule%2A> la valeur <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 L’illustration suivante montre la forme créée dans l’exemple précédent.  
  
 ![Capture d'écran : propriété FillRule de EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Dans l’illustration ci-dessus, notez que le centre et le 3e anneau ne sont pas remplis. En effet, un rayon dessiné à partir de n’importe quel point dans un de ces deux anneaux traverse un nombre pair de segments. Voir l’illustration ci-dessous :  
  
 ![Diagramme : valeur de propriété FillRule de EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **NonZero :** cette règle détermine si un point se trouve dans la région de remplissage du tracé en dessinant un rayon à partir de ce point vers l’infini dans n’importe quelle direction, puis en examinant les emplacements où un segment de la forme coupe le rayon. En commençant à zéro, comptez un point chaque fois qu’un segment coupe le rayon de gauche à droite, et soustrayez un point chaque fois qu’un segment de tracé traverse le rayon de droite à gauche. Comptez ensuite le nombre d’intersections : si le résultat est égal à zéro, le point est à l’extérieur du tracé. Sinon, il est à l’intérieur.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 À l’aide de l’exemple ci-dessus, la valeur <xref:System.Windows.Media.FillRule.Nonzero> pour <xref:System.Windows.Media.GeometryGroup.FillRule%2A> permet ainsi de l’illustration suivante :  
  
 ![Capture d'écran : valeur FillRule de NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Comme vous pouvez le voir, tous les anneaux sont remplis. En effet, tous les segments s’étendent dans la même direction, ce qui signifie qu’un rayon dessiné à partir de n’importe quel point traversera un ou plusieurs segments et que la somme des intersections ne sera pas égale à zéro. Par exemple, dans l’illustration ci-dessous, les flèches rouges représentent la direction et les flèches blanches représentent un rayon arbitraire à partir d’un point situé dans l’anneau intérieur. En commençant par une valeur égale à zéro, pour chaque segment que le rayon traverse, une valeur de un est ajoutée car le segment traverse le rayon de gauche à droite.  
  
 ![Diagramme : valeur de propriété FillRule égale à NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Pour mieux illustrer le comportement de <xref:System.Windows.Media.FillRule.Nonzero> une forme plus complexe avec des segments en cours d’exécution dans différentes directions de règle est requise. Le code XAML suivant crée une forme semblable que l’exemple précédent, sauf qu’il est créé avec un <xref:System.Windows.Media.PathGeometry> plutôt qu’un <xref:System.Windows.Media.EllipseGeometry> cercles concentriques plutôt que ce qui crée quatre arcs concentriques complètement fermés.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 L’illustration suivante montre la forme créée dans l’exemple précédent.  
  
 ![Capture d'écran : valeur de propriété FillRule de NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Notez que le troisième arc partant du centre n’est pas rempli. L’illustration ci-dessous en explique les raisons. Dans l’illustration, les flèches rouges représentent la direction dans laquelle les segments sont dessinés. Les deux flèches blanches représentent deux rayons arbitraires qui partent d’un point dans la région « non remplie ». Comme le montre l’illustration, la somme des valeurs d’un rayon donné qui traverse les segments dans son tracé est égale à zéro. Comme indiqué ci-dessus, une somme égale à zéro signifie que le point ne fait pas partie de la géométrie (il ne fait pas partie du remplissage) tandis qu’une somme qui n’est *pas* égale à zéro, y compris une valeur négative, fait partie de la géométrie.  
  
 ![Diagramme : valeur de propriété FillRule de NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Remarque :** dans le cadre de <xref:System.Windows.Media.FillRule>, toutes les formes sont considérées comme fermées. S’il y a un écart dans un segment, dessinez une ligne imaginaire pour le fermer. Dans l’exemple ci-dessus, on observe existe de petits écarts au niveau des anneaux. On peut donc s’attendre à ce qu’un rayon qui traverse cet écart produise un résultat différent de celui d’un rayon qui s’étend dans une autre direction. Voici une illustration agrandie d’une de ces intervalles et la « segment imaginaire » (segment dessiné à des fins de l’application de la <xref:System.Windows.Media.FillRule>) qui le ferme.  
  
 ![Diagramme : pour FillRule, les segments sont toujours fermés](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Exemple  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
