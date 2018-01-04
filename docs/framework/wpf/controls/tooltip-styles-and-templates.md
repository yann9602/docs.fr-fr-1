---
title: "Styles et modèles ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e39372083ede5649addee4b493f2425116ec2aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="378ba-102">Styles et modèles ToolTip</span><span class="sxs-lookup"><span data-stu-id="378ba-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="378ba-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.ToolTip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="378ba-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="378ba-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="378ba-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="378ba-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="378ba-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="378ba-106">Parties de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="378ba-106">ToolTip Parts</span></span>  
 <span data-ttu-id="378ba-107">Le <xref:System.Windows.Controls.ToolTip> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="378ba-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="378ba-108">États de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="378ba-108">ToolTip States</span></span>  
 <span data-ttu-id="378ba-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ToolTip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="378ba-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="378ba-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="378ba-110">VisualState Name</span></span>|<span data-ttu-id="378ba-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="378ba-111">VisualStateGroup Name</span></span>|<span data-ttu-id="378ba-112">Description</span><span class="sxs-lookup"><span data-stu-id="378ba-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="378ba-113">Closed</span><span class="sxs-lookup"><span data-stu-id="378ba-113">Closed</span></span>|<span data-ttu-id="378ba-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="378ba-114">OpenStates</span></span>|<span data-ttu-id="378ba-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="378ba-115">The default state.</span></span>|  
|<span data-ttu-id="378ba-116">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="378ba-116">Open</span></span>|<span data-ttu-id="378ba-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="378ba-117">OpenStates</span></span>|<span data-ttu-id="378ba-118">Le <xref:System.Windows.Controls.ToolTip> est visible.</span><span class="sxs-lookup"><span data-stu-id="378ba-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="378ba-119">Valide</span><span class="sxs-lookup"><span data-stu-id="378ba-119">Valid</span></span>|<span data-ttu-id="378ba-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="378ba-120">ValidationStates</span></span>|<span data-ttu-id="378ba-121">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="378ba-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="378ba-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="378ba-122">InvalidFocused</span></span>|<span data-ttu-id="378ba-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="378ba-123">ValidationStates</span></span>|<span data-ttu-id="378ba-124">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="378ba-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="378ba-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="378ba-125">InvalidUnfocused</span></span>|<span data-ttu-id="378ba-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="378ba-126">ValidationStates</span></span>|<span data-ttu-id="378ba-127">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="378ba-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="378ba-128">Info-bulle ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="378ba-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="378ba-129">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.ToolTip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="378ba-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="378ba-130">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="378ba-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="378ba-131">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="378ba-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378ba-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="378ba-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="378ba-133">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="378ba-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="378ba-134">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="378ba-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="378ba-135">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="378ba-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="378ba-136">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="378ba-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
