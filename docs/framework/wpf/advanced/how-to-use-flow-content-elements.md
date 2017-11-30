---
title: "Guide pratique pour utiliser les éléments de contenu de flux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1350a380e97631ac290e57de64fec696535fecc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="6d91b-102">Guide pratique pour utiliser les éléments de contenu de flux</span><span class="sxs-lookup"><span data-stu-id="6d91b-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="6d91b-103">L’exemple suivant illustre l’utilisation déclarative de différents éléments de contenu de flux et les attributs associés.</span><span class="sxs-lookup"><span data-stu-id="6d91b-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="6d91b-104">Parmi les éléments et attributs illustrés figurent :</span><span class="sxs-lookup"><span data-stu-id="6d91b-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="6d91b-105"><xref:System.Windows.Documents.Bold> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="6d91b-106">Attribut <xref:System.Windows.Documents.Block.BreakPageBefore%2A></span><span class="sxs-lookup"><span data-stu-id="6d91b-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="6d91b-107">Attribut <xref:System.Windows.Documents.TextElement.FontSize%2A></span><span class="sxs-lookup"><span data-stu-id="6d91b-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="6d91b-108"><xref:System.Windows.Documents.Italic> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="6d91b-109"><xref:System.Windows.Documents.LineBreak> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="6d91b-110"><xref:System.Windows.Documents.List> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="6d91b-111"><xref:System.Windows.Documents.ListItem> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="6d91b-112"><xref:System.Windows.Documents.Paragraph> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="6d91b-113"><xref:System.Windows.Documents.Run> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="6d91b-114"><xref:System.Windows.Documents.Section> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="6d91b-115"><xref:System.Windows.Documents.Span> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="6d91b-116"><xref:System.Windows.Documents.Typography.Variants%2A>attribut (exposant et indice)</span><span class="sxs-lookup"><span data-stu-id="6d91b-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="6d91b-117"><xref:System.Windows.Documents.Underline> (élément)</span><span class="sxs-lookup"><span data-stu-id="6d91b-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d91b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d91b-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
