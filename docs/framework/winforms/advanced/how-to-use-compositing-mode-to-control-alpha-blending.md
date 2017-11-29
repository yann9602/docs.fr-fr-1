---
title: "Comment : utiliser le mode de composition pour commander la fusion alpha"
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
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564d46cb2d72ac63962657b39146489aaafd6a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Comment : utiliser le mode de composition pour commander la fusion alpha
Il peut arriver lorsque vous souhaitez créer une bitmap hors écran ayant les caractéristiques suivantes :  
  
-   Les couleurs ont les valeurs alphanumériques inférieur à 255.  
  
-   Couleurs ne sont pas alphanumériques fusionnés entre eux que vous créez l’image bitmap.  
  
-   Lorsque vous affichez la bitmap terminée, les couleurs de la bitmap sont fusionnée alpha avec les couleurs d’arrière-plan sur le périphérique d’affichage.  
  
 Pour créer une telle bitmap, construisez un espace <xref:System.Drawing.Bitmap> de l’objet et à construire un <xref:System.Drawing.Graphics> objet basé sur cette bitmap. Le mode de composition de la <xref:System.Drawing.Graphics> objet <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Drawing.Graphics> objet basé sur un <xref:System.Drawing.Bitmap> objet. Le code utilise le <xref:System.Drawing.Graphics> objet, ainsi que deux pinceaux translucides (alpha = 160) pour peindre sur la bitmap. Le code remplit une ellipse rouge et une ellipse verte en utilisant des pinceaux translucides. L’ellipse verte chevauche l’ellipse rouge, mais le vert n’est pas fusionnée avec la croix rouge, car le mode de composition le <xref:System.Drawing.Graphics> objet a la valeur <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Le code dessine l’image bitmap à l’écran à deux reprises : une fois sur un arrière-plan blanc et qu’une seule fois sur un arrière-plan multicolore. Les pixels dans la bitmap qui font partie des deux ellipses ont un composant alpha de 160, pour les points de suspension sont fusionnés avec les couleurs d’arrière-plan sur l’écran.  
  
 L’illustration suivante montre la sortie de l’exemple de code. Notez que les points de suspension sont fusionnés avec l’arrière-plan, mais ils ne sont pas fusionnés entre eux.  
  
 ![Source de copie](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 L’exemple de code contient cette instruction :  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Si vous souhaitez que les points de suspension pour être fusionnés entre eux ainsi qu’avec l’arrière-plan, modifiez cette instruction comme suit :  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 L’illustration suivante montre la sortie du code révisé.  
  
 ![Sur la source](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Fusion alpha de lignes et de remplissages](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
