---
title: "Comment&#160;: acc&#233;der &#224; des &#233;l&#233;ments sp&#233;cifiques d&#39;un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms | Microsoft Docs"
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
  - "CheckedListBox (contrôle Windows Forms), accéder aux éléments"
  - "zones de liste déroulante, accéder aux éléments"
  - "ComboBox (contrôle Windows Forms), accéder aux éléments"
  - "zones de liste, accéder aux éléments"
  - "ListBox (contrôle Windows Forms), accéder aux éléments"
  - "ListBox (contrôle Windows Forms), retourner des informations sur les éléments"
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: acc&#233;der &#224; des &#233;l&#233;ments sp&#233;cifiques d&#39;un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms
Il est essentiel de pouvoir accéder aux éléments d'une zone de liste déroulante, d'une zone de liste ou d'une zone de liste de cases à cocher Windows Forms.  Vous pouvez ainsi déterminer par programme ce qui figure dans une liste, à n'importe quelle position.  
  
### Pour accéder à un élément de liste  
  
1.  Interrogez la collection `Items`  en utilisant l'index de l'élément concerné :  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)