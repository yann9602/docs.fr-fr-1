---
title: "Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms"
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
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fe122f509890715c398bef728a98ff874b61817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms
Windows Forms <xref:System.Windows.Forms.RichTextBox> contrôle possède de nombreuses options de mise en forme le texte affiché. Vous pouvez afficher les sélectionnées caractères gras, italique ou souligné à l’aide de la <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriété. Vous pouvez également utiliser cette propriété pour changer la taille et la police des caractères sélectionnés. Le <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriété permet de modifier la couleur des caractères sélectionnés.  
  
### <a name="to-change-the-appearance-of-characters"></a>Pour changer l’apparence de caractères  
  
1.  Définir le <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriété une police appropriée.  
  
     Pour permettre aux utilisateurs de définir la police, la taille et la famille de polices dans une application, vous utiliserez généralement le <xref:System.Windows.Forms.FontDialog> composant. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Définir le <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriété une couleur appropriée.  
  
     Pour permettre aux utilisateurs de définir la couleur dans une application, vous utiliserez généralement le <xref:System.Windows.Forms.ColorDialog> composant. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
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
    >  Ces propriétés affectent uniquement le texte sélectionné ou, si aucun texte n’est sélectionné, le texte tapé à l’emplacement actif du point d’insertion. Pour plus d’informations sur la sélection de texte par programme, consultez <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
