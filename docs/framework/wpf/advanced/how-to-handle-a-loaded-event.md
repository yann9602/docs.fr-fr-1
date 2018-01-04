---
title: "Comment : gérer un événement chargé"
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
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 794de0e64e2f4d974091b92f211d7472d04ecd26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="26bed-102">Comment : gérer un événement chargé</span><span class="sxs-lookup"><span data-stu-id="26bed-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="26bed-103">Cet exemple montre comment gérer les <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> un scénario approprié pour gérer cet événement et événements.</span><span class="sxs-lookup"><span data-stu-id="26bed-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="26bed-104">Le gestionnaire crée un <xref:System.Windows.Controls.Button> lorsque la page se charge.</span><span class="sxs-lookup"><span data-stu-id="26bed-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26bed-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="26bed-105">Example</span></span>  
 <span data-ttu-id="26bed-106">L’exemple suivant utilise [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] avec un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="26bed-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="26bed-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26bed-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="26bed-108">Événements de la durée de vie d’un objet</span><span class="sxs-lookup"><span data-stu-id="26bed-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="26bed-109">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="26bed-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="26bed-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="26bed-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
