---
title: "Comment : répondre à un clic du contrôle Button Windows Forms"
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
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28b0467c8b589882fe5afd7e884d0de55d8ca564
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Comment : répondre à un clic du contrôle Button Windows Forms
L’utilisation de base des Windows Forms <xref:System.Windows.Forms.Button> contrôle consiste à exécuter du code lorsque le bouton est activé.  
  
 En cliquant sur un <xref:System.Windows.Forms.Button> contrôle génère également un nombre d’événements, tels que les <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, et <xref:System.Windows.Forms.Control.MouseUp> événements. Si vous souhaitez attacher des gestionnaires d’événements pour ces événements connexes, veillez à ce que leurs actions ne sont pas en conflit. Par exemple, si vous cliquez sur le bouton efface les informations que l’utilisateur a tapé dans une zone de texte, suspendant le pointeur de la souris sur le bouton ne doit pas afficher une info-bulle contenant ces informations inexistante pour l’instant.  
  
 Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.Button> (contrôle), chaque clic sera traité séparément ; autrement dit, le contrôle ne prend pas en charge l’événement de double-clic.  
  
### <a name="to-respond-to-a-button-click"></a>Pour répondre à un clic de bouton  
  
-   Dans du bouton `Click` <xref:System.EventHandler> écrire le code à exécuter. `Button1_Click`doit être lié au contrôle. Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à exécuter pour les Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
