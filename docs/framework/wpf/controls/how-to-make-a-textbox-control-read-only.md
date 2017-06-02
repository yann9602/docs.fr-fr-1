---
title: "Comment&#160;: mettre un contr&#244;le TextBox en lecture seule | Microsoft Docs"
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
  - "contrôles TextBox en lecture seule"
  - "TextBox (contrôle en lecture seule)"
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: mettre un contr&#244;le TextBox en lecture seule
Cet exemple montre comment configurer un contrôle <xref:System.Windows.Controls.TextBox> afin d'interdire toute entrée ou modification effectuée par l'utilisateur.  
  
## Exemple  
 Pour empêcher les utilisateurs de modifier le contenu d'un contrôle <xref:System.Windows.Controls.TextBox>, affectez la valeur **true** à l'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>.  
  
 [!code-xml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 L'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> affecte uniquement les entrées d'utilisateur, mais pas le texte défini dans la description [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] d'un contrôle <xref:System.Windows.Controls.TextBox> ni le texte défini par programme via la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 Par défaut, <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> a la valeur **false**.  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)