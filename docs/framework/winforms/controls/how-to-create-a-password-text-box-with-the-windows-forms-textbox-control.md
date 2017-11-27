---
title: "Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caf5cef9e23134715101545902e32e72d63c0aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms
Une zone de mot de passe est une zone de texte Windows Forms qui affiche les caractères d’espace réservé lorsqu’un utilisateur tape une chaîne.  
  
### <a name="to-create-a-password-text-box"></a>Pour créer une zone de texte mot de passe  
  
1.  Définir le <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriété de la <xref:System.Windows.Forms.TextBox> contrôle à un caractère spécifique.  
  
     Le <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriété spécifie le caractère affiché dans la zone de texte. Par exemple, si vous souhaitez que des astérisques s’affichent dans la zone de mot de passe, spécifiez * pour la <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriété dans la fenêtre Propriétés. Ensuite, indépendamment du caractère qu’un utilisateur tape dans la zone de texte, un astérisque s’affiche.  
  
2.  (Facultatif) Définir le <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> propriété. La propriété détermine le nombre de caractères peut être tapé dans la zone de texte. Si la longueur maximale est dépassée, le système émet un signal sonore et la zone de texte n’accepte pas plus de caractères. Notez que vous pouvez souhaiter pas cela en tant que la longueur maximale d’un mot de passe peut être utilisé à des pirates cherchant à deviner le mot de passe.  
  
     L’exemple de code suivant montre comment initialiser une zone de texte qui accepte une chaîne de 14 caractères au maximum et affichera des astérisques à la place de la chaîne. Le `InitializeMyControl` procédure s’exécutera pas automatiquement ; il doit être appelé.  
  
    > [!IMPORTANT]
    >  À l’aide de la <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriété sur une zone de texte permet de garantir que les autres personnes ne seront pas en mesure de déterminer un mot de passe utilisateur observant la saisie de celui-ci. Cette mesure de sécurité ne couvre pas toute sorte de stockage ou la transmission du mot de passe qui peut se produire en raison de votre logique d’application. Étant donné que le texte entré n’est pas chiffré en aucune façon, vous devez le considérer comme vous le feriez pour d’autres données confidentielles. Même si elle n’apparaît pas en tant que tel, le mot de passe est toujours traité comme une chaîne de texte brut (sauf si vous avez implémenté une mesure de sécurité supplémentaire).  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextBox>  
 [Vue d’ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Guide pratique pour insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
