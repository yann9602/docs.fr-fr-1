---
title: "Comment : utiliser le modèle maître/détail avec des données XML hiérarchiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ef460664b3701f4942b8c28b8e39f891d7c871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="d9b70-102">Comment : utiliser le modèle maître/détail avec des données XML hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="d9b70-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="d9b70-103">Cet exemple montre comment implémenter le scénario maître / détail avec [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données.</span><span class="sxs-lookup"><span data-stu-id="d9b70-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9b70-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9b70-104">Example</span></span>  
 <span data-ttu-id="d9b70-105">Cet exemple est la [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] version des données de l’exemple abordé dans [utiliser le modèle maître / détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9b70-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="d9b70-106">Dans cet exemple, les données sont dans le fichier `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="d9b70-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="d9b70-107">Notez comment le troisième <xref:System.Windows.Controls.ListBox> contrôle effectue le suivi des modifications de la sélection dans la seconde <xref:System.Windows.Controls.ListBox> en le liant à son <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d9b70-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9b70-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9b70-108">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="d9b70-109">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="d9b70-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
