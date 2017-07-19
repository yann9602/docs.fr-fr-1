---
title: "Comment&#160;: appeler une fonction de page | Microsoft Docs"
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
  - "appeler des fonctions de page"
  - "fonctions, appeler"
  - "fonctions de page, appeler"
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: appeler une fonction de page
Cet exemple montre comment appeler une fonction de page à partir d'une page [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## Exemple  
 Vous pouvez naviguer jusqu'à une fonction de page à l'aide d'un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], de la même manière que vous naviguez jusqu'à une page.  L'exemple suivant le démontre.  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 Si vous devez passer des données à la fonction de page, créez une instance de celle\-ci et passer les données en définissant une propriété.  Vous pouvez également passer les données à l'aide d'un constructeur non défini par défaut, ainsi qu'illustré dans l'exemple suivant.  
  
 [!code-xml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## Voir aussi  
 <xref:System.Windows.Navigation.PageFunction%601>