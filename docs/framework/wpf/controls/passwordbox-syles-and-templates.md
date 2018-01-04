---
title: "Styles et modèles PasswordBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22b73704d21fa719a678799c1d95fc266c661e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="e6a0f-102">Styles et modèles PasswordBox</span><span class="sxs-lookup"><span data-stu-id="e6a0f-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="e6a0f-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.PasswordBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="e6a0f-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e6a0f-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e6a0f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="e6a0f-106">Composants de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="e6a0f-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="e6a0f-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.PasswordBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="e6a0f-108">Élément</span><span class="sxs-lookup"><span data-stu-id="e6a0f-108">Part</span></span>|<span data-ttu-id="e6a0f-109">Type</span><span class="sxs-lookup"><span data-stu-id="e6a0f-109">Type</span></span>|<span data-ttu-id="e6a0f-110">Description</span><span class="sxs-lookup"><span data-stu-id="e6a0f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e6a0f-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="e6a0f-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="e6a0f-112">Un élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="e6a0f-113">Le texte de la <xref:System.Windows.Controls.PasswordBox> s’affiche dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="e6a0f-114">États de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="e6a0f-114">PasswordBox States</span></span>  
 <span data-ttu-id="e6a0f-115">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.PasswordBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="e6a0f-116">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="e6a0f-116">VisualState Name</span></span>|<span data-ttu-id="e6a0f-117">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e6a0f-117">VisualStateGroup Name</span></span>|<span data-ttu-id="e6a0f-118">Description</span><span class="sxs-lookup"><span data-stu-id="e6a0f-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e6a0f-119">Normale</span><span class="sxs-lookup"><span data-stu-id="e6a0f-119">Normal</span></span>|<span data-ttu-id="e6a0f-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-120">CommonStates</span></span>|<span data-ttu-id="e6a0f-121">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-121">The default state.</span></span>|  
|<span data-ttu-id="e6a0f-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e6a0f-122">MouseOver</span></span>|<span data-ttu-id="e6a0f-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-123">CommonStates</span></span>|<span data-ttu-id="e6a0f-124">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e6a0f-125">Désactivé</span><span class="sxs-lookup"><span data-stu-id="e6a0f-125">Disabled</span></span>|<span data-ttu-id="e6a0f-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-126">CommonStates</span></span>|<span data-ttu-id="e6a0f-127">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-127">The control is disabled.</span></span>|  
|<span data-ttu-id="e6a0f-128">Avec focus</span><span class="sxs-lookup"><span data-stu-id="e6a0f-128">Focused</span></span>|<span data-ttu-id="e6a0f-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-129">FocusStates</span></span>|<span data-ttu-id="e6a0f-130">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-130">The control has focus.</span></span>|  
|<span data-ttu-id="e6a0f-131">Sans focus</span><span class="sxs-lookup"><span data-stu-id="e6a0f-131">Unfocused</span></span>|<span data-ttu-id="e6a0f-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-132">FocusStates</span></span>|<span data-ttu-id="e6a0f-133">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="e6a0f-134">Valide</span><span class="sxs-lookup"><span data-stu-id="e6a0f-134">Valid</span></span>|<span data-ttu-id="e6a0f-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-135">ValidationStates</span></span>|<span data-ttu-id="e6a0f-136">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e6a0f-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e6a0f-137">InvalidFocused</span></span>|<span data-ttu-id="e6a0f-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-138">ValidationStates</span></span>|<span data-ttu-id="e6a0f-139">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e6a0f-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e6a0f-140">InvalidUnfocused</span></span>|<span data-ttu-id="e6a0f-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6a0f-141">ValidationStates</span></span>|<span data-ttu-id="e6a0f-142">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="e6a0f-143">PasswordBox ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="e6a0f-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="e6a0f-144">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.PasswordBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="e6a0f-145">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="e6a0f-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e6a0f-146">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="e6a0f-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a0f-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6a0f-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e6a0f-148">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="e6a0f-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e6a0f-149">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="e6a0f-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e6a0f-150">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="e6a0f-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e6a0f-151">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e6a0f-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
