---
title: "Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler"
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
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3f61828b4c8b65ae984685610d6d8609953376a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler
Sur un Windows Form, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle soit le bouton Annuler. Un bouton cancel chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quels que soient les autres contrôles du formulaire a le focus. Ce bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.  
  
### <a name="to-designate-the-cancel-button"></a>Pour désigner le bouton Annuler  
  
1.  Valeur du formulaire <xref:System.Windows.Forms.Form.CancelButton%2A> propriété approprié <xref:System.Windows.Forms.Button> contrôle.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Guide pratique pour désigner un contrôle Button Windows Forms comme bouton Accepter](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
