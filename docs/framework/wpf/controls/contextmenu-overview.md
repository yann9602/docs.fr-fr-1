---
title: Vue d'ensemble de ContextMenu
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
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0776e7960aa76a76422d01180af5fd6a089bc98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-overview"></a><span data-ttu-id="4b8e3-102">Vue d'ensemble de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-102">ContextMenu Overview</span></span>
<span data-ttu-id="4b8e3-103">Le <xref:System.Windows.Controls.ContextMenu> classe représente l’élément qui expose les fonctionnalités à l’aide d’un contexte spécifique <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="4b8e3-104">En règle générale, un utilisateur expose le <xref:System.Windows.Controls.ContextMenu> dans les [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en cliquant sur le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="4b8e3-105">Cette rubrique présente la <xref:System.Windows.Controls.ContextMenu> élément et fournit des exemples d’utilisation dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et le code.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="4b8e3-106">Contrôle ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-106">ContextMenu Control</span></span>  
 <span data-ttu-id="4b8e3-107">A <xref:System.Windows.Controls.ContextMenu> est attaché à un contrôle spécifique.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="4b8e3-108">Le <xref:System.Windows.Controls.ContextMenu> élément vous permet de présenter aux utilisateurs une liste d’éléments qui spécifient des commandes ou des options qui sont associées à un contrôle spécifique, par exemple, un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="4b8e3-109">Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="4b8e3-110">En règle générale, en cliquant sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou entraîne l’application à exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="4b8e3-111">Création d’un ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="4b8e3-112">Les exemples suivants montrent comment créer un <xref:System.Windows.Controls.ContextMenu> avec les sous-menus.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="4b8e3-113">Le <xref:System.Windows.Controls.ContextMenu> contrôles associés à des contrôles de bouton.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="4b8e3-114">Application de styles à un ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="4b8e3-115">À l’aide d’un contrôle <xref:System.Windows.Style>, vous pouvez modifier considérablement l’apparence et le comportement d’un <xref:System.Windows.Controls.ContextMenu> sans avoir à écrire un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="4b8e3-116">Outre la définition de propriétés visuelles, vous pouvez appliquer des styles aux parties d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="4b8e3-117">Par exemple, vous pouvez modifier le comportement de parties du contrôle à l’aide des propriétés, ou vous pouvez ajouter des articles, ou modifier la disposition, un <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="4b8e3-118">Les exemples suivants montrent différentes manières d’ajouter des styles à <xref:System.Windows.Controls.ContextMenu> contrôles.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="4b8e3-119">Le premier exemple définit un style appelé `SimpleSysResources`, qui explique comment utiliser les paramètres système actuels dans votre style.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="4b8e3-120">L’exemple affecte <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> comme le <xref:System.Windows.Controls.Control.Background%2A> couleur et <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> comme le <xref:System.Windows.Controls.Control.Foreground%2A> couleur de la <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="4b8e3-121">L’exemple suivant utilise le <xref:System.Windows.Trigger> élément pour modifier l’apparence d’un <xref:System.Windows.Controls.Menu> en réponse aux événements déclenchés sur le <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="4b8e3-122">Lorsqu’un utilisateur déplace la souris sur le menu, l’apparence de la <xref:System.Windows.Controls.ContextMenu> modifications d’éléments.</span><span class="sxs-lookup"><span data-stu-id="4b8e3-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b8e3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b8e3-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="4b8e3-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="4b8e3-125">Styles et modèles ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4b8e3-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="4b8e3-126">Exemple de galerie de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="4b8e3-126">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
