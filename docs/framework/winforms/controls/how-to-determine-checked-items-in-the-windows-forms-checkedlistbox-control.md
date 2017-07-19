---
title: "Comment&#160;: d&#233;terminer des &#233;l&#233;ments coch&#233;s dans le contr&#244;le CheckedListBox Windows&#160;Forms | Microsoft Docs"
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
  - "cases à cocher, déterminer l'état activé"
  - "CheckedListBox (contrôle Windows Forms), déterminer l'état activé"
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;terminer des &#233;l&#233;ments coch&#233;s dans le contr&#244;le CheckedListBox Windows&#160;Forms
Lorsque vous présentez des données dans un contrôle <xref:System.Windows.Forms.CheckedListBox> Windows Forms, vous pouvez itérer au sein de la collection stockée dans la propriété <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> ou vous déplacer dans la liste à l'aide de la méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> pour déterminer quels éléments sont cochés.  La méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> accepte comme argument le numéro d'index d'un élément et retourne la valeur `true` ou `false`.  Contrairement à ce que pouvez attendre, les propriétés <xref:System.Windows.Forms.ListBox.SelectedItems%2A> et <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> ne déterminent pas les éléments qui sont cochés, mais ceux qui sont en surbrillance.  
  
### Pour déterminer les éléments cochés dans un contrôle CheckedListBox, procédez comme suit :  
  
1.  Itérez au sein de la collection <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>, en commençant par 0, car il s'agit d'une collection de base zéro.  Notez que cette méthode fournit le numéro que porte l'élément dans la liste des éléments cochés, et non dans la liste globale.  Par conséquent, si le premier élément de la liste n'est pas coché alors que le deuxième l'est, le code ci\-dessous affiche une chaîne du type "Checked Item 1 \= MyListItem2".  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     \- ou \-  
  
2.  Avancez pas à pas dans la collection <xref:System.Windows.Forms.CheckedListBox.Items%2A>, en commençant par 0, car il s'agit d'une collection de base zéro, puis appelez la méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> pour chaque élément.  Remarquez que cette méthode fournit le numéro de l'élément dans la liste globale ; par conséquent, si le premier élément de la liste n'est pas coché alors que le deuxième l'est, elle affiche une chaîne semblable à ceci : "Item 2 \= MyListItem2".  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## Voir aussi  
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)