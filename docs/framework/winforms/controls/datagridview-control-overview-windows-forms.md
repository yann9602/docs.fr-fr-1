---
title: "Vue d'ensemble du contrôle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4209866f63931fb3d80f35e211bd5f9b35ed48bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="b89c7-102">Vue d'ensemble du contrôle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b89c7-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="b89c7-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="b89c7-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b89c7-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b89c7-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b89c7-105">Avec la <xref:System.Windows.Forms.DataGridView> (contrôle), vous pouvez afficher et modifier des données tabulaires provenant de différents types de sources de données.</span><span class="sxs-lookup"><span data-stu-id="b89c7-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="b89c7-106">Liaison de données à la <xref:System.Windows.Forms.DataGridView> contrôle est simple et intuitive, et dans de nombreux cas, il est aussi simple que le paramètre de la <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b89c7-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="b89c7-107">Lorsque vous liez à une source de données qui contient plusieurs listes ou tables, définissez la <xref:System.Windows.Forms.DataGridView.DataMember%2A> propriété dans une chaîne qui spécifie la liste ou la table à lier.</span><span class="sxs-lookup"><span data-stu-id="b89c7-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="b89c7-108">Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle de liaison de données Windows Forms standard, il crée une liaison à des instances des classes décrites dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="b89c7-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="b89c7-109">Toute classe qui implémente le <xref:System.Collections.IList> interface, y compris les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="b89c7-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="b89c7-110">Toute classe qui implémente le <xref:System.ComponentModel.IListSource> d’interface, telles que la <xref:System.Data.DataTable> et <xref:System.Data.DataSet> classes.</span><span class="sxs-lookup"><span data-stu-id="b89c7-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="b89c7-111">Toute classe qui implémente le <xref:System.ComponentModel.IBindingList> d’interface, telles que la <xref:System.ComponentModel.BindingList%601> classe.</span><span class="sxs-lookup"><span data-stu-id="b89c7-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="b89c7-112">Toute classe qui implémente le <xref:System.ComponentModel.IBindingListView> d’interface, telles que la <xref:System.Windows.Forms.BindingSource> classe.</span><span class="sxs-lookup"><span data-stu-id="b89c7-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="b89c7-113">Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge la liaison de données aux propriétés publiques des objets retournés par ces interfaces ou à la collection de propriétés retourné par une <xref:System.ComponentModel.ICustomTypeDescriptor> de l’interface, si implémentée sur les objets retournés.</span><span class="sxs-lookup"><span data-stu-id="b89c7-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="b89c7-114">En règle générale, vous allez lier à un <xref:System.Windows.Forms.BindingSource> composant et lier le <xref:System.Windows.Forms.BindingSource> composant vers un autre source de données ou le remplir avec des objets métier.</span><span class="sxs-lookup"><span data-stu-id="b89c7-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="b89c7-115">Le <xref:System.Windows.Forms.BindingSource> composant est la source de données par défaut, car elle peut lier à un large éventail de sources de données et peut résoudre automatiquement de nombreux problèmes de liaison de données.</span><span class="sxs-lookup"><span data-stu-id="b89c7-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="b89c7-116">Pour plus d’informations, consultez [composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="b89c7-116">For more information, see [BindingSource Component](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="b89c7-117">Le <xref:System.Windows.Forms.DataGridView> contrôle peut également être utilisé dans *indépendant* mode, sans magasin de données sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b89c7-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="b89c7-118">Pour obtenir un exemple de code qui utilise un indépendant <xref:System.Windows.Forms.DataGridView> du contrôle, consultez [procédure pas à pas : création d’un contrôle de DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b89c7-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="b89c7-119">Le <xref:System.Windows.Forms.DataGridView> contrôle est hautement configurable et extensible, et il fournit de nombreuses propriétés, méthodes et événements permettant de personnaliser son apparence et son comportement.</span><span class="sxs-lookup"><span data-stu-id="b89c7-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="b89c7-120">Lorsque vous souhaitez que votre application Windows Forms pour afficher des données sous forme de tableau, envisagez d’utiliser le <xref:System.Windows.Forms.DataGridView> contrôle avant d’autres (par exemple, <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="b89c7-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="b89c7-121">Si vous affichez une petite grille de valeurs en lecture seule, ou si vous activez un utilisateur modifier une table avec des millions d’enregistrements, les <xref:System.Windows.Forms.DataGridView> contrôle vous fournira une solution économe en mémoire facilement programmable.</span><span class="sxs-lookup"><span data-stu-id="b89c7-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b89c7-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b89c7-122">In This Section</span></span>  
 [<span data-ttu-id="b89c7-123">Résumé de la technologie du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b89c7-123">DataGridView Control Technology Summary</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="b89c7-124">Résume <xref:System.Windows.Forms.DataGridView> contrôler les concepts et l’utilisation des classes connexes.</span><span class="sxs-lookup"><span data-stu-id="b89c7-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="b89c7-125">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b89c7-125">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="b89c7-126">Décrit l’architecture de le <xref:System.Windows.Forms.DataGridView> contrôle, expliquant sa structure de hiérarchie et l’héritage de type.</span><span class="sxs-lookup"><span data-stu-id="b89c7-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="b89c7-127">Scénarios du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b89c7-127">DataGridView Control Scenarios</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="b89c7-128">Décrit les scénarios les plus courants dans lesquels <xref:System.Windows.Forms.DataGridView> les contrôles sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="b89c7-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="b89c7-129">Répertoire du code du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b89c7-129">DataGridView Control Code Directory</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="b89c7-130">Fournit des liens vers des exemples de code dans la documentation pour différentes <xref:System.Windows.Forms.DataGridView> tâches.</span><span class="sxs-lookup"><span data-stu-id="b89c7-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="b89c7-131">Ces exemples sont classés par type de tâche.</span><span class="sxs-lookup"><span data-stu-id="b89c7-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b89c7-132">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b89c7-132">Related Sections</span></span>  
 [<span data-ttu-id="b89c7-133">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-133">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89c7-134">Décrit les types de colonne dans les Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle utilisé pour afficher les informations et permettre aux utilisateurs de modifier ou ajouter des informations.</span><span class="sxs-lookup"><span data-stu-id="b89c7-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="b89c7-135">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89c7-136">Fournit des rubriques qui décrivent comment remplir le contrôle de données manuellement ou à partir d'une source de données externe.</span><span class="sxs-lookup"><span data-stu-id="b89c7-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="b89c7-137">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-137">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89c7-138">Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.</span><span class="sxs-lookup"><span data-stu-id="b89c7-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="b89c7-139">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89c7-140">Fournit des rubriques qui expliquent comment utiliser efficacement le contrôle pour éviter les problèmes de performances lors de l'utilisation de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="b89c7-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89c7-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b89c7-141">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="b89c7-142">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="b89c7-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="b89c7-143">Fonctionnalités par défaut du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b89c7-144">Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b89c7-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
