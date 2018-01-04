---
title: "Comment : envoyer des données à l'enfant MDI actif"
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
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9268e10b42653dbe0628b3e37e0fad71b35409cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="e3d5e-102">Comment : envoyer des données à l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="e3d5e-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="e3d5e-103">Souvent, dans le contexte de [Applications d’Interface multidocument (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), vous devez envoyer des données à la fenêtre enfant active, par exemple lorsque l’utilisateur colle les données du Presse-papiers dans une application MDI.</span><span class="sxs-lookup"><span data-stu-id="e3d5e-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d5e-104">Pour plus d’informations sur la vérification de la fenêtre enfant a le focus et envoyer son contenu dans le Presse-papiers, consultez [détermination de l’enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="e3d5e-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="e3d5e-105">Pour envoyer des données à la fenêtre enfant MDI active à partir du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e3d5e-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1.  <span data-ttu-id="e3d5e-106">Dans une méthode, copiez le texte dans le Presse-papiers pour le contrôle actif du formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="e3d5e-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3d5e-107">Cet exemple suppose qu’est un formulaire MDI parent (`Form1`) qui a une ou plusieurs fenêtres MDI enfants contenant un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3d5e-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="e3d5e-108">Pour plus d’informations, consultez [création de formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e3d5e-108">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3d5e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3d5e-109">See Also</span></span>  
 [<span data-ttu-id="e3d5e-110">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="e3d5e-110">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="e3d5e-111">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="e3d5e-111">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="e3d5e-112">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="e3d5e-112">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="e3d5e-113">Guide pratique pour déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="e3d5e-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="e3d5e-114">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="e3d5e-114">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
