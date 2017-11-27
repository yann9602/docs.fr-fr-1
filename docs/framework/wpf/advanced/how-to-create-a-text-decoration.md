---
title: "Comment : créer une décoration de texte"
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
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="87580-102">Comment : créer une décoration de texte</span><span class="sxs-lookup"><span data-stu-id="87580-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="87580-103">A <xref:System.Windows.TextDecoration> objet est un ornement visuel que vous pouvez ajouter au texte.</span><span class="sxs-lookup"><span data-stu-id="87580-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="87580-104">Il existe quatre types de décorations de texte : soulignement, ligne de base, barré et surligné.</span><span class="sxs-lookup"><span data-stu-id="87580-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="87580-105">L’exemple suivant montre les emplacements des ornements de texte par rapport au texte.</span><span class="sxs-lookup"><span data-stu-id="87580-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="87580-106">![Diagramme des emplacements d’ornements de texte](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="87580-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="87580-107">Exemple de types de décoration de texte</span><span class="sxs-lookup"><span data-stu-id="87580-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="87580-108">Pour ajouter une décoration de texte à texte, créez un <xref:System.Windows.TextDecoration> de l’objet, puis modifiez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="87580-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="87580-109">Utilisez le <xref:System.Windows.TextDecoration.Location%2A> propriété pour spécifier où l’ornement de texte s’affiche, comme le trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="87580-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="87580-110">Utilisez le <xref:System.Windows.TextDecoration.Pen%2A> propriété pour spécifier l’apparence de la décoration de texte, tel qu’un remplissage uni ou la couleur de dégradé.</span><span class="sxs-lookup"><span data-stu-id="87580-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="87580-111">Si vous ne spécifiez pas une valeur pour le <xref:System.Windows.TextDecoration.Pen%2A> propriété, les valeurs par défaut de décorations de la même couleur que le texte.</span><span class="sxs-lookup"><span data-stu-id="87580-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="87580-112">Une fois que vous avez défini un <xref:System.Windows.TextDecoration> de l’objet, ajoutez-la à la <xref:System.Windows.TextDecorations> collection de l’objet de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="87580-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="87580-113">L’exemple suivant montre une décoration de texte qui a été mise en forme avec un pinceau de dégradé linéaire et un stylet en pointillés.</span><span class="sxs-lookup"><span data-stu-id="87580-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="87580-114">![Décoration de texte avec souligné dégradé linéaire](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="87580-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="87580-115">Exemple d’un soulignement mis en forme avec un dégradé linéaire pinceau et stylet en pointillés</span><span class="sxs-lookup"><span data-stu-id="87580-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="87580-116">Le <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de flux inline qui vous permet d’héberger des liens hypertexte dans le contenu de flux.</span><span class="sxs-lookup"><span data-stu-id="87580-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="87580-117">Par défaut, <xref:System.Windows.Documents.Hyperlink> utilise un <xref:System.Windows.TextDecoration> objet pour afficher un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="87580-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="87580-118"><xref:System.Windows.TextDecoration>objets peuvent être des performances intensif à instancier, en particulier si vous avez plusieurs <xref:System.Windows.Documents.Hyperlink> objets.</span><span class="sxs-lookup"><span data-stu-id="87580-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="87580-119">Si vous utilisez beaucoup <xref:System.Windows.Documents.Hyperlink> éléments, vous souhaiterez afficher un soulignement uniquement lors du déclenchement d’un événement, tel que le <xref:System.Windows.ContentElement.MouseEnter> événement.</span><span class="sxs-lookup"><span data-stu-id="87580-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="87580-120">Dans l’exemple suivant, le soulignement pour le lien « Mon MSN » est dynamique, il n’apparaît que lorsque le <xref:System.Windows.ContentElement.MouseEnter> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="87580-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="87580-121">![Liens hypertexte affichant TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="87580-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="87580-122">Liens hypertexte définis avec TextDecorations</span><span class="sxs-lookup"><span data-stu-id="87580-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="87580-123">Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="87580-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87580-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="87580-124">Example</span></span>  
 <span data-ttu-id="87580-125">Dans l’exemple de code suivant, une décoration de texte souligné utilise la valeur de la police par défaut.</span><span class="sxs-lookup"><span data-stu-id="87580-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="87580-126">Dans l’exemple de code suivant, une décoration de texte souligné est créée avec un pinceau de couleur unie pour le stylet.</span><span class="sxs-lookup"><span data-stu-id="87580-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="87580-127">Dans l’exemple de code suivant, une décoration de texte souligné est créée avec un pinceau de dégradé linéaire pour le stylet en pointillés.</span><span class="sxs-lookup"><span data-stu-id="87580-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="87580-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87580-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="87580-129">Spécifier si un lien hypertexte est souligné ou non</span><span class="sxs-lookup"><span data-stu-id="87580-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
