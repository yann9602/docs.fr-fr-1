---
title: "Comment&#160;: cr&#233;er du texte de taille variable dans un contr&#244;le ComboBox | Microsoft Docs"
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
  - "zones de liste déroulante, dessiner du texte"
  - "ComboBox (contrôle Windows Forms), dessiner un texte personnalisé"
  - "ComboBox (contrôle Windows Forms), exemples (C#)"
  - "exemples (Windows Forms), ComboBox (contrôle)"
  - "texte, dessiner dans les zones de liste déroulante"
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er du texte de taille variable dans un contr&#244;le ComboBox
Cet exemple montre un dessin personnalisé de texte dans un contrôle <xref:System.Windows.Forms.ComboBox>.  Lorsqu'un élément rencontre un certain critère, il est dessiné dans une plus grande police et mis en rouge.  
  
## Exemple  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un Windows Form.  
  
-   Un contrôle <xref:System.Windows.Forms.ComboBox> nommé  `ListBox1`  avec trois éléments dans la propriété <xref:System.Windows.Forms.ComboBox.Items%2A>.  Dans cet exemple, les trois éléments sont nommés  `"One", Two", and Three"`.  La propriété <xref:System.Windows.Forms.ComboBox.DrawMode%2A> de  `ComboBox1`  doit avoir la valeur <xref:System.Windows.Forms.DrawMode>.  
  
    > [!NOTE]
    >  Cette technique est également applicable au contrôle <xref:System.Windows.Forms.ListBox>\- vous pouvez substituer un <xref:System.Windows.Forms.ListBox> au <xref:System.Windows.Forms.ComboBox>.  
  
-   Des références aux espaces de noms <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Drawing?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox.DrawItem>   
 <xref:System.Windows.Forms.DrawItemEventArgs>   
 <xref:System.Windows.Forms.ComboBox.MeasureItem>   
 [Contrôles avec prise en charge intégrée des dessins owner\-drawn](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)   
 [ListBox, contrôle](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)   
 [ComboBox, contrôle](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)