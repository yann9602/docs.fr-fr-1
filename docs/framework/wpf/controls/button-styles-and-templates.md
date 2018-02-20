---
title: "Styles et modèles Button"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d783b3141463ca2c74ddd649848ea49e154415b6
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="c2ff8-102">Styles et modèles Button</span><span class="sxs-lookup"><span data-stu-id="c2ff8-102">Button Styles and Templates</span></span>
<span data-ttu-id="c2ff8-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="c2ff8-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c2ff8-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c2ff8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="c2ff8-106">Parties de bouton</span><span class="sxs-lookup"><span data-stu-id="c2ff8-106">Button Parts</span></span>  
 <span data-ttu-id="c2ff8-107">Le <xref:System.Windows.Controls.Button> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="c2ff8-108">États de bouton</span><span class="sxs-lookup"><span data-stu-id="c2ff8-108">Button States</span></span>  
 <span data-ttu-id="c2ff8-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="c2ff8-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="c2ff8-110">VisualState Name</span></span>|<span data-ttu-id="c2ff8-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c2ff8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c2ff8-112">Description</span><span class="sxs-lookup"><span data-stu-id="c2ff8-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c2ff8-113">Normale</span><span class="sxs-lookup"><span data-stu-id="c2ff8-113">Normal</span></span>|<span data-ttu-id="c2ff8-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-114">CommonStates</span></span>|<span data-ttu-id="c2ff8-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-115">The default state.</span></span>|  
|<span data-ttu-id="c2ff8-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c2ff8-116">MouseOver</span></span>|<span data-ttu-id="c2ff8-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-117">CommonStates</span></span>|<span data-ttu-id="c2ff8-118">Le pointeur de la souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c2ff8-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="c2ff8-119">Pressed</span></span>|<span data-ttu-id="c2ff8-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-120">CommonStates</span></span>|<span data-ttu-id="c2ff8-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-121">The control is pressed.</span></span>|  
|<span data-ttu-id="c2ff8-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="c2ff8-122">Disabled</span></span>|<span data-ttu-id="c2ff8-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-123">CommonStates</span></span>|<span data-ttu-id="c2ff8-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-124">The control is disabled.</span></span>|  
|<span data-ttu-id="c2ff8-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="c2ff8-125">Focused</span></span>|<span data-ttu-id="c2ff8-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-126">FocusStates</span></span>|<span data-ttu-id="c2ff8-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-127">The control has focus.</span></span>|  
|<span data-ttu-id="c2ff8-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="c2ff8-128">Unfocused</span></span>|<span data-ttu-id="c2ff8-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-129">FocusStates</span></span>|<span data-ttu-id="c2ff8-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="c2ff8-131">Valide</span><span class="sxs-lookup"><span data-stu-id="c2ff8-131">Valid</span></span>|<span data-ttu-id="c2ff8-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-132">ValidationStates</span></span>|<span data-ttu-id="c2ff8-133">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c2ff8-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c2ff8-134">InvalidFocused</span></span>|<span data-ttu-id="c2ff8-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-135">ValidationStates</span></span>|<span data-ttu-id="c2ff8-136">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="c2ff8-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c2ff8-137">InvalidUnfocused</span></span>|<span data-ttu-id="c2ff8-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2ff8-138">ValidationStates</span></span>|<span data-ttu-id="c2ff8-139">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="c2ff8-140">Exemple de ControlTemplate de bouton</span><span class="sxs-lookup"><span data-stu-id="c2ff8-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="c2ff8-141">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="c2ff8-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="c2ff8-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c2ff8-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="c2ff8-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ff8-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2ff8-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c2ff8-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="c2ff8-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c2ff8-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="c2ff8-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c2ff8-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="c2ff8-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c2ff8-148">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c2ff8-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
