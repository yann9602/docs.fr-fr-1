---
title: "Comment&#160;: d&#233;finir des options avec les contr&#244;les CheckBox Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "checked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cases à cocher, façons de définir des options"
  - "CheckBox (contrôle Windows Forms), état activé"
  - "CheckBox (contrôle Windows Forms), façons de définir des options"
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir des options avec les contr&#244;les CheckBox Windows&#160;Forms
Le contrôle <xref:System.Windows.Forms.CheckBox> Windows Forms permet de proposer à l'utilisateur des alternatives de type Vrai\/Faux ou Oui\/Non.  Il affiche une coche lorsqu'il est sélectionné.  
  
### Pour définir des options à l'aide de contrôles CheckBox  
  
1.  Lisez la valeur de la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer son état et servez\-vous de cette valeur pour définir une option.  
  
     Dans l'exemple de code ci\-dessous, lorsque l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> du contrôle <xref:System.Windows.Forms.CheckBox> est généré, la propriété <xref:System.Windows.Forms.Control.AllowDrop%2A> du formulaire prend la valeur `false` si la case à cocher est activée.  Cette particularité est utile lorsque vous souhaitez limiter l'interaction avec l'utilisateur.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.CheckBox>   
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [Comment : répondre à un clic du contrôle CheckBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox, contrôle](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)