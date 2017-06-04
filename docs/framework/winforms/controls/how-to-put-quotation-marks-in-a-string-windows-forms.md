---
title: "Comment&#160;: ins&#233;rer des guillemets dans une cha&#238;ne (Windows Forms) | Microsoft Docs"
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
  - "guillemets"
  - "guillemets, ajouter aux chaînes des zones de texte"
  - "TextBox (contrôle Windows Forms), afficher les guillemets"
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ins&#233;rer des guillemets dans une cha&#238;ne (Windows Forms)
Quelquefois, vous pouvez souhaiter placer des guillemets \(""\) dans une chaîne de texte.  Par exemple :  
  
 She said, "You deserve a treat\!"  
  
 Vous pouvez également utiliser le champ <xref:Microsoft.VisualBasic.ControlChars.Quote> comme une constante.  
  
### Pour placer des guillemets dans une chaîne de votre code  
  
1.  En [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], insérez deux guillemets sur une ligne comme un guillemet incorporé.  En [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insérez la séquence d'échappement \\" en tant que guillemet incorporé.  Par exemple, pour créer la chaîne précédente, utilisez le code suivant :  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     ou  
  
2.  Insérez le caractère ASCII ou Unicode correspondant au guillemet.  En [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], utilisez le caractère ASCII \(34\).  En [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], utilisez le caractère Unicode \(\\u0022\).  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  Dans cet exemple, vous ne pouvez pas utiliser \\u0022, car vous ne pouvez pas utiliser un nom universel qui désigne un caractère dans le jeu de caractères de base.  Le cas échéant, cela provoquerait l'erreur C3851.  Pour plus d'informations, consultez [Erreur du compilateur C3851](../Topic/Compiler%20Error%20C3851.md).  
  
     ou  
  
3.  Vous pouvez également définir une constante pour le caractère et l'utiliser lorsque cela est nécessaire.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 <xref:Microsoft.VisualBasic.ControlChars.Quote>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)