---
title: "Comment : positionner le curseur au début ou à la fin du texte dans un contrôle TextBox"
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
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0efa81a9606235b214f30a8c6febb94ea2968714
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="e154d-102">Comment : positionner le curseur au début ou à la fin du texte dans un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="e154d-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="e154d-103">Cet exemple montre comment positionner le curseur au début ou à la fin du contenu texte d’un <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e154d-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e154d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e154d-104">Example</span></span>  
 <span data-ttu-id="e154d-105">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code décrit une <xref:System.Windows.Controls.TextBox> contrôler et lui assigne un nom.</span><span class="sxs-lookup"><span data-stu-id="e154d-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="e154d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e154d-106">Example</span></span>  
 <span data-ttu-id="e154d-107">Pour positionner le curseur au début du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez le <xref:System.Windows.Controls.TextBox.Select%2A> (méthode) et spécifiez la sélection de la position de départ de 0 et une longueur de sélection de 0.</span><span class="sxs-lookup"><span data-stu-id="e154d-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="e154d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e154d-108">Example</span></span>  
 <span data-ttu-id="e154d-109">Pour positionner le curseur à la fin du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez le <xref:System.Windows.Controls.TextBox.Select%2A> (méthode) et spécifier la position de départ de sélection égale à la longueur du contenu texte et une longueur de sélection de 0.</span><span class="sxs-lookup"><span data-stu-id="e154d-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="e154d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e154d-110">See Also</span></span>  
 [<span data-ttu-id="e154d-111">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="e154d-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="e154d-112">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="e154d-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
