---
title: "Comment : extraire le texte d'un RichTextBox"
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
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36a34e8f5a96f8b45a6c830ec3c1edeea816bd3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Comment : extraire le texte d'un RichTextBox
Cet exemple montre comment extraire le contenu d’un <xref:System.Windows.Controls.RichTextBox> en tant que texte brut.  
  
## <a name="example"></a>Exemple  
 Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code décrit un jeu nommé <xref:System.Windows.Controls.RichTextBox> contrôle avec du contenu simple.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Exemple  
 Le code suivant implémente une méthode qui prend un <xref:System.Windows.Controls.RichTextBox> en tant qu’argument et retourne une chaîne représentant le contenu de texte brut de la <xref:System.Windows.Controls.RichTextBox>.  
  
 La méthode crée un nouveau <xref:System.Windows.Documents.TextRange> à partir du contenu de la <xref:System.Windows.Controls.RichTextBox>, à l’aide du <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> et <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> pour indiquer la plage de contenu à extraire.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A>et <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> chacune des propriétés retournent un <xref:System.Windows.Documents.TextPointer>et sont accessibles dans le FlowDocument sous-jacent qui représente le contenu de la <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange>Fournit une propriété de texte, qui retourne les parties de texte brut de la <xref:System.Windows.Documents.TextRange> sous forme de chaîne.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Vue d’ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)
