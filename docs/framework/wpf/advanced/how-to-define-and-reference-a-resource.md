---
title: "Comment : définir et référencer une ressource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="69345-102">Comment : définir et référencer une ressource</span><span class="sxs-lookup"><span data-stu-id="69345-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="69345-103">Cet exemple montre comment définir une ressource et y fait référence à l’aide d’un attribut dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69345-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="69345-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="69345-104">Example</span></span>  
 <span data-ttu-id="69345-105">L’exemple suivant définit deux types de ressources : un <xref:System.Windows.Media.SolidColorBrush> ressources et plusieurs <xref:System.Windows.Style> ressources.</span><span class="sxs-lookup"><span data-stu-id="69345-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="69345-106">Le <xref:System.Windows.Media.SolidColorBrush> ressource `MyBrush` est utilisée pour fournir la valeur de plusieurs propriétés qui prennent chacune un <xref:System.Windows.Media.Brush> de type valeur.</span><span class="sxs-lookup"><span data-stu-id="69345-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="69345-107">Le <xref:System.Windows.Style> ressources `PageBackground`, `TitleText` et `Label` chaque cible d’un type de contrôle particulier.</span><span class="sxs-lookup"><span data-stu-id="69345-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="69345-108">Les styles de définissent diverses propriétés différentes sur les contrôles ciblés lorsque cette ressource de style est référencée par la clé de ressource et qu’il est utilisée pour définir le <xref:System.Windows.FrameworkElement.Style%2A> propriétés de plusieurs éléments de contrôle spécifiques définis dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69345-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="69345-109">Notez que l’une des propriétés des accesseurs Set de la `Label` style fait également référence à la `MyBrush` ressources définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="69345-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="69345-110">Il s’agit d’une technique courante, mais il est important de se rappeler que les ressources sont analysées et entrés dans un dictionnaire de ressources dans l’ordre où elles sont fournies.</span><span class="sxs-lookup"><span data-stu-id="69345-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="69345-111">Ressources sont également demandées dans l’ordre qui se trouvent dans le dictionnaire si vous utilisez la [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) de les référencer à partir d’une autre ressource.</span><span class="sxs-lookup"><span data-stu-id="69345-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="69345-112">Assurez-vous que toutes les ressources que vous référencez sont défini plus haut dans la collection de ressources où cette ressource est demandée.</span><span class="sxs-lookup"><span data-stu-id="69345-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="69345-113">Si nécessaire, vous pouvez contourner l’ordre strict de création des références de ressources à l’aide un [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) fassent référence à la ressource lors de l’exécution à la place, mais vous devez être conscient que cette DynamicResource technique a des conséquences sur les performances.</span><span class="sxs-lookup"><span data-stu-id="69345-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="69345-114">Pour plus d’informations, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="69345-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="69345-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69345-115">See Also</span></span>  
 [<span data-ttu-id="69345-116">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="69345-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="69345-117">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="69345-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
