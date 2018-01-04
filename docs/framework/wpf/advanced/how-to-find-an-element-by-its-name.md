---
title: "Comment : rechercher un élément par son nom"
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a><span data-ttu-id="8b608-102">Comment : rechercher un élément par son nom</span><span class="sxs-lookup"><span data-stu-id="8b608-102">How to: Find an Element by Its Name</span></span>
<span data-ttu-id="8b608-103">Cet exemple explique comment utiliser le <xref:System.Windows.FrameworkElement.FindName%2A> méthode pour rechercher un élément par son <xref:System.Windows.FrameworkElement.Name%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="8b608-103">This example describes how to use the <xref:System.Windows.FrameworkElement.FindName%2A> method to find an element by its <xref:System.Windows.FrameworkElement.Name%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b608-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b608-104">Example</span></span>  
 <span data-ttu-id="8b608-105">Dans cet exemple, la méthode à rechercher un élément particulier par son nom est écrit en tant que le Gestionnaire d’événements d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="8b608-105">In this example, the method to find a particular element by its name is written as the event handler of a button.</span></span> <span data-ttu-id="8b608-106">`stackPanel`est la <xref:System.Windows.FrameworkElement.Name%2A> de la racine de <xref:System.Windows.FrameworkElement> recherché, et la méthode d’exemple indique ensuite visuellement l’élément trouvé en effectuant un cast en tant que <xref:System.Windows.Controls.TextBlock> et modifier l’un de le <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriétés.</span><span class="sxs-lookup"><span data-stu-id="8b608-106">`stackPanel` is the <xref:System.Windows.FrameworkElement.Name%2A> of the root <xref:System.Windows.FrameworkElement> being searched, and the example method then visually indicates the found element by casting it as <xref:System.Windows.Controls.TextBlock> and changing one of the <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] properties.</span></span>  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
