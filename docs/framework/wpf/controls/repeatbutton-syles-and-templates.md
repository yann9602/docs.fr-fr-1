---
title: "Styles et modèles RepeatButton"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4895757e909d5e15fd6540b19e1eeec414e1f4e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="repeatbutton-syles-and-templates"></a><span data-ttu-id="1bc65-102">Styles et modèles RepeatButton</span><span class="sxs-lookup"><span data-stu-id="1bc65-102">RepeatButton Syles and Templates</span></span>
<span data-ttu-id="1bc65-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Primitives.RepeatButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bc65-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="1bc65-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bc65-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1bc65-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1bc65-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="repeatbutton-parts"></a><span data-ttu-id="1bc65-106">Composants de RepeatButton</span><span class="sxs-lookup"><span data-stu-id="1bc65-106">RepeatButton Parts</span></span>  
 <span data-ttu-id="1bc65-107">Le <xref:System.Windows.Controls.Primitives.RepeatButton> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="1bc65-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>  
  
## <a name="repeatbutton-states"></a><span data-ttu-id="1bc65-108">États de RepeatButton</span><span class="sxs-lookup"><span data-stu-id="1bc65-108">RepeatButton States</span></span>  
 <span data-ttu-id="1bc65-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.RepeatButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bc65-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
|<span data-ttu-id="1bc65-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="1bc65-110">VisualState Name</span></span>|<span data-ttu-id="1bc65-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1bc65-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1bc65-112">Description</span><span class="sxs-lookup"><span data-stu-id="1bc65-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1bc65-113">Normale</span><span class="sxs-lookup"><span data-stu-id="1bc65-113">Normal</span></span>|<span data-ttu-id="1bc65-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-114">CommonStates</span></span>|<span data-ttu-id="1bc65-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="1bc65-115">The default state.</span></span>|  
|<span data-ttu-id="1bc65-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="1bc65-116">MouseOver</span></span>|<span data-ttu-id="1bc65-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-117">CommonStates</span></span>|<span data-ttu-id="1bc65-118">Le pointeur de la souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bc65-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1bc65-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="1bc65-119">Pressed</span></span>|<span data-ttu-id="1bc65-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-120">CommonStates</span></span>|<span data-ttu-id="1bc65-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="1bc65-121">The control is pressed.</span></span>|  
|<span data-ttu-id="1bc65-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="1bc65-122">Disabled</span></span>|<span data-ttu-id="1bc65-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-123">CommonStates</span></span>|<span data-ttu-id="1bc65-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="1bc65-124">The control is disabled.</span></span>|  
|<span data-ttu-id="1bc65-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="1bc65-125">Focused</span></span>|<span data-ttu-id="1bc65-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-126">FocusStates</span></span>|<span data-ttu-id="1bc65-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="1bc65-127">The control has focus.</span></span>|  
|<span data-ttu-id="1bc65-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="1bc65-128">Unfocused</span></span>|<span data-ttu-id="1bc65-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-129">FocusStates</span></span>|<span data-ttu-id="1bc65-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="1bc65-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="1bc65-131">Valide</span><span class="sxs-lookup"><span data-stu-id="1bc65-131">Valid</span></span>|<span data-ttu-id="1bc65-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-132">ValidationStates</span></span>|<span data-ttu-id="1bc65-133">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="1bc65-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1bc65-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1bc65-134">InvalidFocused</span></span>|<span data-ttu-id="1bc65-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-135">ValidationStates</span></span>|<span data-ttu-id="1bc65-136">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="1bc65-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1bc65-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1bc65-137">InvalidUnfocused</span></span>|<span data-ttu-id="1bc65-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1bc65-138">ValidationStates</span></span>|<span data-ttu-id="1bc65-139">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="1bc65-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="1bc65-140">Exemple de ControlTemplate RepeatButton</span><span class="sxs-lookup"><span data-stu-id="1bc65-140">RepeatButton ControlTemplate Example</span></span>  
 <span data-ttu-id="1bc65-141">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Primitives.RepeatButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bc65-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RepeatButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]  
  
 <span data-ttu-id="1bc65-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="1bc65-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1bc65-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="1bc65-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc65-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bc65-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1bc65-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="1bc65-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="1bc65-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="1bc65-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="1bc65-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="1bc65-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1bc65-148">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1bc65-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
