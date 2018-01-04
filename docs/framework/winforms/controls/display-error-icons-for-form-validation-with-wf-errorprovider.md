---
title: "Comment : afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms"
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
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 738ca9670635f78e8cb04318b192127184766c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Comment : afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms
Vous pouvez utiliser Windows Forms <xref:System.Windows.Forms.ErrorProvider> composant affiche une icône d’erreur lorsque l’utilisateur entre des données non valides. Vous devez disposer d’au moins deux contrôles du formulaire afin d’onglet entre eux et ainsi appeler le code de validation.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Pour afficher une icône d’erreur lorsque la valeur d’un contrôle n’est pas valide  
  
1.  Ajoutez deux contrôles, par exemple, les zones de texte, à un Windows Form.  
  
2.  Ajouter un <xref:System.Windows.Forms.ErrorProvider> composant au formulaire.  
  
3.  Sélectionnez le premier contrôle et ajoutez du code à ses <xref:System.Windows.Forms.Control.Validating> Gestionnaire d’événements. Dans l’ordre pour ce code s’exécute correctement, la procédure doit être connectée à l’événement. Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à exécuter pour les Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Le code suivant teste la validité des données entrées par l’utilisateur ; Si les données ne seront pas valides, le <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode est appelée. Le premier argument de la <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode spécifie le contrôle à afficher à côté de l’icône. Le deuxième argument est le texte d’erreur à afficher.  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  Exécutez le projet. Type des données non valides (dans cet exemple, non numérique) dans le premier contrôle, puis onglet à la seconde. Lorsque l’icône d’erreur est affiché, placez le pointeur de la souris pour afficher le texte d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [Vue d’ensemble du composant ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Guide pratique pour afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
