---
title: "Comment&#160;: s&#233;lectionner du texte dans le contr&#244;le TextBox Windows Forms | Microsoft Docs"
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
  - "zones de texte, sélectionner du texte par programme"
  - "texte, sélectionner par programme dans des zones de texte"
  - "TextBox (contrôle Windows Forms), sélectionner du texte par programme"
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Comment&#160;: s&#233;lectionner du texte dans le contr&#244;le TextBox Windows Forms
Vous pouvez sélectionner du texte par programmation dans le contrôle <xref:System.Windows.Forms.TextBox> Windows Forms.  Par exemple, si vous créez une fonction qui recherche du texte pour une chaîne particulière, vous pouvez sélectionner le texte afin d'alerter visuellement le lecteur de la position de la chaîne trouvée.  
  
### Pour sélectionner du texte par programmation  
  
1.  Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> au début du texte que vous souhaitez sélectionner.  
  
     La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est un nombre qui indique le point d'insertion dans la chaîne de texte, 0 étant la position la plus à gauche.  Si la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a une valeur égale ou supérieure au nombre de caractères dans la zone de texte, le point d'insertion est placé après le dernier caractère.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> la longueur du texte que vous souhaitez sélectionner.  
  
     La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> est une valeur numérique qui définit la largeur du point d'insertion.  Le fait d'affecter à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> un nombre supérieur à 0 a pour conséquence la sélection de ce nombre de caractères, à partir du point d'insertion actuel.  
  
3.  \(Facultatif\) Accédez au texte sélectionné par l'intermédiaire de la propriété <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.  
  
     Le code ci\-dessous sélectionne le contenu d'une zone de texte lorsque l'événement <xref:System.Windows.Forms.Control.Enter> du contrôle survient.  Cet exemple permet de vérifier si la zone de texte comporte une valeur pour la propriété <xref:System.Windows.Forms.TextBox.Text%2A> qui n'est pas `null` et ne correspond pas à une chaîne vide.  Lorsque la zone de texte reçoit le focus, le texte actuel de cette dernière est sélectionné.  Le gestionnaire d'événements `TextBox1_Enter` doit être lié au contrôle ; pour plus d'informations, consultez [Comment : créer des gestionnaires d'événements pour les Windows Forms au moment de l'exécution](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Pour tester cet exemple, appuyez sur la touche Tab jusqu'à ce que la zone de texte ait le focus.  Si vous cliquez dans la zone de texte, le texte est désélectionné.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)