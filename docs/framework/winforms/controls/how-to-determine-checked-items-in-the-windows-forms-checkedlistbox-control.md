---
title: "Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63960740b2fc0cb2c96f9a853480f37857c7901b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms
Lors de la présentation des données dans les Windows Forms <xref:System.Windows.Forms.CheckedListBox> (contrôle), vous pouvez soit itérer la collection stockée dans la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriété, ou parcourez la liste à l’aide de la <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode pour déterminer quels éléments sont activés. Le <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode prend un numéro d’index en tant que son argument et retourne `true` ou `false`. Contrairement à ce que vous pouvez attendre, le <xref:System.Windows.Forms.ListBox.SelectedItems%2A> et <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> propriétés ne déterminent pas les éléments qui sont vérifiées ; ils déterminent quels éléments sont mis en surbrillance.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Pour déterminer les éléments sélectionnés dans un contrôle CheckedListBox  
  
1.  Itérer au sein du <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, en commençant par 0, car la collection est de base zéro. Notez que cette méthode fournit le numéro d’article dans la liste des éléments activés, pas dans la liste globale. Par conséquent, si le premier élément dans la liste n’est pas vérifié et le deuxième élément est activé, le code ci-dessous contient un texte tel que « Checked Item 1 = MyListItem2 ».  
  
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
  
     - ou  
  
2.  Parcourir le <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, en commençant à 0 car la collection est de base zéro, puis appelez le <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode pour chaque élément. Notez que cette méthode fournit le numéro d’article dans la liste globale, afin que si le premier élément dans la liste n’est pas activée et le deuxième élément est activé, il affiche un nom tel que « l’élément 2 = MyListItem2 ».  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
