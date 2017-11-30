---
title: "Comment : répondre à un clic du contrôle CheckBox Windows Forms"
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
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f15adb84f92c9434d6835e80f08bf1d9bd500ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="04624-102">Comment : répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04624-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="04624-103">Chaque fois qu’un utilisateur clique sur un Windows Form <xref:System.Windows.Forms.CheckBox> (contrôle), le <xref:System.Windows.Forms.Control.Click> événement se produit.</span><span class="sxs-lookup"><span data-stu-id="04624-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="04624-104">Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="04624-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="04624-105">Pour répondre aux clics de la case à cocher</span><span class="sxs-lookup"><span data-stu-id="04624-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="04624-106">Dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements, utilisez le <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété pour déterminer l’état du contrôle et effectuer toute action requise.</span><span class="sxs-lookup"><span data-stu-id="04624-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="04624-107">Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.CheckBox> (contrôle), chaque clic sera traité séparément ; autrement dit, la <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="04624-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04624-108">Lorsque le <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> propriété est `true` (la valeur par défaut), le <xref:System.Windows.Forms.CheckBox> est sélectionné automatiquement ou désactivé lorsqu’il est activé.</span><span class="sxs-lookup"><span data-stu-id="04624-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="04624-109">Dans le cas contraire, vous devez définir manuellement la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété lorsque le <xref:System.Windows.Forms.Control.Click> événement se produit.</span><span class="sxs-lookup"><span data-stu-id="04624-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="04624-110">Vous pouvez également utiliser le <xref:System.Windows.Forms.CheckBox> contrôle afin de déterminer un plan d’action.</span><span class="sxs-lookup"><span data-stu-id="04624-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="04624-111">Pour déterminer l’action lorsqu’une case à cocher est activé.</span><span class="sxs-lookup"><span data-stu-id="04624-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="04624-112">Utilisez une instruction case pour interroger la valeur de la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété pour déterminer l’action.</span><span class="sxs-lookup"><span data-stu-id="04624-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="04624-113">Lorsque le <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, le <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété peut retourner trois valeurs qui représentent la case activée, la case désactivée ou un troisième état indéterminé dans lequel la boîte d’avec un texte estompé apparence pour indiquer l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="04624-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="04624-114">Lorsque le <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, le <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété renvoie `true` pour les deux <xref:System.Windows.Forms.CheckState.Checked> et <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="04624-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04624-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04624-115">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="04624-116">Vue d'ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="04624-116">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="04624-117">Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04624-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="04624-118">CheckBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="04624-118">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
