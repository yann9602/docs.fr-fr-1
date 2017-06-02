---
title: "Comment&#160;: d&#233;terminer le moment o&#249; les attributs de mise en forme changent dans le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), zones de texte"
  - "RichTextBox (contrôle Windows Forms), déterminer les modifications de police"
  - "SelBold (propriété)"
  - "SelChange (événement)"
  - "zones de texte, déterminer les modifications de police"
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;terminer le moment o&#249; les attributs de mise en forme changent dans le contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms est souvent utilisé pour mettre en forme du texte avec des attributs, tels que des options de police ou des styles de paragraphe.  Votre application peut avoir besoin de conserver une trace de tous les changements de mise en forme du texte pour l'affichage d'une barre d'outils, comme c'est le cas dans de nombreuses applications de traitement de texte.  
  
### Pour répondre aux changements des attributs de mise en forme  
  
1.  Écrivez du code dans le gestionnaire d'événements <xref:System.Windows.Forms.RichTextBox.SelectionChanged> de manière à réaliser une action appropriée en fonction de la valeur de l'attribut.  L'exemple suivant change l'apparence d'un bouton de barre d'outils en fonction de la valeur de la propriété <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>.  Le bouton de barre d'outils ne sera mis à jour que lorsque le point d'insertion sera déplacé dans le contrôle.  
  
     L'exemple ci\-dessous illustre un formulaire avec un contrôle <xref:System.Windows.Forms.RichTextBox> et un contrôle <xref:System.Windows.Forms.ToolBar> contenant un bouton de barre d'outils.  Pour plus d'informations sur les barres d'outils et les boutons de barre d'outils, consultez [Comment : ajouter des boutons à un contrôle ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)