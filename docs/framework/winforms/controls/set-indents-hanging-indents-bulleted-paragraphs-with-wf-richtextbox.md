---
title: "Guide pratique pour définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms"
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
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b1398c0438f9ebe528e9394014f5f6529ea8f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Guide pratique pour définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms
Windows Forms <xref:System.Windows.Forms.RichTextBox> contrôle possède de nombreuses options de mise en forme le texte affiché. Vous pouvez mettre en forme des paragraphes sélectionnés sous forme de listes à puces en définissant le <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriété. Vous pouvez également utiliser le <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, et <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriétés à définir la mise en retrait des paragraphes par rapport à gauche et les bords droit du contrôle et le bord gauche d’autres lignes de texte.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Pour mettre en forme un paragraphe sous forme de liste à puces  
  
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
  
### <a name="to-indent-a-paragraph"></a>Pour mettre en retrait un paragraphe  
  
1.  Définir le <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> propriété à un entier représentant la distance en pixels entre le bord gauche du contrôle et le bord gauche du texte.  
  
2.  Définir le <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriété à un entier représentant la distance en pixels entre le bord gauche de la première ligne de texte dans le paragraphe et le bord gauche des lignes suivantes dans le même paragraph. La valeur de la <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriété s’applique uniquement aux lignes d’un paragraphe qui ont été renvoyées sous la première ligne.  
  
3.  Définir le <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> à un entier représentant la distance en pixels entre le bord droit du contrôle et le bord droit du texte de la propriété.  
  
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
    >  Toutes ces propriétés affectent tous les paragraphes contenant du texte sélectionné et également le texte tapé après le point d’insertion actif. Par exemple, quand un utilisateur sélectionne un mot dans un paragraphe puis ajuste le retrait, les nouveaux paramètres s’appliquent à l’ensemble du paragraphe contenant ce mot et également à tous les paragraphes entrés ultérieurement après le paragraphe sélectionné. Pour plus d’informations sur la sélection de texte par programme, consultez <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
