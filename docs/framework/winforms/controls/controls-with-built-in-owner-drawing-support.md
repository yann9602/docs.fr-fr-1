---
title: "Contrôles avec prise en charge intégrée des dessins owner-drawn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd297dcc11005d6b6d47bb9ce3853a757046e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="5179f-102">Contrôles avec prise en charge intégrée des dessins owner-drawn</span><span class="sxs-lookup"><span data-stu-id="5179f-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="5179f-103">Le dessin owner-drawn dans Windows Forms, qui est également appelé dessin personnalisé, est une technique permettant de changer l’apparence visuelle de certains contrôles.</span><span class="sxs-lookup"><span data-stu-id="5179f-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5179f-104">Le mot « contrôle » dans cette rubrique est utilisé pour signifier des classes qui dérivent soit <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="5179f-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="5179f-105">En règle générale, Windows gère automatiquement la peinture à l’aide des paramètres de propriété tels que <xref:System.Windows.Forms.Control.BackColor%2A> pour déterminer l’apparence d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="5179f-106">Avec le dessin owner-drawn, vous contrôlez le processus de dessin, en changeant l’apparence des éléments qui ne sont pas disponibles via des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5179f-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="5179f-107">Par exemple, de nombreux contrôles vous permettent de définir la couleur du texte qui s’affiche, mais vous êtes limité à une seule couleur.</span><span class="sxs-lookup"><span data-stu-id="5179f-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="5179f-108">Le dessin owner-drawn vous permet d’effectuer des opérations comme afficher une partie du texte en noir et une autre en rouge.</span><span class="sxs-lookup"><span data-stu-id="5179f-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="5179f-109">Dans la pratique, le dessin owner-drawn est similaire au dessin de graphiques dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="5179f-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="5179f-110">Par exemple, vous pouvez utiliser des méthodes graphiques dans un gestionnaire pour le formulaire <xref:System.Windows.Forms.Control.Paint> événement pour émuler un `ListBox` contrôle, mais vous devrez écrire votre propre code pour gérer toutes les interactions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5179f-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="5179f-111">Avec le dessin owner-drawn, le contrôle utilise votre code pour dessiner son contenu, mais il conserve par ailleurs toutes ses capacités intrinsèques.</span><span class="sxs-lookup"><span data-stu-id="5179f-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="5179f-112">Vous pouvez utiliser des méthodes graphiques pour dessiner chaque élément du contrôle ou pour personnaliser certains aspects de chaque élément, tout en utilisant l’apparence par défaut pour d’autres aspects de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="5179f-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="5179f-113">Dessin owner-drawn dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5179f-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="5179f-114">Pour effectuer du dessin owner-drawn dans les contrôles qui le prennent en charge, vous définissez généralement une propriété, et vous gérez un ou plusieurs événements.</span><span class="sxs-lookup"><span data-stu-id="5179f-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="5179f-115">La plupart des contrôles qui prennent en charge le dessin owner-drawn ont une propriété `OwnerDraw` ou `DrawMode` qui indique si le contrôle déclenche son ou ses événements de dessin quand il se dessine lui-même.</span><span class="sxs-lookup"><span data-stu-id="5179f-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="5179f-116">Les contrôles qui n’ont pas une propriété `OwnerDraw` ou `DrawMode` incluent le contrôle `DataGridView`, qui fournit des événements de dessin qui se produisent automatiquement, et le contrôle `ToolStrip`, qui est dessiné à l’aide d’une classe de rendu externe qui a ses propres événements de dessin.</span><span class="sxs-lookup"><span data-stu-id="5179f-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="5179f-117">Il existe de nombreux types d’événements de dessin, mais un événement de dessin se produit généralement pour dessiner un élément dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="5179f-118">Le gestionnaire d’événements reçoit un objet `EventArgs` qui contient des informations sur l’élément dessiné et des outils que vous pouvez utiliser pour le dessiner.</span><span class="sxs-lookup"><span data-stu-id="5179f-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="5179f-119">Par exemple, cet objet contient en général, numéro d’index de l’élément dans sa collection parente, un <xref:System.Drawing.Rectangle> qui indique l’élément affiche les limites et un <xref:System.Drawing.Graphics> pour appeler les méthodes de peinture.</span><span class="sxs-lookup"><span data-stu-id="5179f-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="5179f-120">Pour certains événements, l’objet `EventArgs` fournit plus d’informations sur l’élément sur les méthodes que vous pouvez appeler pour dessiner certains aspects de l’élément par défaut, comme l’arrière-plan ou un rectangle de focus.</span><span class="sxs-lookup"><span data-stu-id="5179f-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="5179f-121">Pour créer un contrôle réutilisable contenant vos personnalisations owner-drawn, créez une classe qui dérive d’une classe de contrôle prenant en charge le dessin owner-drawn.</span><span class="sxs-lookup"><span data-stu-id="5179f-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="5179f-122">Au lieu de gérer les événements de dessin, incluez votre code de dessin owner-drawn dans la ou les méthodes `On`*nom_événement* appropriées de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="5179f-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="5179f-123">Vérifiez que vous appelez dans ce cas la ou les méthodes `On`*nom_événement* de la classe de base, pour que les utilisateurs de votre contrôle puissent gérer les événements de dessin owner-drawn et fournir une personnalisation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5179f-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="5179f-124">Les contrôles Windows Forms suivants prennent en charge le dessin owner-drawn dans toutes les versions du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="5179f-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="5179f-125"><xref:System.Windows.Forms.MenuItem>(utilisé par <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="5179f-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="5179f-126">Les contrôles suivants prennent en charge owner-drawn seulement dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="5179f-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="5179f-127">Les contrôles suivants prennent en charge le dessin owner-drawn et sont nouveaux dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="5179f-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="5179f-128">Les sections suivantes contiennent des informations détaillées supplémentaires pour chacun de ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="5179f-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="5179f-129">Contrôles Edit et Combobox</span><span class="sxs-lookup"><span data-stu-id="5179f-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="5179f-130">Le <xref:System.Windows.Forms.ListBox> et <xref:System.Windows.Forms.ComboBox> vous permettent de dessiner des éléments individuels dans le contrôle tous dans la même taille, ou dans des tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="5179f-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5179f-131">Bien que le <xref:System.Windows.Forms.CheckedListBox> contrôle est dérivé le <xref:System.Windows.Forms.ListBox> contrôle, il ne prend pas en charge owner-drawn.</span><span class="sxs-lookup"><span data-stu-id="5179f-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="5179f-132">Pour dessiner chaque élément dans la même taille, affectez le `DrawMode` propriété <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> et gérer le `DrawItem` événement.</span><span class="sxs-lookup"><span data-stu-id="5179f-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="5179f-133">Pour dessiner chaque élément à l’aide d’une taille différente, affectez le `DrawMode` propriété <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> et gérer à la fois le `MeasureItem` et `DrawItem` les événements.</span><span class="sxs-lookup"><span data-stu-id="5179f-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="5179f-134">L’événement `MeasureItem` vous permet d’indiquer la taille d’un élément avant que l’événement `DrawItem` se produise pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="5179f-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="5179f-135">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="5179f-136">Guide pratique pour créer du texte de taille variable dans un contrôle ComboBox</span><span class="sxs-lookup"><span data-stu-id="5179f-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="5179f-137">MenuItem, composant</span><span class="sxs-lookup"><span data-stu-id="5179f-137">MenuItem Component</span></span>  
 <span data-ttu-id="5179f-138">Le <xref:System.Windows.Forms.MenuItem> composant représente un élément de menu dans un <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> composant.</span><span class="sxs-lookup"><span data-stu-id="5179f-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="5179f-139">Pour dessiner un <xref:System.Windows.Forms.MenuItem>, définissez son `OwnerDraw` propriété `true` et gérer son `DrawItem` événement.</span><span class="sxs-lookup"><span data-stu-id="5179f-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="5179f-140">Pour personnaliser la taille de l’élément de menu avant que l’événement `DrawItem` se produise, gérez l’événement `MeasureItem` de l’élément.</span><span class="sxs-lookup"><span data-stu-id="5179f-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="5179f-141">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="5179f-142">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="5179f-142">TabControl Control</span></span>  
 <span data-ttu-id="5179f-143">Le <xref:System.Windows.Forms.TabControl> contrôle vous permet de dessiner des onglets individuels dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="5179f-144">Owner-drawn affecte uniquement les onglets ; le <xref:System.Windows.Forms.TabPage> contenu n’est pas affecté.</span><span class="sxs-lookup"><span data-stu-id="5179f-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="5179f-145">Pour dessiner chaque onglet un <xref:System.Windows.Forms.TabControl>, définissez le `DrawMode` propriété <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> et gérer le `DrawItem` événement.</span><span class="sxs-lookup"><span data-stu-id="5179f-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="5179f-146">Cet événement se produit une fois pour chaque onglet uniquement quand l’onglet est visible dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="5179f-147">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="5179f-148">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="5179f-148">ToolTip Component</span></span>  
 <span data-ttu-id="5179f-149">Le <xref:System.Windows.Forms.ToolTip> composant vous permet de dessiner l’info-bulle entièrement lorsqu’elle est affichée.</span><span class="sxs-lookup"><span data-stu-id="5179f-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="5179f-150">Pour dessiner un <xref:System.Windows.Forms.ToolTip>, définissez son `OwnerDraw` propriété `true` et gérer son `Draw` événement.</span><span class="sxs-lookup"><span data-stu-id="5179f-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="5179f-151">Pour personnaliser la taille de la <xref:System.Windows.Forms.ToolTip> avant la `Draw` événement se produit, gérer la `Popup` événement et l’ensemble le <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriété dans le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5179f-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="5179f-152">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="5179f-153">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="5179f-153">ListView Control</span></span>  
 <span data-ttu-id="5179f-154">Le <xref:System.Windows.Forms.ListView> contrôle vous permet de dessiner des éléments individuels, des sous-éléments et des en-têtes de colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="5179f-155">Pour activer le dessin owner-drawn dans le contrôle, définissez la propriété `OwnerDraw` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="5179f-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="5179f-156">Pour dessiner chaque élément dans le contrôle, gérez l’événement `DrawItem`.</span><span class="sxs-lookup"><span data-stu-id="5179f-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="5179f-157">Pour dessiner chaque sous-élément ou en-tête de colonne dans le contrôle lorsque le <xref:System.Windows.Forms.ListView.View%2A> est définie sur <xref:System.Windows.Forms.View.Details>, gérer les `DrawSubItem` et `DrawColumnHeader` les événements.</span><span class="sxs-lookup"><span data-stu-id="5179f-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="5179f-158">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="5179f-159">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="5179f-159">TreeView Control</span></span>  
 <span data-ttu-id="5179f-160">Le <xref:System.Windows.Forms.TreeView> contrôle vous permet de dessiner des nœuds individuels dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="5179f-161">Pour dessiner uniquement le texte affiché dans chaque nœud, affectez le `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> et gérer le `DrawNode` événement pour dessiner le texte.</span><span class="sxs-lookup"><span data-stu-id="5179f-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="5179f-162">Pour dessiner tous les éléments de chaque nœud, affectez le `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> et gérer le `DrawNode` événement pour dessiner n’importe quel élément que vous avez besoin, telles que le texte, des icônes, cases à cocher, signes plus et moins et les lignes qui connectent les nœuds.</span><span class="sxs-lookup"><span data-stu-id="5179f-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="5179f-163">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="5179f-164">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="5179f-164">DataGridView Control</span></span>  
 <span data-ttu-id="5179f-165">Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de dessiner des cellules et des lignes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5179f-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="5179f-166">Pour dessiner des cellules individuelles, gérez l’événement `CellPainting`.</span><span class="sxs-lookup"><span data-stu-id="5179f-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="5179f-167">Pour dessiner des lignes individuelles ou des éléments de ligne, gérez un des événements `RowPrePaint` ou `RowPostPaint`, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="5179f-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="5179f-168">L’événement `RowPrePaint` se produit avant le dessin des cellules d’une ligne, et l’événement se produit `RowPostPaint` après le dessin des cellules.</span><span class="sxs-lookup"><span data-stu-id="5179f-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="5179f-169">Vous pouvez gérer ces deux événements et l’événement `CellPainting` pour dessiner séparément l’arrière-plan de la ligne, les cellules individuelles et le premier plan de la ligne, ou vous pouvez fournir des personnalisations spécifiques là où vous en avez besoin et utiliser l’affichage par défaut pour les autres éléments de la ligne.</span><span class="sxs-lookup"><span data-stu-id="5179f-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="5179f-170">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="5179f-171">Guide pratique pour personnaliser l’apparence des cellules du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5179f-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="5179f-172">Guide pratique pour personnaliser l’apparence des lignes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5179f-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="5179f-173">ToolStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="5179f-173">ToolStrip Control</span></span>  
 <span data-ttu-id="5179f-174"><xref:System.Windows.Forms.ToolStrip>et les contrôles dérivés vous permettent de personnaliser l’aspect de leur apparence.</span><span class="sxs-lookup"><span data-stu-id="5179f-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="5179f-175">Pour fournir un rendu personnalisé pour <xref:System.Windows.Forms.ToolStrip> contrôles, définir le `Renderer` propriété d’un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> à un `ToolStripRenderer` de l’objet et de gérer une ou plusieurs des nombreux événements de dessin fournis par le `ToolStripRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="5179f-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="5179f-176">Vous pouvez également définir un `Renderer` propriété à une instance de votre propre classe dérivée de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> qui implémente ou substitue spécifique `On` *EventName* méthodes.</span><span class="sxs-lookup"><span data-stu-id="5179f-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="5179f-177">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5179f-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="5179f-178">Guide pratique pour créer et définir un renderer personnalisé pour le contrôle ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5179f-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="5179f-179">Guide pratique pour personnaliser le dessin d’un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5179f-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="5179f-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5179f-180">See Also</span></span>  
 [<span data-ttu-id="5179f-181">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5179f-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
