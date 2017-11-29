---
title: Vue d'ensemble de Menu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81611e7c5f509314b10e3188106870bdc67dfb0e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="d2aad-102">Vue d'ensemble de Menu</span><span class="sxs-lookup"><span data-stu-id="d2aad-102">Menu Overview</span></span>
<span data-ttu-id="d2aad-103">La <xref:System.Windows.Controls.Menu> classe vous permet d’organiser des éléments associés aux commandes et gestionnaires d’événements dans un ordre hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="d2aad-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="d2aad-104">Chaque <xref:System.Windows.Controls.Menu> élément contient une collection de <xref:System.Windows.Controls.MenuItem> éléments.</span><span class="sxs-lookup"><span data-stu-id="d2aad-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="d2aad-105">Contrôle Menu</span><span class="sxs-lookup"><span data-stu-id="d2aad-105">Menu Control</span></span>  
 <span data-ttu-id="d2aad-106">Le <xref:System.Windows.Controls.Menu> contrôle présente une liste d’éléments qui spécifient des commandes ou des options pour une application.</span><span class="sxs-lookup"><span data-stu-id="d2aad-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="d2aad-107">En règle générale, en cliquant sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou entraîne l’application à exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="d2aad-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="d2aad-108">Création de menus</span><span class="sxs-lookup"><span data-stu-id="d2aad-108">Creating Menus</span></span>  
 <span data-ttu-id="d2aad-109">L’exemple suivant crée un <xref:System.Windows.Controls.Menu> à manipuler du texte dans un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d2aad-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d2aad-110">Le <xref:System.Windows.Controls.Menu> contient <xref:System.Windows.Controls.MenuItem> objets qui utilisent le <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, et <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriétés et le <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, et <xref:System.Windows.Controls.MenuItem.Click> événements.</span><span class="sxs-lookup"><span data-stu-id="d2aad-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="d2aad-111">MenuItems avec raccourcis clavier</span><span class="sxs-lookup"><span data-stu-id="d2aad-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="d2aad-112">Raccourcis clavier sont des combinaisons de caractères qui peuvent être entrées avec le clavier pour appeler <xref:System.Windows.Controls.Menu> commandes.</span><span class="sxs-lookup"><span data-stu-id="d2aad-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="d2aad-113">Par exemple, le raccourci clavier de la **copie** est CTRL+C.</span><span class="sxs-lookup"><span data-stu-id="d2aad-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="d2aad-114">Il existe deux propriétés à utiliser avec les raccourcis clavier et des éléments de menu :<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2aad-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="d2aad-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="d2aad-115">InputGestureText</span></span>  
 <span data-ttu-id="d2aad-116">L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> propriété à attribuer le texte de raccourci clavier à <xref:System.Windows.Controls.MenuItem> contrôles.</span><span class="sxs-lookup"><span data-stu-id="d2aad-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="d2aad-117">Cette opération ne fait que placer le raccourci clavier dans l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="d2aad-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="d2aad-118">Il n’associe pas la commande avec le <xref:System.Windows.Controls.MenuItem>.</span><span class="sxs-lookup"><span data-stu-id="d2aad-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="d2aad-119">L’application doit gérer l’entrée de l’utilisateur pour exécuter l’action.</span><span class="sxs-lookup"><span data-stu-id="d2aad-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="d2aad-120">Commande</span><span class="sxs-lookup"><span data-stu-id="d2aad-120">Command</span></span>  
 <span data-ttu-id="d2aad-121">L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.MenuItem.Command%2A> propriété pour associer le **ouvrir** et **enregistrer** avec des commandes <xref:System.Windows.Controls.MenuItem> contrôles.</span><span class="sxs-lookup"><span data-stu-id="d2aad-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="d2aad-122">Non seulement la propriété de la commande associer une commande avec un <xref:System.Windows.Controls.MenuItem>, mais elle fournit également le texte de mouvement d’entrée à utiliser comme un raccourci.</span><span class="sxs-lookup"><span data-stu-id="d2aad-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="d2aad-123">Le <xref:System.Windows.Controls.MenuItem> classe a également un <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> propriété qui spécifie l’élément où la commande se produit.</span><span class="sxs-lookup"><span data-stu-id="d2aad-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="d2aad-124">Si <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas défini, l’élément qui a le focus clavier reçoit la commande.</span><span class="sxs-lookup"><span data-stu-id="d2aad-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="d2aad-125">Pour plus d’informations sur les commandes, consultez [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2aad-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="d2aad-126">Styles de menu</span><span class="sxs-lookup"><span data-stu-id="d2aad-126">Menu Styling</span></span>  
 <span data-ttu-id="d2aad-127">Avec contrôle de style, vous pouvez modifier considérablement l’apparence et le comportement de <xref:System.Windows.Controls.Menu> contrôles sans devoir écrire un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d2aad-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="d2aad-128">En plus de définir des propriétés visuelles, vous pouvez également appliquer un <xref:System.Windows.Style> aux parties individuelles d’un contrôle, modifier le comportement de parties du contrôle à travers des propriétés ou ajouter des parties supplémentaires ou modifier la disposition d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="d2aad-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="d2aad-129">Les exemples suivants illustrent plusieurs façons d’ajouter un <xref:System.Windows.Style> à un <xref:System.Windows.Controls.Menu> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d2aad-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="d2aad-130">Le premier exemple de code définit un <xref:System.Windows.Style> appelée `Simple` qui montre comment utiliser les paramètres système actuels dans votre style.</span><span class="sxs-lookup"><span data-stu-id="d2aad-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="d2aad-131">Le code assigne la couleur du pinceau `MenuHighlightBrush` comme couleur d’arrière-plan du menu et celle du pinceau `MenuTextBrush` comme couleur de premier plan du menu.</span><span class="sxs-lookup"><span data-stu-id="d2aad-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="d2aad-132">Notez que vous utilisez des clés de ressource pour assigner les pinceaux.</span><span class="sxs-lookup"><span data-stu-id="d2aad-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="d2aad-133">L’exemple suivant utilise <xref:System.Windows.Trigger> les éléments qui vous permettent de modifier l’apparence d’un <xref:System.Windows.Controls.MenuItem> en réponse aux événements qui se produisent sur le <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="d2aad-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="d2aad-134">Lorsque vous déplacez la souris sur le <xref:System.Windows.Controls.Menu>, la couleur de premier plan et de modifier les caractéristiques de police des éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="d2aad-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d2aad-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2aad-135">See Also</span></span>  
 [<span data-ttu-id="d2aad-136">Exemple de galerie de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d2aad-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
