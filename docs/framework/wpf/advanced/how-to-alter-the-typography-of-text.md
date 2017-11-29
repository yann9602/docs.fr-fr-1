---
title: "Comment : modifier la typographie d'un texte"
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
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd18434c971831ea49813cda4ffdbc462154511a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="f00cc-102">Comment : modifier la typographie d'un texte</span><span class="sxs-lookup"><span data-stu-id="f00cc-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="f00cc-103">L’exemple suivant montre comment définir la <xref:System.Windows.Documents.TextElement.Typography%2A> d’attribut, à l’aide de <xref:System.Windows.Documents.Paragraph> en tant que l’élément de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="f00cc-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f00cc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f00cc-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="f00cc-105">La figure suivante montre le rendu de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="f00cc-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="f00cc-106">![Capture d’écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="f00cc-106">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="f00cc-107">Par contraste, l’illustration suivante montre comment s’affiche un exemple similaire avec des propriétés typographiques par défaut.</span><span class="sxs-lookup"><span data-stu-id="f00cc-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="f00cc-108">![Capture d’écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="f00cc-108">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="f00cc-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f00cc-109">Example</span></span>  
 <span data-ttu-id="f00cc-110">L’exemple suivant montre comment définir le <xref:System.Windows.Controls.TextBox.Typography%2A> propriété par programmation.</span><span class="sxs-lookup"><span data-stu-id="f00cc-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="f00cc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f00cc-111">See Also</span></span>  
 [<span data-ttu-id="f00cc-112">Vue d’ensemble des documents dynamiques</span><span class="sxs-lookup"><span data-stu-id="f00cc-112">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
