---
title: "Comment : analyser l'encre avec des indications d'analyse"
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
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b97f7fe0314b6bf839e4e639e32a48f9261def73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a><span data-ttu-id="c5b3b-102">Comment : analyser l'encre avec des indications d'analyse</span><span class="sxs-lookup"><span data-stu-id="c5b3b-102">How to: Analyze Ink with Analysis Hints</span></span>
<span data-ttu-id="c5b3b-103">Un [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) fournit une indication pour le [System.Windows.Ink.InkAnalyze](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) à laquelle elle est associée.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-103">An [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) provides a hint for the [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) to which it is attached.</span></span>  <span data-ttu-id="c5b3b-104">L’indicateur s’applique à la zone spécifiée par la [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) propriété de la [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) et fournit un contexte supplémentaire à l’analyseur d’encre à améliorer la précision de la reconnaissance.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-104">The hint applies to the area specified by the [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) property of the [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) and provides extra context to the ink analyzer to improve recognition accuracy.</span></span> <span data-ttu-id="c5b3b-105">Le [System.Windows.Ink.InkAnalyze](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) s’applique à ces informations de contexte lors de l’analyse de l’encre obtenue dans zone de l’indicateur.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-105">The [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) applies this context information when analyzing ink obtained from within the hint's area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b3b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5b3b-106">Example</span></span>  
 <span data-ttu-id="c5b3b-107">L’exemple suivant est une application qui utilise plusieurs [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objets sur un formulaire qui accepte une entrée d’encre.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-107">The following example is an application that uses multiple [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objects on a form that accepts ink input.</span></span> <span data-ttu-id="c5b3b-108">L’application utilise le [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) propriété afin de fournir des informations de contexte pour chaque entrée sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-108">The application uses the [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) property to provide context information for each entry on the form.</span></span>  <span data-ttu-id="c5b3b-109">L’application utilise une analyse en arrière-plan pour analyser l’encre et efface la forme d’encre toutes les cinq secondes après que l’utilisateur arrête l’ajout de services d’encre.</span><span class="sxs-lookup"><span data-stu-id="c5b3b-109">The application uses background analysis to analyze the ink and clears the form of all ink five seconds after the user stops adding ink.</span></span>  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
