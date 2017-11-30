---
title: "Architecture du contrôle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb44a32e63fd7a0ff0e480c205d5459da2ce2bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="c6783-102">Architecture du contrôle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c6783-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="c6783-103">Le <xref:System.Windows.Forms.DataGridView> contrôle et ses classes connexes sont conçus pour être un système flexible et extensible pour afficher et modifier des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="c6783-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="c6783-104">Ces classes sont toutes contenues dans le <xref:System.Windows.Forms?displayProperty=nameWithType> espace de noms et elles portent toutes le préfixe « DataGridView ».</span><span class="sxs-lookup"><span data-stu-id="c6783-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="c6783-105">Éléments d'architecture</span><span class="sxs-lookup"><span data-stu-id="c6783-105">Architecture Elements</span></span>  
 <span data-ttu-id="c6783-106">Le serveur principal <xref:System.Windows.Forms.DataGridView> dérivent des classes auxiliaires <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="c6783-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="c6783-107">Le modèle objet suivant illustre la <xref:System.Windows.Forms.DataGridViewElement> hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="c6783-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="c6783-108">![Modèle objet DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="c6783-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="c6783-109">Modèle objet DataGridViewElement</span><span class="sxs-lookup"><span data-stu-id="c6783-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="c6783-110">Le <xref:System.Windows.Forms.DataGridViewElement> classe fournit une référence au parent <xref:System.Windows.Forms.DataGridView> contrôler et a un <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété, qui contient une valeur qui représente une combinaison de valeurs à partir de la <xref:System.Windows.Forms.DataGridViewElementStates> énumération.</span><span class="sxs-lookup"><span data-stu-id="c6783-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="c6783-111">Les sections suivantes décrivent les <xref:System.Windows.Forms.DataGridView> Compagnon classes plus en détail.</span><span class="sxs-lookup"><span data-stu-id="c6783-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="c6783-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="c6783-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="c6783-113">Le <xref:System.Windows.Forms.DataGridViewElementStates> énumération contient les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6783-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="c6783-114">Les valeurs de cette énumération peuvent être combinées avec les opérateurs logiques au niveau du bit, donc la <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété peut exprimer plusieurs États à la fois.</span><span class="sxs-lookup"><span data-stu-id="c6783-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="c6783-115">Par exemple, un <xref:System.Windows.Forms.DataGridViewElement> peuvent être simultanément <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, et <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="c6783-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="c6783-116">Cellules et les bandes</span><span class="sxs-lookup"><span data-stu-id="c6783-116">Cells and Bands</span></span>  
 <span data-ttu-id="c6783-117">Le <xref:System.Windows.Forms.DataGridView> contrôle comprend deux types d’objets fondamentaux : les cellules et les bandes.</span><span class="sxs-lookup"><span data-stu-id="c6783-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="c6783-118">Toutes les cellules dérivent la <xref:System.Windows.Forms.DataGridViewCell> classe de base.</span><span class="sxs-lookup"><span data-stu-id="c6783-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="c6783-119">Les deux types des bandes, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewRow>, dérivent toutes les deux la <xref:System.Windows.Forms.DataGridViewBand> classe de base.</span><span class="sxs-lookup"><span data-stu-id="c6783-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="c6783-120">Le <xref:System.Windows.Forms.DataGridView> contrôle interagit avec plusieurs classes, mais sont les plus couramment rencontrés <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, et <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="c6783-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="c6783-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="c6783-121">DataGridViewCell</span></span>  
 <span data-ttu-id="c6783-122">La cellule est l’unité fondamentale d’interaction pour le <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c6783-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="c6783-123">Affichage est centré sur les cellules et saisie de données est souvent effectuée dans les cellules.</span><span class="sxs-lookup"><span data-stu-id="c6783-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="c6783-124">Vous pouvez accéder aux cellules à l’aide de la <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection de la <xref:System.Windows.Forms.DataGridViewRow> classe et vous pouvez accéder les cellules sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection de la <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6783-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c6783-125">Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewCell> hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="c6783-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="c6783-126">![Modèle objet DataGridViewCell](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="c6783-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="c6783-127">Modèle objet DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="c6783-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="c6783-128">Le <xref:System.Windows.Forms.DataGridViewCell> type est une classe de base abstraite de laquelle dérivent tous les types de cellules.</span><span class="sxs-lookup"><span data-stu-id="c6783-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="c6783-129"><xref:System.Windows.Forms.DataGridViewCell>et ses types dérivés ne sont pas des contrôles Windows Forms, mais certains contrôles Windows Forms de hôte.</span><span class="sxs-lookup"><span data-stu-id="c6783-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="c6783-130">Toutes les fonctionnalités d’édition prise en charge par une cellule sont généralement gérée par un contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="c6783-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="c6783-131"><xref:System.Windows.Forms.DataGridViewCell>objets ne contrôlent pas de leur propre apparence et les fonctionnalités de peinture de la même façon que les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6783-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="c6783-132">Au lieu de cela, le <xref:System.Windows.Forms.DataGridView> est responsable de l’apparence de son <xref:System.Windows.Forms.DataGridViewCell> objets.</span><span class="sxs-lookup"><span data-stu-id="c6783-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="c6783-133">Vous pouvez affecter de manière significative l’apparence et le comportement des cellules en interagissant avec le <xref:System.Windows.Forms.DataGridView> événements et les propriétés du contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6783-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="c6783-134">Lorsque vous avez des spécifications spéciales pour les personnalisations qui sont au-delà des capacités de la <xref:System.Windows.Forms.DataGridView> (contrôle), vous pouvez implémenter votre propre classe qui dérive de <xref:System.Windows.Forms.DataGridViewCell> ou l’une de ses classes enfants.</span><span class="sxs-lookup"><span data-stu-id="c6783-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="c6783-135">La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="c6783-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="c6783-136">Vos types de cellule personnalisé</span><span class="sxs-lookup"><span data-stu-id="c6783-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="c6783-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="c6783-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="c6783-138">Le schéma de la <xref:System.Windows.Forms.DataGridView> magasin de données attaché du contrôle est exprimée dans le <xref:System.Windows.Forms.DataGridView> les colonnes du contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6783-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="c6783-139">Vous pouvez accéder à la <xref:System.Windows.Forms.DataGridView> les colonnes du contrôle à l’aide de la <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="c6783-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="c6783-140">Vous pouvez accéder à des colonnes sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="c6783-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="c6783-141">Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewColumn> hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="c6783-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="c6783-142">![Modèle objet DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="c6783-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="c6783-143">Modèle objet DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="c6783-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="c6783-144">Certains des types de cellule clés ont des types de colonne correspondants.</span><span class="sxs-lookup"><span data-stu-id="c6783-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="c6783-145">Ils sont dérivés de la <xref:System.Windows.Forms.DataGridViewColumn> classe de base.</span><span class="sxs-lookup"><span data-stu-id="c6783-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="c6783-146">La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="c6783-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="c6783-147">Vos types de colonnes personnalisées</span><span class="sxs-lookup"><span data-stu-id="c6783-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="c6783-148">Contrôles d’édition DataGridView</span><span class="sxs-lookup"><span data-stu-id="c6783-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="c6783-149">Les cellules qui prennent en charge les fonctionnalités d’édition avancées en général utilisent un contrôle hébergé qui est dérivé d’un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6783-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="c6783-150">Ces contrôles implémentent également le <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span><span class="sxs-lookup"><span data-stu-id="c6783-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="c6783-151">Le modèle objet suivant illustre l’utilisation de ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="c6783-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="c6783-152">![DataGridView, modèle d’objet de contrôle d’édition](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="c6783-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="c6783-153">Modèle objet de contrôle d’édition DataGridView</span><span class="sxs-lookup"><span data-stu-id="c6783-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="c6783-154">Les contrôles d’édition suivants sont fournis avec le <xref:System.Windows.Forms.DataGridView> contrôle :</span><span class="sxs-lookup"><span data-stu-id="c6783-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="c6783-155">Pour plus d’informations sur la création de vos propres modification des contrôles, consultez [Comment : héberger des contrôles dans les cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="c6783-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="c6783-156">Le tableau suivant illustre la relation entre les types de cellules, des types de colonnes et des contrôles d’édition.</span><span class="sxs-lookup"><span data-stu-id="c6783-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="c6783-157">Type de cellule</span><span class="sxs-lookup"><span data-stu-id="c6783-157">Cell type</span></span>|<span data-ttu-id="c6783-158">Contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="c6783-158">Hosted control</span></span>|<span data-ttu-id="c6783-159">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="c6783-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="c6783-160">N/A</span><span class="sxs-lookup"><span data-stu-id="c6783-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="c6783-161">N/A</span><span class="sxs-lookup"><span data-stu-id="c6783-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="c6783-162">N/A</span><span class="sxs-lookup"><span data-stu-id="c6783-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="c6783-163">N/A</span><span class="sxs-lookup"><span data-stu-id="c6783-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="c6783-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="c6783-164">DataGridViewRow</span></span>  
 <span data-ttu-id="c6783-165">Le <xref:System.Windows.Forms.DataGridViewRow> affiche de classe les données d’un enregistrement des champs à partir des données des magasins à laquelle le <xref:System.Windows.Forms.DataGridView> contrôle est attaché.</span><span class="sxs-lookup"><span data-stu-id="c6783-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="c6783-166">Vous pouvez accéder à la <xref:System.Windows.Forms.DataGridView> les lignes du contrôle à l’aide de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="c6783-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="c6783-167">Vous pouvez accéder à des lignes sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="c6783-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="c6783-168">Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewRow> hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="c6783-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="c6783-169">![Modèle objet DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="c6783-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="c6783-170">Modèle objet DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="c6783-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="c6783-171">Vous pouvez dériver vos propres types à partir de la <xref:System.Windows.Forms.DataGridViewRow> classe, bien que cela ne soit généralement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c6783-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="c6783-172">Le <xref:System.Windows.Forms.DataGridView> contrôle a plusieurs événements liés à la ligne et propriétés pour personnaliser le comportement de son <xref:System.Windows.Forms.DataGridViewRow> objets.</span><span class="sxs-lookup"><span data-stu-id="c6783-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="c6783-173">Si vous activez le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriété, une ligne spéciale pour l’ajout de nouvelles lignes apparaît en tant que la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="c6783-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="c6783-174">Cette ligne fait partie de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, mais il possède des fonctionnalités spéciales qui peuvent nécessiter votre attention.</span><span class="sxs-lookup"><span data-stu-id="c6783-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="c6783-175">Pour plus d’informations, consultez [à l’aide de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c6783-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6783-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6783-176">See Also</span></span>  
 [<span data-ttu-id="c6783-177">Vue d’ensemble du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c6783-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="c6783-178">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6783-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c6783-179">Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6783-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
