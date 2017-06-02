---
title: "Comment&#160;: envoyer des donn&#233;es &#224; l&#39;enfant MDI actif | Microsoft Docs"
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
  - "formulaires enfants"
  - "Presse-papiers, obtenir des données à partir de"
  - "Presse-papiers, coller"
  - "MDI, envoyer des données aux formulaires"
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: envoyer des donn&#233;es &#224; l&#39;enfant MDI actif
Il vous arrivera souvent, dans le contexte des [applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), de devoir envoyer des données à la fenêtre enfant active, par exemple pour coller dans une application MDI les données que l'utilisateur a placées dans le Presse\-papiers.  
  
> [!NOTE]
>  Pour plus d'informations sur la façon de déterminer quelle fenêtre enfant a le focus et envoyer son contenu au Presse\-papiers, consultez [Détermination de l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).  
  
### Pour envoyer des données à la fenêtre MDI enfant active à partir du Presse\-papiers  
  
1.  Dans une méthode, copiez le texte du Presse\-papiers dans le contrôle actif du formulaire enfant actif.  
  
    > [!NOTE]
    >  Cet exemple suppose qu'il existe un formulaire MDI parent \(`Form1`\) doté d'une ou de plusieurs fenêtres MDI enfants contenant un contrôle <xref:System.Windows.Forms.RichTextBox>.  Pour plus d'informations, consultez [Création de formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
  
    ```  
  
## Voir aussi  
 [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [Comment : déterminer l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [Comment : réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)