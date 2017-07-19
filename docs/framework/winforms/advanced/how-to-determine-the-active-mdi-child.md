---
title: "Comment&#160;: d&#233;terminer l&#39;enfant MDI actif | Microsoft Docs"
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
  - "Presse-papiers, copier les données dans"
  - "MDI, activer des formulaires"
  - "MDI, fenêtres enfants"
  - "MDI, repérer le focus"
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;terminer l&#39;enfant MDI actif
Vous aurez parfois besoin de fournir une commande opérant sur le contrôle qui a le focus dans le formulaire enfant actif.  Supposons, par exemple, que vous voulez copier un texte sélectionné dans la zone de texte du formulaire enfant vers le Presse\-papiers.  Pour ce faire, vous devez créer une procédure copiant le texte sélectionné dans le Presse\-papiers à l'aide de l'événement <xref:System.Windows.Forms.Control.Click> de l'élément Copier du menu Edition standard.  
  
 Étant donné qu'une application MDI peut posséder plusieurs instances du même formulaire enfant, la procédure doit savoir quel formulaire utiliser.  Pour spécifier le formulaire à utiliser, faites appel à la propriété <xref:System.Windows.Forms.Form.ActiveMdiChild%2A>, laquelle retourne le formulaire enfant qui a le focus ou qui était actif en dernier.  
  
 Lorsqu'il existe plusieurs contrôles dans un formulaire, vous devez également spécifier lequel est actif.  À l'instar de la propriété <xref:System.Windows.Forms.Form.ActiveMdiChild%2A>, la propriété <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> retourne le contrôle qui a le focus dans le formulaire enfant actif.  La procédure ci\-dessous montre une procédure de copie pouvant être appelée à partir d'un menu de formulaire enfant, un menu de formulaire MDI ou un bouton de la barre d'outils.  
  
### Pour déterminer l'enfant MDI actif \(et copier son texte dans le Presse\-papiers\)  
  
1.  Dans une méthode, copiez le texte du contrôle actif du formulaire enfant actif dans le Presse\-papiers.  
  
    > [!NOTE]
    >  Cet exemple suppose qu'il existe un formulaire MDI parent \(`Form1`\) doté d'une ou de plusieurs fenêtres MDI enfants contenant un contrôle <xref:System.Windows.Forms.RichTextBox>.  Pour plus d'informations, consultez [Création de formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
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
 [Comment : envoyer des données à l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [Comment : réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)