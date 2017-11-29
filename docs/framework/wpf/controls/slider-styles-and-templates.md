---
title: "Styles et modèles Slider"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9dfa340cf42e5e7ed105bf14eb0f7a24ea85a1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="3e483-102">Styles et modèles Slider</span><span class="sxs-lookup"><span data-stu-id="3e483-102">Slider Styles and Templates</span></span>
<span data-ttu-id="3e483-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Slider> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="3e483-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3e483-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3e483-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="3e483-106">Parties de curseur</span><span class="sxs-lookup"><span data-stu-id="3e483-106">Slider Parts</span></span>  
 <span data-ttu-id="3e483-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Slider> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="3e483-108">Élément</span><span class="sxs-lookup"><span data-stu-id="3e483-108">Part</span></span>|<span data-ttu-id="3e483-109">Type</span><span class="sxs-lookup"><span data-stu-id="3e483-109">Type</span></span>|<span data-ttu-id="3e483-110">Description</span><span class="sxs-lookup"><span data-stu-id="3e483-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3e483-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="3e483-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="3e483-112">Le conteneur de l’élément qui indique la position de la <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="3e483-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="3e483-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="3e483-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3e483-114">L’élément qui affiche une plage de sélection le long de la <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="3e483-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="3e483-115">La plage de sélection est visible uniquement si le <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="3e483-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="3e483-116">États de curseur</span><span class="sxs-lookup"><span data-stu-id="3e483-116">Slider States</span></span>  
 <span data-ttu-id="3e483-117">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Slider> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="3e483-118">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="3e483-118">VisualState Name</span></span>|<span data-ttu-id="3e483-119">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3e483-119">VisualStateGroup Name</span></span>|<span data-ttu-id="3e483-120">Description</span><span class="sxs-lookup"><span data-stu-id="3e483-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3e483-121">Normale</span><span class="sxs-lookup"><span data-stu-id="3e483-121">Normal</span></span>|<span data-ttu-id="3e483-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e483-122">CommonStates</span></span>|<span data-ttu-id="3e483-123">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="3e483-123">The default state.</span></span>|  
|<span data-ttu-id="3e483-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="3e483-124">MouseOver</span></span>|<span data-ttu-id="3e483-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e483-125">CommonStates</span></span>|<span data-ttu-id="3e483-126">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="3e483-127">Désactivé</span><span class="sxs-lookup"><span data-stu-id="3e483-127">Disabled</span></span>|<span data-ttu-id="3e483-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e483-128">CommonStates</span></span>|<span data-ttu-id="3e483-129">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="3e483-129">The control is disabled.</span></span>|  
|<span data-ttu-id="3e483-130">Avec focus</span><span class="sxs-lookup"><span data-stu-id="3e483-130">Focused</span></span>|<span data-ttu-id="3e483-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3e483-131">FocusStates</span></span>|<span data-ttu-id="3e483-132">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="3e483-132">The control has focus.</span></span>|  
|<span data-ttu-id="3e483-133">Sans focus</span><span class="sxs-lookup"><span data-stu-id="3e483-133">Unfocused</span></span>|<span data-ttu-id="3e483-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3e483-134">FocusStates</span></span>|<span data-ttu-id="3e483-135">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="3e483-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="3e483-136">Valide</span><span class="sxs-lookup"><span data-stu-id="3e483-136">Valid</span></span>|<span data-ttu-id="3e483-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e483-137">ValidationStates</span></span>|<span data-ttu-id="3e483-138">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="3e483-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3e483-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3e483-139">InvalidFocused</span></span>|<span data-ttu-id="3e483-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e483-140">ValidationStates</span></span>|<span data-ttu-id="3e483-141">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="3e483-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3e483-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3e483-142">InvalidUnfocused</span></span>|<span data-ttu-id="3e483-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e483-143">ValidationStates</span></span>|<span data-ttu-id="3e483-144">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="3e483-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="3e483-145">Exemple de ControlTemplate de curseur</span><span class="sxs-lookup"><span data-stu-id="3e483-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="3e483-146">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Slider> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e483-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="3e483-147">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e483-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3e483-148">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="3e483-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e483-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e483-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3e483-150">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="3e483-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="3e483-151">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="3e483-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="3e483-152">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="3e483-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3e483-153">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3e483-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
