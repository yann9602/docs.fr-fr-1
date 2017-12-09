---
title: "Styles et modèles GroupBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a39e09812c54df533fdac27b5bfcaedd3fb93ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="15e82-102">Styles et modèles GroupBox</span><span class="sxs-lookup"><span data-stu-id="15e82-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="15e82-103">Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="15e82-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="15e82-104">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="15e82-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="15e82-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="15e82-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="15e82-106">Parties de la zone de groupe</span><span class="sxs-lookup"><span data-stu-id="15e82-106">GroupBox Parts</span></span>  
 <span data-ttu-id="15e82-107">Le <xref:System.Windows.Controls.GroupBox> contrôle n’a pas de composants nommés.</span><span class="sxs-lookup"><span data-stu-id="15e82-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="15e82-108">États de GroupBox</span><span class="sxs-lookup"><span data-stu-id="15e82-108">GroupBox States</span></span>  
 <span data-ttu-id="15e82-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="15e82-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="15e82-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="15e82-110">VisualState Name</span></span>|<span data-ttu-id="15e82-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="15e82-111">VisualStateGroup Name</span></span>|<span data-ttu-id="15e82-112">Description</span><span class="sxs-lookup"><span data-stu-id="15e82-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="15e82-113">Valide</span><span class="sxs-lookup"><span data-stu-id="15e82-113">Valid</span></span>|<span data-ttu-id="15e82-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15e82-114">ValidationStates</span></span>|<span data-ttu-id="15e82-115">Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.</span><span class="sxs-lookup"><span data-stu-id="15e82-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="15e82-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="15e82-116">InvalidFocused</span></span>|<span data-ttu-id="15e82-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15e82-117">ValidationStates</span></span>|<span data-ttu-id="15e82-118">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="15e82-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="15e82-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="15e82-119">InvalidUnfocused</span></span>|<span data-ttu-id="15e82-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15e82-120">ValidationStates</span></span>|<span data-ttu-id="15e82-121">Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="15e82-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="15e82-122">GroupBox ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="15e82-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="15e82-123">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="15e82-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="15e82-124">Le <xref:System.Windows.Controls.ControlTemplate> utilise un ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="15e82-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="15e82-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="15e82-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e82-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15e82-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="15e82-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="15e82-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="15e82-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="15e82-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="15e82-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="15e82-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="15e82-130">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="15e82-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
