---
title: "Comment : grouper, trier et filtrer des données dans le contrôle DataGrid"
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
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3c8afacfafbe14794bf17a4e9a4df7c175a3668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="10db9-102">Comment : grouper, trier et filtrer des données dans le contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-102">How to: Group, Sort, and Filter Data in the DataGrid Control</span></span>
<span data-ttu-id="10db9-103">Il est souvent utile d’afficher les données dans un <xref:System.Windows.Controls.DataGrid> de différentes façons par regroupement, le tri et filtrage des données.</span><span class="sxs-lookup"><span data-stu-id="10db9-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="10db9-104">Pour regrouper, trier et filtrer les données d’une <xref:System.Windows.Controls.DataGrid>, liez-le à un <xref:System.Windows.Data.CollectionView> qui prend en charge ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="10db9-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="10db9-105">Vous pouvez ensuite travailler avec les données dans le <xref:System.Windows.Data.CollectionView> sans affecter les données sources sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="10db9-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="10db9-106">Les modifications dans la vue de collection sont répercutées dans le <xref:System.Windows.Controls.DataGrid> l’interface utilisateur (IU).</span><span class="sxs-lookup"><span data-stu-id="10db9-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>  
  
 <span data-ttu-id="10db9-107">Le <xref:System.Windows.Data.CollectionView> classe fournit le regroupement et tri des fonctionnalités pour une source de données qui implémente le <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="10db9-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="10db9-108">Le <xref:System.Windows.Data.CollectionViewSource> classe vous permet de définir les propriétés d’un <xref:System.Windows.Data.CollectionView> à partir de XAML.</span><span class="sxs-lookup"><span data-stu-id="10db9-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>  
  
 <span data-ttu-id="10db9-109">Dans cet exemple, une collection de `Task` objets est lié à un <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="10db9-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="10db9-110">Le <xref:System.Windows.Data.CollectionViewSource> est utilisé comme le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="10db9-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="10db9-111">Tri, regroupement et filtrage sont effectuées sur le <xref:System.Windows.Data.CollectionViewSource> et s’affichent dans le <xref:System.Windows.Controls.DataGrid> l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10db9-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="10db9-112">![Données groupées dans un DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span><span class="sxs-lookup"><span data-stu-id="10db9-112">![Grouped data in a DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span></span>  
<span data-ttu-id="10db9-113">Données groupées dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-113">Grouped Data in a DataGrid</span></span>  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="10db9-114">Utilisation de CollectionViewSource en tant que ItemsSource</span><span class="sxs-lookup"><span data-stu-id="10db9-114">Using a CollectionViewSource as an ItemsSource</span></span>  
 <span data-ttu-id="10db9-115">Pour regrouper, trier et filtrer des données dans un <xref:System.Windows.Controls.DataGrid> (contrôle), vous liez le <xref:System.Windows.Controls.DataGrid> à un <xref:System.Windows.Data.CollectionView> qui prend en charge ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="10db9-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="10db9-116">Dans cet exemple, le <xref:System.Windows.Controls.DataGrid> est lié à un <xref:System.Windows.Data.CollectionViewSource> qui fournit ces fonctions pour un <xref:System.Collections.Generic.List%601> de `Task` objets.</span><span class="sxs-lookup"><span data-stu-id="10db9-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="10db9-117">Pour lier un DataGrid à un CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="10db9-117">To bind a DataGrid to a CollectionViewSource</span></span>  
  
1.  <span data-ttu-id="10db9-118">Créer une collection de données qui implémente le <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="10db9-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
     <span data-ttu-id="10db9-119">Si vous utilisez <xref:System.Collections.Generic.List%601> pour créer votre collection, vous devez créer une nouvelle classe qui hérite de <xref:System.Collections.Generic.List%601> au lieu d’instancier une instance de <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="10db9-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="10db9-120">Cela vous permet de lier des données à la collection en XAML.</span><span class="sxs-lookup"><span data-stu-id="10db9-120">This enables you to data bind to the collection in XAML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="10db9-121">Les objets dans la collection doivent implémenter la <xref:System.ComponentModel.INotifyPropertyChanged> interface modifiée et <xref:System.ComponentModel.IEditableObject> interface dans l’ordre pour le <xref:System.Windows.Controls.DataGrid> pour répondre correctement aux modifications apportées aux propriétés et les modifications.</span><span class="sxs-lookup"><span data-stu-id="10db9-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="10db9-122">Pour plus d’informations, consultez [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="10db9-122">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  <span data-ttu-id="10db9-123">En XAML, créez une instance de la classe de collection et définissez la [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="10db9-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
3.  <span data-ttu-id="10db9-124">En XAML, créez une instance de la <xref:System.Windows.Data.CollectionViewSource> classe, définissez la [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md)et définir l’instance de votre classe de collection en tant que le <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="10db9-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  <span data-ttu-id="10db9-125">Créez une instance de la <xref:System.Windows.Controls.DataGrid> , puis définissez le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété le <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="10db9-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  <span data-ttu-id="10db9-126">Pour accéder à la <xref:System.Windows.Data.CollectionViewSource> à partir de votre code, utilisez la <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> méthode pour obtenir une référence à la <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="10db9-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="10db9-127">Regrouper des éléments dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-127">Grouping items in a DataGrid</span></span>  
 <span data-ttu-id="10db9-128">Pour spécifier la façon dont les éléments sont regroupés dans un <xref:System.Windows.Controls.DataGrid>, vous utilisez la <xref:System.Windows.Data.PropertyGroupDescription> type pour regrouper les éléments dans la vue de source.</span><span class="sxs-lookup"><span data-stu-id="10db9-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="10db9-129">Pour regrouper des éléments dans une grille de données à l’aide de XAML</span><span class="sxs-lookup"><span data-stu-id="10db9-129">To group items in a DataGrid using XAML</span></span>  
  
1.  <span data-ttu-id="10db9-130">Créer un <xref:System.Windows.Data.PropertyGroupDescription> qui spécifie la propriété à regrouper.</span><span class="sxs-lookup"><span data-stu-id="10db9-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="10db9-131">Vous pouvez spécifier la propriété en XAML ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="10db9-131">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="10db9-132">En XAML, affectez le <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> au nom de la propriété à regrouper.</span><span class="sxs-lookup"><span data-stu-id="10db9-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>  
  
    2.  <span data-ttu-id="10db9-133">Dans le code, passez le nom de la propriété au groupe par le constructeur.</span><span class="sxs-lookup"><span data-stu-id="10db9-133">In code, pass the name of the property to group by to the constructor.</span></span>  
  
2.  <span data-ttu-id="10db9-134">Ajouter le <xref:System.Windows.Data.PropertyGroupDescription> à la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="10db9-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="10db9-135">Ajoutez des instances supplémentaires de <xref:System.Windows.Data.PropertyGroupDescription> à la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection pour ajouter davantage de niveaux de regroupement.</span><span class="sxs-lookup"><span data-stu-id="10db9-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  <span data-ttu-id="10db9-136">Pour supprimer un groupe, supprimez le <xref:System.Windows.Data.PropertyGroupDescription> à partir de la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="10db9-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
5.  <span data-ttu-id="10db9-137">Pour supprimer tous les groupes, appelez le <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> méthode de la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="10db9-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 <span data-ttu-id="10db9-138">Lorsque les éléments sont regroupés dans le <xref:System.Windows.Controls.DataGrid>, vous pouvez définir un <xref:System.Windows.Controls.GroupStyle> qui spécifie l’apparence de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="10db9-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="10db9-139">Vous appliquez le <xref:System.Windows.Controls.GroupStyle> en l’ajoutant à la <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="10db9-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="10db9-140">Si vous avez plusieurs niveaux de regroupement, vous pouvez appliquer différents styles à chaque niveau de groupe.</span><span class="sxs-lookup"><span data-stu-id="10db9-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="10db9-141">Les styles sont appliqués dans l’ordre dans lequel elles sont définies.</span><span class="sxs-lookup"><span data-stu-id="10db9-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="10db9-142">Par exemple, si vous définissez deux styles, la première s’appliqueront aux groupes de lignes de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="10db9-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="10db9-143">Le deuxième style sera appliqué à tous les groupes de lignes au deuxième niveau et inférieure.</span><span class="sxs-lookup"><span data-stu-id="10db9-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="10db9-144">Le <xref:System.Windows.FrameworkElement.DataContext%2A> de la <xref:System.Windows.Controls.GroupStyle> est le <xref:System.Windows.Data.CollectionViewGroup> représentant le groupe.</span><span class="sxs-lookup"><span data-stu-id="10db9-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="10db9-145">Pour modifier l’apparence des en-têtes de groupe de lignes</span><span class="sxs-lookup"><span data-stu-id="10db9-145">To change the appearance of row group headers</span></span>  
  
1.  <span data-ttu-id="10db9-146">Créer un <xref:System.Windows.Controls.GroupStyle> qui définit l’apparence du groupe de lignes.</span><span class="sxs-lookup"><span data-stu-id="10db9-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>  
  
2.  <span data-ttu-id="10db9-147">Placez le <xref:System.Windows.Controls.GroupStyle> à l’intérieur de la `<DataGrid.GroupStyle>` balises.</span><span class="sxs-lookup"><span data-stu-id="10db9-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="10db9-148">Tri des éléments dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-148">Sorting items in a DataGrid</span></span>  
 <span data-ttu-id="10db9-149">Pour spécifier la façon dont les éléments sont triés dans un <xref:System.Windows.Controls.DataGrid>, vous utilisez la <xref:System.ComponentModel.SortDescription> type pour trier les éléments dans la vue de source.</span><span class="sxs-lookup"><span data-stu-id="10db9-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>  
  
#### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="10db9-150">Pour trier les éléments dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-150">To sort items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="10db9-151">Créer un <xref:System.ComponentModel.SortDescription> qui spécifie la propriété à trier.</span><span class="sxs-lookup"><span data-stu-id="10db9-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="10db9-152">Vous pouvez spécifier la propriété en XAML ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="10db9-152">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="10db9-153">En XAML, affectez le <xref:System.ComponentModel.SortDescription.PropertyName%2A> au nom de la propriété à trier.</span><span class="sxs-lookup"><span data-stu-id="10db9-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>  
  
    2.  <span data-ttu-id="10db9-154">Dans le code, passez le nom de la propriété à trier et <xref:System.ComponentModel.ListSortDirection> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="10db9-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>  
  
2.  <span data-ttu-id="10db9-155">Ajouter le <xref:System.ComponentModel.SortDescription> à la <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="10db9-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="10db9-156">Ajoutez des instances supplémentaires de <xref:System.ComponentModel.SortDescription> à la <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection pour trier en fonction des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="10db9-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="10db9-157">Le filtrage des éléments dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-157">Filtering items in a DataGrid</span></span>  
 <span data-ttu-id="10db9-158">Pour filtrer les éléments dans un <xref:System.Windows.Controls.DataGrid> à l’aide un <xref:System.Windows.Data.CollectionViewSource>, vous fournir la logique de filtrage dans le gestionnaire pour le <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="10db9-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
#### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="10db9-159">Pour filtrer les éléments dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="10db9-159">To filter items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="10db9-160">Ajoutez un gestionnaire pour le <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="10db9-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
2.  <span data-ttu-id="10db9-161">Dans la <xref:System.Windows.Data.CollectionViewSource.Filter> Gestionnaire d’événements, définir la logique de filtrage.</span><span class="sxs-lookup"><span data-stu-id="10db9-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>  
  
     <span data-ttu-id="10db9-162">Le filtre sera appliqué chaque fois que la vue soit actualisée.</span><span class="sxs-lookup"><span data-stu-id="10db9-162">The filter will be applied every time the view is refreshed.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 <span data-ttu-id="10db9-163">Ou bien, vous pouvez filtrer les éléments dans un <xref:System.Windows.Controls.DataGrid> en créant une méthode qui fournit la logique et le paramètre de filtrage le <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> propriété à laquelle appliquer le filtre.</span><span class="sxs-lookup"><span data-stu-id="10db9-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="10db9-164">Pour voir un exemple de cette méthode, consultez [filtrer des données dans une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="10db9-164">To see an example of this method, see [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10db9-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="10db9-165">Example</span></span>  
 <span data-ttu-id="10db9-166">L’exemple suivant montre le regroupement, le tri et filtrage `Task` les données dans un <xref:System.Windows.Data.CollectionViewSource> et l’affichage groupés, triée et filtrée `Task` les données dans un <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="10db9-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="10db9-167">Le <xref:System.Windows.Data.CollectionViewSource> est utilisé comme le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="10db9-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="10db9-168">Tri, regroupement et filtrage sont effectuées sur le <xref:System.Windows.Data.CollectionViewSource> et s’affichent dans le <xref:System.Windows.Controls.DataGrid> l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10db9-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="10db9-169">Pour tester cet exemple, vous devrez ajuster le nom DGGroupSortFilterExample correspondre au nom de votre projet.</span><span class="sxs-lookup"><span data-stu-id="10db9-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="10db9-170">Si vous utilisez Visual Basic, vous devez modifier le nom de classe pour <xref:System.Windows.Window> à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="10db9-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10db9-171">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="10db9-171">Compiling the Code</span></span>  
  
-  
  
## <a name="robust-programming"></a><span data-ttu-id="10db9-172">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="10db9-172">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="10db9-173">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="10db9-173">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10db9-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10db9-174">See Also</span></span>  
 [<span data-ttu-id="10db9-175">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="10db9-175">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="10db9-176">Créer et effectuer une liaison à un ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="10db9-176">Create and Bind to an ObservableCollection</span></span>](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [<span data-ttu-id="10db9-177">Filtrer les données d’une vue</span><span class="sxs-lookup"><span data-stu-id="10db9-177">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="10db9-178">Trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="10db9-178">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="10db9-179">Trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="10db9-179">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
