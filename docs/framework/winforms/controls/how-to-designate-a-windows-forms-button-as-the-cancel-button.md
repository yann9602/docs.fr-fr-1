---
title: "Comment&#160;: d&#233;signer un contr&#244;le Button Windows Forms en tant que bouton Annuler | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), désigner comme bouton Annuler"
  - "boutons, boutons Annuler"
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;signer un contr&#244;le Button Windows Forms en tant que bouton Annuler
Sur tout Windows Form, vous pouvez désigner un contrôle <xref:System.Windows.Forms.Button> comme bouton Annuler.  Lorsque l'utilisateur appuie sur la touche ENTRÉE, le bouton Annuler est sélectionné, et cela même si un autre contrôle a le focus.  Ce bouton est généralement programmé pour permettre à l'utilisateur de quitter rapidement une opération sans valider aucune action.  
  
### Pour désigner le bouton Annuler  
  
1.  Définissez la propriété <xref:System.Windows.Forms.Form.CancelButton%2A> du formulaire à l'aide du contrôle <xref:System.Windows.Forms.Button> approprié.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Form.CancelButton%2A>   
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Comment : désigner un contrôle Button Windows Forms comme bouton Accepter](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)