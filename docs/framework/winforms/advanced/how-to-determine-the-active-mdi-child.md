---
title: "Comment : déterminer l'enfant MDI actif"
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
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="ca2bd-102">Comment : déterminer l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="ca2bd-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="ca2bd-103">Parfois, vous devez fournir une commande qui fonctionne sur le contrôle qui a le focus sur le formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="ca2bd-104">Par exemple, supposons que vous souhaitez copier le texte sélectionné dans le Presse-papiers à partir de la zone de texte du formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="ca2bd-105">Vous devez créer une procédure qui copie le texte sélectionné vers le Presse-papiers à l’aide de la <xref:System.Windows.Forms.Control.Click> l’événement de l’élément de menu de copie dans le menu Edition standard.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="ca2bd-106">Comme une application MDI peut avoir plusieurs instances du même formulaire enfant, la procédure a besoin de connaître le formulaire à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="ca2bd-107">Pour spécifier le formulaire, utilisez le <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriété, qui retourne le formulaire enfant qui a le focus ou qui était actif en dernier.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="ca2bd-108">Lorsque vous avez plusieurs contrôles dans un formulaire, vous devez également spécifier quel contrôle est actif.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="ca2bd-109">Comme le <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriété, le <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriété retourne le contrôle a le focus sur le formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="ca2bd-110">La procédure ci-dessous illustre une procédure de copie qui peut être appelée à partir d’un menu de formulaire enfant, un menu sur le formulaire MDI ou un bouton de barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="ca2bd-111">Pour déterminer l’enfant MDI actif (pour copier le texte dans le Presse-papiers)</span><span class="sxs-lookup"><span data-stu-id="ca2bd-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="ca2bd-112">Dans une méthode, copiez le texte du contrôle actif du formulaire enfant actif dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca2bd-113">Cet exemple suppose qu’est un formulaire MDI parent (`Form1`) qui a une ou plusieurs fenêtres MDI enfants contenant un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ca2bd-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ca2bd-114">Pour plus d’informations, consultez [création de formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ca2bd-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca2bd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca2bd-115">See Also</span></span>  
 [<span data-ttu-id="ca2bd-116">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="ca2bd-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="ca2bd-117">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="ca2bd-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="ca2bd-118">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="ca2bd-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="ca2bd-119">Guide pratique pour envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="ca2bd-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="ca2bd-120">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="ca2bd-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
