---
title: "Comment : créer un dégradé linéaire"
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
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a>Comment : créer un dégradé linéaire
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit des dégradés linéaires horizontales, verticales et diagonales. Par défaut, la couleur d’un dégradé linéaire varie de façon régulière. Toutefois, vous pouvez personnaliser un dégradé linéaire afin que la couleur change de façon non uniforme.  
  
 L’exemple suivant remplit une ligne, une ellipse et un rectangle avec un pinceau de dégradé linéaire horizontal.  
  
 Le <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructeur reçoit quatre arguments : deux points et deux couleurs. Le premier point (0, 10) est associé à la première couleur (rouge), et le deuxième point (200, 10) est associé à la deuxième couleur (bleu). Comme pour tout, à partir de la ligne (0, 10) à (200, 10) passe progressivement du rouge au bleu.  
  
 Les 10 s dans les points (50, 10) et (200, 10) n’est pas important. L’essentiel est que les deux points aient la même coordonnée deuxième : la ligne reliant les est horizontale. L’ellipse et le rectangle passent également du rouge au bleu puisque la coordonnée horizontale va de 0 à 200.  
  
 L’illustration suivante montre la ligne, les points de suspension et le rectangle. Notez que le dégradé de couleur se répète lorsque la coordonnée horizontale dépasse 200.  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Pour utiliser des dégradés linéaires horizontaux  
  
-   Passez le bleu opaque rouge et opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 Dans l’exemple précédent, les composants de couleur changent linéairement lorsque vous passez de la coordonnée horizontale de 0 à une coordonnée horizontale de 200. Par exemple, un point dont la première coordonnée se trouve à mi-chemin entre 0 et 200 aura un composant bleu qui se trouve à mi-chemin entre 0 et 255.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]vous permet d’ajuster la façon dont une couleur varie d’un bord d’un dégradé à l’autre. Supposons que vous souhaitez créer un pinceau de dégradé change de couleur rouge conformément au tableau suivant.  
  
|Coordonnée horizontale|Composants RVB|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Notez que le composant rouge est à la moitié de son intensité lorsque la coordonnée horizontale est seulement 20 % de la façon de 0 à 200.  
  
 L’exemple suivant définit la <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> propriété d’un <xref:System.Drawing.Drawing2D.LinearGradientBrush> objet à associer les trois intensité relative à trois positions relatives. Comme dans le tableau précédent, une intensité relative 0,5 est associée à une position relative de 0,2. Le code remplit une ellipse et un rectangle avec le pinceau de dégradé.  
  
 L’illustration suivante montre l’ellipse résultant et le rectangle.  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>Pour personnaliser des dégradés linéaires  
  
-   Passez le rouge opaque noir et opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Les dégradés dans les exemples précédents ont été horizontales ; Autrement dit, la couleur passe progressivement lorsque vous déplacez le long de n’importe quelle ligne horizontale. Vous pouvez également définir des dégradés verticaux et en diagonale.  
  
 L’exemple suivant passe les points (0, 0) et (200, 100) à un <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructeur. Associé à la couleur bleue (0, 0), et est associée à la couleur verte (200, 100). Le pinceau de dégradé linéaire remplit une ligne (avec la largeur du stylet 10) et une ellipse.  
  
 L’illustration suivante montre la ligne et l’ellipse. Notez que la couleur de l’ellipse change progressivement lorsque vous déplacez le long d’une ligne qui est parallèle à la ligne passant par (0, 0) et (200, 100).  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Pour créer des dégradés linéaires en diagonale  
  
-   Passez l’opaque bleu et le vert opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'un pinceau à dégradé pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
