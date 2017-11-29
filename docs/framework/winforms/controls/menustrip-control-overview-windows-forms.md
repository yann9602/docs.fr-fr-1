---
title: "Vue d'ensemble du contrôle MenuStrip (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06cd4e812f4acf546dad577a2e1ddc571281ebe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="5ffb5-102">Vue d'ensemble du contrôle MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5ffb5-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="5ffb5-103">Les menus exposent des fonctionnalités à vos utilisateurs en maintenant les commandes regroupées par un thème commun.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="5ffb5-104">Le <xref:System.Windows.Forms.MenuStrip> contrôle est nouveau dans cette version de Visual Studio et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="5ffb5-105">Avec le contrôle, vous pouvez créer facilement des menus tels que ceux de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="5ffb5-106">Le <xref:System.Windows.Forms.MenuStrip> contrôle prend en charge l’interface multidocument (MDI) et la fusion de menus, les info-bulles, les dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="5ffb5-107">Vous pouvez améliorer la facilité d’utilisation et la lisibilité de vos menus en ajoutant des touches d’accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="5ffb5-108">Le <xref:System.Windows.Forms.MenuStrip> contrôle remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.MainMenu> contrôle ; Toutefois, le <xref:System.Windows.Forms.MainMenu> contrôle est conservé pour la compatibilité descendante et l’utilisation future si vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="5ffb5-109">Comment utiliser le contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="5ffb5-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="5ffb5-110">Utilisez le <xref:System.Windows.Forms.MenuStrip> le contrôle à :</span><span class="sxs-lookup"><span data-stu-id="5ffb5-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="5ffb5-111">Créez facilement personnalisées, employées couramment menus qui prennent en charge utilisateur interface et mise en page fonctionnalités avancées, telles que texte et image classement et alignement, opérations de glisser-déplacer, MDI, dépassement de capacité et autres modes d’accès aux commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="5ffb5-112">Prend en charge de l’apparence par défaut et le comportement du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="5ffb5-113">Gérer les événements de manière cohérente pour tous les conteneurs et les éléments contenus, de la même façon que vous gérez des événements pour d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="5ffb5-114">Le tableau suivant indique certaines propriétés particulièrement importantes de <xref:System.Windows.Forms.MenuStrip> et des classes associées.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="5ffb5-115">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ffb5-115">Property</span></span>|<span data-ttu-id="5ffb5-116">Description</span><span class="sxs-lookup"><span data-stu-id="5ffb5-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="5ffb5-117">Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> qui est utilisé pour afficher une liste de formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="5ffb5-118">Obtient ou définit comment les menus enfants sont fusionnés avec les menus parents dans les applications MDI.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="5ffb5-119">Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="5ffb5-120">Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="5ffb5-121">Obtient ou définit une valeur indiquant si les info-bulles sont affichées pour le <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="5ffb5-122">Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="5ffb5-123">Obtient ou définit les touches de raccourci associés à la <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="5ffb5-124">Obtient ou définit une valeur qui indique si les touches de raccourci sont associés les <xref:System.Windows.Forms.ToolStripMenuItem> s’affichent en regard du <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="5ffb5-125">Le tableau suivant présente les importantes <xref:System.Windows.Forms.MenuStrip> classes auxiliaires.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="5ffb5-126">Classe</span><span class="sxs-lookup"><span data-stu-id="5ffb5-126">Class</span></span>|<span data-ttu-id="5ffb5-127">Description</span><span class="sxs-lookup"><span data-stu-id="5ffb5-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="5ffb5-128">Représente une option sélectionnable affichée sur un <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="5ffb5-129">Représente un menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="5ffb5-130">Représente un contrôle qui permet à l’utilisateur à sélectionner un seul élément dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou un élément de menu de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="5ffb5-131">Fournit des fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments de liste déroulante lorsque vous cliquez sur.</span><span class="sxs-lookup"><span data-stu-id="5ffb5-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ffb5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ffb5-132">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
