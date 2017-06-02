---
title: "Gestion de l&#39;&#233;tat d&#39;un objet graphique | Microsoft Docs"
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
  - "graphiques, découper"
  - "graphiques, gérer l'état"
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Gestion de l&#39;&#233;tat d&#39;un objet graphique
La classe <xref:System.Drawing.Graphics> est au cœur de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Pour dessiner quoi que ce soit, vous obtenez un objet <xref:System.Drawing.Graphics>, définissez ses propriétés et appelez ses méthodes \(<xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A> et autres méthodes de même nature\).  
  
 L'exemple suivant appelle la méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> d'un objet <xref:System.Drawing.Graphics>.  Le premier argument passé à la méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> est un objet <xref:System.Drawing.Pen>.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## État graphique  
 Un objet <xref:System.Drawing.Graphics> est bien plus qu'un simple fournisseur de méthodes de dessin telles que <xref:System.Drawing.Graphics.DrawLine%2A> et <xref:System.Drawing.Graphics.DrawRectangle%2A>.  Il gère également l'état graphique qui se décompose comme suit :  
  
-   Paramètres de qualité  
  
-   Transformations  
  
-   Région de découpage  
  
### Paramètres de qualité  
 Un objet <xref:System.Drawing.Graphics> possède plusieurs propriétés qui ont un impact sur la qualité des éléments dessinés.  Vous pouvez ainsi définir la propriété <xref:System.Drawing.Graphics.TextRenderingHint%2A> pour spécifier \(le cas échéant\), le type d'anticrénelage appliqué au texte.  Les autres propriétés ayant une incidence sur la qualité sont <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A> et <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 L'exemple suivant dessine deux ellipses, l'une avec le mode lissage <xref:System.Drawing.Drawing2D.SmoothingMode> et l'autre avec le mode lissage <xref:System.Drawing.Drawing2D.SmoothingMode> :  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### Transformations  
 Un objet <xref:System.Drawing.Graphics> gère deux transformations \(universelle et page\) qui s'appliquent à tous les éléments dessinés par cet objet <xref:System.Drawing.Graphics>.  Toute transformation affine peut être stockée dans la transformation universelle.  Les transformations affines comprennent l'ajustement, la rotation, la réflexion, l'inclinaison et la translation.  La transformation de page peut servir à l'ajustement et au changement d'unités \(par exemple, des pixels en pouces\).  Pour plus d'informations, consultez [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
 L'exemple suivant définit les transformations universelles et pages d'un objet <xref:System.Drawing.Graphics>.  La transformation universelle est définie sur une rotation de trente degrés.  La transformation de page est définie pour que les coordonnées passées à la seconde <xref:System.Drawing.Graphics.DrawEllipse%2A> soient traitées en millimètres et non en pixels.  Le code fait deux appels identiques à la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A>.  La transformation universelle s'applique au premier appel de <xref:System.Drawing.Graphics.DrawEllipse%2A> tandis que les deux transformations \(universelles et pages\) s'appliquent au second appel de <xref:System.Drawing.Graphics.DrawEllipse%2A>.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 L'illustration suivante affiche les deux ellipses.  Notez que la rotation de trente degrés porte sur l'origine du système de coordonnées \(dans le coin supérieur gauche de la zone cliente\) et non sur les centres des ellipses.  Vous noterez aussi que la largeur du crayon de 1 signifie 1 pixel pour la première ellipse et 1 millimètre pour la seconde.  
  
 ![Ovales](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### Région de découpage  
 Un objet <xref:System.Drawing.Graphics> gère une région de découpage qui s'applique à tous les éléments dessinés par cet objet <xref:System.Drawing.Graphics>.  Pour définir la région de découpage, appelez la méthode <xref:System.Drawing.Graphics.SetClip%2A>.  
  
 L'exemple suivant crée une région en forme de signe plus constituée par l'union de deux rectangles.  Cette région représente la région de découpage d'un objet <xref:System.Drawing.Graphics>.  Ensuite, le code dessine deux traits qui se limitent à l'intérieur de la région de découpage.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/ToolBarOrient_snip/visualbasic/toolbargraphics/new.bmp Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 L'illustration suivante montre deux traits découpés.  
  
 ![Zone de découpage limitée](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation de conteneurs graphiques imbriqués](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)