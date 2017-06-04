---
title: "Splines de B&#233;zier dans GDI+ | Microsoft Docs"
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
  - "splines de Bézier"
  - "GDI+, splines de Bézier"
  - "splines, Bézier"
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Splines de B&#233;zier dans GDI+
Une spline de Bézier est une courbe spécifiée par quatre points : les deux points de terminaison \(p1 et p2\) et deux points de contrôle \(c1 et c2\).  La courbe commence en p1 et finit en p2.  Elle ne passe pas par les points de contrôle, mais ces derniers agissent comme des aimants qui l'attirent dans certaines directions et influencent sa courbure.  L'illustration suivante montre une courbe de Bézier avec ses points de terminaison et ses points de contrôle.  
  
 ![Splines de Bézier](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.png "Aboutgdip02\_art11a")  
  
 La courbe part de p1 et se dirige vers le point de contrôle c1.  La tangente de la courbe en p1 est la ligne dessinée de p1 à c1.  La tangente de la courbe en p2 est la ligne dessinée de c2 à p2.  
  
## Dessin des splines de Bézier  
 Pour dessiner une spline de Bézier, vous avez besoin d'une instance de la classe <xref:System.Drawing.Graphics> et d'un objet <xref:System.Drawing.Pen>.  L'instance de la classe <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawBezier%2A> et l'objet <xref:System.Drawing.Pen> stocke des attributs \(largeur et couleur notamment\) de la ligne utilisée pour représenter la courbe.  L'objet <xref:System.Drawing.Pen> est passé à la méthode <xref:System.Drawing.Graphics.DrawBezier%2A> en tant qu'argument.  Les autres arguments passés à la méthode <xref:System.Drawing.Graphics.DrawBezier%2A> définissent les points de terminaison et les points de contrôle.  L'exemple suivant dessine une courbe de Bézier définie par le point de départ \(0, 0\), les points de contrôles \(40, 20\) et \(80, 150\) et le point de terminaison \(100, 10\) :  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 L'illustration suivante représente la courbe, les points de contrôle et deux lignes tangentes.  
  
 ![Splines de Bézier](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.png "Aboutgdip02\_art12")  
  
 Les splines de Bézier doivent leur nom à Pierre Bézier qui fut le premier à développer ces courbes pour le design dans l'industrie automobile.  Depuis, les splines ont fait leurs preuves dans de nombreuses activités de conception assistée par ordinateur ; elles sont également utilisées pour définir les contours des polices de caractères.  Les splines de Bézier peuvent produire une grande variété de formes, dont voici quelques illustrations.  
  
 ![Chemins d'accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.png "Aboutgdip02\_art13")  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Comment : créer un objet Pen](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)