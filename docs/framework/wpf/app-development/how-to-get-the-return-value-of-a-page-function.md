---
title: "Comment&#160;: obtenir la valeur de retour d&#39;une fonction de page | Microsoft Docs"
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
  - "fonctions, obtenir les valeurs de retour de"
  - "obtenir, valeurs de retour de fonctions de page"
  - "fonctions de page, obtenir les valeurs de retour de"
  - "valeurs de retour de fonctions de page"
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: obtenir la valeur de retour d&#39;une fonction de page
Cet exemple indique comment obtenir le résultat renvoyé par une fonction de page.  
  
## Exemple  
 Pour obtenir le résultat renvoyé par une fonction de page, vous devez gérer le <xref:System.Windows.Navigation.PageFunction%601.Return> de la fonction de page appelée.  
  
 [!code-xml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## Voir aussi  
 <xref:System.Windows.Navigation.PageFunction%601>