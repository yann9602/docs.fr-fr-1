---
title: StaticResource, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="bbf12-102">StaticResource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="bbf12-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="bbf12-103">Fournit une valeur pour tout [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en recherchant une référence à une ressource déjà définie.</span><span class="sxs-lookup"><span data-stu-id="bbf12-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="bbf12-104">Comportement de recherche de cette ressource est analogue à la recherche au moment du chargement, qui recherche des ressources qui ont été précédemment chargées à partir du balisage d’actuel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page ainsi que d’autres sources d’application et génère cette valeur de ressource en tant que le valeur de propriété dans les objets d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bbf12-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="bbf12-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="bbf12-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="bbf12-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="bbf12-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="bbf12-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="bbf12-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="bbf12-108">La clé pour la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="bbf12-108">The key for the requested resource.</span></span> <span data-ttu-id="bbf12-109">Cette clé a été initialement affectée par le [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) si une ressource a été créée dans la balise ou est fournie comme le `key` paramètre lors de l’appel <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.</span><span class="sxs-lookup"><span data-stu-id="bbf12-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf12-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bbf12-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbf12-111">A `StaticResource` ne devez pas tenter de faire une référence vers l’avant à une ressource qui est définie lexical dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier.</span><span class="sxs-lookup"><span data-stu-id="bbf12-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="bbf12-112">Tente de faire n’est pas pris en charge, et même si une telle référence n’échoue pas, la tentative de référence vers l’avant entraînera une baisse des performances temps charge lorsque les tables de hachage interne représentant un <xref:System.Windows.ResourceDictionary> sont recherchés.</span><span class="sxs-lookup"><span data-stu-id="bbf12-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="bbf12-113">Pour de meilleurs résultats, ajustez la composition de vos dictionnaires de ressources de manière à éviter les références vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="bbf12-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="bbf12-114">Si vous ne pouvez pas éviter une référence vers l’avant, utilisez [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="bbf12-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="bbf12-115">Spécifié <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante, identifiée par un [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) à un niveau dans votre page, application, thèmes de contrôle disponibles et ressources externes ou ressources système.</span><span class="sxs-lookup"><span data-stu-id="bbf12-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="bbf12-116">La recherche de ressource se produit dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="bbf12-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="bbf12-117">Pour plus d’informations sur le comportement de recherche de ressources statiques et dynamiques, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bbf12-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="bbf12-118">Une clé de ressource peut être n’importe quelle chaîne définie dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="bbf12-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="bbf12-119">Une clé de ressource peut être également les autres types d’objet, comme un <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="bbf12-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="bbf12-120">A <xref:System.Type> clé est essentielle à Comment contrôles peuvent être un style thèmes, via une clé de style implicite.</span><span class="sxs-lookup"><span data-stu-id="bbf12-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="bbf12-121">Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bbf12-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="bbf12-122">L’autre moyen déclaratif de référencement d’une ressource est un [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bbf12-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="bbf12-123">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="bbf12-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="bbf12-124">Le jeton de chaîne fourni après la chaîne d'identificateur `StaticResource` est assigné en tant que valeur <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> de la classe d'extension <xref:System.Windows.StaticResourceExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="bbf12-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="bbf12-125">`StaticResource`peut être utilisé dans la syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="bbf12-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="bbf12-126">Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> propriété est requise.</span><span class="sxs-lookup"><span data-stu-id="bbf12-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="bbf12-127">`StaticResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :</span><span class="sxs-lookup"><span data-stu-id="bbf12-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="bbf12-128">L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="bbf12-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="bbf12-129">
          `StaticResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.</span><span class="sxs-lookup"><span data-stu-id="bbf12-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="bbf12-130">Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.StaticResourceExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="bbf12-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="bbf12-131">`StaticResource` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="bbf12-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="bbf12-132">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="bbf12-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="bbf12-133">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="bbf12-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="bbf12-134">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="bbf12-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf12-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbf12-135">See Also</span></span>  
 [<span data-ttu-id="bbf12-136">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="bbf12-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="bbf12-137">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bbf12-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="bbf12-138">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="bbf12-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="bbf12-139">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="bbf12-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="bbf12-140">Ressources et code</span><span class="sxs-lookup"><span data-stu-id="bbf12-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)
