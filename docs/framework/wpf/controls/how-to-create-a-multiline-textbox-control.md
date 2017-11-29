---
title: "Comment : créer un contrôle TextBox multiligne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244eb38ea47bbd7376c2f8c6f5b2609fbd9c4330
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="6ff4f-102">Comment : créer un contrôle TextBox multiligne</span><span class="sxs-lookup"><span data-stu-id="6ff4f-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="6ff4f-103">Cet exemple montre comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un <xref:System.Windows.Controls.TextBox> contrôle se développe automatiquement pour s’adapter à plusieurs lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="6ff4f-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff4f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ff4f-104">Example</span></span>  
 <span data-ttu-id="6ff4f-105">Définition de la <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribut **encapsuler** amène le texte entré à la ligne vers une nouvelle ligne lorsque le bord de la <xref:System.Windows.Controls.TextBox> contrôle est atteinte, développer automatiquement le <xref:System.Windows.Controls.TextBox> contrôle pour faire de la place pour une nouvelle ligne, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6ff4f-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="6ff4f-106">Définition de la <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribut **true** provoque une nouvelle ligne à insérer lorsque la touche retournée est activée, développer à nouveau automatiquement le <xref:System.Windows.Controls.TextBox> pour faire place pour une nouvelle ligne, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6ff4f-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="6ff4f-107">Le <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribut ajoute une barre de défilement à la <xref:System.Windows.Controls.TextBox>, de sorte que le contenu de la <xref:System.Windows.Controls.TextBox> puisse être défilé si le <xref:System.Windows.Controls.TextBox> s’étend au-delà de la taille de la trame ou fenêtre qui l’entoure.</span><span class="sxs-lookup"><span data-stu-id="6ff4f-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="6ff4f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ff4f-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="6ff4f-109">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="6ff4f-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="6ff4f-110">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6ff4f-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
