---
title: "Styles et modèles Expander"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04225458e9889c511b7aaa359239512e316cbb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="89aae-102">Styles et modèles Expander</span><span class="sxs-lookup"><span data-stu-id="89aae-102">Expander Styles and Templates</span></span>
<span data-ttu-id="89aae-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Expander> contrôle.</span><span class="sxs-lookup"><span data-stu-id="89aae-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="89aae-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="89aae-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="89aae-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="89aae-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="89aae-106">Composants d’Expander</span><span class="sxs-lookup"><span data-stu-id="89aae-106">Expander Parts</span></span>  
 <span data-ttu-id="89aae-107">Le <xref:System.Windows.Controls.Expander> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="89aae-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="89aae-108">États d’Expander</span><span class="sxs-lookup"><span data-stu-id="89aae-108">Expander States</span></span>  
 <span data-ttu-id="89aae-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Expander> contrôle.</span><span class="sxs-lookup"><span data-stu-id="89aae-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="89aae-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="89aae-110">VisualState Name</span></span>|<span data-ttu-id="89aae-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="89aae-111">VisualStateGroup Name</span></span>|<span data-ttu-id="89aae-112">Description</span><span class="sxs-lookup"><span data-stu-id="89aae-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="89aae-113">Normale</span><span class="sxs-lookup"><span data-stu-id="89aae-113">Normal</span></span>|<span data-ttu-id="89aae-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="89aae-114">CommonStates</span></span>|<span data-ttu-id="89aae-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="89aae-115">The default state.</span></span>|  
|<span data-ttu-id="89aae-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="89aae-116">MouseOver</span></span>|<span data-ttu-id="89aae-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="89aae-117">CommonStates</span></span>|<span data-ttu-id="89aae-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="89aae-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="89aae-119">Désactivé</span><span class="sxs-lookup"><span data-stu-id="89aae-119">Disabled</span></span>|<span data-ttu-id="89aae-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="89aae-120">CommonStates</span></span>|<span data-ttu-id="89aae-121">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="89aae-121">The control is disabled.</span></span>|  
|<span data-ttu-id="89aae-122">Avec focus</span><span class="sxs-lookup"><span data-stu-id="89aae-122">Focused</span></span>|<span data-ttu-id="89aae-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="89aae-123">FocusStates</span></span>|<span data-ttu-id="89aae-124">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="89aae-124">The control has focus.</span></span>|  
|<span data-ttu-id="89aae-125">Sans focus</span><span class="sxs-lookup"><span data-stu-id="89aae-125">Unfocused</span></span>|<span data-ttu-id="89aae-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="89aae-126">FocusStates</span></span>|<span data-ttu-id="89aae-127">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="89aae-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="89aae-128">Développé</span><span class="sxs-lookup"><span data-stu-id="89aae-128">Expanded</span></span>|<span data-ttu-id="89aae-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-129">ExpansionStates</span></span>|<span data-ttu-id="89aae-130">Le contrôle est développé.</span><span class="sxs-lookup"><span data-stu-id="89aae-130">The control is expanded.</span></span>|  
|<span data-ttu-id="89aae-131">Réduit</span><span class="sxs-lookup"><span data-stu-id="89aae-131">Collapsed</span></span>|<span data-ttu-id="89aae-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-132">ExpansionStates</span></span>|<span data-ttu-id="89aae-133">Le contrôle n’est pas développé.</span><span class="sxs-lookup"><span data-stu-id="89aae-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="89aae-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="89aae-134">ExpandDown</span></span>|<span data-ttu-id="89aae-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-135">ExpandDirectionStates</span></span>|<span data-ttu-id="89aae-136">Le contrôle se développe vers le bas.</span><span class="sxs-lookup"><span data-stu-id="89aae-136">The control expands down.</span></span>|  
|<span data-ttu-id="89aae-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="89aae-137">ExpandUp</span></span>|<span data-ttu-id="89aae-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-138">ExpandDirectionStates</span></span>|<span data-ttu-id="89aae-139">Le contrôle se développe des.</span><span class="sxs-lookup"><span data-stu-id="89aae-139">The control expands up.</span></span>|  
|<span data-ttu-id="89aae-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="89aae-140">ExpandLeft</span></span>|<span data-ttu-id="89aae-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-141">ExpandDirectionStates</span></span>|<span data-ttu-id="89aae-142">Le contrôle se développe de gauche.</span><span class="sxs-lookup"><span data-stu-id="89aae-142">The control expands left.</span></span>|  
|<span data-ttu-id="89aae-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="89aae-143">ExpandRight</span></span>|<span data-ttu-id="89aae-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="89aae-144">ExpandDirectionStates</span></span>|<span data-ttu-id="89aae-145">Le contrôle s’étend à droite.</span><span class="sxs-lookup"><span data-stu-id="89aae-145">The control expands right.</span></span>|  
|<span data-ttu-id="89aae-146">Valide</span><span class="sxs-lookup"><span data-stu-id="89aae-146">Valid</span></span>|<span data-ttu-id="89aae-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89aae-147">ValidationStates</span></span>|<span data-ttu-id="89aae-148">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="89aae-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="89aae-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="89aae-149">InvalidFocused</span></span>|<span data-ttu-id="89aae-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89aae-150">ValidationStates</span></span>|<span data-ttu-id="89aae-151">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="89aae-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="89aae-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="89aae-152">InvalidUnfocused</span></span>|<span data-ttu-id="89aae-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89aae-153">ValidationStates</span></span>|<span data-ttu-id="89aae-154">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="89aae-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="89aae-155">Exemple d’Expander ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="89aae-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="89aae-156">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Expander> contrôle.</span><span class="sxs-lookup"><span data-stu-id="89aae-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="89aae-157">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="89aae-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="89aae-158">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="89aae-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89aae-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89aae-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="89aae-160">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="89aae-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="89aae-161">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="89aae-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="89aae-162">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="89aae-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="89aae-163">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="89aae-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
