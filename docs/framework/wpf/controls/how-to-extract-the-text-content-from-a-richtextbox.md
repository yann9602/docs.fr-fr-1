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
ms.openlocfilehash: f24b71bcb5f013c4b7054dd0948e5f2709230a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="13c98-102">Comment : extraire le texte d'un RichTextBox</span><span class="sxs-lookup"><span data-stu-id="13c98-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="13c98-103">Cet exemple montre comment extraire le contenu d’un <xref:System.Windows.Controls.RichTextBox> en tant que texte brut.</span><span class="sxs-lookup"><span data-stu-id="13c98-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13c98-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="13c98-104">Example</span></span>  
 <span data-ttu-id="13c98-105">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code décrit un jeu nommé <xref:System.Windows.Controls.RichTextBox> contrôle avec du contenu simple.</span><span class="sxs-lookup"><span data-stu-id="13c98-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="13c98-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="13c98-106">Example</span></span>  
 <span data-ttu-id="13c98-107">Le code suivant implémente une méthode qui prend un <xref:System.Windows.Controls.RichTextBox> en tant qu’argument et retourne une chaîne représentant le contenu de texte brut de la <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="13c98-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="13c98-108">La méthode crée un nouveau <xref:System.Windows.Documents.TextRange> à partir du contenu de la <xref:System.Windows.Controls.RichTextBox>, à l’aide du <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> et <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> pour indiquer la plage de contenu à extraire.</span><span class="sxs-lookup"><span data-stu-id="13c98-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="13c98-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A>et <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> chacune des propriétés retournent un <xref:System.Windows.Documents.TextPointer>et sont accessibles dans le FlowDocument sous-jacent qui représente le contenu de la <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="13c98-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="13c98-110"><xref:System.Windows.Documents.TextRange>Fournit une propriété de texte, qui retourne les parties de texte brut de la <xref:System.Windows.Documents.TextRange> sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="13c98-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="13c98-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13c98-111">See Also</span></span>  
 [<span data-ttu-id="13c98-112">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="13c98-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="13c98-113">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="13c98-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
