---
title: "Vue d&#39;ensemble du contr&#244;le TextBox (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "zones de texte, ajouter"
  - "TextBox (contrôle Windows Forms), à propos des contrôles TextBox"
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le TextBox (Windows Forms)
Les zones de texte Windows Forms sont utilisées pour obtenir des informations de la part de l'utilisateur ou pour afficher du texte.  Le contrôle <xref:System.Windows.Forms.TextBox> est généralement utilisé pour le texte modifiable bien qu'il puisse également être en lecture seule.  Les zones de texte peuvent afficher plusieurs lignes, renvoyer le texte à la ligne selon la taille du contrôle et ajouter une mise en forme de base.  Le contrôle <xref:System.Windows.Forms.TextBox> fournit un unique style de format pour le texte affiché ou entré dans le contrôle.  Pour pouvoir afficher différents styles de mise en forme du texte, utilisez le contrôle <xref:System.Windows.Forms.RichTextBox>.  Pour plus d'informations, consultez [Vue d'ensemble du contrôle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).  
  
## Utilisation du contrôle TextBox  
 Le texte affiché par le contrôle est contenu dans la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  Par défaut, vous pouvez entrer jusqu'à 2 048 caractères dans une zone de texte.  Si vous attribuez la valeur `true` à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A>, vous pouvez entrer jusqu'à 32 Ko de texte.  La propriété <xref:System.Windows.Forms.TextBox.Text%2A> peut être définie au moment du design avec la fenêtre Propriétés, au moment de l'exécution dans le code ou par l'entrée d'utilisateur au moment de l'exécution.  Le contenu en cours d'une zone de texte peut être récupéré au moment de l'exécution en lisant la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
 L'exemple de code suivant définit le texte dans le contrôle au moment de l'exécution.  La procédure `InitializeMyControl`  ne s'exécutera pas automatiquement ; elle doit être appelée.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)