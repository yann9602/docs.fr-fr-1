---
title: "Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms"
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
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8de64ac28fe57e3c448c671859053fad4aae3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="1cbb5-102">Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cbb5-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="1cbb5-103">Lorsque les Windows Forms <xref:System.Windows.Forms.TextBox> contrôle reçoit d’abord le focus, l’insertion de la valeur par défaut dans la zone de texte située à gauche du texte existant.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="1cbb5-104">L’utilisateur peut déplacer le point d’insertion avec le clavier ou la souris.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="1cbb5-105">Si la zone de texte perd, puis reprend le focus, le point d’insertion sera, là où l’utilisateur a placé en dernier.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="1cbb5-106">Dans certains cas, ce comportement peut être déconcertant pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="1cbb5-107">Dans un traitement de texte, l’utilisateur peut s’y attendre nouveaux caractères apparaissent après le texte existant.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="1cbb5-108">Dans une application d’entrée de données, l’utilisateur peut attendre des nouveaux caractères à remplacer l’entrée existante.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="1cbb5-109">Le <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> et <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriétés vous permettent de modifier le comportement selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="1cbb5-110">Pour contrôler le point d’insertion dans un contrôle de zone de texte</span><span class="sxs-lookup"><span data-stu-id="1cbb5-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="1cbb5-111">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="1cbb5-112">Zéro place le point d’insertion immédiatement à gauche du premier caractère.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="1cbb5-113">(Facultatif) Définir le <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriété à la longueur du texte que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="1cbb5-114">Le code ci-dessous retourne toujours le point d’insertion à 0.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="1cbb5-115">Le `TextBox1_Enter` Gestionnaire d’événements doit être lié au contrôle ; pour plus d’informations, consultez [création de gestionnaires d’événements dans les Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1cbb5-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="1cbb5-116">Le fait de rendre le Point d’Insertion Visible par défaut</span><span class="sxs-lookup"><span data-stu-id="1cbb5-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="1cbb5-117">Le <xref:System.Windows.Forms.TextBox> point d’insertion est visible par défaut dans une nouveau formulaire uniquement si le <xref:System.Windows.Forms.TextBox> contrôle apparaît en premier dans l’ordre de tabulation.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="1cbb5-118">Sinon, le point d’insertion s’affiche uniquement si vous donnez le <xref:System.Windows.Forms.TextBox> le focus avec la souris ou du clavier.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="1cbb5-119">Pour que l’insertion de zone de texte pointent visible par défaut sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="1cbb5-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="1cbb5-120">Définir le <xref:System.Windows.Forms.TextBox> du contrôle <xref:System.Windows.Forms.Control.TabIndex%2A> propriété `0`.</span><span class="sxs-lookup"><span data-stu-id="1cbb5-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbb5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cbb5-121">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="1cbb5-122">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="1cbb5-122">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="1cbb5-123">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cbb5-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="1cbb5-124">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1cbb5-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="1cbb5-125">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="1cbb5-125">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="1cbb5-126">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cbb5-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="1cbb5-127">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cbb5-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="1cbb5-128">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="1cbb5-128">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
