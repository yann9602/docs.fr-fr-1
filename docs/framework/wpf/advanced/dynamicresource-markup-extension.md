---
title: DynamicResource, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="3f97b-102">DynamicResource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="3f97b-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="3f97b-103">Fournit une valeur pour tout [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en différant cette valeur pour être une référence à une ressource définie.</span><span class="sxs-lookup"><span data-stu-id="3f97b-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="3f97b-104">Comportement de recherche de cette ressource est analogue à la recherche au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f97b-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3f97b-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="3f97b-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="3f97b-106">Utilisation des éléments de propriété XAML</span><span class="sxs-lookup"><span data-stu-id="3f97b-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3f97b-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="3f97b-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="3f97b-108">Clé pour la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="3f97b-108">The key for the requested resource.</span></span> <span data-ttu-id="3f97b-109">Cette clé a été initialement affectée par le [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) si une ressource a été créée dans la balise ou est fournie comme le `key` paramètre lors de l’appel <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.</span><span class="sxs-lookup"><span data-stu-id="3f97b-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f97b-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3f97b-110">Remarks</span></span>  
 <span data-ttu-id="3f97b-111">A `DynamicResource` créera une expression temporaire pendant la compilation initiale et donc différer la recherche des ressources jusqu'à ce que la valeur de la ressource demandée est réellement nécessaire afin de construire un objet.</span><span class="sxs-lookup"><span data-stu-id="3f97b-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="3f97b-112">Cela peut potentiellement être après le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est chargée.</span><span class="sxs-lookup"><span data-stu-id="3f97b-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="3f97b-113">La valeur de ressource est trouvée en fonction de recherche de clé par rapport à tous les dictionnaires de ressources actif à partir de la portée de la page actuelle et est remplacée par l’expression d’espace réservé de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3f97b-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f97b-114">En termes de la propriété de dépendance, un `DynamicResource` expression est équivalente à la position où la référence de ressource dynamique est appliquée.</span><span class="sxs-lookup"><span data-stu-id="3f97b-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="3f97b-115">Si vous définissez une valeur locale pour une propriété qui avait précédemment une `DynamicResource` expression en tant que la valeur locale, le `DynamicResource` est entièrement supprimée.</span><span class="sxs-lookup"><span data-stu-id="3f97b-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="3f97b-116">Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="3f97b-117">Certains scénarios d’accès aux ressources sont particulièrement appropriés pour `DynamicResource` par opposition à un [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="3f97b-118">Consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) pour une discussion concernant le bien-fondé relatif et les implications en matière de performances de `DynamicResource` et `StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="3f97b-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="3f97b-119">Spécifié <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante déterminée par [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) à un niveau dans votre page, application, thèmes de contrôle disponibles et ressources externes ou les ressources système et le recherche de ressources aura lieu dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="3f97b-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="3f97b-120">Pour plus d’informations sur la recherche de ressources pour les ressources statiques et dynamiques, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="3f97b-121">Une clé de ressource peut être n’importe quelle chaîne définie dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="3f97b-122">Une clé de ressource peut être également les autres types d’objet, comme un <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="3f97b-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="3f97b-123">A <xref:System.Type> clé est essentielle à la façon dont les contrôles peuvent avoir le format par des thèmes.</span><span class="sxs-lookup"><span data-stu-id="3f97b-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="3f97b-124">Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="3f97b-125">pour la recherche de valeurs de ressources, telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, suivez la même logique de recherche de ressources que celles utilisées par `DynamicResource`.</span><span class="sxs-lookup"><span data-stu-id="3f97b-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="3f97b-126">L’autre moyen déclaratif de référencement d’une ressource est un [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="3f97b-127">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f97b-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3f97b-128">Le jeton de chaîne fourni après la chaîne d'identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d'extension <xref:System.Windows.DynamicResourceExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="3f97b-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="3f97b-129">`DynamicResource`peut être utilisé dans la syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="3f97b-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="3f97b-130">Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> propriété est requise.</span><span class="sxs-lookup"><span data-stu-id="3f97b-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="3f97b-131">`DynamicResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :</span><span class="sxs-lookup"><span data-stu-id="3f97b-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="3f97b-132">L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="3f97b-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="3f97b-133">
          `DynamicResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.</span><span class="sxs-lookup"><span data-stu-id="3f97b-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="3f97b-134">Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.DynamicResourceExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="3f97b-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="3f97b-135">`DynamicResource` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f97b-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="3f97b-136">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="3f97b-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3f97b-137">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3f97b-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="3f97b-138">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3f97b-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f97b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f97b-139">See Also</span></span>  
 [<span data-ttu-id="3f97b-140">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="3f97b-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="3f97b-141">Ressources et code</span><span class="sxs-lookup"><span data-stu-id="3f97b-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="3f97b-142">x:Key, directive</span><span class="sxs-lookup"><span data-stu-id="3f97b-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="3f97b-143">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="3f97b-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3f97b-144">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="3f97b-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="3f97b-145">StaticResource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="3f97b-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="3f97b-146">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="3f97b-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
