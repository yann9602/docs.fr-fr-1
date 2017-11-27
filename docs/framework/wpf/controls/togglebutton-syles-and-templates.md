---
title: "Styles et modèles ToggleButton"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd6696ff9d62b4aa3397ac8567edc3fb387ba96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="f260d-102">Styles et modèles ToggleButton</span><span class="sxs-lookup"><span data-stu-id="f260d-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="f260d-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f260d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="f260d-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="f260d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f260d-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f260d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="f260d-106">Composants de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="f260d-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="f260d-107">Le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="f260d-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="f260d-108">États de bouton bascule</span><span class="sxs-lookup"><span data-stu-id="f260d-108">ToggleButton States</span></span>  
 <span data-ttu-id="f260d-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f260d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="f260d-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="f260d-110">VisualState Name</span></span>|<span data-ttu-id="f260d-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f260d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f260d-112">Description</span><span class="sxs-lookup"><span data-stu-id="f260d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f260d-113">Normale</span><span class="sxs-lookup"><span data-stu-id="f260d-113">Normal</span></span>|<span data-ttu-id="f260d-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f260d-114">CommonStates</span></span>|<span data-ttu-id="f260d-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="f260d-115">The default state.</span></span>|  
|<span data-ttu-id="f260d-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f260d-116">MouseOver</span></span>|<span data-ttu-id="f260d-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f260d-117">CommonStates</span></span>|<span data-ttu-id="f260d-118">Le pointeur de la souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f260d-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f260d-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="f260d-119">Pressed</span></span>|<span data-ttu-id="f260d-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f260d-120">CommonStates</span></span>|<span data-ttu-id="f260d-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="f260d-121">The control is pressed.</span></span>|  
|<span data-ttu-id="f260d-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="f260d-122">Disabled</span></span>|<span data-ttu-id="f260d-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f260d-123">CommonStates</span></span>|<span data-ttu-id="f260d-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="f260d-124">The control is disabled.</span></span>|  
|<span data-ttu-id="f260d-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="f260d-125">Focused</span></span>|<span data-ttu-id="f260d-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f260d-126">FocusStates</span></span>|<span data-ttu-id="f260d-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="f260d-127">The control has focus.</span></span>|  
|<span data-ttu-id="f260d-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="f260d-128">Unfocused</span></span>|<span data-ttu-id="f260d-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f260d-129">FocusStates</span></span>|<span data-ttu-id="f260d-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f260d-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="f260d-131">Activé</span><span class="sxs-lookup"><span data-stu-id="f260d-131">Checked</span></span>|<span data-ttu-id="f260d-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f260d-132">CheckStates</span></span>|<span data-ttu-id="f260d-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f260d-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="f260d-134">elle est désactivée</span><span class="sxs-lookup"><span data-stu-id="f260d-134">Unchecked</span></span>|<span data-ttu-id="f260d-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f260d-135">CheckStates</span></span>|<span data-ttu-id="f260d-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="f260d-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="f260d-137">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="f260d-137">Indeterminate</span></span>|<span data-ttu-id="f260d-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f260d-138">CheckStates</span></span>|<span data-ttu-id="f260d-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>est `true`, et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.</span><span class="sxs-lookup"><span data-stu-id="f260d-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="f260d-140">Valide</span><span class="sxs-lookup"><span data-stu-id="f260d-140">Valid</span></span>|<span data-ttu-id="f260d-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f260d-141">ValidationStates</span></span>|<span data-ttu-id="f260d-142">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="f260d-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f260d-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f260d-143">InvalidFocused</span></span>|<span data-ttu-id="f260d-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f260d-144">ValidationStates</span></span>|<span data-ttu-id="f260d-145">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="f260d-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f260d-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f260d-146">InvalidUnfocused</span></span>|<span data-ttu-id="f260d-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f260d-147">ValidationStates</span></span>|<span data-ttu-id="f260d-148">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="f260d-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f260d-149">Si l’état visuel Indeterminate n’existe pas dans votre modèle de contrôle, puis l’état visuel Unchecked sera utilisé comme état visuel par défaut.</span><span class="sxs-lookup"><span data-stu-id="f260d-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="f260d-150">Exemple de ControlTemplate ToggleButton</span><span class="sxs-lookup"><span data-stu-id="f260d-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="f260d-151">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f260d-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="f260d-152">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="f260d-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f260d-153">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="f260d-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f260d-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f260d-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f260d-155">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="f260d-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f260d-156">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="f260d-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f260d-157">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="f260d-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f260d-158">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f260d-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
