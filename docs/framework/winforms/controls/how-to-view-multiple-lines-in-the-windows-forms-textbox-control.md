---
title: "Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8f39e031835275818504151e66834f0634b7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms
Par défaut, Windows Forms <xref:System.Windows.Forms.TextBox> contrôle affiche une ligne unique de texte et n’affiche pas de barres de défilement. Si le texte est plus long que l’espace disponible, seule une partie du texte est visible. Vous pouvez modifier ce comportement par défaut en définissant le <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, et <xref:System.Windows.Forms.TextBox.ScrollBars%2A> valeurs appropriées aux propriétés.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Pour afficher un retour chariot dans le contrôle de zone de texte  
  
-   Pour afficher un retour chariot dans une ligne multi <xref:System.Windows.Forms.TextBox>, utilisez le <xref:System.Environment.NewLine%2A> propriété.  
  
     N’oubliez pas que l’interprétation des caractères d’échappement (\\) est spécifique au langage. Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de caractères de saut de ligne et de retour chariot.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Pour afficher plusieurs lignes dans le contrôle de zone de texte  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`. Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est `true` (la valeur par défaut), puis le texte du contrôle apparaîtra comme un ou plusieurs paragraphes ; sinon, il apparaîtra sous forme de liste dans laquelle certaines lignes peuvent être tronquées à la périphérie du contrôle.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours le contrôle. L’utilisateur peut utiliser le pointeur de la souris pour vous déplacer dans le contrôle si le texte est trop long à afficher à la fois.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Utilisez cette valeur si vous souhaitez afficher une liste de lignes, dont certaines peuvent être plus longue que la largeur de la <xref:System.Windows.Forms.TextBox> contrôle.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Utilisez cette valeur si la liste peut être plus longue que la hauteur du contrôle.|  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |`false`|Texte dans le contrôle ne sera pas automatiquement encapsulé, donc il défilera vers la droite jusqu'à ce qu’un saut de ligne est atteinte. Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Horizontal> les barres de défilement ou <xref:System.Windows.Forms.ScrollBars.Both>, ci-dessus.|  
    |`true` (par défaut)|La barre de défilement horizontal n’apparaître pas. Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Vertical> les barres de défilement ou <xref:System.Windows.Forms.ScrollBars.None>ci-dessus, pour afficher un ou plusieurs paragraphes.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextBox>  
 [Vue d’ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Guide pratique pour insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
