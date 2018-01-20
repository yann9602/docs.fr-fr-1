---
title: "ListView, contrôle (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8328bc705349ffeaa78d95e95ed0955ac6faa5c3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="83e75-102">ListView, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="83e75-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="83e75-103">Le contrôle `ListView` Windows Forms affiche une liste d'éléments avec des icônes.</span><span class="sxs-lookup"><span data-stu-id="83e75-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="83e75-104">Vous pouvez utiliser un affichage de liste pour créer une interface utilisateur comme le volet droit de l'Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="83e75-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83e75-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="83e75-105">In This Section</span></span>  
 [<span data-ttu-id="83e75-106">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="83e75-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="83e75-107">Décrit ce contrôle et ses principales fonctionnalités et propriétés.</span><span class="sxs-lookup"><span data-stu-id="83e75-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="83e75-108">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-109">Décrit comment ajouter ou supprimer des éléments dans un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="83e75-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="83e75-110">Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-111">Décrit comment créer des colonnes pour afficher des informations sur chaque élément de la liste.</span><span class="sxs-lookup"><span data-stu-id="83e75-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="83e75-112">Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-113">Décrit comment associer un affichage de liste à une liste d'images appropriée pour l'affichage de petites ou grandes icônes.</span><span class="sxs-lookup"><span data-stu-id="83e75-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="83e75-114">Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-115">Décrit comment afficher des informations sur chaque élément de la liste dans des colonnes.</span><span class="sxs-lookup"><span data-stu-id="83e75-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="83e75-116">Guide pratique pour sélectionner un élément dans le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-117">Décrit comment sélectionner un élément par programmation.</span><span class="sxs-lookup"><span data-stu-id="83e75-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="83e75-118">Guide pratique pour grouper des éléments dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-119">Décrit comment créer des groupes pour l'affichage par catégorie et comment assigner des éléments à chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="83e75-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="83e75-120">Cette fonctionnalité est disponible uniquement pour [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83e75-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83e75-121">Guide pratique pour activer l'affichage en mosaïque dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-122">Décrit comment afficher les éléments sous forme de vignettes, chacune d'elles composée d'une grande icône et de plusieurs lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="83e75-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="83e75-123">Cette fonctionnalité est disponible uniquement pour [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83e75-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83e75-124">Guide pratique pour afficher une marque d'insertion dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83e75-125">Décrit comment implémenter les commentaires utilisateur pour les opérations de glisser-déplacer dans lesquelles une marque d’insertion indique l’emplacement de dépôt pour chaque position du pointeur de la souris.</span><span class="sxs-lookup"><span data-stu-id="83e75-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="83e75-126">Cette fonctionnalité est disponible uniquement pour [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83e75-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83e75-127">Guide pratique pour ajouter des fonctions de recherche à un contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="83e75-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="83e75-128">Décrit comment rechercher un élément par programmation à l'aide de coordonnées d'écran ou de la recherche de texte.</span><span class="sxs-lookup"><span data-stu-id="83e75-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   <span data-ttu-id="83e75-129">[Guide pratique pour activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="83e75-129">[How to: Enable Tile View in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="83e75-130">[Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="83e75-130">[How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="83e75-131">[Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="83e75-131">[How to: Add Columns to the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="83e75-132">[Guide pratique pour regrouper des éléments dans un contrôle ListView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="83e75-132">[How to: Group Items in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="83e75-133">[Procédure pas à pas : création d’une interface de style Explorateur avec les contrôles ListView et TreeView à l’aide du concepteur](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="83e75-133">[Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83e75-134">Référence</span><span class="sxs-lookup"><span data-stu-id="83e75-134">Reference</span></span>  
 <span data-ttu-id="83e75-135">Classe <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="83e75-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="83e75-136">Décrit cette classe et fournit des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="83e75-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83e75-137">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="83e75-137">Related Sections</span></span>  
 [<span data-ttu-id="83e75-138">Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="83e75-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="83e75-139">Décrit comment hériter d’un élément dans un affichage de liste ou d’un nœud dans une arborescence pour ajouter des champs, des méthodes ou des constructeurs dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="83e75-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="83e75-140">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="83e75-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="83e75-141">Explique ce qu’est une liste d’images et ses principales fonctionnalités et propriétés.</span><span class="sxs-lookup"><span data-stu-id="83e75-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="83e75-142">Guide pratique pour créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="83e75-143">Fournit des instructions pour disposer un Windows Form avec plusieurs volets.</span><span class="sxs-lookup"><span data-stu-id="83e75-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="83e75-144">Fonctionnalités de Windows XP et contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-144">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="83e75-145">Explique comment tirer parti des fonctionnalités spécifiques à Windows XP qui s'appliquent au contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="83e75-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e75-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83e75-146">See Also</span></span>  
 [<span data-ttu-id="83e75-147">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83e75-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
