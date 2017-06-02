---
title: "Comment&#160;: fractionner une fen&#234;tre horizontalement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SplitContainer (contrôle Windows Forms), fractionnement horizontal"
  - "fenêtres fractionnées, modifier l'orientation du fractionnement"
  - "fenêtres fractionnées, horizontale"
  - "fenêtres, fractionner horizontalement"
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: fractionner une fen&#234;tre horizontalement
L'exemple de code suivant fait en sorte que le séparateur qui divise le contrôle <xref:System.Windows.Forms.SplitContainer> soit horizontal.  
  
> [!NOTE]
>  La propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> du contrôle <xref:System.Windows.Forms.SplitContainer> détermine la direction du séparateur et non du contrôle lui\-même.  
  
### Pour fractionner une fenêtre horizontalement  
  
1.  Dans une procédure, affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> du contrôle <xref:System.Windows.Forms.SplitContainer> la valeur <xref:System.Windows.Forms.Orientation>.  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)