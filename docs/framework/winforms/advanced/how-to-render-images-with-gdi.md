---
title: "Comment&#160;: rendre des images avec GDI+ | Microsoft Docs"
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
  - "GDI+, afficher des images existantes"
  - "images (Windows Forms), créer"
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: rendre des images avec GDI+
Vous pouvez utiliser [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour rendre des images existant sous la forme de fichiers dans vos applications.  Pour cela, vous devez créer un nouvel objet d'une classe <xref:System.Drawing.Image> \(telle que <xref:System.Drawing.Bitmap>\), puis créer un objet <xref:System.Drawing.Graphics> qui référence la surface de dessin à utiliser et ensuite appeler la méthode <xref:System.Drawing.Graphics.DrawImage%2A> de l'objet <xref:System.Drawing.Graphics>.  L'image est peinte sur la surface de dessin représentée par la classe graphique.  Vous pouvez avoir recours à l'éditeur d'images pour créer et modifier les fichiers image au moment du design et rendre ces images avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] au moment de l'exécution.  Pour plus d'informations, consultez [Image Editor for Icons](../Topic/Image%20Editor%20for%20Icons.md).  
  
### Pour rendre une image avec GDI\+  
  
1.  Créez un objet représentant l'image à afficher.  Cet objet doit être membre d'une classe qui hérite de <xref:System.Drawing.Image>, par exemple <xref:System.Drawing.Bitmap> ou <xref:System.Drawing.Imaging.Metafile>.  Voici un exemple :  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2.  Créez un objet <xref:System.Drawing.Graphics> représentant la surface de dessin à utiliser.  Pour plus d'informations, consultez [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3.  Appelez <xref:System.Drawing.Graphics.DrawImage%2A> de l'objet Graphics pour rendre l'image.  Vous devez spécifier à la fois l'image à dessiner et les coordonnées indiquant sa position.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## Voir aussi  
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Stylets, lignes et rectangles dans GDI\+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)   
 [Comment : dessiner du texte dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Drawing Lines or Closed Figures](../Topic/Drawing%20Lines%20or%20Closed%20Figures%20\(Image%20Editor%20for%20Icons\).md)   
 [Image Editor for Icons](../Topic/Image%20Editor%20for%20Icons.md)