---
title: "Styles et modèles TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d4fdb652876f2df049b71c18b0b79b7b435da8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="cd73e-102">Styles et modèles TextBox</span><span class="sxs-lookup"><span data-stu-id="cd73e-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="cd73e-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="cd73e-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cd73e-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cd73e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="cd73e-106">Parties de la zone de texte</span><span class="sxs-lookup"><span data-stu-id="cd73e-106">TextBox Parts</span></span>  
 <span data-ttu-id="cd73e-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cd73e-108">Élément</span><span class="sxs-lookup"><span data-stu-id="cd73e-108">Part</span></span>|<span data-ttu-id="cd73e-109">Type</span><span class="sxs-lookup"><span data-stu-id="cd73e-109">Type</span></span>|<span data-ttu-id="cd73e-110">Description</span><span class="sxs-lookup"><span data-stu-id="cd73e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cd73e-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="cd73e-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cd73e-112">Un élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="cd73e-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="cd73e-113">Le texte de la <xref:System.Windows.Controls.TextBox> s’affiche dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="cd73e-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="cd73e-114">États de la zone de texte</span><span class="sxs-lookup"><span data-stu-id="cd73e-114">TextBox States</span></span>  
 <span data-ttu-id="cd73e-115">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cd73e-116">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="cd73e-116">VisualState Name</span></span>|<span data-ttu-id="cd73e-117">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cd73e-117">VisualStateGroup Name</span></span>|<span data-ttu-id="cd73e-118">Description</span><span class="sxs-lookup"><span data-stu-id="cd73e-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cd73e-119">Normale</span><span class="sxs-lookup"><span data-stu-id="cd73e-119">Normal</span></span>|<span data-ttu-id="cd73e-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-120">CommonStates</span></span>|<span data-ttu-id="cd73e-121">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="cd73e-121">The default state.</span></span>|  
|<span data-ttu-id="cd73e-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cd73e-122">MouseOver</span></span>|<span data-ttu-id="cd73e-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-123">CommonStates</span></span>|<span data-ttu-id="cd73e-124">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cd73e-125">Désactivé</span><span class="sxs-lookup"><span data-stu-id="cd73e-125">Disabled</span></span>|<span data-ttu-id="cd73e-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-126">CommonStates</span></span>|<span data-ttu-id="cd73e-127">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="cd73e-127">The control is disabled.</span></span>|  
|<span data-ttu-id="cd73e-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="cd73e-128">ReadOnly</span></span>|<span data-ttu-id="cd73e-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-129">CommonStates</span></span>|<span data-ttu-id="cd73e-130">L’utilisateur ne peut pas modifier le texte dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cd73e-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="cd73e-131">Avec focus</span><span class="sxs-lookup"><span data-stu-id="cd73e-131">Focused</span></span>|<span data-ttu-id="cd73e-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-132">FocusStates</span></span>|<span data-ttu-id="cd73e-133">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="cd73e-133">The control has focus.</span></span>|  
|<span data-ttu-id="cd73e-134">Sans focus</span><span class="sxs-lookup"><span data-stu-id="cd73e-134">Unfocused</span></span>|<span data-ttu-id="cd73e-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-135">FocusStates</span></span>|<span data-ttu-id="cd73e-136">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="cd73e-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="cd73e-137">Valide</span><span class="sxs-lookup"><span data-stu-id="cd73e-137">Valid</span></span>|<span data-ttu-id="cd73e-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-138">ValidationStates</span></span>|<span data-ttu-id="cd73e-139">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd73e-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cd73e-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cd73e-140">InvalidFocused</span></span>|<span data-ttu-id="cd73e-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-141">ValidationStates</span></span>|<span data-ttu-id="cd73e-142">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="cd73e-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cd73e-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cd73e-143">InvalidUnfocused</span></span>|<span data-ttu-id="cd73e-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd73e-144">ValidationStates</span></span>|<span data-ttu-id="cd73e-145">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="cd73e-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="cd73e-146">Exemple de ControlTemplate de zone de texte</span><span class="sxs-lookup"><span data-stu-id="cd73e-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="cd73e-147">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd73e-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="cd73e-148">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="cd73e-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cd73e-149">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="cd73e-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd73e-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd73e-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="cd73e-151">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="cd73e-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="cd73e-152">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="cd73e-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="cd73e-153">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="cd73e-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="cd73e-154">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cd73e-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
