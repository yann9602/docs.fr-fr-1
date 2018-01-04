---
title: "Comment : naviguer par le biais de l’historique de Navigation"
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
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3bfc809dbe76c17859cb3fcd83f8a293a24b308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="47a5a-102">Comment : naviguer par le biais de l’historique de Navigation</span><span class="sxs-lookup"><span data-stu-id="47a5a-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="47a5a-103">Cet exemple illustre comment naviguer entrées vers l’arrière de l’historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="47a5a-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47a5a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="47a5a-104">Example</span></span>  
 <span data-ttu-id="47a5a-105">Code qui s’exécute à partir du contenu qui est hébergé dans un <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> utiliser <xref:System.Windows.Navigation.NavigationService>, ou [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] pouvez accéder par le biais de l’historique de navigation, une entrée à la fois.</span><span class="sxs-lookup"><span data-stu-id="47a5a-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> use <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="47a5a-106">Une entrée navigation nécessite tout d’abord vérifier que sont entrées dans l’historique de navigation arrière, en inspectant le **CanGoBack** propriété, avant de naviguer vers l’arrière une entrée, en appelant le **GoBack** méthode.</span><span class="sxs-lookup"><span data-stu-id="47a5a-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="47a5a-107">Ceci est illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="47a5a-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="47a5a-108">**CanGoBack** et **GoBack** sont implémentées par <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, et <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="47a5a-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47a5a-109">Si vous appelez **GoBack**, et il n’y aucune entrée dans l’historique de navigation précédent, un <xref:System.InvalidOperationException> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="47a5a-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
