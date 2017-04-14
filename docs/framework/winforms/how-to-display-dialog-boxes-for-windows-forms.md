---
title: "Comment&#160;: afficher des bo&#238;tes de dialogue pour les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "boîtes de dialogue, afficher pour les Windows Forms"
  - "boîtes de dialogue Windows Forms, afficher"
  - "Windows Forms, appeler un formulaire à partir d'un autre"
  - "Windows Forms, afficher"
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: afficher des bo&#238;tes de dialogue pour les Windows Forms
Les boîtes de dialogue s'affichent comme n'importe quel autre formulaire d'une application.  Le formulaire de démarrage est automatiquement chargé lorsque l'application est exécutée.  Pour faire apparaître dans l'application un deuxième formulaire ou une deuxième boîte de dialogue, écrivez du code pour le charger et l'afficher.  De la même manière, pour faire disparaître un formulaire ou une boîte de dialogue, écrivez du code pour le décharger ou le masquer.  
  
### Pour afficher une boîte de dialogue  
  
1.  Naviguez jusqu'au gestionnaire d'événements avec lequel vous voulez ouvrir la boîte de dialogue.  L'ouverture peut résulter de la sélection d'une commande de menu, d'un clic sur un bouton ou de tout autre événement choisi.  
  
2.  Dans le gestionnaire d'événements, ajoutez le code d'ouverture de la boîte de dialogue.  Dans cet exemple, un événement Click sur un bouton est utilisé pour afficher la boîte de dialogue :  
  
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