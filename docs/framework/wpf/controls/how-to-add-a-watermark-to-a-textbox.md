---
title: "Comment : ajouter un filigrane à un TextBox"
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
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4497b72f229a8f3d62ecb1829fda88ea3d76bbb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="2068b-102">Comment : ajouter un filigrane à un TextBox</span><span class="sxs-lookup"><span data-stu-id="2068b-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="2068b-103">L’exemple suivant montre comment faciliter l’utilisation d’un <xref:System.Windows.Controls.TextBox> en affichant une image d’arrière-plan explicative à l’intérieur de la <xref:System.Windows.Controls.TextBox> jusqu'à ce que l’utilisateur entre le texte, à partir de laquelle l’image est supprimée.</span><span class="sxs-lookup"><span data-stu-id="2068b-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="2068b-104">En outre, l’image d’arrière-plan est restaurée si l’utilisateur supprime son entrée.</span><span class="sxs-lookup"><span data-stu-id="2068b-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="2068b-105">Voir l’illustration ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2068b-105">See illustration below.</span></span>  
  
 <span data-ttu-id="2068b-106">![Une zone de texte avec une image d’arrière-plan](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="2068b-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2068b-107">La raison pour laquelle une image d’arrière-plan est utilisée dans cet exemple au lieu de cela, il suffit de manipuler le <xref:System.Windows.Controls.TextBox.Text%2A> propriété du <xref:System.Windows.Controls.TextBox>, est qu’une image d’arrière-plan n’interférera pas avec la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="2068b-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2068b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2068b-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2068b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2068b-109">See Also</span></span>  
 [<span data-ttu-id="2068b-110">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="2068b-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="2068b-111">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2068b-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
