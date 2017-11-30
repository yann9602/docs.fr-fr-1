---
title: "Comment : naviguer vers l'avant ou vers l'arrière dans l'historique de navigation"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="07518-102">Comment : naviguer vers l'avant ou vers l'arrière dans l'historique de navigation</span><span class="sxs-lookup"><span data-stu-id="07518-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="07518-103">Cet exemple illustre comment naviguer vers l’avant ou vers l’arrière à des entrées de l’historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="07518-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07518-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="07518-104">Example</span></span>  
 <span data-ttu-id="07518-105">Code qui s’exécute à partir du contenu dans les hôtes suivants peut naviguer vers l’avant ou vers l’historique de navigation, une entrée à la fois.</span><span class="sxs-lookup"><span data-stu-id="07518-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="07518-106"><xref:System.Windows.Navigation.NavigationWindow>à l’aide de<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="07518-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="07518-107"><xref:System.Windows.Controls.Frame>à l’aide de<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="07518-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="07518-108">Avant que vous pouvez naviguer vers l’avant à une entrée, vous devez tout d’abord vérifier que sont entrées dans l’historique de navigation avant en inspectant le **CanGoForward** propriété.</span><span class="sxs-lookup"><span data-stu-id="07518-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="07518-109">Pour naviguer vers l’avant à une entrée, vous appelez le **GoForward** (méthode).</span><span class="sxs-lookup"><span data-stu-id="07518-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="07518-110">Ceci est illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07518-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="07518-111">Avant que vous puissiez naviguer arrière d’une entrée, vous devez tout d’abord vérifier que sont entrées dans l’historique de navigation arrière en inspectant le **CanGoBack** propriété.</span><span class="sxs-lookup"><span data-stu-id="07518-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="07518-112">Pour accéder à l’arrière d’une entrée, vous appelez le **GoBack** (méthode).</span><span class="sxs-lookup"><span data-stu-id="07518-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="07518-113">Ceci est illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07518-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="07518-114">**CanGoForward**, **GoForward**, **CanGoBack**, et **GoBack** sont implémentées par <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, et <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="07518-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07518-115">Si vous appelez **GoForward**, et il n’y aucune entrée dans l’historique de navigation avant, ou si vous appelez **GoBack**, et il n’y aucune entrée dans l’historique de navigation précédent, un <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="07518-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
