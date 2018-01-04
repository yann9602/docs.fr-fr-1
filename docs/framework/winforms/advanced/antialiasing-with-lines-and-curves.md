---
title: "Anticrénelage avec des lignes et des courbes"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a>Anticrénelage avec des lignes et des courbes
Lorsque vous utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour dessiner une ligne, vous fournissez le point de départ et le point de fin de la ligne, mais il est inutile de fournir des informations sur les pixels individuels sur la ligne. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fonctionne en association avec le logiciel de pilote d’affichage pour déterminer quels pixels seront activées pour afficher la ligne sur un périphérique d’affichage particulier.  
  
## <a name="aliasing"></a>Utilisation d’alias  
 Envisagez la ligne droite rouge qui va du point (4, 2) au point (16, 10). Supposons que le système de coordonnées a son origine dans le coin supérieur gauche et que l’unité de mesure est le pixel. Supposons également que l’axe des x point vers la droite et les points de l’axe des y vers le bas. L’illustration suivante montre une vue agrandie de la ligne rouge dessinée sur un arrière-plan multicolore.  
  
 ![Ligne, sans anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Les pixels rouges utilisés pour rendre la ligne sont opaques. Il n’y a aucun pixel partiellement transparent dans la ligne. Ce type de rendu donne une apparence en escalier à la ligne et la ligne ressemble escalier. Cette technique qui représente une ligne comme un escalier est appelée crénelage ; l’escalier est un alias pour la ligne théorique.  
  
## <a name="antialiasing"></a>anticrénelage  
 Une technique plus sophistiquée pour le rendu d’une ligne implique l’utilisation de pixels partiellement transparents et pixels opaques. Pixels sont définies sur rouge pur, ou un mélange de rouge et de la couleur d’arrière-plan, en fonction de leur proximité qu’ils sont à la ligne. Ce type de rendu est appelé anticrénelage et donne une ligne le œil humain perçoit plus lisse. L’illustration suivante montre comment certains pixels sont fusionnés avec l’arrière-plan pour produire une ligne non crénelé.  
  
 ![Anticrénelage d’une ligne](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 L’anticrénelage, également appelé lissage, peut également être appliqué aux courbes. L’illustration suivante montre une vue agrandie d’une ellipse lissée.  
  
 ![Anticrénelage de courbes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 L’illustration suivante montre la même ellipse en taille réelle, sans anticrénelage et avec anticrénelage.  
  
 ![Exemple d’anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Pour dessiner des lignes et des courbes qui utilisent l’anticrénelage, créez une instance de la <xref:System.Drawing.Graphics> puis définissez son <xref:System.Drawing.Graphics.SmoothingMode%2A> propriété <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ou <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Appelez ensuite l’une des méthodes de dessin de ce même <xref:System.Drawing.Graphics> classe.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Guide pratique pour utiliser l‘anticrénelage avec du texte](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
