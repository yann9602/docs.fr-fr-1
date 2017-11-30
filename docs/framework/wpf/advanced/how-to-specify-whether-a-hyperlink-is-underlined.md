---
title: "Comment : spécifier si un lien hypertexte est souligné ou non"
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
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7914b3b3332b7ea0abe05b3048b5016888e2d93e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="8128a-102">Comment : spécifier si un lien hypertexte est souligné ou non</span><span class="sxs-lookup"><span data-stu-id="8128a-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="8128a-103">Le <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de flux inline qui vous permet d’héberger des liens hypertexte dans le contenu de flux.</span><span class="sxs-lookup"><span data-stu-id="8128a-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="8128a-104">Par défaut, <xref:System.Windows.Documents.Hyperlink> utilise un <xref:System.Windows.TextDecoration> objet pour afficher un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="8128a-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="8128a-105"><xref:System.Windows.TextDecoration>objets peuvent être des performances intensif à instancier, en particulier si vous avez plusieurs <xref:System.Windows.Documents.Hyperlink> objets.</span><span class="sxs-lookup"><span data-stu-id="8128a-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="8128a-106">Si vous utilisez beaucoup <xref:System.Windows.Documents.Hyperlink> éléments, vous souhaiterez afficher un soulignement uniquement lors du déclenchement d’un événement, tel que le <xref:System.Windows.ContentElement.MouseEnter> événement.</span><span class="sxs-lookup"><span data-stu-id="8128a-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="8128a-107">Dans l’exemple suivant, le soulignement pour le lien « Mon MSN » est dynamique, il n’apparaît que lorsque le <xref:System.Windows.ContentElement.MouseEnter> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="8128a-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="8128a-108">![Liens hypertexte affichant TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="8128a-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="8128a-109">Liens hypertexte définis avec TextDecorations</span><span class="sxs-lookup"><span data-stu-id="8128a-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="8128a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="8128a-110">Example</span></span>  
 <span data-ttu-id="8128a-111">L’exemple de balise suivant montre un <xref:System.Windows.Documents.Hyperlink> défini avec et sans soulignement :</span><span class="sxs-lookup"><span data-stu-id="8128a-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="8128a-112">L’exemple de code suivant montre comment créer un soulignement pour le <xref:System.Windows.Documents.Hyperlink> sur la <xref:System.Windows.ContentElement.MouseEnter> événement et le supprimer sur le <xref:System.Windows.ContentElement.MouseLeave> événement.</span><span class="sxs-lookup"><span data-stu-id="8128a-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="8128a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8128a-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="8128a-114">Optimisation des performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="8128a-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="8128a-115">Créer une décoration de texte</span><span class="sxs-lookup"><span data-stu-id="8128a-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
