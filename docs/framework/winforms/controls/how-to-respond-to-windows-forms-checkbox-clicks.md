---
title: "Comment&#160;: r&#233;pondre &#224; un clic du contr&#244;le CheckBox Windows Forms | Microsoft Docs"
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
  - "cases à cocher, répondre aux événements"
  - "CheckBox (contrôle Windows Forms), événements Click"
  - "événements Click, CheckBox (contrôle)"
  - "double-clics"
  - "événements (Windows Forms), événements Click"
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: r&#233;pondre &#224; un clic du contr&#244;le CheckBox Windows Forms
Chaque fois qu'un utilisateur clique sur un contrôle <xref:System.Windows.Forms.CheckBox> Windows Forms, l'événement <xref:System.Windows.Forms.Control.Click> se produit.  Vous pouvez programmer votre application de telle sorte qu'elle effectue une action déterminée par l'état de la case à cocher.  
  
### Pour répondre à un clic du contrôle CheckBox  
  
1.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click>, utilisez la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer l'état du contrôle et effectuer toute action requise.  
  
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
    >  Si l'utilisateur tente de double\-cliquer sur le contrôle <xref:System.Windows.Forms.CheckBox>, chaque clic sera traité séparément ; et cela parce que le contrôle <xref:System.Windows.Forms.CheckBox> ne prend pas en charge l'événement double\-clic.  
  
    > [!NOTE]
    >  Lorsque la propriété <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> a la valeur `true` \(par défaut\), le <xref:System.Windows.Forms.CheckBox> est sélectionné automatiquement ou désactivé lorsqu'il fait l'objet d'un clic.  Sinon, vous devez définir manuellement la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> lorsque se produit l'événement <xref:System.Windows.Forms.Control.Click>.  
  
     Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.CheckBox> pour déterminer l'action à effectuer.  
  
### Pour déterminer l'action à effectuer à la suite d'un clic du contrôle CheckBox  
  
1.  Utilisez une instruction case pour connaître la valeur de la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> et déterminer l'action requise.  Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> a la valeur `true`, la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut retourner trois valeurs représentant la case activée, la case désactivée ou un troisième état indéterminé dans lequel la case est affichée avec une apparence estompée indiquant que l'option n'est pas disponible.  
  
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
    >  Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> a la valeur `true`, la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> retourne `true` à la fois pour <xref:System.Windows.Forms.CheckState> et <xref:System.Windows.Forms.CheckState>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.CheckBox>   
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [Comment : définir des options avec les contrôles CheckBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [CheckBox, contrôle](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)