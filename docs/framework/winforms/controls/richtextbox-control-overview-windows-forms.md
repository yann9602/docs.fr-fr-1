---
title: "Vue d&#39;ensemble du contr&#244;le RichTextBox (Windows Forms) | Microsoft Docs"
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
  - "RichTextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "RichTextBox (contrôle Windows Forms), à propos du contrôle RichTextBox"
  - "zones de texte, à propos des zones de texte"
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Vue d&#39;ensemble du contr&#244;le RichTextBox (Windows Forms)
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms permet d'afficher, d'entrer et de manipuler du texte mis en forme.  Le contrôle <xref:System.Windows.Forms.RichTextBox> effectue les mêmes tâches que le contrôle <xref:System.Windows.Forms.TextBox>, mais il peut également afficher des polices, des couleurs et des liens, charger du texte et des images incorporées à partir d'un fichier, ainsi que rechercher des caractères spécifiques.  Le contrôle <xref:System.Windows.Forms.RichTextBox> est généralement utilisé pour fournir des fonctionnalités de manipulation et d'affichage de texte semblables à celles des applications de traitement de texte comme Microsoft Word.  À l'instar du contrôle <xref:System.Windows.Forms.TextBox>, le contrôle <xref:System.Windows.Forms.RichTextBox> peut afficher des barres de défilement, mais contrairement au contrôle <xref:System.Windows.Forms.TextBox>, son comportement par défaut consiste à afficher les barres horizontale et verticale et il propose des paramètres de barre de défilement supplémentaires.  
  
## Utilisation du contrôle RichTextBox  
 Comme pour le contrôle <xref:System.Windows.Forms.TextBox>, le texte affiché est défini par la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A>.  Le contrôle <xref:System.Windows.Forms.RichTextBox> est doté de nombreuses propriétés de mise en forme du texte.  Pour plus d'informations sur ces propriétés, consultez [Comment : définir les attributs de police du contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) et [Comment : définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md).  Pour manipuler les fichiers, les méthodes <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> et <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> peuvent afficher et écrire plusieurs formats de fichier \(tels que texte brut, texte brut Unicode et texte riche \(RTF\).  Pour obtenir la liste des formats de fichier, consultez [RichTextBoxStreamType, énumération](frlrfSystemWindowsFormsRichTextBoxStreamTypeClassTopic).  Vous pouvez utiliser la méthode <xref:System.Windows.Forms.RichTextBox.Find%2A> pour rechercher des chaînes de texte ou des caractères spécifiques.  
  
 Vous pouvez également utiliser un contrôle <xref:System.Windows.Forms.RichTextBox> pour les liens de style Web lie en attribuant à la propriété <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> la valeur `true` et en écrivant le code pour gérer l'événement <xref:System.Windows.Forms.RichTextBox.LinkClicked>.  Pour plus d'informations, consultez [Comment : afficher des liens de style Web avec le contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md).  Vous pouvez empêcher l'utilisateur de manipuler le texte \(en tout ou partie\) en attribuant à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> la valeur `true`.  
  
 Vous pouvez annuler et rétablir la plupart des opérations d'édition dans un contrôle <xref:System.Windows.Forms.RichTextBox> en appelant les méthodes <xref:System.Windows.Forms.TextBoxBase.Undo%2A> et <xref:System.Windows.Forms.RichTextBox.Redo%2A>.  La méthode <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> vous permet de déterminer si la dernière opération annulée par l'utilisateur peut être réappliquée au contrôle.  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)