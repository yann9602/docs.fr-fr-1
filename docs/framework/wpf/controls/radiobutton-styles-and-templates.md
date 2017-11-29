---
title: "Styles et modèles RadioButton"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384a587fe01fb69ff5d377f2aa34d03ff110880d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="cfd1d-102">Styles et modèles RadioButton</span><span class="sxs-lookup"><span data-stu-id="cfd1d-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="cfd1d-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.RadioButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="cfd1d-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cfd1d-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cfd1d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="cfd1d-106">Composants de RadioButton</span><span class="sxs-lookup"><span data-stu-id="cfd1d-106">RadioButton Parts</span></span>  
 <span data-ttu-id="cfd1d-107">Le <xref:System.Windows.Controls.RadioButton> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="cfd1d-108">États de RadioButton</span><span class="sxs-lookup"><span data-stu-id="cfd1d-108">RadioButton States</span></span>  
 <span data-ttu-id="cfd1d-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.RadioButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="cfd1d-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="cfd1d-110">VisualState Name</span></span>|<span data-ttu-id="cfd1d-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cfd1d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="cfd1d-112">Description</span><span class="sxs-lookup"><span data-stu-id="cfd1d-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cfd1d-113">Normale</span><span class="sxs-lookup"><span data-stu-id="cfd1d-113">Normal</span></span>|<span data-ttu-id="cfd1d-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-114">CommonStates</span></span>|<span data-ttu-id="cfd1d-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-115">The default state.</span></span>|  
|<span data-ttu-id="cfd1d-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cfd1d-116">MouseOver</span></span>|<span data-ttu-id="cfd1d-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-117">CommonStates</span></span>|<span data-ttu-id="cfd1d-118">Le pointeur de la souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cfd1d-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="cfd1d-119">Pressed</span></span>|<span data-ttu-id="cfd1d-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-120">CommonStates</span></span>|<span data-ttu-id="cfd1d-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-121">The control is pressed.</span></span>|  
|<span data-ttu-id="cfd1d-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="cfd1d-122">Disabled</span></span>|<span data-ttu-id="cfd1d-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-123">CommonStates</span></span>|<span data-ttu-id="cfd1d-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-124">The control is disabled.</span></span>|  
|<span data-ttu-id="cfd1d-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="cfd1d-125">Focused</span></span>|<span data-ttu-id="cfd1d-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-126">FocusStates</span></span>|<span data-ttu-id="cfd1d-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-127">The control has focus.</span></span>|  
|<span data-ttu-id="cfd1d-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="cfd1d-128">Unfocused</span></span>|<span data-ttu-id="cfd1d-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-129">FocusStates</span></span>|<span data-ttu-id="cfd1d-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="cfd1d-131">Activé</span><span class="sxs-lookup"><span data-stu-id="cfd1d-131">Checked</span></span>|<span data-ttu-id="cfd1d-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-132">CheckStates</span></span>|<span data-ttu-id="cfd1d-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="cfd1d-134">elle est désactivée</span><span class="sxs-lookup"><span data-stu-id="cfd1d-134">Unchecked</span></span>|<span data-ttu-id="cfd1d-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-135">CheckStates</span></span>|<span data-ttu-id="cfd1d-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="cfd1d-137">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="cfd1d-137">Indeterminate</span></span>|<span data-ttu-id="cfd1d-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-138">CheckStates</span></span>|<span data-ttu-id="cfd1d-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>est `true`, et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="cfd1d-140">Valide</span><span class="sxs-lookup"><span data-stu-id="cfd1d-140">Valid</span></span>|<span data-ttu-id="cfd1d-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-141">ValidationStates</span></span>|<span data-ttu-id="cfd1d-142">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cfd1d-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cfd1d-143">InvalidFocused</span></span>|<span data-ttu-id="cfd1d-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-144">ValidationStates</span></span>|<span data-ttu-id="cfd1d-145">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cfd1d-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cfd1d-146">InvalidUnfocused</span></span>|<span data-ttu-id="cfd1d-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cfd1d-147">ValidationStates</span></span>|<span data-ttu-id="cfd1d-148">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="cfd1d-149">RadioButton ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="cfd1d-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="cfd1d-150">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.RadioButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="cfd1d-151">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="cfd1d-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cfd1d-152">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="cfd1d-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd1d-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfd1d-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="cfd1d-154">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="cfd1d-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="cfd1d-155">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="cfd1d-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="cfd1d-156">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="cfd1d-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="cfd1d-157">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cfd1d-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
