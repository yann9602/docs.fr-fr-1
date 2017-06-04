---
title: "Comment&#160;: afficher des lignes multiples dans le contr&#244;le TextBox Windows Forms | Microsoft Docs"
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
  - "retour chariot"
  - "CRLF"
  - "fin de ligne"
  - "saut de ligne"
  - "MultiLine (propriété dans le contrôle TextBox)"
  - "newline"
  - "ScrollBars (propriété), dans les contrôles TextBox"
  - "TextBox (contrôle Windows Forms), afficher des lignes multiples"
  - "WordWrap (propriété)"
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: afficher des lignes multiples dans le contr&#244;le TextBox Windows Forms
Par défaut, le contrôle <xref:System.Windows.Forms.TextBox> Windows Forms affiche une seule ligne de texte et n'affiche pas les barres de défilement.  Si le texte est plus long que l'espace disponible, seule une partie du texte est visible.  Vous pouvez modifier ce comportement par défaut en attribuant les valeurs appropriées aux propriétés <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> et <xref:System.Windows.Forms.TextBox.ScrollBars%2A>.  
  
### Pour afficher un retour chariot dans le contrôle TextBox  
  
-   Pour afficher un retour chariot dans un contrôle <xref:System.Windows.Forms.TextBox> multiligne, utilisez la propriété <xref:System.Environment.NewLine%2A>.  
  
     Sachez que l'interprétation des caractères d'échappement \(\\\) est spécifique au langage.  Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de caractères retour chariot\-saut de ligne.  
  
### Pour afficher plusieurs lignes dans le contrôle TextBox  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`.  Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> a la valeur `true` \(valeur par défaut\), le texte du contrôle apparaîtra comme un ou plusieurs paragraphes ; sinon, il apparaîtra comme une liste dans laquelle certaines lignes peuvent être tronquées au niveau du bord du contrôle.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |------------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars>|Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours au contrôle.  L'utilisateur peut utiliser le pointeur de la souris pour se déplacer dans le contrôle si le texte est trop long pour être affiché en entier en une seule fois.|  
    |<xref:System.Windows.Forms.ScrollBars>|Utilisez cette valeur si vous voulez afficher une liste de lignes, dont certaines peuvent être plus longues que la largeur du contrôle <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.Windows.Forms.ScrollBars>|Utilisez cette valeur s'il est possible que la liste soit plus longue que la hauteur du contrôle.|  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |------------|-----------------|  
    |`false`|Le texte dans le contrôle ne sera pas automatiquement renvoyé à la ligne, donc il défilera vers la droite jusqu'au prochain saut de ligne.  Utilisez cette valeur si vous avez choisi les barres de défilement <xref:System.Windows.Forms.ScrollBars> ou <xref:System.Windows.Forms.ScrollBars> ci\-dessus.|  
    |`true` \(par défaut\)|La barre de défilement horizontal n'apparaîtra pas.  Utilisez cette valeur si vous avez choisi les barres de défilement <xref:System.Windows.Forms.ScrollBars> ou <xref:System.Windows.Forms.ScrollBars> ci\-dessus afin d'afficher un ou plusieurs paragraphes.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)