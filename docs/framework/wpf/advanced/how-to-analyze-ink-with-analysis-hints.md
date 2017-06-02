---
title: "Comment&#160;: analyser l&#39;encre avec des indications d&#39;analyse | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "objets AnalysisHintNode"
  - "analyser l'encre"
  - "encre, objets AnalysisHintNode"
  - "encre, analyser"
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: analyser l&#39;encre avec des indications d&#39;analyse
Un <xref:System.Windows.Ink.AnalysisHintNode> fournit une indication pour le <xref:System.Windows.Ink.InkAnalyzer> auquel il est attaché.  Cette indication s'applique à la zone spécifiée par la propriété <xref:System.Windows.Ink.ContextNode.Location%2A> du <xref:System.Windows.Ink.AnalysisHintNode> et fournit un contexte supplémentaire à l'analyseur d'encre afin d'améliorer l'exactitude de la reconnaissance.  <xref:System.Windows.Ink.InkAnalyzer> applique ces informations de contexte lors de l'analyse de l'encre obtenue dans la zone de l'indication.  
  
## Exemple  
 L'exemple suivant est une application qui utilise plusieurs objets <xref:System.Windows.Ink.AnalysisHintNode> sur un formulaire qui accepte l'entrée d'encre.  L'application utilise la propriété <xref:System.Windows.Ink.AnalysisHintNode.Factoid%2A> afin de fournir des informations de contexte pour chaque entrée du formulaire.  L'application utilise l'analyse d'arrière\-plan pour analyser l'encre et efface toute l'encre du formulaire cinq secondes après que l'utilisateur cesse d'ajouter de l'encre.  
  
 [!code-xml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]