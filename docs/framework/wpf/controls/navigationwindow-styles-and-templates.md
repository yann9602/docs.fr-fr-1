---
title: "Styles et modèles NavigationWindow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b638d43fb59506572e2ccddd9da7188639bff279
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="a61ab-102">Styles et modèles NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="a61ab-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="a61ab-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Navigation.NavigationWindow> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a61ab-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="a61ab-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="a61ab-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a61ab-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a61ab-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="a61ab-106">Éléments de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="a61ab-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="a61ab-107">Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Navigation.NavigationWindow> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a61ab-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="a61ab-108">Élément</span><span class="sxs-lookup"><span data-stu-id="a61ab-108">Part</span></span>|<span data-ttu-id="a61ab-109">Type</span><span class="sxs-lookup"><span data-stu-id="a61ab-109">Type</span></span>|<span data-ttu-id="a61ab-110">Description</span><span class="sxs-lookup"><span data-stu-id="a61ab-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a61ab-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="a61ab-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="a61ab-112">La zone pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="a61ab-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="a61ab-113">États de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="a61ab-113">NavigationWindow States</span></span>  
 <span data-ttu-id="a61ab-114">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Navigation.NavigationWindow> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a61ab-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="a61ab-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="a61ab-115">VisualState Name</span></span>|<span data-ttu-id="a61ab-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a61ab-116">VisualStateGroup Name</span></span>|<span data-ttu-id="a61ab-117">Description</span><span class="sxs-lookup"><span data-stu-id="a61ab-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a61ab-118">Valide</span><span class="sxs-lookup"><span data-stu-id="a61ab-118">Valid</span></span>|<span data-ttu-id="a61ab-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a61ab-119">ValidationStates</span></span>|<span data-ttu-id="a61ab-120">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="a61ab-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a61ab-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a61ab-121">InvalidFocused</span></span>|<span data-ttu-id="a61ab-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a61ab-122">ValidationStates</span></span>|<span data-ttu-id="a61ab-123">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="a61ab-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a61ab-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a61ab-124">InvalidUnfocused</span></span>|<span data-ttu-id="a61ab-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a61ab-125">ValidationStates</span></span>|<span data-ttu-id="a61ab-126">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="a61ab-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="a61ab-127">NavigationWindow ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="a61ab-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="a61ab-128">Bien que cet exemple contienne tous les éléments qui sont définis dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Navigation.NavigationWindow> par défaut, les valeurs spécifiques doivent être considérées comme exemples.</span><span class="sxs-lookup"><span data-stu-id="a61ab-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="a61ab-129">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="a61ab-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a61ab-130">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="a61ab-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61ab-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a61ab-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a61ab-132">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="a61ab-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a61ab-133">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="a61ab-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a61ab-134">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="a61ab-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a61ab-135">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a61ab-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
