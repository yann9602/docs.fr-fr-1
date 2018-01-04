---
title: "Comment : trouver un TreeViewItem dans un TreeView"
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
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 696a9e2d92b9c44e4aedbcc200b41e5548cd7411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="0c2d0-102">Comment : trouver un TreeViewItem dans un TreeView</span><span class="sxs-lookup"><span data-stu-id="0c2d0-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="0c2d0-103">Le <xref:System.Windows.Controls.TreeView> contrôle offre un moyen pratique pour afficher des données hiérarchiques.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="0c2d0-104">Si votre <xref:System.Windows.Controls.TreeView> est lié à une source de données, le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété offre un moyen pratique pour vous permettre de récupérer rapidement l’objet de données sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="0c2d0-105">Il est généralement préférable d’utiliser l’objet de données sous-jacent, mais parfois vous devez manipuler par programme contenant des données <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="0c2d0-106">Par exemple, vous devrez peut-être développer par programme le <xref:System.Windows.Controls.TreeViewItem>, ou sélectionnez un autre élément dans le <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="0c2d0-107">Pour rechercher un <xref:System.Windows.Controls.TreeViewItem> qui contient un objet de données spécifique, vous devez parcourir chaque niveau de la <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="0c2d0-108">Les éléments dans un <xref:System.Windows.Controls.TreeView> peuvent également être virtualisées pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="0c2d0-109">Dans le cas où les éléments peuvent être virtualisés, vous devez également créer un <xref:System.Windows.Controls.TreeViewItem> pour vérifier si elle contient l’objet de données.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c2d0-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c2d0-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="0c2d0-111">Description</span><span class="sxs-lookup"><span data-stu-id="0c2d0-111">Description</span></span>  
 <span data-ttu-id="0c2d0-112">L’exemple suivant recherche une <xref:System.Windows.Controls.TreeView> pour un objet spécifique et retourne l’objet qui contient <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="0c2d0-113">L’exemple vérifie que chaque <xref:System.Windows.Controls.TreeViewItem> est instancié afin que ses éléments enfants peuvent être recherchés.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="0c2d0-114">Cet exemple fonctionne également si le <xref:System.Windows.Controls.TreeView> n’utilise pas d’éléments virtualisés.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c2d0-115">L’exemple suivant fonctionne pour tout <xref:System.Windows.Controls.TreeView>, quel que soit le modèle de données sous-jacente et recherche chaque <xref:System.Windows.Controls.TreeViewItem> jusqu'à ce que l’objet est trouvé.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="0c2d0-116">Une autre technique qui offre de meilleures performances consiste à rechercher le modèle de données pour l’objet spécifié, effectuer le suivi de son emplacement dans la hiérarchie de données et recherchez correspondant <xref:System.Windows.Controls.TreeViewItem> dans le <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="0c2d0-117">Toutefois, la technique qui offre de meilleures performances nécessite une connaissance du modèle de données et ne peut pas être généralisée pour tous <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="0c2d0-118">Code</span><span class="sxs-lookup"><span data-stu-id="0c2d0-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="0c2d0-119">Le code précédent s’appuie sur une personnalisée <xref:System.Windows.Controls.VirtualizingStackPanel> qui expose une méthode nommée `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="0c2d0-120">Le code suivant définit personnalisé <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="0c2d0-121">Le code XAML suivant montre comment créer un <xref:System.Windows.Controls.TreeView> qui utilise le <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c2d0-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0c2d0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c2d0-122">See Also</span></span>  
 [<span data-ttu-id="0c2d0-123">Améliorer les performances d'un contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="0c2d0-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
