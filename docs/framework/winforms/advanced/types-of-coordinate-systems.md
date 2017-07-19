---
title: "Types de syst&#232;mes de coordonn&#233;es | Microsoft Docs"
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
  - "systèmes de coordonnées"
  - "périphérique (système de coordonnées)"
  - "page (système de coordonnées)"
  - "transformation de page"
  - "transformations, page"
  - "transformations, universelles"
  - "unité de mesure"
  - "système de coordonnées universelles"
  - "transformation universelle"
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Types de syst&#232;mes de coordonn&#233;es
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] utilise trois espaces de coordonnées : les coordonnées universelles, les coordonnées de page et les coordonnées de périphérique.  Les coordonnées universelles permettent de modéliser un graphique universel particulier ; ce sont celles que vous passez aux méthodes dans le .NET Framework.  Les coordonnées de page font référence au système de coordonnées utilisé par une surface de dessin, telle qu'un formulaire ou un contrôle.  Les coordonnées de périphérique sont utilisées par le périphérique physique sur lequel le dessin est réalisé, tel qu'un écran ou une feuille de papier.  Lorsque vous effectuez l'appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, les points que vous passez à la méthode <xref:System.Drawing.Graphics.DrawLine%2A> \(`(0, 0)` et `(160, 80)`\) se trouvent dans l'espace de coordonnées universelles.  Pour que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] puisse dessiner la ligne à l'écran, ces coordonnées subissent tout d'abord une séquence de transformations.  L'une de ces transformations, appelée transformation universelle, convertit les coordonnées universelles en coordonnées de page ; une autre, appelée transformation de page, convertit les coordonnées de page en coordonnées de périphérique.  
  
## Transformations et systèmes de coordonnées  
 Supposons que vous vouliez travailler dans un système de coordonnées dont l'origine se trouve dans le corps \(et non dans le coin supérieur gauche\) de la zone cliente.  Par exemple, vous souhaitez une origine située à 100 pixels du bord gauche de la zone cliente et à 50 pixels du bord supérieur de la zone cliente.  L'illustration suivante représente le système de coordonnées correspondant.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.png "AboutGdip05\_art01")  
  
 Lorsque vous effectuez l'appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, vous obtenez la ligne représentée par l'illustration suivante.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.png "AboutGdip05\_art02")  
  
 Les extrémités de cette ligne ont les coordonnées suivantes dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|World|\(0, 0\) à \(160, 80\)|  
|Page|\(100, 50\) à \(260, 130\)|  
|Périphérique|\(100, 50\) à \(260, 130\)|  
  
 Notez que l'espace de coordonnées de la page a toujours son origine dans le coin supérieur gauche de la zone cliente.  D'autre part, comme l'unité de mesure est le pixel, les coordonnées de périphérique sont identiques aux coordonnées de page.  Si vous définissez une autre unité de mesure \(le pouce, par exemple\), les coordonnées de périphérique seront différentes des coordonnées de page.  
  
 La transformation universelle, qui mappe les coordonnées universelles aux coordonnées de page, est contenue dans la propriété <xref:System.Drawing.Graphics.Transform%2A> de la classe <xref:System.Drawing.Graphics>.  Dans l'exemple précédent, la transformation universelle est une translation de 100 unités dans la direction x et de 50 unités dans la direction y.  L'exemple suivant définit la transformation universelle d'un objet <xref:System.Drawing.Graphics>, puis utilise cet objet <xref:System.Drawing.Graphics> pour dessiner la ligne illustrée par la figure précédente :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 La transformation de page mappe les coordonnées de page aux coordonnées de périphérique.  La classe <xref:System.Drawing.Graphics> fournit les propriétés <xref:System.Drawing.Graphics.PageUnit%2A> et <xref:System.Drawing.Graphics.PageScale%2A> pour manipuler cette transformation.  La classe <xref:System.Drawing.Graphics> fournit également deux propriétés en lecture seule \(<xref:System.Drawing.Graphics.DpiX%2A> et <xref:System.Drawing.Graphics.DpiY%2A>\) qui permettent d'examiner les points par pouce \(horizontalement et verticalement\) du périphérique d'affichage.  
  
 Vous pouvez utiliser la propriété <xref:System.Drawing.Graphics.PageUnit%2A> de la classe <xref:System.Drawing.Graphics> pour spécifier une unité de mesure différente du pixel.  
  
> [!NOTE]
>  Vous ne pouvez pas affecter à la propriété <xref:System.Drawing.Graphics.PageUnit%2A> la valeur <xref:System.Drawing.GraphicsUnit>, car il ne s'agit pas d'une unité physique et une exception sera provoquée.  
  
 L'exemple suivant dessine une ligne qui va du point \(0, 0\) au point \(2, 1\), le point \(2, 1\) se trouvant 2 pouces à droite et 1 pouce au\-dessous du point \(0, 0\) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Si vous ne spécifiez pas la largeur du stylet lorsque vous construisez ce dernier, l'exemple précédent dessine une ligne d'un pouce d'épaisseur.  Vous pouvez spécifier la largeur du stylet dans le deuxième argument du constructeur <xref:System.Drawing.Pen> :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 En admettant que le périphérique d'affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans la direction verticale, voici les coordonnées des extrémités de la ligne de l'exemple précédent dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|World|\(0, 0\) à \(2, 1\)|  
|Page|\(0, 0\) à \(2, 1\)|  
|Périphérique|\(0, 0\) à \(192, 96\)|  
  
 Comme l'origine de l'espace de coordonnées universelles correspond au coin supérieur gauche de la zone cliente, les coordonnées de page sont identiques aux coordonnées universelles.  
  
 Vous pouvez combiner transformations universelles et transformations de page pour obtenir divers effets.  Supposons que vous utilisiez le pouce comme unité de mesure et un système de coordonnées dont l'origine est à 2 pouces du bord gauche et à 1\/2 pouce du bord supérieur de la zone cliente.  L'exemple suivant définit les transformations universelles et de page d'un objet <xref:System.Drawing.Graphics>, puis dessine une ligne qui va de \(0, 0\) à \(2, 1\) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 L'illustration suivante représente cette ligne et le système de coordonnées.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.png "AboutGdip05\_art03")  
  
 En admettant que le périphérique d'affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans la direction verticale, voici les coordonnées des extrémités de la ligne de l'exemple précédent dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|World|\(0, 0\) à \(2, 1\)|  
|Page|\(2, 0.5\) à \(4, 1.5\)|  
|Périphérique|\(192, 48\) à \(384, 144\)|  
  
## Voir aussi  
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [Représentation matricielle des transformations](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)