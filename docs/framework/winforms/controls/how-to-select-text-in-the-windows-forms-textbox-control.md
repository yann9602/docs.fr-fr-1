---
title: "Comment : sélectionner du texte dans le contrôle TextBox Windows Forms"
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
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ad19f3daca43fb33e845b632ac7d92b00f544c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Comment : sélectionner du texte dans le contrôle TextBox Windows Forms
Vous pouvez sélectionner le texte par programmation dans les Windows Forms <xref:System.Windows.Forms.TextBox> contrôle. Par exemple, si vous créez une fonction qui recherche du texte pour une chaîne particulière, vous pouvez sélectionner le texte afin d’alerter visuellement le lecteur de la position de la chaîne trouvée.  
  
### <a name="to-select-text-programmatically"></a>Pour sélectionner du texte par programme  
  
1.  Définir le <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriété au début du texte que vous souhaitez sélectionner.  
  
     Le <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriété est un nombre qui indique le point d’insertion dans la chaîne de texte, 0 étant la position la plus à gauche. Si la <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est définie sur une valeur égale ou supérieure au nombre de caractères dans la zone de texte, le point d’insertion est placé après le dernier caractère.  
  
2.  Définir le <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriété à la longueur du texte que vous souhaitez sélectionner.  
  
     Le <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriété est une valeur numérique qui définit la largeur du point d’insertion. Définition de la <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> par un nombre supérieur à 0 ce nombre de caractères à sélectionner, en commençant à partir du point d’insertion.  
  
3.  (Facultatif) Accédez au texte sélectionné par le biais du <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> propriété.  
  
     Le code ci-dessous sélectionne le contenu d’un texte de zone lors du contrôle <xref:System.Windows.Forms.Control.Enter> événement se produit. Cet exemple vérifie si la zone de texte comporte une valeur pour le <xref:System.Windows.Forms.TextBox.Text%2A> propriété n’est pas `null` ou une chaîne vide. Lorsque la zone de texte reçoit le focus, le texte actuel dans la zone de texte est sélectionné. Le `TextBox1_Enter` Gestionnaire d’événements doit être lié au contrôle ; pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à exécuter pour les Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Pour tester cet exemple, appuyez sur la touche Tab jusqu'à ce que la zone de texte a le focus. Si vous cliquez dans la zone de texte, le texte est désélectionné.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextBox>  
 [Vue d’ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Guide pratique pour insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
