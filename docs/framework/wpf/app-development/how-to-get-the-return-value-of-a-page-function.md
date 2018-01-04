---
title: Guide pratique pour obtenir la valeur de retour d'une fonction de page
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
- functions [WPF], getting return values of
- page functions [WPF], getting return values of
- return values of page functions [WPF]
- getting [WPF], return values of page functions
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19a5ebf7ce686f22b65e7b464367eac63bc50b20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a><span data-ttu-id="270ef-102">Guide pratique pour obtenir la valeur de retour d'une fonction de page</span><span class="sxs-lookup"><span data-stu-id="270ef-102">How to: Get the Return Value of a Page Function</span></span>
<span data-ttu-id="270ef-103">Cet exemple montre comment obtenir le résultat retourné par une fonction de page.</span><span class="sxs-lookup"><span data-stu-id="270ef-103">This example shows how to get the result that is returned by a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="270ef-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="270ef-104">Example</span></span>  
 <span data-ttu-id="270ef-105">Pour obtenir le résultat est retourné à partir d’une fonction de page, vous devez gérer <xref:System.Windows.Navigation.PageFunction%601.Return> de la fonction de la page que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="270ef-105">To get the result that is returned from a page function, you need to handle <xref:System.Windows.Navigation.PageFunction%601.Return> of the page function you are calling.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="270ef-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="270ef-106">See Also</span></span>  
 <xref:System.Windows.Navigation.PageFunction%601>
