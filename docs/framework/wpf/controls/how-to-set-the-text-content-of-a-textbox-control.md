---
title: "Comment : définir le texte d'un contrôle TextBox"
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
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8da173fb91745f83aac2b4461a917c1fff6e9cb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="cbdb7-102">Comment : définir le texte d'un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="cbdb7-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="cbdb7-103">Cet exemple montre comment utiliser le <xref:System.Windows.Controls.TextBox.Text%2A> propriété pour définir le texte initial d’un <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cbdb7-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="cbdb7-104">**Remarque** bien que le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version de l’exemple peut utiliser le `<TextBox.Text>` balises autour du texte du bouton de chaque <xref:System.Windows.Controls.TextBox> contenu, il n’est pas nécessaire, car le <xref:System.Windows.Controls.TextBox> s’applique le <xref:System.Windows.Markup.ContentPropertyAttribute> attribut le <xref:System.Windows.Controls.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="cbdb7-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="cbdb7-105">Pour plus d’informations, consultez [vue d’ensemble du XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="cbdb7-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbdb7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbdb7-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="cbdb7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbdb7-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="cbdb7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbdb7-108">See Also</span></span>  
 [<span data-ttu-id="cbdb7-109">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="cbdb7-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="cbdb7-110">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="cbdb7-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
