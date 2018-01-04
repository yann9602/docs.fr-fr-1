---
title: "Styles et modèles ProgressBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6809ce2f51af8a1baf535afa8fe80f4e5b5f53e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="6864a-102">Styles et modèles ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6864a-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="6864a-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6864a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="6864a-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="6864a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6864a-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6864a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="6864a-106">Parties de la barre de progression</span><span class="sxs-lookup"><span data-stu-id="6864a-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="6864a-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6864a-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="6864a-108">Élément</span><span class="sxs-lookup"><span data-stu-id="6864a-108">Part</span></span>|<span data-ttu-id="6864a-109">Type</span><span class="sxs-lookup"><span data-stu-id="6864a-109">Type</span></span>|<span data-ttu-id="6864a-110">Description</span><span class="sxs-lookup"><span data-stu-id="6864a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6864a-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="6864a-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="6864a-112">Objet qui indique la progression.</span><span class="sxs-lookup"><span data-stu-id="6864a-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="6864a-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="6864a-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="6864a-114">Objet qui définit le chemin d’accès de l’indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="6864a-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="6864a-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="6864a-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="6864a-116">Objet qui embellit la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="6864a-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="6864a-117">États de la barre de progression</span><span class="sxs-lookup"><span data-stu-id="6864a-117">ProgressBar States</span></span>  
 <span data-ttu-id="6864a-118">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6864a-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="6864a-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="6864a-119">VisualState Name</span></span>|<span data-ttu-id="6864a-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6864a-120">VisualStateGroup Name</span></span>|<span data-ttu-id="6864a-121">Description</span><span class="sxs-lookup"><span data-stu-id="6864a-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="6864a-122">Déterminé</span><span class="sxs-lookup"><span data-stu-id="6864a-122">Determinate</span></span>|<span data-ttu-id="6864a-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6864a-123">CommonStates</span></span>|<span data-ttu-id="6864a-124"><xref:System.Windows.Controls.ProgressBar>signale la progression en fonction de la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="6864a-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="6864a-125">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="6864a-125">Indeterminate</span></span>|<span data-ttu-id="6864a-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6864a-126">CommonStates</span></span>|<span data-ttu-id="6864a-127"><xref:System.Windows.Controls.ProgressBar>signale la progression générale avec un modèle extensible.</span><span class="sxs-lookup"><span data-stu-id="6864a-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="6864a-128">Valide</span><span class="sxs-lookup"><span data-stu-id="6864a-128">Valid</span></span>|<span data-ttu-id="6864a-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6864a-129">ValidationStates</span></span>|<span data-ttu-id="6864a-130">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="6864a-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6864a-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6864a-131">InvalidFocused</span></span>|<span data-ttu-id="6864a-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6864a-132">ValidationStates</span></span>|<span data-ttu-id="6864a-133">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="6864a-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6864a-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6864a-134">InvalidUnfocused</span></span>|<span data-ttu-id="6864a-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6864a-135">ValidationStates</span></span>|<span data-ttu-id="6864a-136">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="6864a-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="6864a-137">ProgressBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="6864a-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="6864a-138">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6864a-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="6864a-139">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="6864a-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6864a-140">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="6864a-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6864a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6864a-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6864a-142">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="6864a-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6864a-143">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="6864a-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6864a-144">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="6864a-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6864a-145">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6864a-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
