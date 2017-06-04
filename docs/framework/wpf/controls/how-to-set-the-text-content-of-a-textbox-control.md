---
title: "Comment&#160;: d&#233;finir le texte d&#39;un contr&#244;le TextBox | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Texte, définir"
  - "TextBox (contrôle), définir un contenu de texte"
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir le texte d&#39;un contr&#244;le TextBox
Cet exemple montre comment utiliser la propriété <xref:System.Windows.Controls.TextBox.Text%2A> pour définir le texte initial d'un contrôle <xref:System.Windows.Controls.TextBox>.  
  
 **Remarque** Bien que la version [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de l'exemple puisse utiliser les balises `<TextBox.Text>` autour du texte du contenu  <xref:System.Windows.Controls.TextBox> de chaque bouton, cela n'est pas nécessaire car <xref:System.Windows.Controls.TextBox> applique l'attribut <xref:System.Windows.Markup.ContentPropertyAttribute> à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.  Pour plus d'informations, consultez [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
## Exemple  
 [!code-xml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## Exemple  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)