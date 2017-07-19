---
title: "Comment&#160;: cr&#233;er des gestionnaires d&#39;&#233;v&#233;nements pour les Windows Forms au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), gestionnaires d'événements"
  - "gestionnaires d'événements, créer"
  - "exemples (Windows Forms), gestion des événements"
  - "au moment de l'exécution, créer des gestionnaires d'événements"
  - "Windows Forms, gestion des événements"
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er des gestionnaires d&#39;&#233;v&#233;nements pour les Windows Forms au moment de l&#39;ex&#233;cution
En plus de créer des événements à l'aide du Concepteur Windows Forms, vous pouvez créer un gestionnaire d'événements au moment de l'exécution.  Cette action vous permet de connecter des gestionnaires d'événements en fonction de conditions déclenchées par le code au moment de l'exécution, plutôt que de les connecter au premier démarrage du programme.  
  
### Pour créer un gestionnaire d'événements au moment de l'exécution  
  
1.  Ouvrez le formulaire dans l'éditeur de code auquel vous voulez ajouter un gestionnaire d'événements.  
  
2.  Ajoutez à votre formulaire une méthode portant la signature de l'événement à gérer.  
  
     Par exemple, si vous gérez l'événement <xref:System.Windows.Forms.Control.Click> d'un contrôle <xref:System.Windows.Forms.Button>, vous pouvez créer la méthode suivante :  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  Ajoutez au gestionnaire d'événements le code approprié à votre application.  
  
4.  Déterminez le formulaire ou le contrôle pour lequel vous voulez créer un gestionnaire d'événements.  
  
5.  Dans une méthode de la classe de votre formulaire, ajoutez le code indiquant au gestionnaire d'événements de gérer l'événement.  Par exemple, le code suivant indique au gestionnaire d'événements `button1_Click` de gérer l'événement <xref:System.Windows.Forms.Control.Click> d'un contrôle <xref:System.Windows.Forms.Button> :  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     La méthode <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> présentée dans le code Visual Basic ci\-dessus établit un gestionnaire d'événements Click pour le bouton.  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)