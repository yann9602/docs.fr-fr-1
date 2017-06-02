---
title: "Comment&#160;: cr&#233;er un d&#233;grad&#233; lin&#233;aire | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "couleurs, créer des dégradés linéaires"
  - "dégradés"
  - "dégradés, créer des dégradés linéaires"
  - "dégradés linéaires, créer"
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: cr&#233;er un d&#233;grad&#233; lin&#233;aire
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit des dégradés linéaires horizontaux, verticaux et diagonaux.  Par défaut, la couleur d'un dégradé linéaire varie de façon régulière.  Toutefois, il est possible de le personnaliser pour obtenir une variation irrégulière de la couleur.  
  
 L'exemple suivant remplit une ligne, une ellipse et un rectangle avec un pinceau à dégradé linéaire horizontal.  
  
 Le constructeur <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> reçoit quatre arguments : deux points et deux couleurs.  Le premier point \(0, 10\) est associé à la première couleur \(rouge\) et le second \(200, 10\) est associé à la seconde couleur \(bleu\).  Le trait dessiné de \(0, 10\) à \(200, 10\) passe donc progressivement du rouge au bleu.  
  
 Parmi les points, les valeurs 10 \(50, 10\) et \(200, 10\) n'ont pas d'importance.  L'essentiel est que les deux points aient une seconde coordonnée identique, pour que le trait qui les relie soit horizontal.  L'ellipse et le rectangle passent également du rouge au bleu puisque la coordonnée horizontale progresse de 0 à 200.  
  
 L'illustration suivante montre le trait, l'ellipse et le rectangle.  Notez que le dégradé de couleur se répète lorsque la coordonnée horizontale dépasse 200.  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### Pour utiliser des dégradés linéaires horizontaux  
  
-   Passez le rouge opaque et le bleu opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 Dans l'exemple précédent, les composants de couleur changent linéairement lorsque vous passez de la coordonnée horizontale 0 à la coordonnée horizontale 200.  Par exemple, un point dont la première coordonnée se trouve à mi\-chemin entre 0 et 200 aura un composant bleu à mi\-chemin entre 0 et 255.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] vous permet d'ajuster la façon dont une couleur varie d'un bord d'un dégradé à l'autre.  à supposer que vous vouliez créer un pinceau à dégradé qui passe du noir au rouge conformément au tableau suivant.  
  
|Coordonnée horizontale|des composants RGB ;|  
|----------------------------|--------------------------|  
|0|\(0, 0, 0\)|  
|40|\(128, 0, 0\)|  
|200|\(255, 0, 0\)|  
  
 Notez que le composant rouge atteint la moitié de son intensité lorsque la coordonnée horizontale n'a progressé que de 20 pour cent sur la plage de valeurs comprise entre 0 et 200.  
  
 L'exemple suivant définit la propriété <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> d'un objet <xref:System.Drawing.Drawing2D.LinearGradientBrush> pour associer trois intensités relatives à trois positions relatives.  Comme dans le tableau précédent, l'exemple associe une intensité relative égale à 0,5 à une position relative de 0,2.  Le code remplit une ellipse et un rectangle avec le pinceau à dégradé.  
  
 L'illustration suivante présente l'ellipse et le rectangle ainsi obtenus.  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### Pour personnaliser des dégradés linéaires  
  
-   Passez le noir opaque et le rouge opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Dans les exemples précédents, les dégradés étaient horizontaux ; la couleur change progressivement à mesure que vous vous déplacez le long d'une ligne horizontale quelconque.  Vous pouvez également définir des dégradés verticaux et en diagonale.  
  
 L'exemple suivant passe les points \(0, 0\) et \(200, 100\) à un constructeur <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>.  La couleur bleue est associée à \(0,0\) et la couleur verte à \(200,100\).  Le pinceau à dégradé linéaire remplit une ligne \(correspondant à une épaisseur de crayon égale à 10\) et une ellipse.  
  
 L'illustration suivante contient la ligne et l'ellipse.  Notez que la couleur qui remplit l'ellipse change progressivement à mesure que vous vous déplacez le long de n'importe quelle ligne parallèle à une ligne passant par \(0, 0\) et \(200, 100\).  
  
 ![Dégradé linéaire](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### Pour créer des dégradés linéaires en diagonale  
  
-   Passez le bleu opaque et le vert opaque en tant que troisième et quatrième arguments, respectivement.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## Voir aussi  
 [Utilisation d'un pinceau à dégradé pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)