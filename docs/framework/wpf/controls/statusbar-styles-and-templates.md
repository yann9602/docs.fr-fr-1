---
title: "Styles et modèles StatusBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 370f8f9bc61ffbdd3b98743d11f61613803e6d98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="17a68-102">Styles et modèles StatusBar</span><span class="sxs-lookup"><span data-stu-id="17a68-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="17a68-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Primitives.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="17a68-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="17a68-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="17a68-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="17a68-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="17a68-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="17a68-106">Composants de StatusBar</span><span class="sxs-lookup"><span data-stu-id="17a68-106">StatusBar Parts</span></span>  
 <span data-ttu-id="17a68-107">Le <xref:System.Windows.Controls.Primitives.StatusBar> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="17a68-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="17a68-108">États de StatusBar</span><span class="sxs-lookup"><span data-stu-id="17a68-108">StatusBar States</span></span>  
 <span data-ttu-id="17a68-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="17a68-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="17a68-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="17a68-110">VisualState Name</span></span>|<span data-ttu-id="17a68-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="17a68-111">VisualStateGroup Name</span></span>|<span data-ttu-id="17a68-112">Description</span><span class="sxs-lookup"><span data-stu-id="17a68-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="17a68-113">Valide</span><span class="sxs-lookup"><span data-stu-id="17a68-113">Valid</span></span>|<span data-ttu-id="17a68-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-114">ValidationStates</span></span>|<span data-ttu-id="17a68-115">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="17a68-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="17a68-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="17a68-116">InvalidFocused</span></span>|<span data-ttu-id="17a68-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-117">ValidationStates</span></span>|<span data-ttu-id="17a68-118">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="17a68-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="17a68-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="17a68-119">InvalidUnfocused</span></span>|<span data-ttu-id="17a68-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-120">ValidationStates</span></span>|<span data-ttu-id="17a68-121">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="17a68-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="17a68-122">Composants de StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="17a68-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="17a68-123">Le <xref:System.Windows.Controls.Primitives.StatusBarItem> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="17a68-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="17a68-124">États de StatusBar</span><span class="sxs-lookup"><span data-stu-id="17a68-124">StatusBar States</span></span>  
 <span data-ttu-id="17a68-125">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.StatusBarItem> contrôle.</span><span class="sxs-lookup"><span data-stu-id="17a68-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="17a68-126">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="17a68-126">VisualState Name</span></span>|<span data-ttu-id="17a68-127">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="17a68-127">VisualStateGroup Name</span></span>|<span data-ttu-id="17a68-128">Description</span><span class="sxs-lookup"><span data-stu-id="17a68-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="17a68-129">Valide</span><span class="sxs-lookup"><span data-stu-id="17a68-129">Valid</span></span>|<span data-ttu-id="17a68-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-130">ValidationStates</span></span>|<span data-ttu-id="17a68-131">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="17a68-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="17a68-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="17a68-132">InvalidFocused</span></span>|<span data-ttu-id="17a68-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-133">ValidationStates</span></span>|<span data-ttu-id="17a68-134">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="17a68-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="17a68-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="17a68-135">InvalidUnfocused</span></span>|<span data-ttu-id="17a68-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17a68-136">ValidationStates</span></span>|<span data-ttu-id="17a68-137">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="17a68-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="17a68-138">StatusBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="17a68-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="17a68-139">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Primitives.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="17a68-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="17a68-140">Le <xref:System.Windows.Controls.ControlTemplate> utilise un ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="17a68-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="17a68-141">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="17a68-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a68-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17a68-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="17a68-143">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="17a68-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="17a68-144">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="17a68-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="17a68-145">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="17a68-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="17a68-146">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="17a68-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
