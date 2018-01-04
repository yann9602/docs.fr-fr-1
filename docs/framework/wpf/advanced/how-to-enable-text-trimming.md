---
title: "Comment : activer la suppression de texte"
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
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdaafa62815c75d8ab364a18d909d867f90052c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="684f4-102">Comment : activer la suppression de texte</span><span class="sxs-lookup"><span data-stu-id="684f4-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="684f4-103">Cet exemple illustre l’utilisation et les effets des valeurs disponibles dans le <xref:System.Windows.TextTrimming> énumération.</span><span class="sxs-lookup"><span data-stu-id="684f4-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="684f4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="684f4-104">Example</span></span>  
 <span data-ttu-id="684f4-105">L’exemple suivant définit un <xref:System.Windows.Controls.TextBlock> élément avec la <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ensemble d’attributs.</span><span class="sxs-lookup"><span data-stu-id="684f4-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="684f4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="684f4-106">Example</span></span>  
 <span data-ttu-id="684f4-107">Paramètre correspondant <xref:System.Windows.TextTrimming> propriété dans le code est illustrée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="684f4-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="684f4-108">Il existe actuellement trois options pour le texte de la suppression : **CharacterEllipsis**, **WordEllipsis**, et **aucun**.</span><span class="sxs-lookup"><span data-stu-id="684f4-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="684f4-109">Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **CharacterEllipsis**, texte est tronqué et poursuivi avec les points de suspension du caractère le plus proche de la bordure de la suppression.</span><span class="sxs-lookup"><span data-stu-id="684f4-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="684f4-110">Ce paramètre tend à rogner le texte pour qu’il s’adapte mieux aux limites de la suppression, mais il peut provoquer la suppression partielle de certains mots.</span><span class="sxs-lookup"><span data-stu-id="684f4-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="684f4-111">L’illustration suivante montre l’effet de ce paramètre sur un <xref:System.Windows.Controls.TextBlock> similaire à celui défini ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="684f4-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="684f4-112">![Exemple : TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="684f4-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="684f4-113">Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **WordEllipsis**, texte est tronqué et poursuivi avec les points de suspension à la fin du premier mot entier le plus proche de la bordure de la suppression.</span><span class="sxs-lookup"><span data-stu-id="684f4-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="684f4-114">Ce paramètre n’affiche pas les mots partiellement ajustées, mais ne tend ne pas à rogner le texte avec autant que la **CharacterEllipsis** paramètre.</span><span class="sxs-lookup"><span data-stu-id="684f4-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="684f4-115">L’illustration suivante montre l’effet de ce paramètre sur le <xref:System.Windows.Controls.TextBlock> défini ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="684f4-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="684f4-116">![Exemple : TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="684f4-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="684f4-117">Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **aucun**, aucune suppression de texte n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="684f4-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="684f4-118">Dans ce cas, le texte est simplement rogné à la limite du conteneur de texte parent.</span><span class="sxs-lookup"><span data-stu-id="684f4-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="684f4-119">L’illustration suivante montre l’effet de ce paramètre sur un <xref:System.Windows.Controls.TextBlock> similaire à celui défini ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="684f4-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="684f4-120">![Exemple : TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="684f4-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
