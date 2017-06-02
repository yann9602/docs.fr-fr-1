---
title: "Comment&#160;: d&#233;finir les attributs de police du contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "fichiers .rtf, mettre en forme dans le contrôle RichTextBox"
  - "polices, modifier les attributs dans le contrôle RichTextBox"
  - "mettre en forme (Windows Forms)"
  - "RichTextBox (contrôle Windows Forms), définir des attributs de police"
  - "fichiers RTF, mettre en forme dans le contrôle RichTextBox"
  - "texte (Windows Forms)"
  - "zones de texte, mettre en forme du texte"
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;finir les attributs de police du contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms est doté de nombreuses options de mise en forme du texte qu'il affiche.  Vous pouvez afficher les caractères sélectionnés en gras, soulignés ou en italique à l'aide de la propriété <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>.  Vous pouvez également utiliser cette propriété pour changer la taille et la police des caractères sélectionnés.  La propriété <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> permet de modifier la couleur des caractères sélectionnés.  
  
### Pour modifier l'apparence des caractères  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> une police appropriée.  
  
     Pour permettre aux utilisateurs de définir la famille de polices, la taille et la police d'une application, vous utiliserez généralement le composant <xref:System.Windows.Forms.FontDialog>.  Pour une vue d'ensemble, consultez [Vue d'ensemble du composant FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> une couleur appropriée.  
  
     Pour permettre aux utilisateurs de définir la couleur dans une application, vous utiliserez généralement le composant <xref:System.Windows.Forms.ColorDialog>.  Pour une vue d'ensemble, consultez [Vue d'ensemble du composant ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  Ces propriétés n'affectent que le texte sélectionné ou, si aucun texte n'est sélectionné, le texte tapé à l'emplacement actuel du point d'insertion.  Pour plus d'informations sur la sélection de texte par programme, consultez [TextBoxBase.Select, méthode](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic).  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)