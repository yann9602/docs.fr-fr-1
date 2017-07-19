---
title: "Comment&#160;: r&#233;pondre &#224; un clic du contr&#244;le Button Windows Forms | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), réponse à un clic"
  - "boutons, répondre aux événements Click"
  - "événements Click, contrôle bouton"
  - "événements Click, répondre à"
  - "double-clics"
  - "événements (Windows Forms), événements Click"
  - "exemples (Windows Forms), contrôles"
  - "MouseDown (événement)"
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: r&#233;pondre &#224; un clic du contr&#244;le Button Windows Forms
Le contrôle <xref:System.Windows.Forms.Button> Windows Forms est principalement employé pour exécuter du code lorsque l'utilisateur clique dessus.  
  
 Le fait de cliquer sur un contrôle <xref:System.Windows.Forms.Button> génère également un certain nombre d'événements, tels que <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp>.  Si vous avez l'intention d'attacher des gestionnaires d'événements à ces événements connexes, veillez à ce que leurs actions respectives ne soient pas conflictuelles.  Par exemple, si le fait de cliquer sur le bouton efface les informations que l'utilisateur a entrées dans une zone de texte, le passage du pointeur ne doit plus entraîner l'affichage d'une info\-bulle contenant les informations qui ont été effacées.  
  
 Si l'utilisateur tente de double\-cliquer sur le contrôle <xref:System.Windows.Forms.Button>, chaque clic sera traité séparément, et cela parce que le contrôle ne prend pas en charge l'événement double\-clic.  
  
### Pour répondre au clic d'un bouton  
  
-   Dans le `Click`  du bouton <xref:System.EventHandler>, écrivez le code à exécuter.  `Button1_Click`  doit être lié au contrôle.  Pour plus d'informations, consultez [Comment : créer des gestionnaires d'événements pour les Windows Forms au moment de l'exécution](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
  
    ```cpp#  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)