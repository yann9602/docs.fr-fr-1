---
title: "Modèles et styles intralignes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dccf0b274121ff4fe88c9270119a2f631ffcf29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="ee584-102">Modèles et styles intralignes</span><span class="sxs-lookup"><span data-stu-id="ee584-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="ee584-103">Fournit des <xref:System.Windows.Style> objets et les objets de modèle (<xref:System.Windows.FrameworkTemplate> sous-classes) afin de définir l’apparence visuelle d’un élément dans les ressources, afin qu’ils peuvent être utilisés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="ee584-103"> provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="ee584-104">Pour cette raison, les attributs dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui prennent les types <xref:System.Windows.Style> et <xref:System.Windows.FrameworkTemplate> presque toujours font référence aux styles et modèles existant des ressources plutôt que définir de nouveaux inline.</span><span class="sxs-lookup"><span data-stu-id="ee584-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="ee584-105">Limitations des modèles et des Styles intralignes</span><span class="sxs-lookup"><span data-stu-id="ee584-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="ee584-106">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], pouvant techniquement définir les propriétés de style et de modèle de deux façons.</span><span class="sxs-lookup"><span data-stu-id="ee584-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="ee584-107">Vous pouvez utiliser la syntaxe d’attribut pour faire référence à un style qui a été défini dans une ressource, par exemple `<` *objet*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="ee584-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="ee584-108">Ou vous pouvez utiliser la syntaxe d’élément de propriété pour définir un style intraligne, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ee584-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="ee584-109">`<`*objet*`>`</span><span class="sxs-lookup"><span data-stu-id="ee584-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="ee584-110">`<`*objet*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="ee584-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="ee584-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="ee584-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="ee584-112">`</`*objet*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="ee584-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="ee584-113">`</`*objet*`>`</span><span class="sxs-lookup"><span data-stu-id="ee584-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="ee584-114">L’utilisation de l’attribut est beaucoup plus courante.</span><span class="sxs-lookup"><span data-stu-id="ee584-114">The attribute usage is much more common.</span></span> <span data-ttu-id="ee584-115">Un style qui est définie en ligne et les ressources non définies dans nécessairement consacré à l’élément conteneur uniquement et ne peut pas être réutilisé aussi facilement car il n’a aucune clé de ressource.</span><span class="sxs-lookup"><span data-stu-id="ee584-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="ee584-116">En général un style de la ressource définie est plus souple et utile et est plus conforme générales [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] principe de séparer la logique de programme dans le code de la conception dans le balisage modèle de programmation.</span><span class="sxs-lookup"><span data-stu-id="ee584-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="ee584-117">En général il n’existe aucune raison pour laquelle définir un style ou un modèle en ligne, même si vous comptez utiliser uniquement ce style ou modèle à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="ee584-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="ee584-118">La plupart des éléments qui peuvent prendre un style ou un modèle prennent également en charge une propriété de contenu et un modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="ee584-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="ee584-119">Si vous utilisez uniquement l’arborescence logique de créer dans un style ou de la création de modèles qu’une seule fois, il est encore plus facile de renseigner simplement cette propriété de contenu avec les éléments enfants équivalents dans les balises directes.</span><span class="sxs-lookup"><span data-stu-id="ee584-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="ee584-120">Cela permettrait de contourner les mécanismes de style et de modèle complètement.</span><span class="sxs-lookup"><span data-stu-id="ee584-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="ee584-121">Autres syntaxes activées par les extensions de balisage qui retournent un objet sont également possibles pour les styles et modèles.</span><span class="sxs-lookup"><span data-stu-id="ee584-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="ee584-122">Deux extensions des scénarios possibles incluent [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) et <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="ee584-122">Two such extensions that have possible scenarios include [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee584-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee584-123">See Also</span></span>  
 [<span data-ttu-id="ee584-124">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="ee584-124">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
