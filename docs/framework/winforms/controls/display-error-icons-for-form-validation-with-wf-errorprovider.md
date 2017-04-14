---
title: "Comment&#160;: afficher des ic&#244;nes d&#39;erreur pour la validation de formulaire &#224; l&#39;aide du composant ErrorProvider Windows Forms | Microsoft Docs"
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
  - "icônes d'erreur"
  - "messages d'erreur, afficher les icônes"
  - "ErrorProvider (composant Windows Forms), afficher les icônes d'erreur"
  - "erreurs (Windows Forms), afficher aux utilisateurs"
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: afficher des ic&#244;nes d&#39;erreur pour la validation de formulaire &#224; l&#39;aide du composant ErrorProvider Windows Forms
Le composant <xref:System.Windows.Forms.ErrorProvider> Windows Forms vous permet d'afficher une icône d'erreur lorsque l'utilisateur entre des données incorrectes.  Le formulaire doit contenir au moins deux contrôles pour que vous puissiez passer de l'un à l'autre et ainsi appeler le code de validation.  
  
### Pour afficher une icône d'erreur lorsque la valeur d'un contrôle est incorrecte  
  
1.  Ajoutez deux contrôles, par exemple des zones de texte, à un Windows Form.  
  
2.  Ajoutez un composant <xref:System.Windows.Forms.ErrorProvider> au formulaire.  
  
3.  Sélectionnez le premier contrôle et ajoutez du code à son gestionnaire d'événements <xref:System.Windows.Forms.Control.Validating>.  Pour que ce code s'exécute sans problème, la procédure doit être connectée à l'événement.  Pour plus d'informations, consultez [Comment : créer des gestionnaires d'événements pour les Windows Forms au moment de l'exécution](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Le code suivant teste la validité des données entrées par l'utilisateur ; si ces données sont incorrectes, la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> est appelée.  Le premier argument de la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> spécifie le contrôle en regard duquel l'icône doit être affichée.  Le deuxième argument est le texte d'erreur à afficher.  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  Exécutez le projet.  Tapez des données incorrectes \(non numériques, dans cet exemple\) dans le premier contrôle, puis utilisez la touche TABULATION pour passer au second.  Lorsque l'icône d'erreur s'affiche, placez le pointeur de la souris sur cette icône pour afficher le texte d'erreur.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>   
 [Vue d'ensemble du composant ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [Comment : afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)