---
title: "Styles et modèles Menu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e007ae09e57353446feb13b3693e62c985f522d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="551eb-102">Styles et modèles Menu</span><span class="sxs-lookup"><span data-stu-id="551eb-102">Menu Styles and Templates</span></span>
<span data-ttu-id="551eb-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Menu> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="551eb-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="551eb-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="551eb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="551eb-106">Éléments de menu</span><span class="sxs-lookup"><span data-stu-id="551eb-106">Menu Parts</span></span>  
 <span data-ttu-id="551eb-107">Le <xref:System.Windows.Controls.Menu> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="551eb-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="551eb-108">Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Menu>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> au sein d’un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="551eb-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="551eb-109">(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans le <xref:System.Windows.Controls.Menu>; le <xref:System.Windows.Controls.ScrollViewer> permet le défilement dans le contrôle).</span><span class="sxs-lookup"><span data-stu-id="551eb-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="551eb-110">Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de la <xref:System.Windows.Controls.ScrollViewer>, vous devez donner le <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="551eb-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="551eb-111">États du menu</span><span class="sxs-lookup"><span data-stu-id="551eb-111">Menu States</span></span>  
 <span data-ttu-id="551eb-112">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Menu> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="551eb-113">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="551eb-113">VisualState Name</span></span>|<span data-ttu-id="551eb-114">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="551eb-114">VisualStateGroup Name</span></span>|<span data-ttu-id="551eb-115">Description</span><span class="sxs-lookup"><span data-stu-id="551eb-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="551eb-116">Valide</span><span class="sxs-lookup"><span data-stu-id="551eb-116">Valid</span></span>|<span data-ttu-id="551eb-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-117">ValidationStates</span></span>|<span data-ttu-id="551eb-118">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="551eb-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="551eb-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="551eb-119">InvalidFocused</span></span>|<span data-ttu-id="551eb-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-120">ValidationStates</span></span>|<span data-ttu-id="551eb-121">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="551eb-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="551eb-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="551eb-122">InvalidUnfocused</span></span>|<span data-ttu-id="551eb-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-123">ValidationStates</span></span>|<span data-ttu-id="551eb-124">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="551eb-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="551eb-125">Composants de MenuItem</span><span class="sxs-lookup"><span data-stu-id="551eb-125">MenuItem Parts</span></span>  
 <span data-ttu-id="551eb-126">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Menu> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="551eb-127">Élément</span><span class="sxs-lookup"><span data-stu-id="551eb-127">Part</span></span>|<span data-ttu-id="551eb-128">Type</span><span class="sxs-lookup"><span data-stu-id="551eb-128">Type</span></span>|<span data-ttu-id="551eb-129">Description</span><span class="sxs-lookup"><span data-stu-id="551eb-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="551eb-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="551eb-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="551eb-131">La zone pour le sous-menu.</span><span class="sxs-lookup"><span data-stu-id="551eb-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="551eb-132">Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.MenuItem>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> au sein d’un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="551eb-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="551eb-133">(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans le <xref:System.Windows.Controls.MenuItem>; le <xref:System.Windows.Controls.ScrollViewer> permet le défilement dans le contrôle).</span><span class="sxs-lookup"><span data-stu-id="551eb-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="551eb-134">Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de la <xref:System.Windows.Controls.ScrollViewer>, vous devez donner le <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="551eb-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="551eb-135">États de MenuItem</span><span class="sxs-lookup"><span data-stu-id="551eb-135">MenuItem States</span></span>  
 <span data-ttu-id="551eb-136">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.MenuItem> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="551eb-137">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="551eb-137">VisualState Name</span></span>|<span data-ttu-id="551eb-138">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="551eb-138">VisualStateGroup Name</span></span>|<span data-ttu-id="551eb-139">Description</span><span class="sxs-lookup"><span data-stu-id="551eb-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="551eb-140">Valide</span><span class="sxs-lookup"><span data-stu-id="551eb-140">Valid</span></span>|<span data-ttu-id="551eb-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-141">ValidationStates</span></span>|<span data-ttu-id="551eb-142">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="551eb-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="551eb-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="551eb-143">InvalidFocused</span></span>|<span data-ttu-id="551eb-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-144">ValidationStates</span></span>|<span data-ttu-id="551eb-145">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="551eb-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="551eb-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="551eb-146">InvalidUnfocused</span></span>|<span data-ttu-id="551eb-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="551eb-147">ValidationStates</span></span>|<span data-ttu-id="551eb-148">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="551eb-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="551eb-149">Menu et MenuItem ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="551eb-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="551eb-150">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Menu> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="551eb-151">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.MenuItem> contrôle.</span><span class="sxs-lookup"><span data-stu-id="551eb-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="551eb-152">L’exemple suivant définit le `MenuScrollViewer`, qui est utilisé dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="551eb-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="551eb-153">Les <xref:System.Windows.Controls.ControlTemplate> exemples utilisent une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="551eb-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="551eb-154">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="551eb-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551eb-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="551eb-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="551eb-156">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="551eb-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="551eb-157">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="551eb-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="551eb-158">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="551eb-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="551eb-159">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="551eb-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
