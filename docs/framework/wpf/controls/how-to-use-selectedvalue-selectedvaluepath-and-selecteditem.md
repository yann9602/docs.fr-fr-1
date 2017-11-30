---
title: "Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdc478d62ca97f8f61c26fbbf1ee6c3ea8b4e189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="8c1f2-102">Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem</span><span class="sxs-lookup"><span data-stu-id="8c1f2-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="8c1f2-103">Cet exemple montre comment utiliser le <xref:System.Windows.Controls.TreeView.SelectedValue%2A> et <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriétés pour spécifier une valeur pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> d’un <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c1f2-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8c1f2-104">Example</span></span>  
 <span data-ttu-id="8c1f2-105">Le <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété offre un moyen de spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> dans un <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="8c1f2-106">Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> représente un objet dans le <xref:System.Windows.Controls.ItemsControl.Items%2A> collection et <xref:System.Windows.Controls.TreeView> affiche la valeur d’une propriété unique de l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="8c1f2-107">Le <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété spécifie le chemin d’accès à la propriété qui est utilisée pour déterminer la valeur de la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="8c1f2-108">Les exemples de cette rubrique illustrent ce concept.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="8c1f2-109">L’exemple suivant montre un <xref:System.Windows.Data.XmlDataProvider> qui contient des informations sur les employés.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="8c1f2-110">L’exemple suivant définit un <xref:System.Windows.HierarchicalDataTemplate> qui affiche le `EmployeeName` et `EmployeeWorkDay` de la `Employee`.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="8c1f2-111">Notez que la <xref:System.Windows.HierarchicalDataTemplate> ne spécifie pas le `EmployeeNumber` en tant que partie du modèle.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="8c1f2-112">L’exemple suivant montre un <xref:System.Windows.Controls.TreeView> qui utilise défini précédemment <xref:System.Windows.HierarchicalDataTemplate> et qui définit les <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété le `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="8c1f2-113">Lorsque vous sélectionnez un `EmployeeName` dans les <xref:System.Windows.Controls.TreeView>, le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété retourne le `EmployeeInfo` élément de données correspondant au `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="8c1f2-114">Toutefois, étant donné que la <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> de ce <xref:System.Windows.Controls.TreeView> a la valeur `EmployeeNumber`, le <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a la valeur la `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="8c1f2-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="8c1f2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c1f2-115">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="8c1f2-116">Vue d'ensemble de TreeView</span><span class="sxs-lookup"><span data-stu-id="8c1f2-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="8c1f2-117">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="8c1f2-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
