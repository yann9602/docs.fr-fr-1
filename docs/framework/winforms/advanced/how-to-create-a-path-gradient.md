---
title: "Comment&#160;: cr&#233;er un d&#233;grad&#233; de trac&#233; | Microsoft Docs"
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
  - "dégradés, créer un chemin d'accès"
  - "chemins d'accès des graphiques, créer un dégradé"
  - "dégradés des chemins d'accès, créer"
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er un d&#233;grad&#233; de trac&#233;
La classe <xref:System.Drawing.Drawing2D.PathGradientBrush> vous permet de personnaliser la façon dont vous remplissez une forme avec des changements de couleurs progressifs.  Vous pouvez, par exemple, spécifier une couleur pour le centre d'un tracé et une autre pour son contour.  Vous pouvez également spécifier des couleurs différentes pour chacun des points situés sur le contour d'un tracé.  
  
> [!NOTE]
>  Dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], un tracé correspond à une séquence de lignes et de courbes gérée par un objet <xref:System.Drawing.Drawing2D.GraphicsPath>.  Pour plus d'informations sur les tracés [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], consultez [Tracés graphiques dans GDI\+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) et [Génération et dessin de tracés](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).  
  
### Pour remplir une ellipse avec un dégradé de tracé  
  
-   L'exemple ci\-dessous remplit une ellipse avec une brosse à dégradé de tracé.  La couleur définie pour le centre est le bleu et celle du contour est cyan.  L'illustration suivante montre l'ellipse remplie.  
  
     ![Tracé en dégradé](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     Par défaut, une brosse à dégradé de tracé ne s'étend pas à l'extérieur de la limite du tracé.  Si vous utilisez la brosse à dégradé de tracé pour remplir une illustration qui s'étend au\-delà de la limite du tracé, la zone de l'écran à l'extérieur du tracé ne sera pas remplie.  
  
     L'illustration suivante présente le résultat de la modification de l'appel <xref:System.Drawing.Graphics.FillEllipse%2A> en lui affectant `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)` dans le code suivant.  
  
     ![Tracé en dégradé](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     L'exemple de code précédent est destiné à être utilisé avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
### Pour spécifier des points sur la limite  
  
-   L'exemple suivant génère une brosse à dégradé de tracé à partir d'un tracé en forme d'étoile.  Le code définit la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> qui fixe le rouge comme couleur du centre de l'étoile.  Puis, il définit la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> pour spécifier les différentes couleurs \(stockées dans le tableau `colors`\) des points contenus dans le tableau `points`.  La dernière instruction du code remplit le tracé en forme d'étoile à l'aide de la brosse à dégradé de tracé.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   L'exemple suivant dessine un dégradé de tracé sans un objet <xref:System.Drawing.Drawing2D.GraphicsPath> dans le code.  Dans l'exemple, le constructeur particulier <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> reçoit un tableau de points, mais ne nécessite pas d'objet <xref:System.Drawing.Drawing2D.GraphicsPath>.  Notez en outre que <xref:System.Drawing.Drawing2D.PathGradientBrush> sert à remplir un rectangle et non pas un tracé.  Le rectangle étant plus long que le tracé fermé qui a servi à définir la brosse, celle‑ci n'a pas peint entièrement le rectangle.  L'illustration suivante montre le rectangle \(ligne en pointillé\) et la partie du rectangle que la brosse à dégradé de tracé a peinte.  
  
     ![Dégradé](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### Pour personnaliser un dégradé de tracé  
  
-   L'une des méthodes permettant de personnaliser une brosse à dégradé de tracé consiste à définir la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>.  Les échelles de focus spécifient un tracé qui se situe à l'intérieur du tracé principal.  Au lieu d'occuper uniquement le point central, la couleur centrale couvre entièrement le tracé intérieur.  
  
     L'exemple suivant crée une brosse à dégradé de tracé à partir d'un tracé elliptique.  Le code définit le bleu comme couleur de contour, le cyan comme couleur centrale, puis il utilise la brosse à dégradé de tracé pour remplir le tracé elliptique.  
  
     Ensuite, il définit les échelles de focus de la brosse à dégradé de tracé.  La valeur attribuée à l'échelle de focus x est 0,3 et celle attribuée à l'échelle de focus y est 0,8.  Le code appelle la méthode <xref:System.Drawing.Graphics.TranslateTransform%2A> d'un objet <xref:System.Drawing.Graphics> de sorte que l'appel suivant à la méthode <xref:System.Drawing.Graphics.FillPath%2A> remplisse une ellipse qui se situe à droite de la première.  
  
     Pour vous représenter l'effet des échelles de focus, imaginez une petite ellipse ayant le même centre que celui de l'ellipse principale.  La petite ellipse \(intérieure\) correspond à l'ellipse principale ajustée \(autour de son centre\) selon un facteur égal à 0,3 dans le sens horizontal et à 0,8 dans le sens vertical.  Lorsque vous allez du contour de l'ellipse extérieure vers celui de l'ellipse intérieure, la couleur passe progressivement du bleu au cyan.  Lorsque vous allez du contour de l'ellipse intérieure vers le centre commun, la couleur reste le cyan.  
  
     L'illustration suivante montre la sortie du code ci\-dessous.  Dans l'ellipse située à gauche, seul le point central est de couleur cyan.  Quant à l'ellipse située à droite, elle est de couleur cyan partout sur le tracé intérieur.  
  
 ![Dégradé](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### Pour personnaliser avec interpolation  
  
-   Il existe une autre manière de personnaliser une brosse à dégradé de tracé. Elle consiste à définir une matrice de couleurs d'interpolation et une matrice de positions d'interpolation.  
  
     L'exemple suivant crée une brosse à dégradé de tracé à partir d'un triangle.  Le code définit la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> de la brosse à dégradé de tracé pour spécifier un tableau de couleurs d'interpolation \(vert foncé, cyan, bleu\) et un tableau de positions d'interpolation \(0, 0,25, 1\).  Lorsque vous vous déplacez du contour du triangle vers le point central, la couleur passe progressivement du vert foncé au cyan, puis du cyan au bleu.  Le passage du vert foncé au cyan intervient à 25 % de la distance qui sépare le vert foncé du bleu.  
  
     L'illustration suivante montre le triangle rempli avec la brosse à dégradé de tracé personnalisée.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### Pour définir le point central  
  
-   Par défaut, le point central d'une brosse à dégradé de tracé correspond au centre du tracé utilisé pour générer la brosse.  Vous pouvez changer l'emplacement du point central en définissant la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> de la classe <xref:System.Drawing.Drawing2D.PathGradientBrush>.  
  
     L'exemple suivant crée une brosse à dégradé de tracé à partir d'une ellipse.  Le centre de l'ellipse se situe à \(70, 35\), mais le point central de la brosse à dégradé de tracé reçoit pour valeurs \(120, 40\).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     L'illustration ci‑dessous représente l'ellipse remplie et le point central de la brosse à dégradé de tracé.  
  
     ![Tracé en dégradé](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   Vous pouvez définir le point central d'une brosse à dégradé de tracé à un emplacement situé à l'extérieur du tracé qui a servi à générer la brosse.  L'exemple suivant remplace l'appel servant à définir la propriété <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> dans le code précédent.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     L'illustration suivante montre le résultat, après cette modification.  
  
     ![Tracé en dégradé](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     Dans l'illustration précédente, les points situés à l'extrémité droite de l'ellipse ne sont pas d'un bleu pur \(bien qu'ils s'en rapprochent\).  Les couleurs du dégradé sont placées comme si le remplissage atteignait le point \(145, 35\), là où la couleur serait un bleu pur \(0, 0, 255\).  Cependant, le remplissage n'atteint jamais ce point \(145, 35\), puisqu'une brosse à dégradé de tracé peint uniquement l'intérieur de son tracé.  
  
## Compilation du code  
 Les exemples précédents sont destinés à une utilisation avec Windows Forms et nécessitent <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un pinceau à dégradé pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)