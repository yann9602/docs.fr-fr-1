---
title: "Comment&#160;: d&#233;finir les retraits, les retraits n&#233;gatifs de premi&#232;re ligne et les listes &#224; puces avec le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), zones de texte"
  - "RichTextBox (contrôle Windows Forms), définir des retraits et des listes à puces"
  - "fichiers RTF, mettre en forme dans le contrôle RichTextBox"
  - "zones de texte, puces"
  - "zones de texte, définir les retraits"
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir les retraits, les retraits n&#233;gatifs de premi&#232;re ligne et les listes &#224; puces avec le contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms est doté de nombreuses options de mise en forme du texte qu'il affiche.  Vous pouvez mettre en forme des paragraphes sélectionnés sous forme de listes à puces en définissant la propriété <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>.  Vous pouvez également utiliser les propriétés <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> et <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> pour définir la mise en retrait des paragraphes par rapport aux bords droit et gauche du contrôle et au bord gauche d'autres lignes de texte.  
  
### Pour mettre en forme un paragraphe sous forme de liste à puce  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> la valeur `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### Pour mettre un paragraphe en retrait  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> un entier représentant la distance en pixels entre le bord gauche du contrôle et le bord gauche du texte.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> un entier représentant la distance en pixels entre le bord gauche de la première ligne de texte du paragraphe et le bord gauche des lignes suivantes du même paragraphe.  La valeur de la propriété <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> ne s'applique qu'aux lignes d'un paragraphe qui ont été renvoyées sous la première ligne.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> un entier représentant la distance en pixels entre le bord droit du contrôle et le bord droit du texte.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  Toutes ces propriétés affectent tout paragraphe contenant du texte sélectionné, de même que le texte tapé après le point d'insertion actuel.  Par exemple, lorsqu'un utilisateur sélectionne un mot dans un paragraphe, puis ajuste la mise en retrait, les nouveaux paramètres s'appliqueront à l'ensemble du paragraphe contenant ce mot, de même qu'à tout paragraphe entré ultérieurement à la suite du paragraphe sélectionné.  Pour plus d'informations sur la sélection de texte par programme, consultez [TextBoxBase.Select, méthode](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic).  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)