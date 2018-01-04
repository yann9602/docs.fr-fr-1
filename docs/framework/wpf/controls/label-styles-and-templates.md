---
title: "Styles et modèles Label"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6189470b5a0a01911bfe71ddfa003f72f64356c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="7a5f9-102">Styles et modèles Label</span><span class="sxs-lookup"><span data-stu-id="7a5f9-102">Label Styles and Templates</span></span>
<span data-ttu-id="7a5f9-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Label> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="7a5f9-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7a5f9-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7a5f9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="7a5f9-106">Parties de l’étiquette</span><span class="sxs-lookup"><span data-stu-id="7a5f9-106">Label Parts</span></span>  
 <span data-ttu-id="7a5f9-107">Le <xref:System.Windows.Controls.Label> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="7a5f9-108">États d’étiquette</span><span class="sxs-lookup"><span data-stu-id="7a5f9-108">Label States</span></span>  
 <span data-ttu-id="7a5f9-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Label> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="7a5f9-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="7a5f9-110">VisualState Name</span></span>|<span data-ttu-id="7a5f9-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7a5f9-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7a5f9-112">Description</span><span class="sxs-lookup"><span data-stu-id="7a5f9-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7a5f9-113">Valide</span><span class="sxs-lookup"><span data-stu-id="7a5f9-113">Valid</span></span>|<span data-ttu-id="7a5f9-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a5f9-114">ValidationStates</span></span>|<span data-ttu-id="7a5f9-115">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7a5f9-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7a5f9-116">InvalidFocused</span></span>|<span data-ttu-id="7a5f9-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a5f9-117">ValidationStates</span></span>|<span data-ttu-id="7a5f9-118">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7a5f9-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7a5f9-119">InvalidUnfocused</span></span>|<span data-ttu-id="7a5f9-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a5f9-120">ValidationStates</span></span>|<span data-ttu-id="7a5f9-121">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="7a5f9-122">Exemple de ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7a5f9-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="7a5f9-123">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Label> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="7a5f9-124">Le <xref:System.Windows.Controls.ControlTemplate> utilise un ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="7a5f9-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7a5f9-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="7a5f9-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5f9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a5f9-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7a5f9-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="7a5f9-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7a5f9-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="7a5f9-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7a5f9-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="7a5f9-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7a5f9-130">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7a5f9-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
