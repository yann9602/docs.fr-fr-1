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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Comment : répondre à un clic du contrôle CheckBox Windows Forms
Chaque fois qu’un utilisateur clique sur un Windows Form <xref:System.Windows.Forms.CheckBox> (contrôle), le <xref:System.Windows.Forms.Control.Click> événement se produit. Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Pour répondre aux clics de la case à cocher  
  
1.  Dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements, utilisez le <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété pour déterminer l’état du contrôle et effectuer toute action requise.  
  
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
    >  Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.CheckBox> (contrôle), chaque clic sera traité séparément ; autrement dit, la <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement de double-clic.  
  
    > [!NOTE]
    >  Lorsque le <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> propriété est `true` (la valeur par défaut), le <xref:System.Windows.Forms.CheckBox> est sélectionné automatiquement ou désactivé lorsqu’il est activé. Dans le cas contraire, vous devez définir manuellement la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété lorsque le <xref:System.Windows.Forms.Control.Click> événement se produit.  
  
     Vous pouvez également utiliser le <xref:System.Windows.Forms.CheckBox> contrôle afin de déterminer un plan d’action.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Pour déterminer l’action lorsqu’une case à cocher est activé.  
  
1.  Utilisez une instruction case pour interroger la valeur de la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété pour déterminer l’action. Lorsque le <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, le <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété peut retourner trois valeurs qui représentent la case activée, la case désactivée ou un troisième état indéterminé dans lequel la boîte d’avec un texte estompé apparence pour indiquer l’option n’est pas disponible.  
  
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
    >  Lorsque le <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, le <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété renvoie `true` pour les deux <xref:System.Windows.Forms.CheckState.Checked> et <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.CheckBox>  
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [CheckBox, contrôle](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
