---
title: "Comment : ajouter des détails de ligne à un contrôle DataGrid"
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
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 036e06d110df8900ab46f0d501f30b4a163c8eb9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="3f15c-102">Comment : ajouter des détails de ligne à un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="3f15c-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="3f15c-103">Lorsque vous utilisez la <xref:System.Windows.Controls.DataGrid> (contrôle), vous pouvez personnaliser la présentation des données en ajoutant une section de détails de ligne.</span><span class="sxs-lookup"><span data-stu-id="3f15c-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="3f15c-104">Ajout d’une section de détails de ligne vous permet de regrouper des données dans un modèle qui est éventuellement visible ou réduit.</span><span class="sxs-lookup"><span data-stu-id="3f15c-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="3f15c-105">Par exemple, vous pouvez ajouter des détails de la ligne à un <xref:System.Windows.Controls.DataGrid> qui présente uniquement un résumé des données pour chaque ligne dans le <xref:System.Windows.Controls.DataGrid>, mais présente davantage de champs de données lorsque l’utilisateur sélectionne une ligne.</span><span class="sxs-lookup"><span data-stu-id="3f15c-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="3f15c-106">Vous définissez le modèle pour la section de détails de ligne dans le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="3f15c-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="3f15c-107">L’illustration suivante montre un exemple d’une section de détails de ligne.</span><span class="sxs-lookup"><span data-stu-id="3f15c-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="3f15c-108">![DataGrid affiché avec détails de la ligne](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="3f15c-108">![DataGrid shown with row details](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="3f15c-109">Vous définissez le modèle de détails de ligne comme XAML inline ou en tant que ressource.</span><span class="sxs-lookup"><span data-stu-id="3f15c-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="3f15c-110">Les deux approches sont affichés dans les procédures suivantes.</span><span class="sxs-lookup"><span data-stu-id="3f15c-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="3f15c-111">Un modèle de données qui a été ajouté comme une ressource peut être utilisée dans le projet sans recréer le modèle.</span><span class="sxs-lookup"><span data-stu-id="3f15c-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="3f15c-112">Un modèle de données qui a été ajouté comme XAML inline est uniquement accessible à partir du contrôle où il est défini.</span><span class="sxs-lookup"><span data-stu-id="3f15c-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="3f15c-113">Pour afficher les détails de la ligne à l’aide de XAML inline</span><span class="sxs-lookup"><span data-stu-id="3f15c-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="3f15c-114">Créer un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="3f15c-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="3f15c-115">Dans l'élément <xref:System.Windows.Controls.DataGrid>, ajoutez un élément <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f15c-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="3f15c-116">Créer un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails de ligne.</span><span class="sxs-lookup"><span data-stu-id="3f15c-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="3f15c-117">Le XAML suivant affiche la <xref:System.Windows.Controls.DataGrid> et comment définir le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span><span class="sxs-lookup"><span data-stu-id="3f15c-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="3f15c-118">Le <xref:System.Windows.Controls.DataGrid> affiche trois valeurs dans chaque ligne et trois valeurs plus lorsque la ligne est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="3f15c-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="3f15c-119">Le code suivant montre la requête qui est utilisée pour sélectionner les données qui s’affiche dans le <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="3f15c-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="3f15c-120">Dans cet exemple, la requête sélectionne des données à partir d’une entité qui contient des informations sur le client.</span><span class="sxs-lookup"><span data-stu-id="3f15c-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="3f15c-121">Pour afficher les détails de la ligne à l’aide d’une ressource</span><span class="sxs-lookup"><span data-stu-id="3f15c-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="3f15c-122">Créer un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="3f15c-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="3f15c-123">Ajouter un <xref:System.Windows.FrameworkElement.Resources%2A> élément à l’élément racine, comme un <xref:System.Windows.Window> contrôle ou une <xref:System.Windows.Controls.Page> contrôler ou ajouter un <xref:System.Windows.Application.Resources%2A> élément à la <xref:System.Windows.Application> classe dans le fichier App.xaml (ou Application.xaml).</span><span class="sxs-lookup"><span data-stu-id="3f15c-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="3f15c-124">Dans l’élément de ressources, créez un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails de ligne.</span><span class="sxs-lookup"><span data-stu-id="3f15c-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="3f15c-125">Le XAML suivant affiche la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> défini dans la <xref:System.Windows.Application> classe.</span><span class="sxs-lookup"><span data-stu-id="3f15c-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="3f15c-126">Sur le <xref:System.Windows.DataTemplate>, définissez le [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) à une valeur qui identifie de façon unique le modèle de données.</span><span class="sxs-lookup"><span data-stu-id="3f15c-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="3f15c-127">Dans le <xref:System.Windows.Controls.DataGrid> élément, définissez la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété pour la ressource définie dans les étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="3f15c-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="3f15c-128">Assignez la ressource comme une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="3f15c-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="3f15c-129">Le XAML suivant affiche le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété définie sur la ressource à partir de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="3f15c-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="3f15c-130">Pour définir la visibilité et empêcher le défilement horizontal pour les détails de la ligne</span><span class="sxs-lookup"><span data-stu-id="3f15c-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="3f15c-131">Si nécessaire, définissez la <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> propriété un <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> valeur.</span><span class="sxs-lookup"><span data-stu-id="3f15c-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="3f15c-132">Par défaut, la valeur est définie <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="3f15c-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="3f15c-133">Vous pouvez le définir sur <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> pour afficher les détails de toutes les lignes ou <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> pour masquer les détails pour toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="3f15c-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="3f15c-134">Si nécessaire, définissez la <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> propriété `true` pour empêcher la ligne de détails de section de faire défiler horizontalement.</span><span class="sxs-lookup"><span data-stu-id="3f15c-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
