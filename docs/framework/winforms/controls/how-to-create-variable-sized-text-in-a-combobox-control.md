---
title: "Comment : créer du texte de taille variable dans un contrôle ComboBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6f0dcfd24414ef868a1a5414af4fcde1b9a14ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Comment : créer du texte de taille variable dans un contrôle ComboBox
Cet exemple montre un dessin personnalisé de texte dans un <xref:System.Windows.Forms.ComboBox> contrôle. Lorsqu’un élément répond à certains critères, il est dessiné dans une plus grande police et mis en rouge.  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Un Windows form.  
  
-   A <xref:System.Windows.Forms.ComboBox> contrôle nommé `ListBox1` avec trois éléments dans le <xref:System.Windows.Forms.ComboBox.Items%2A> propriété. Dans cet exemple, les trois éléments sont nommés `"One", Two", and Three"`. Le <xref:System.Windows.Forms.ComboBox.DrawMode%2A> propriété du `ComboBox1` doit avoir la valeur <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Cette technique est également applicable à la <xref:System.Windows.Forms.ListBox> contrôle, vous pouvez remplacer un <xref:System.Windows.Forms.ListBox> pour le <xref:System.Windows.Forms.ComboBox>.  
  
-   Références aux espaces de noms <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [Contrôles avec prise en charge intégrée du dessin owner-drawn](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [ListBox, contrôle](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [ComboBox, contrôle](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
