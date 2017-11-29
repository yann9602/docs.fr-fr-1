---
title: "Comment : utiliser la vérification de l'orthographe avec un menu contextuel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 257f343a7fa01e251159797a83e89b533292b6b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Comment : utiliser la vérification de l'orthographe avec un menu contextuel
Par défaut, lorsque vous activez la vérification orthographique dans un contrôle d’édition, tels que <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>, vous obtenez les options de vérification orthographique dans le menu contextuel. Par exemple, les utilisateurs le droit d’un mot mal orthographié, ils obtiennent un ensemble de suggestions orthographiques ou l’option **ignorer tout**. Toutefois, lorsque vous remplacez le menu de contexte par défaut avec votre propre menu contextuel personnalisé, cette fonctionnalité n’est perdue, et vous devez écrire du code pour réactiver la fonctionnalité de vérification orthographique dans le menu contextuel. L’exemple suivant montre comment activer cette fonctionnalité sur un <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui crée un <xref:System.Windows.Controls.TextBox> avec des événements qui sont utilisées pour implémenter le menu contextuel.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le code qui implémente le menu contextuel.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Le code utilisé pour y parvenir avec un <xref:System.Windows.Controls.RichTextBox> est similaire. La principale différence réside dans le paramètre passé à la `GetSpellingError` (méthode). Pour un <xref:System.Windows.Controls.TextBox>, passez à l’index de l’entier de la position du point d’insertion :  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Pour un <xref:System.Windows.Controls.RichTextBox>, passez le <xref:System.Windows.Documents.TextPointer> qui spécifie la position du point d’insertion :  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Vue d’ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Activer la vérification de l'orthographe dans un contrôle d'édition de texte](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [Utiliser un menu contextuel personnalisé avec un TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
