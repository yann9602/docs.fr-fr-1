---
title: "Types de systèmes de coordonnées"
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
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be89584ee8e7a82c405bf8664bfad18ced6d989a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-coordinate-systems"></a>Types de systèmes de coordonnées
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]utilise trois espaces de coordonnées : monde, page et périphérique. Coordonnées universelles sont les coordonnées utilisées pour modéliser un environnement graphique particulier et les coordonnées que vous passez aux méthodes dans le .NET Framework. Les coordonnées de page font référence au système de coordonnées utilisé par une surface de dessin, comme un formulaire ou un contrôle. Coordonnées de périphérique sont les coordonnées utilisées par le périphérique physique qui est dessiné, tel qu’un écran ou une feuille de papier. Lorsque vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, les points que vous passez à la <xref:System.Drawing.Graphics.DrawLine%2A> méthode —`(0, 0)` et `(160, 80)`, se trouvent dans l’espace de coordonnées universelles. Avant de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut dessiner la ligne à l’écran, les coordonnées passent par une séquence de transformations. Une transformation, appelée la transformation universelle, convertit les coordonnées universelles en coordonnées de page, et une autre transformation, appelée la transformation de page, convertit les coordonnées de page en coordonnées de périphérique.  
  
## <a name="transforms-and-coordinate-systems"></a>Les transformations et les systèmes de coordonnées  
 Supposons que vous souhaitez travailler avec un système de coordonnées qui a son origine dans le corps de la zone cliente plutôt que dans le coin supérieur gauche. Imaginons, par exemple, que vous vouliez d’origine située à 100 pixels du bord gauche de la zone cliente et à 50 pixels à partir du haut de la zone cliente. L’illustration suivante montre un système de coordonnées.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Lorsque vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, vous obtenez la ligne représentée dans l’illustration suivante.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Les coordonnées des points de terminaison de la ligne dans les trois espaces de coordonnées sont les suivantes :  
  
|||  
|-|-|  
|World|(0, 0) à (160, 80)|  
|Page|(100, 50) à (260, 130)|  
|Périphérique|(100, 50) à (260, 130)|  
  
 Notez que l’espace de coordonnées de page a son origine dans le coin supérieur gauche de la zone cliente ; Ce sera toujours le cas. Notez également que, car l’unité de mesure est le pixel, les coordonnées de périphérique sont les mêmes que les coordonnées de page. Si vous définissez l’unité de mesure avec une valeur différente de pixels (par exemple, pouces), puis les coordonnées de périphérique sera différentes de coordonnées de la page.  
  
 La transformation universelle, qui mappe les coordonnées universelles aux coordonnées de page, est conservée dans le <xref:System.Drawing.Graphics.Transform%2A> propriété de la <xref:System.Drawing.Graphics> classe. Dans l’exemple précédent, la transformation universelle est une translation de 100 unités dans la direction x et de 50 unités sur l’axe y. L’exemple suivant définit la transformation universelle d’un <xref:System.Drawing.Graphics> de l’objet, puis l’utilise <xref:System.Drawing.Graphics> objet à dessiner la ligne illustrée dans la figure précédente :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 La transformation de page mappe les coordonnées de page aux coordonnées de périphérique. Le <xref:System.Drawing.Graphics> classe fournit le <xref:System.Drawing.Graphics.PageUnit%2A> et <xref:System.Drawing.Graphics.PageScale%2A> propriétés pour la manipulation de la transformation de page. Le <xref:System.Drawing.Graphics> classe fournit également deux propriétés en lecture seule, <xref:System.Drawing.Graphics.DpiX%2A> et <xref:System.Drawing.Graphics.DpiY%2A>, pour examiner les points par pouce du périphérique d’affichage horizontales et verticales.  
  
 Vous pouvez utiliser la <xref:System.Drawing.Graphics.PageUnit%2A> propriété de la <xref:System.Drawing.Graphics> classe pour spécifier une unité de mesure autre que le pixel.  
  
> [!NOTE]
>  Vous ne pouvez pas définir le <xref:System.Drawing.Graphics.PageUnit%2A> propriété <xref:System.Drawing.GraphicsUnit.World>, comme cela n’est pas une unité physique et provoquera une exception.  
  
 L’exemple suivant dessine une ligne à partir de (0, 0) à (2, 1), où le point (2, 1) est 2 pouces à droite et 1 pouce vers le bas à partir du point (0, 0) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Si vous ne spécifiez la largeur du stylet lorsque vous construisez le stylet, l’exemple précédent Dessine une ligne d’un pouce de large. Vous pouvez spécifier la largeur du stylet dans le deuxième argument de la <xref:System.Drawing.Pen> constructeur :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Si nous partons du principe que le périphérique d’affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans le sens vertical, les points de terminaison de la ligne dans l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|World|(0, 0) à (2, 1)|  
|Page|(0, 0) à (2, 1)|  
|Périphérique|(0, 0, à (192, 96)|  
  
 Notez que l’origine de l’espace de coordonnées universelles étant à l’angle supérieur gauche de la zone cliente, les coordonnées de page sont les mêmes que les coordonnées de monde.  
  
 Vous pouvez combiner les transformations universelles et de page pour obtenir divers effets. Par exemple, supposons que vous souhaitez utiliser pouces comme unité de mesure et que vous souhaitez l’origine de votre système de coordonnées à 2 pouces du bord gauche de la zone cliente et le 1/2 pouce à partir du haut de la zone cliente. L’exemple suivant définit les transformations universelles et de page d’un <xref:System.Drawing.Graphics> de l’objet, puis dessine une ligne à partir de (0, 0) à (2, 1) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 L’illustration suivante montre la ligne et le système de coordonnées.  
  
 ![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Si nous partons du principe que le périphérique d’affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans le sens vertical, les points de terminaison de la ligne dans l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|World|(0, 0) à (2, 1)|  
|Page|(2, 0,5) à (4, 1.5)|  
|Périphérique|(192, 48) à (384, 144)|  
  
## <a name="see-also"></a>Voir aussi  
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Représentation matricielle des transformations](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
