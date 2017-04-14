---
title: "Comment&#160;: contr&#244;ler le point d&#39;insertion dans un contr&#244;le TextBox Windows Forms | Microsoft Docs"
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
  - "points d'insertion, contrôles TextBox"
  - "zones de texte, contrôler le point d'insertion"
  - "TextBox (contrôle Windows Forms), point d'insertion"
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: contr&#244;ler le point d&#39;insertion dans un contr&#244;le TextBox Windows Forms
Lorsqu'un contrôle <xref:System.Windows.Forms.TextBox> Windows Forms reçoit d'abord le focus, l'insertion par défaut dans la zone de texte est à gauche du texte existant.  L'utilisateur peut déplacer le point d'insertion à l'aide du clavier ou de la souris.  Si la zone de texte perd, puis reprend le focus, le point d'insertion sera là où l'utilisateur l'a placé en dernier.  
  
 Dans certains cas, ce comportement peut déconcerter l'utilisateur.  Dans une application de traitement de texte, l'utilisateur peut s'attendre à ce que de nouveaux caractères apparaissent après le texte existant.  Dans une application d'entrée de données, l'utilisateur peut s'attendre à ce que de nouveaux caractères remplacent l'entrée existante.  Les propriétés <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> et <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vous permettent de modifier le comportement du contrôle selon vos besoins.  
  
### Pour contrôler le point d'insertion dans un contrôle TextBox  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> une valeur appropriée.  Zéro place le point d'insertion immédiatement à gauche du premier caractère.  
  
2.  \(Facultatif\) Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> la longueur du texte que vous souhaitez sélectionner.  
  
     Le code ci\-dessous retourne toujours le point d'insertion à 0.  Le gestionnaire d'événements `TextBox1_Enter` doit être lié au contrôle ; pour plus d'informations, consultez [Création de gestionnaires d'événements dans les Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## Point d'insertion visible par défaut  
 Pour que le point d'insertion <xref:System.Windows.Forms.TextBox> s'affiche par défaut dans un nouveau formulaire, le contrôle <xref:System.Windows.Forms.TextBox> doit figurer en tête dans l'ordre de tabulation.  Sinon, il s'affiche uniquement si vous donnez le focus au contrôle <xref:System.Windows.Forms.TextBox> à l'aide du clavier ou de la souris.  
  
#### Pour que le point d'insertion TextBox s'affiche par défaut dans un nouveau formulaire  
  
-   Affectez à la propriété <xref:System.Windows.Forms.Control.TabIndex%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur `0`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)