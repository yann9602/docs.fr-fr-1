---
title: "Anticr&#233;nelage avec des lignes et des courbes | Microsoft Docs"
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
  - "anticrénelage"
  - "anticrénelage, modes de lissage"
  - "GDI+, anticrénelage"
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Anticr&#233;nelage avec des lignes et des courbes
Lorsque vous utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour dessiner une ligne, vous fournissez le point de début et le point de fin de cette ligne, mais vous n'avez pas à préciser d'informations sur les pixels individuels.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionne en collaboration avec le logiciel du pilote d'affichage pour déterminer quels pixels activer pour afficher la ligne sur un périphérique d'affichage particulier.  
  
## Crénelage  
 Prenez le segment de droite rouge qui va du point \(4, 2\) au point \(16, 10\).  Supposez que le système de coordonnées a son origine dans le coin supérieur gauche et que l'unité de mesure est le pixel.  Supposez également que l'axe des abscisses \(x\) pointe vers la droite et que l'axe des ordonnées \(y\) pointe vers le bas.  L'illustration suivante représente une vue agrandie de la ligne rouge dessinée sur un arrière\-plan multicolore.  
  
 ![Ligne sans anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.png "AboutGdip02\_Art33")  
  
 Les pixels rouges utilisés pour le rendu de la ligne sont opaques.  Il n'y a pas de pixels partiellement transparents dans cette ligne.  Ce type de rendu donne à la ligne un aspect d'escalier.  Cette technique qui représente une ligne comme un escalier est appelée crénelage ; l'escalier est un alias pour la ligne théorique.  
  
## Anticrénelage  
 Une technique plus élaborée de rendu de ligne consiste à utiliser des pixels partiellement transparents et des pixels opaques.  Les pixels sont définis comme étant de couleur rouge franche ou comme étant une fusion de rouge et de la couleur d'arrière\-plan en fonction de leur proximité par rapport à la ligne.  Ce type de rendu est appelé anticrénelage et donne une ligne plus lisse pour l'œil humain.  L'illustration suivante montre comment certains pixels sont fusionnés avec l'arrière\-plan pour produire une ligne non crénelée.  
  
 ![Anticrénelage d'une ligne](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.png "AboutGdip02\_Art34")  
  
 L'anticrénelage \(ou lissage\) peut également être appliqué aux courbes.  L'illustration suivante représente une vue agrandie d'une ellipse lissée.  
  
 ![Anticrénelage de courbes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.png "AboutGdip02\_Art35")  
  
 L'illustration suivante montre la même ellipse en taille réelle, sans anticrénelage et avec anticrénelage.  
  
 ![Exemple d'anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02\_Art36")  
  
 Pour dessiner des lignes et des courbes qui utilisent l'anticrénelage, créez une instance de la classe <xref:System.Drawing.Graphics> et affectez à sa propriété <xref:System.Drawing.Graphics.SmoothingMode%2A> la valeur <xref:System.Drawing.Drawing2D.SmoothingMode> ou <xref:System.Drawing.Drawing2D.SmoothingMode>.  Appelez ensuite l'une des méthodes de dessin de la même classe <xref:System.Drawing.Graphics>.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : utiliser l'anticrénelage avec du texte](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)