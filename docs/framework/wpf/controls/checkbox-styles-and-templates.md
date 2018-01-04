---
title: "Styles et modèles CheckBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b37be727c8a124ea7c4955b3eaf23d1bc9a485
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="e3c73-102">Styles et modèles CheckBox</span><span class="sxs-lookup"><span data-stu-id="e3c73-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="e3c73-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.CheckBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3c73-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="e3c73-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3c73-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e3c73-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e3c73-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="e3c73-106">Parties de la case à cocher</span><span class="sxs-lookup"><span data-stu-id="e3c73-106">CheckBox Parts</span></span>  
 <span data-ttu-id="e3c73-107">Le <xref:System.Windows.Controls.CheckBox> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="e3c73-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="e3c73-108">États de case à cocher</span><span class="sxs-lookup"><span data-stu-id="e3c73-108">CheckBox States</span></span>  
 <span data-ttu-id="e3c73-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.CheckBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3c73-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="e3c73-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="e3c73-110">VisualState Name</span></span>|<span data-ttu-id="e3c73-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e3c73-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e3c73-112">Description</span><span class="sxs-lookup"><span data-stu-id="e3c73-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e3c73-113">Normale</span><span class="sxs-lookup"><span data-stu-id="e3c73-113">Normal</span></span>|<span data-ttu-id="e3c73-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-114">CommonStates</span></span>|<span data-ttu-id="e3c73-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="e3c73-115">The default state.</span></span>|  
|<span data-ttu-id="e3c73-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e3c73-116">MouseOver</span></span>|<span data-ttu-id="e3c73-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-117">CommonStates</span></span>|<span data-ttu-id="e3c73-118">Le pointeur de la souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3c73-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e3c73-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="e3c73-119">Pressed</span></span>|<span data-ttu-id="e3c73-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-120">CommonStates</span></span>|<span data-ttu-id="e3c73-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="e3c73-121">The control is pressed.</span></span>|  
|<span data-ttu-id="e3c73-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="e3c73-122">Disabled</span></span>|<span data-ttu-id="e3c73-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-123">CommonStates</span></span>|<span data-ttu-id="e3c73-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="e3c73-124">The control is disabled.</span></span>|  
|<span data-ttu-id="e3c73-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="e3c73-125">Focused</span></span>|<span data-ttu-id="e3c73-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-126">FocusStates</span></span>|<span data-ttu-id="e3c73-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="e3c73-127">The control has focus.</span></span>|  
|<span data-ttu-id="e3c73-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="e3c73-128">Unfocused</span></span>|<span data-ttu-id="e3c73-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-129">FocusStates</span></span>|<span data-ttu-id="e3c73-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="e3c73-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="e3c73-131">Activé</span><span class="sxs-lookup"><span data-stu-id="e3c73-131">Checked</span></span>|<span data-ttu-id="e3c73-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-132">CheckStates</span></span>|<span data-ttu-id="e3c73-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e3c73-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="e3c73-134">elle est désactivée</span><span class="sxs-lookup"><span data-stu-id="e3c73-134">Unchecked</span></span>|<span data-ttu-id="e3c73-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-135">CheckStates</span></span>|<span data-ttu-id="e3c73-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="e3c73-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="e3c73-137">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="e3c73-137">Indeterminate</span></span>|<span data-ttu-id="e3c73-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-138">CheckStates</span></span>|<span data-ttu-id="e3c73-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>est `true`, et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.</span><span class="sxs-lookup"><span data-stu-id="e3c73-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="e3c73-140">Valide</span><span class="sxs-lookup"><span data-stu-id="e3c73-140">Valid</span></span>|<span data-ttu-id="e3c73-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-141">ValidationStates</span></span>|<span data-ttu-id="e3c73-142">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="e3c73-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e3c73-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e3c73-143">InvalidUnfocused</span></span>|<span data-ttu-id="e3c73-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-144">ValidationStates</span></span>|<span data-ttu-id="e3c73-145">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="e3c73-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e3c73-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e3c73-146">InvalidFocused</span></span>|<span data-ttu-id="e3c73-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e3c73-147">ValidationStates</span></span>|<span data-ttu-id="e3c73-148">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="e3c73-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="e3c73-149">Exemple de ControlTemplate de case à cocher</span><span class="sxs-lookup"><span data-stu-id="e3c73-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="e3c73-150">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.CheckBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3c73-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="e3c73-151">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="e3c73-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e3c73-152">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="e3c73-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c73-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3c73-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e3c73-154">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="e3c73-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e3c73-155">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="e3c73-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e3c73-156">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="e3c73-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e3c73-157">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e3c73-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
