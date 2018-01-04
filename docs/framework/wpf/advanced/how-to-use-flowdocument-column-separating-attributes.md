---
title: "Comment : utiliser les attributs de séparation de colonnes de FlowDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 779dd7862ba9a6f0d8656decc3ca0791574033fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="f2559-102">Comment : utiliser les attributs de séparation de colonnes de FlowDocument</span><span class="sxs-lookup"><span data-stu-id="f2559-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="f2559-103">Cet exemple montre comment utiliser les fonctionnalités de séparation de colonnes d’un <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="f2559-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2559-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2559-104">Example</span></span>  
 <span data-ttu-id="f2559-105">L’exemple suivant définit un <xref:System.Windows.Documents.FlowDocument>et définit les <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, et <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributs.</span><span class="sxs-lookup"><span data-stu-id="f2559-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="f2559-106">Le <xref:System.Windows.Documents.FlowDocument> contient un paragraphe unique d’exemple de contenu.</span><span class="sxs-lookup"><span data-stu-id="f2559-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="f2559-107">L’illustration suivante montre les effets de la <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, et <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributs dans un rendu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="f2559-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="f2559-108">![Capture d’écran : FlowDocument intra-colonnes](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span><span class="sxs-lookup"><span data-stu-id="f2559-108">![Screenshot: FlowDocument Intra Column](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span></span>
