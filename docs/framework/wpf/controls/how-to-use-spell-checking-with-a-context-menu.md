---
title: "Comment&#160;: utiliser la v&#233;rification de l&#39;orthographe avec un menu contextuel | Microsoft Docs"
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
  - "activer la vérification de l'orthographe dans une zone de texte (WPF)"
  - "réactiver la vérification de l'orthographe dans une zone de texte (WPF)"
  - "vérification de l'orthographe avec un menu contextuel (WPF)"
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: utiliser la v&#233;rification de l&#39;orthographe avec un menu contextuel
Par défaut, lorsque vous activez la correction orthographique dans un contrôle d'édition comme <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>, vous placez des options de correction orthographique dans le menu contextuel.  Par exemple, lorsque les utilisateurs cliquent avec le bouton droit sur un mot mal orthographié, ils obtiennent un ensemble de propositions ou l'option **Ignorer tout**.  Toutefois, lorsque vous remplacez le menu contextuel par défaut par votre propre menu contextuel personnalisé, cette fonctionnalité est perdue et vous devez écrire le code pour revalider la fonction de correction orthographique dans le menu contextuel.  L'exemple suivant indique comment activer cette fonctionnalité sur un <xref:System.Windows.Controls.TextBox>.  
  
## Exemple  
 L'exemple suivant illustre le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui crée un <xref:System.Windows.Controls.TextBox> avec des événements utilisés pour implémenter le menu contextuel.  
  
 [!code-xml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## Exemple  
 L'exemple suivant illustre le code qui implémente le menu contextuel.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Le code utilisé à cette fin avec un <xref:System.Windows.Controls.RichTextBox> est similaire.  La principale différence se situe au niveau du paramètre transmis à la méthode `GetSpellingError`.  Pour un <xref:System.Windows.Controls.TextBox>, passez l'index d'entiers de la position du signe insertion :  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Pour un <xref:System.Windows.Controls.RichTextBox>, transmettez le <xref:System.Windows.Documents.TextPointer> qui indique la position du signe insertion :  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [Activer la vérification de l'orthographe dans un contrôle d'édition de texte](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)   
 [Utiliser un menu contextuel personnalisé avec un TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)