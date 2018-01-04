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
# <a name="how-to-analyze-ink-with-analysis-hints"></a>Comment : analyser l'encre avec des indications d'analyse
Un [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) fournit une indication pour le [System.Windows.Ink.InkAnalyze](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) à laquelle elle est associée.  L’indicateur s’applique à la zone spécifiée par la [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) propriété de la [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) et fournit un contexte supplémentaire à l’analyseur d’encre à améliorer la précision de la reconnaissance. Le [System.Windows.Ink.InkAnalyze](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) s’applique à ces informations de contexte lors de l’analyse de l’encre obtenue dans zone de l’indicateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant est une application qui utilise plusieurs [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objets sur un formulaire qui accepte une entrée d’encre. L’application utilise le [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) propriété afin de fournir des informations de contexte pour chaque entrée sur le formulaire.  L’application utilise une analyse en arrière-plan pour analyser l’encre et efface la forme d’encre toutes les cinq secondes après que l’utilisateur arrête l’ajout de services d’encre.  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
