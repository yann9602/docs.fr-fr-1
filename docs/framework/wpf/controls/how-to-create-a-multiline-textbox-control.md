---
title: "Comment&#160;: cr&#233;er un contr&#244;le TextBox multiligne | Microsoft Docs"
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
  - "TextBox (contrôle), plusieurs lignes de texte"
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un contr&#244;le TextBox multiligne
Cet exemple indique comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un contrôle <xref:System.Windows.Controls.TextBox> qui se développe automatiquement pour s'adapter à plusieurs lignes de texte.  
  
## Exemple  
 L'affectation de la valeur **Wrap** à l'attribut <xref:System.Windows.Controls.TextBox.TextWrapping%2A> amène le texte entré à être renvoyé sur une nouvelle ligne lorsque le bord du contrôle <xref:System.Windows.Controls.TextBox> est atteint, et à étendre automatiquement le contrôle <xref:System.Windows.Controls.TextBox> pour faire de la place pour une nouvelle ligne, si nécessaire.  
  
 La définition de l'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> à **true** provoque l'insertion d'une nouvelle ligne lors de l'appui sur la touche RETOUR, en étendant encore une fois automatiquement le contrôle <xref:System.Windows.Controls.TextBox> pour faire de la place pour une nouvelle ligne, si nécessaire.  
  
 L'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> ajoute une barre de défilement à la <xref:System.Windows.Controls.TextBox>, afin que le contenu de la <xref:System.Windows.Controls.TextBox> puisse être défilé si la <xref:System.Windows.Controls.TextBox> se développe au delà de la taille de la trame ou fenêtre qui l'entoure.  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## Voir aussi  
 <xref:System.Windows.TextWrapping>   
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)