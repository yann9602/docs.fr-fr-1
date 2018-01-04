---
title: "Comment : implémenter une classe CompositeCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b33e3a61b91c2f9e2362a270216038d61770b815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="a26c2-102">Comment : implémenter une classe CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="a26c2-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="a26c2-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="a26c2-103">Example</span></span>  
 <span data-ttu-id="a26c2-104">L’exemple suivant montre comment afficher plusieurs collections et éléments comme une liste à l’aide la <xref:System.Windows.Data.CompositeCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="a26c2-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="a26c2-105">Dans cet exemple, `GreekGods` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` des objets personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a26c2-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="a26c2-106">Modèles de données sont définies afin que `GreekGod` objets et `GreekHero` objets s’affichent avec un OR et une couleur d’arrière-plan cyan, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a26c2-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a26c2-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a26c2-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="a26c2-108">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="a26c2-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="a26c2-109">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a26c2-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
