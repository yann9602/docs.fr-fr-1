---
title: "Comment : afficher des boîtes de dialogue pour les Windows Forms"
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
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46e4d019bbd586c0ed46794f55c65da7bcc657f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Comment : afficher des boîtes de dialogue pour les Windows Forms
Afficher une boîte de dialogue de la même façon que vous affichez toute autre forme dans une application. Le formulaire de démarrage charge automatiquement lorsque l’application est exécutée. Pour rendre un deuxième formulaire ou une boîte de dialogue s’affichent dans l’application, écrire du code pour charger et l’afficher. De même, pour rendre le formulaire ou la boîte de dialogue zone disparaissent, écrire du code pour décharger ou le masquer.  
  
### <a name="to-display-a-dialog-box"></a>Pour afficher une boîte de dialogue  
  
1.  Accédez au gestionnaire d’événements avec lequel vous souhaitez ouvrir la boîte de dialogue. Cela peut se produire lorsqu’une commande de menu est sélectionnée, un clic sur un bouton ou de tout autre événement se produit.  
  
2.  Dans le Gestionnaire d’événements, ajoutez le code pour ouvrir la boîte de dialogue. Dans cet exemple, un événement de clic de bouton est utilisé pour afficher la boîte de dialogue :  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
