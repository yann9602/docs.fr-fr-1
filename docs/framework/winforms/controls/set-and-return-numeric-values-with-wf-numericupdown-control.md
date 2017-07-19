---
title: "Comment&#160;: d&#233;finir et retourner des valeurs num&#233;riques &#224; l&#39;aide du contr&#244;le NumericUpDown Windows Forms | Microsoft Docs"
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
  - "valeurs numériques, Windows Forms"
  - "NumericUpDown (contrôle Windows Forms), définir et retourner des valeurs"
  - "contrôles Windows Forms, NumericUpDown"
  - "Windows Forms, valeurs numériques"
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir et retourner des valeurs num&#233;riques &#224; l&#39;aide du contr&#244;le NumericUpDown Windows Forms
La valeur numérique du contrôle <xref:System.Windows.Forms.NumericUpDown> Windows Forms est déterminée par sa propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A>.  Vous pouvez écrire des tests conditionnels pour la valeur du contrôle comme vous le feriez avec n'importe quelle autre propriété.  La propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> une fois définie, vous pouvez la modifier directement en écrivant du code pour effectuer sur elle des opérations, ou bien appeler les méthodes <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> et <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
### Pour définir la valeur numérique  
  
1.  Assignez une valeur à la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> dans le code ou dans la fenêtre Propriétés.  
  
    ```vb  
    NumericUpDown1.Value = 55  
  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     ou  
  
2.  Appelez la méthode <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ou <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> pour augmenter ou diminuer la valeur de l'incrément spécifié par la propriété <xref:System.Windows.Forms.NumericUpDown.Increment%2A>.  
  
    ```vb  
    NumericUpDown1.UpButton()  
  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### Pour retourner la valeur numérique  
  
-   Accédez à la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> dans le code.  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.NumericUpDown>   
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=fullName>   
 [NumericUpDown, contrôle](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [Vue d'ensemble du contrôle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)