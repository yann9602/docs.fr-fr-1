---
title: "Comment&#160;: retourner un r&#233;sultat &#224; partir d&#39;une fonction de page | Microsoft Docs"
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
  - "fonctions, retourner à partir de"
  - "fonctions de page, retourner à partir de"
  - "retourner à partir de fonctions de page"
ms.assetid: 87804905-7e8f-417b-b0e3-5622da686396
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: retourner un r&#233;sultat &#224; partir d&#39;une fonction de page
Cet exemple montre comment retourner un résultat à partir d'une fonction de page.  
  
## Exemple  
 Pour retourner un résultat à partir d'une fonction de page, vous devez appeler <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> et passer une instance de <xref:System.Windows.Navigation.ReturnEventArgs%601>.  
  
 [!code-xml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml1)]  
[!code-xml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml2)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml.cs#pagefunctionreturnaresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/GetStringPageFunction.xaml.vb#pagefunctionreturnaresultcodebehind)]  
  
## Voir aussi  
 <xref:System.Windows.Navigation.PageFunction%601>