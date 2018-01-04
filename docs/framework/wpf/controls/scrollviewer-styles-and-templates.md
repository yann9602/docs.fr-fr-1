---
title: "Styles et modèles ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74f8a693a143e1c6788dd79a1c1bbd1954f8cfd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="19cff-102">Styles et modèles ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="19cff-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="19cff-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="19cff-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="19cff-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="19cff-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="19cff-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="19cff-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="19cff-106">Composants de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="19cff-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="19cff-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="19cff-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="19cff-108">Élément</span><span class="sxs-lookup"><span data-stu-id="19cff-108">Part</span></span>|<span data-ttu-id="19cff-109">Type</span><span class="sxs-lookup"><span data-stu-id="19cff-109">Type</span></span>|<span data-ttu-id="19cff-110">Description</span><span class="sxs-lookup"><span data-stu-id="19cff-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="19cff-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="19cff-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="19cff-112">L’espace réservé pour le contenu dans le <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="19cff-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="19cff-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="19cff-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="19cff-114">Le <xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu horizontalement.</span><span class="sxs-lookup"><span data-stu-id="19cff-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="19cff-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="19cff-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="19cff-116">Le <xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu verticalement.</span><span class="sxs-lookup"><span data-stu-id="19cff-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="19cff-117">États de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="19cff-117">ScrollViewer States</span></span>  
 <span data-ttu-id="19cff-118">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="19cff-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="19cff-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="19cff-119">VisualState Name</span></span>|<span data-ttu-id="19cff-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="19cff-120">VisualStateGroup Name</span></span>|<span data-ttu-id="19cff-121">Description</span><span class="sxs-lookup"><span data-stu-id="19cff-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="19cff-122">Valide</span><span class="sxs-lookup"><span data-stu-id="19cff-122">Valid</span></span>|<span data-ttu-id="19cff-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="19cff-123">ValidationStates</span></span>|<span data-ttu-id="19cff-124">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="19cff-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="19cff-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="19cff-125">InvalidFocused</span></span>|<span data-ttu-id="19cff-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="19cff-126">ValidationStates</span></span>|<span data-ttu-id="19cff-127">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="19cff-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="19cff-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="19cff-128">InvalidUnfocused</span></span>|<span data-ttu-id="19cff-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="19cff-129">ValidationStates</span></span>|<span data-ttu-id="19cff-130">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="19cff-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="19cff-131">ScrollViewer ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="19cff-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="19cff-132">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="19cff-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="19cff-133">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="19cff-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="19cff-134">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="19cff-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cff-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19cff-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="19cff-136">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="19cff-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="19cff-137">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="19cff-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="19cff-138">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="19cff-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="19cff-139">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="19cff-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
