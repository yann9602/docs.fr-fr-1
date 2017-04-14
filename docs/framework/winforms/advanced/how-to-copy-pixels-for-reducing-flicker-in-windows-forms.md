---
title: "Comment&#160;: copier des pixels pour r&#233;duire le scintillement dans les Windows Forms | Microsoft Docs"
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
  - "transfert de blocs de bits"
  - "bitblt"
  - "scintillement"
  - "scintillement, réduire dans les Windows Forms"
  - "graphiques, copier"
  - "graphiques, réduire le scintillement"
  - "pixels, copier"
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: copier des pixels pour r&#233;duire le scintillement dans les Windows Forms
Lorsque vous animez un graphique simple, les utilisateurs peuvent parfois être exposés à un scintillement ou à d'autres effets visuels indésirables.  Une façon de limiter ce problème consiste à utiliser un processus « bitblt » sur le graphique.  Bitblt représente le « transfert par bloc de bits » des données couleur d'un rectangle de pixels d'origine vers un rectangle de pixels de destination.  
  
 Avec les Windows Forms, le processus bitblt s'effectue à l'aide de la méthode <xref:System.Drawing.Graphics.CopyFromScreen%2A> de la classe <xref:System.Drawing.Graphics>.  Dans les paramètres de la méthode, vous spécifiez la source et de destination \(en tant que points\), la taille de la zone à copier et l'objet Graphics utilisé pour dessiner la nouvelle forme.  
  
 Dans l'exemple ci\-dessous, une forme est dessinée sur le formulaire dans son gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Ensuite, la méthode <xref:System.Drawing.Graphics.CopyFromScreen%2A> est utilisée pour dupliquer la forme.  
  
> [!NOTE]
>  L'affectation à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> du formulaire de la valeur `true` permettra de mettre deux fois en mémoire tampon le code de graphiques figurant dans l'événement <xref:System.Windows.Forms.Control.Paint>.  Cela ne permettra pas d'améliorer les performances de façon significative lors de l'utilisation du code ci\-dessous, mais vous pourrez en tenir compte lorsque vous utiliserez du code plus complexe pour la manipulation graphique.  
  
## Exemple  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## Compilation du code  
 Le code ci\-dessus est exécuté dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint> du formulaire afin que les graphiques persistent si le formulaire est redessiné.  Par conséquent, vous ne devez pas appeler de méthodes graphiques dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>, car les dessins ne seront pas redessinés si le formulaire est redimensionné ou masqué par un autre formulaire.  
  
## Voir aussi  
 <xref:System.Drawing.CopyPixelOperation>   
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=fullName>   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)