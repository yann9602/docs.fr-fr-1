---
title: "Comment&#160;: cr&#233;er des objets graphiques pour le dessin | Microsoft Docs"
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
  - "GDI+, créer des images"
  - "graphiques (Windows Forms), créer"
  - "Graphics (classe)"
  - "images (Windows Forms), créer"
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: cr&#233;er des objets graphiques pour le dessin
Avant de pouvoir dessiner des traits et des formes, de rendre du texte ou d'afficher et de manipuler des images avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous devez créer un objet <xref:System.Drawing.Graphics>.  L'objet <xref:System.Drawing.Graphics> représente une surface de dessin [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et l'objet utilisé pour créer des images graphiques.  
  
 Deux étapes sont nécessaires à l'utilisation de graphiques :  
  
1.  Création d'un objet <xref:System.Drawing.Graphics>.  
  
2.  Utilisation de l'objet <xref:System.Drawing.Graphics> pour dessiner des traits et des formes, pour rendre du texte ou pour afficher et manipuler des images.  
  
## Création d'un objet Graphics  
 Un objet Graphics peut être créé de diverses manières.  
  
#### Pour créer un objet Graphics  
  
-   Recevoir une référence à un objet Graphics dans le cadre de <xref:System.Windows.Forms.PaintEventArgs> de l'événement <xref:System.Windows.Forms.Control.Paint> d'un formulaire ou d'un contrôle.  Cette approche est généralement utilisée pour obtenir une référence à un objet Graphics lors de la création du code de peinture d'un contrôle.  De la même façon, vous pouvez également obtenir un objet Graphics en tant que propriété du <xref:System.Drawing.Printing.PrintPageEventArgs> lors de la gestion de l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour un <xref:System.Drawing.Printing.PrintDocument>.  
  
     ou  
  
-   Appelez la méthode <xref:System.Windows.Forms.Control.CreateGraphics%2A> d'un contrôle ou d'un formulaire afin d'obtenir une référence à un objet <xref:System.Drawing.Graphics> représentant la surface de dessin de ce contrôle ou formulaire.  Utilisez cette méthode si vous voulez dessiner sur un formulaire ou un contrôle existant.  
  
     ou  
  
-   Créez un objet <xref:System.Drawing.Graphics> à partir de n'importe quel objet héritant de la classe <xref:System.Drawing.Image>.  Cette approche est utile si vous voulez modifier une image existante.  
  
     Les sections qui suivent expliquent en détail chacun de ces processus.  
  
## PaintEventArgs dans le gestionnaire d'événements Paint  
 Lors de la programmation du <xref:System.Windows.Forms.PaintEventHandler> pour des contrôles ou de <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour un <xref:System.Drawing.Printing.PrintDocument>, un objet Graphics est fourni en tant que l'une des propriétés de <xref:System.Windows.Forms.PaintEventArgs> ou de <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### Pour obtenir une référence à un objet Graphics à partir des PaintEventArgs de l'événement Paint  
  
1.  Déclarez l'objet <xref:System.Drawing.Graphics>.  
  
2.  Assignez la variable pour qu'elle référence l'objet <xref:System.Drawing.Graphics> passé dans le cadre de <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Insérez le code de peinture du formulaire ou du contrôle.  
  
     L'exemple suivant explique comment référencer un objet <xref:System.Drawing.Graphics> à partir de <xref:System.Windows.Forms.PaintEventArgs> de l'événement <xref:System.Windows.Forms.Control.Paint> :  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## Méthode CreateGraphics  
 Vous pouvez aussi appeler la méthode <xref:System.Windows.Forms.Control.CreateGraphics%2A> d'un contrôle ou d'un formulaire afin d'obtenir une référence à un objet <xref:System.Drawing.Graphics> représentant la surface de dessin de ce contrôle ou formulaire.  
  
#### Pour créer un objet Graphics à l'aide de la méthode CreateGraphics  
  
-   Appelez la méthode <xref:System.Windows.Forms.Control.CreateGraphics%2A> du formulaire ou contrôle sur lequel vous voulez rendre des graphiques.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## Création à partir d'un objet Image  
 Une autre solution consiste à créer un objet Graphics à partir de n'importe quel objet dérivé de la classe <xref:System.Drawing.Image>.  
  
#### Pour créer un objet Graphics à partir d'un objet Image  
  
-   Appelez la méthode <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=fullName>, en fournissant le nom de la variable Image à partir de laquelle vous voulez créer un objet <xref:System.Drawing.Graphics>.  
  
     L'exemple ci\-dessous explique comment utiliser un objet <xref:System.Drawing.Bitmap> :  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  Vous pouvez créer des objets <xref:System.Drawing.Graphics> uniquement à partir de fichiers .bmp non indexés, tels que des fichiers .bmp 16 bits, 24 bits et 32 bits.  Chaque pixel d'un fichier .bmp non indexé contient une couleur, contrairement aux pixels des fichiers .bmp indexés, qui contiennent un index dans une table de couleurs.  
  
## Dessin et manipulation de formes et d'images  
 Une fois l'objet <xref:System.Drawing.Graphics> créé, il peut être employé pour dessiner des traits et des formes, pour rendre du texte ou pour afficher et manipuler des images.  Les principaux objets utilisés avec l'objet <xref:System.Drawing.Graphics> sont les suivants :  
  
-   La classe <xref:System.Drawing.Pen> est utilisée pour dessiner des traits, tracer le contour de formes ou rendre d'autres représentations géométriques.  
  
-   La classe <xref:System.Drawing.Brush> est utilisée pour remplir des zones de graphiques, telles que du texte, des images ou des formes remplies.  
  
-   La classe <xref:System.Drawing.Font> décrit les formes à utiliser pour le rendu de texte.  
  
-   La structure <xref:System.Drawing.Color> représente les différentes couleurs à afficher.  
  
#### Pour utiliser l'objet Graphics que vous avez créé  
  
-   Utilisez l'objet approprié figurant dans la liste ci\-dessus pour dessiner ce dont vous avez besoin.  
  
     Pour plus d'informations, consultez les rubriques suivantes :  
  
    |Pour rendre|Consultez|  
    |-----------------|---------------|  
    |Lignes|[Comment : dessiner une ligne dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |formes|[Comment : dessiner une forme avec contour](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Texte|[Comment : dessiner du texte dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |Images|[Comment : rendre des images avec GDI\+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## Voir aussi  
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : rendre des images avec GDI\+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)