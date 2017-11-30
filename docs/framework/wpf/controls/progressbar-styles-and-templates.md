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
ms.openlocfilehash: 475607381f16d7b42f26f12809a11d5eaf4e74bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="10274-102">Styles et modèles ProgressBar</span><span class="sxs-lookup"><span data-stu-id="10274-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="10274-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="10274-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="10274-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="10274-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="10274-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="10274-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="10274-106">Parties de la barre de progression</span><span class="sxs-lookup"><span data-stu-id="10274-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="10274-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="10274-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="10274-108">Élément</span><span class="sxs-lookup"><span data-stu-id="10274-108">Part</span></span>|<span data-ttu-id="10274-109">Type</span><span class="sxs-lookup"><span data-stu-id="10274-109">Type</span></span>|<span data-ttu-id="10274-110">Description</span><span class="sxs-lookup"><span data-stu-id="10274-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="10274-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="10274-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="10274-112">Objet qui indique la progression.</span><span class="sxs-lookup"><span data-stu-id="10274-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="10274-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="10274-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="10274-114">Objet qui définit le chemin d’accès de l’indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="10274-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="10274-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="10274-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="10274-116">Objet qui embellit la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="10274-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="10274-117">États de la barre de progression</span><span class="sxs-lookup"><span data-stu-id="10274-117">ProgressBar States</span></span>  
 <span data-ttu-id="10274-118">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="10274-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="10274-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="10274-119">VisualState Name</span></span>|<span data-ttu-id="10274-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="10274-120">VisualStateGroup Name</span></span>|<span data-ttu-id="10274-121">Description</span><span class="sxs-lookup"><span data-stu-id="10274-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="10274-122">Déterminé</span><span class="sxs-lookup"><span data-stu-id="10274-122">Determinate</span></span>|<span data-ttu-id="10274-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10274-123">CommonStates</span></span>|<span data-ttu-id="10274-124"><xref:System.Windows.Controls.ProgressBar>signale la progression en fonction de la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="10274-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="10274-125">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="10274-125">Indeterminate</span></span>|<span data-ttu-id="10274-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10274-126">CommonStates</span></span>|<span data-ttu-id="10274-127"><xref:System.Windows.Controls.ProgressBar>signale la progression générale avec un modèle extensible.</span><span class="sxs-lookup"><span data-stu-id="10274-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="10274-128">Valide</span><span class="sxs-lookup"><span data-stu-id="10274-128">Valid</span></span>|<span data-ttu-id="10274-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10274-129">ValidationStates</span></span>|<span data-ttu-id="10274-130">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="10274-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="10274-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="10274-131">InvalidFocused</span></span>|<span data-ttu-id="10274-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10274-132">ValidationStates</span></span>|<span data-ttu-id="10274-133">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="10274-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="10274-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="10274-134">InvalidUnfocused</span></span>|<span data-ttu-id="10274-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10274-135">ValidationStates</span></span>|<span data-ttu-id="10274-136">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="10274-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="10274-137">ProgressBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="10274-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="10274-138">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="10274-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="10274-139">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="10274-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="10274-140">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="10274-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10274-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10274-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="10274-142">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="10274-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="10274-143">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="10274-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="10274-144">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="10274-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="10274-145">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="10274-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
