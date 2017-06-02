---
title: "Comment&#160;: d&#233;signer un contr&#244;le Button Windows Forms comme bouton Accepter | Microsoft Docs"
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
  - "bouton d'acceptation des Windows Forms"
  - "bouton (contrôle Windows Forms), désigner comme bouton par défaut"
  - "boutons, valeur par défaut sur les Windows Forms"
  - "contrôles Windows Forms, bouton par défaut dans Windows Form"
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;signer un contr&#244;le Button Windows Forms comme bouton Accepter
Sur tout Windows Form, vous pouvez désigner un contrôle <xref:System.Windows.Forms.Button> comme bouton Accepter \(également appelé bouton par défaut\).  Lorsque l'utilisateur appuie sur la touche ENTRÉE, le bouton par défaut est sélectionné, et cela même si un autre contrôle a le focus  
  
> [!NOTE]
>  Il existe des exceptions à cette règle : lorsque le contrôle qui a le focus est un autre bouton, auquel cas c'est ce deuxième bouton qui est activé, une zone de texte multiligne ou un contrôle personnalisé qui intercepte la touche ENTRÉE.  
  
### Pour désigner le bouton Accepter  
  
1.  Définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire à l'aide du contrôle <xref:System.Windows.Forms.Button> approprié.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>   
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)