---
title: "Comment&#160;: ajouter et supprimer des &#233;l&#233;ments d&#39;un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms | Microsoft Docs"
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
  - "CheckedListBox (contrôle Windows Forms), ajouter et enlever des éléments"
  - "zones de liste déroulante, ajouter des éléments"
  - "zones de liste déroulante, supprimer des éléments"
  - "ComboBox (contrôle Windows Forms), ajouter et enlever des éléments"
  - "zones de liste, ajouter des éléments"
  - "zones de liste, supprimer des éléments"
  - "ListBox (contrôle Windows Forms), ajouter et enlever des éléments"
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: ajouter et supprimer des &#233;l&#233;ments d&#39;un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms
Il existe de nombreuses façons d'ajouter des éléments à une zone de liste déroulante, une zone de liste ou une zone de liste de cases à cocher Windows Forms, car ces contrôles peuvent être liés à une infinité de sources de données.  Toutefois, cette rubrique illustre la méthode la plus simple et ne nécessite pas de liaison de données.  Les éléments affichés sont généralement des chaînes ; cependant, il est possible d'utiliser n'importe quel objet.  Le texte affiché dans le contrôle correspond à la valeur retournée par la méthode `ToString`  de l'objet.  
  
### Pour ajouter des éléments  
  
1.  Ajoutez la chaîne ou l'objet à la liste au moyen de la méthode `Add` de la classe `ObjectCollection`.  La collection est référencée à l'aide de la propriété `Items`  :  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     \- ou \-  
  
2.  Insérez la chaîne ou l'objet à l'endroit de la liste souhaité à l'aide de la méthode `Insert`  :  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     \- ou \-  
  
3.  Assignez tout un tableau à la collection `Items`  :  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### Pour supprimer un élément  
  
1.  Appelez la méthode `Remove`  ou `RemoveAt`  pour supprimer des éléments.  
  
     `Remove`  possède un argument qui spécifie l'élément à supprimer. `RemoveAt`  supprime l'élément avec le numéro d'index spécifié.  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### Pour supprimer tous les éléments  
  
1.  Appelez la méthode `Clear` pour supprimer tous les éléments de la collection :  
  
    ```vb  
    ListBox1.Items.Clear()  
  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)