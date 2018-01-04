---
title: "Styles et modèles ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edf8c50424a9694c4e00f5bf319d3122999bda85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="f7a1b-102">Styles et modèles ListBox</span><span class="sxs-lookup"><span data-stu-id="f7a1b-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="f7a1b-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.ListBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="f7a1b-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f7a1b-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f7a1b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="f7a1b-106">Parties de ListBox</span><span class="sxs-lookup"><span data-stu-id="f7a1b-106">ListBox Parts</span></span>  
 <span data-ttu-id="f7a1b-107">Le <xref:System.Windows.Controls.ListBox> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="f7a1b-108">Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ListBox>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> au sein d’un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="f7a1b-109">(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans le <xref:System.Windows.Controls.ListBox>; le <xref:System.Windows.Controls.ScrollViewer> permet le défilement dans le contrôle).</span><span class="sxs-lookup"><span data-stu-id="f7a1b-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="f7a1b-110">Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de la <xref:System.Windows.Controls.ScrollViewer>, vous devez donner le <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="f7a1b-111">États du contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="f7a1b-111">ListBox States</span></span>  
 <span data-ttu-id="f7a1b-112">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ListBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="f7a1b-113">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="f7a1b-113">VisualState Name</span></span>|<span data-ttu-id="f7a1b-114">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f7a1b-114">VisualStateGroup Name</span></span>|<span data-ttu-id="f7a1b-115">Description</span><span class="sxs-lookup"><span data-stu-id="f7a1b-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f7a1b-116">Valide</span><span class="sxs-lookup"><span data-stu-id="f7a1b-116">Valid</span></span>|<span data-ttu-id="f7a1b-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-117">ValidationStates</span></span>|<span data-ttu-id="f7a1b-118">Le contrôle est valide.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-118">The control is valid.</span></span>|  
|<span data-ttu-id="f7a1b-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f7a1b-119">InvalidFocused</span></span>|<span data-ttu-id="f7a1b-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-120">ValidationStates</span></span>|<span data-ttu-id="f7a1b-121">Le contrôle n’est pas valide et a le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="f7a1b-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f7a1b-122">InvalidUnfocused</span></span>|<span data-ttu-id="f7a1b-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-123">ValidationStates</span></span>|<span data-ttu-id="f7a1b-124">Le contrôle n’est pas valide et n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="f7a1b-125">Parties de ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="f7a1b-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="f7a1b-126">Le <xref:System.Windows.Controls.ListBoxItem> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="f7a1b-127">États de ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="f7a1b-127">ListBoxItem States</span></span>  
 <span data-ttu-id="f7a1b-128">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ListBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="f7a1b-129">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="f7a1b-129">VisualState Name</span></span>|<span data-ttu-id="f7a1b-130">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f7a1b-130">VisualStateGroup Name</span></span>|<span data-ttu-id="f7a1b-131">Description</span><span class="sxs-lookup"><span data-stu-id="f7a1b-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f7a1b-132">Normale</span><span class="sxs-lookup"><span data-stu-id="f7a1b-132">Normal</span></span>|<span data-ttu-id="f7a1b-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-133">CommonStates</span></span>|<span data-ttu-id="f7a1b-134">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-134">The default state.</span></span>|  
|<span data-ttu-id="f7a1b-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f7a1b-135">MouseOver</span></span>|<span data-ttu-id="f7a1b-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-136">CommonStates</span></span>|<span data-ttu-id="f7a1b-137">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f7a1b-138">Désactivé</span><span class="sxs-lookup"><span data-stu-id="f7a1b-138">Disabled</span></span>|<span data-ttu-id="f7a1b-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-139">CommonStates</span></span>|<span data-ttu-id="f7a1b-140">L’élément est désactivé.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-140">The item is disabled.</span></span>|  
|<span data-ttu-id="f7a1b-141">Avec focus</span><span class="sxs-lookup"><span data-stu-id="f7a1b-141">Focused</span></span>|<span data-ttu-id="f7a1b-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-142">FocusStates</span></span>|<span data-ttu-id="f7a1b-143">L’élément a le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-143">The item has focus.</span></span>|  
|<span data-ttu-id="f7a1b-144">Sans focus</span><span class="sxs-lookup"><span data-stu-id="f7a1b-144">Unfocused</span></span>|<span data-ttu-id="f7a1b-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-145">FocusStates</span></span>|<span data-ttu-id="f7a1b-146">L’élément n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="f7a1b-147">Non sélectionné</span><span class="sxs-lookup"><span data-stu-id="f7a1b-147">Unselected</span></span>|<span data-ttu-id="f7a1b-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-148">SelectionStates</span></span>|<span data-ttu-id="f7a1b-149">L’élément n’est pas sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-149">The item is not selected.</span></span>|  
|<span data-ttu-id="f7a1b-150">Selected</span><span class="sxs-lookup"><span data-stu-id="f7a1b-150">Selected</span></span>|<span data-ttu-id="f7a1b-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-151">SelectionStates</span></span>|<span data-ttu-id="f7a1b-152">L’élément est actuellement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="f7a1b-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="f7a1b-153">SelectedUnfocused</span></span>|<span data-ttu-id="f7a1b-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-154">SelectionStates</span></span>|<span data-ttu-id="f7a1b-155">L’élément est sélectionné mais n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="f7a1b-156">Valide</span><span class="sxs-lookup"><span data-stu-id="f7a1b-156">Valid</span></span>|<span data-ttu-id="f7a1b-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-157">ValidationStates</span></span>|<span data-ttu-id="f7a1b-158">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f7a1b-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f7a1b-159">InvalidFocused</span></span>|<span data-ttu-id="f7a1b-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-160">ValidationStates</span></span>|<span data-ttu-id="f7a1b-161">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f7a1b-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f7a1b-162">InvalidUnfocused</span></span>|<span data-ttu-id="f7a1b-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f7a1b-163">ValidationStates</span></span>|<span data-ttu-id="f7a1b-164">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="f7a1b-165">Exemple de ControlTemplate pour les contrôles ListBox</span><span class="sxs-lookup"><span data-stu-id="f7a1b-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="f7a1b-166">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.ListBoxItem> contrôles.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="f7a1b-167">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="f7a1b-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f7a1b-168">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="f7a1b-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a1b-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7a1b-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f7a1b-170">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="f7a1b-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f7a1b-171">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="f7a1b-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f7a1b-172">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="f7a1b-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f7a1b-173">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f7a1b-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
