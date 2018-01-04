---
title: ComponentResourceKey, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bfaee35ba9f8cf60deb01c52a142433d08021c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="e9843-102">ComponentResourceKey, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="e9843-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="e9843-103">Définit et référence des clés pour les ressources qui sont chargés à partir des assemblys externes.</span><span class="sxs-lookup"><span data-stu-id="e9843-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="e9843-104">Cela permet une recherche de ressource spécifier un type de cible dans un assembly, plutôt qu’un dictionnaire de ressources explicite dans un assembly ou une classe.</span><span class="sxs-lookup"><span data-stu-id="e9843-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="e9843-105">Utilisation d’attributs XAML (définition de clé, compacte)</span><span class="sxs-lookup"><span data-stu-id="e9843-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="e9843-106">Utilisation d’attributs XAML (définition de clé, détaillé)</span><span class="sxs-lookup"><span data-stu-id="e9843-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="e9843-107">Utilisation d’attributs XAML (demande de ressource, compact)</span><span class="sxs-lookup"><span data-stu-id="e9843-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="e9843-108">Utilisation d’attributs XAML (demande de ressource, détaillé)</span><span class="sxs-lookup"><span data-stu-id="e9843-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e9843-109">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="e9843-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="e9843-110">Le nom public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type qui est défini dans l’assembly de ressources.</span><span class="sxs-lookup"><span data-stu-id="e9843-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="e9843-111">La clé pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="e9843-111">The key for the resource.</span></span> <span data-ttu-id="e9843-112">Lors de la recherche de ressources, `targetID` sera similaire à la [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e9843-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9843-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e9843-113">Remarks</span></span>  
 <span data-ttu-id="e9843-114">Comme indiqué dans les utilisations ci-dessus, un {`ComponentResourceKey`} extension de balisage se trouve dans deux emplacements :</span><span class="sxs-lookup"><span data-stu-id="e9843-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="e9843-115">La définition d’une clé dans un dictionnaire de ressources de thème, tel que fourni par un auteur de contrôle.</span><span class="sxs-lookup"><span data-stu-id="e9843-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="e9843-116">L’accès à une ressource du thème à partir de l’assembly, lorsque vous apprêter le contrôle mais souhaitez utiliser les valeurs de propriété qui viennent de ressources fournies par les thèmes du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e9843-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="e9843-117">Pour faire référence à des ressources de composant qui proviennent de thèmes, il est généralement recommandé d’utiliser `{DynamicResource}` plutôt que `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="e9843-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="e9843-118">Cela est illustré dans les utilisations.</span><span class="sxs-lookup"><span data-stu-id="e9843-118">This is shown in the usages.</span></span> <span data-ttu-id="e9843-119">`{DynamicResource}`est recommandée car le thème lui-même peut être modifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9843-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="e9843-120">Si vous souhaitez que la ressource de composant qui correspond le mieux à l’intention de l’auteur de contrôle pour un thème de prise en charge, vous devez activer votre référence de ressource de composant d’être également dynamique.</span><span class="sxs-lookup"><span data-stu-id="e9843-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="e9843-121">Le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifie un type qui existe dans l’assembly cible où la ressource est définie.</span><span class="sxs-lookup"><span data-stu-id="e9843-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="e9843-122">A `ComponentResourceKey` peut être définie et utilisée indépendamment de savoir exactement où le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> est défini, mais par la suite doit résoudre le via les assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="e9843-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="e9843-123">Une utilisation commune pour <xref:System.Windows.ComponentResourceKey> consiste à définir des clés qui sont ensuite exposées en tant que membres d’une classe.</span><span class="sxs-lookup"><span data-stu-id="e9843-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="e9843-124">Pour cela, vous utilisez la <xref:System.Windows.ComponentResourceKey> constructeur de classe, pas l’extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="e9843-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="e9843-125">Pour plus d’informations, consultez <xref:System.Windows.ComponentResourceKey>, ou la section « Définition et référencement de clés pour les ressources de thème » de la rubrique [vue d’ensemble de la création de contrôle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="e9843-126">Pour établir des clés et faisant référence à des ressources de clé, la syntaxe d’attribut est généralement utilisée pour le `ComponentResourceKey` extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="e9843-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="e9843-127">La syntaxe compacte indiquée s’appuie sur la <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> signature de constructeur et l’utilisation des paramètres positionnels d’une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="e9843-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="e9843-128">L’ordre dans lequel le `targetTypeName` et `targetID` figurent est important.</span><span class="sxs-lookup"><span data-stu-id="e9843-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="e9843-129">La syntaxe détaillée s’appuie sur le <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructeur par défaut, puis définit la <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> d’une manière analogue à la syntaxe d’attribut réelle sur un élément objet.</span><span class="sxs-lookup"><span data-stu-id="e9843-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="e9843-130">Dans la syntaxe détaillée, l’ordre dans lequel les propriétés sont définies n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="e9843-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="e9843-131">La relation et les mécanismes de cette alternative (compacte et détaillée) est décrite plus en détail dans la rubrique [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="e9843-132">Techniquement, la valeur de `targetID` peut être n’importe quel objet, il n’a pas à être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e9843-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="e9843-133">Toutefois, l’utilisation la plus courante dans WPF est d’aligner les `targetID` valeur avec les formulaires qui sont des chaînes, et où ces chaînes sont valides dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="e9843-134">`ComponentResourceKey`peut être utilisé dans la syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="e9843-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="e9843-135">Dans ce cas, en spécifiant la valeur des deux le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> propriétés est requis pour initialiser correctement l’extension.</span><span class="sxs-lookup"><span data-stu-id="e9843-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="e9843-136">Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation de lecteur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.ComponentResourceKey> classe.</span><span class="sxs-lookup"><span data-stu-id="e9843-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="e9843-137">`ComponentResourceKey` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="e9843-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="e9843-138">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="e9843-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="e9843-139">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="e9843-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="e9843-140">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9843-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9843-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e9843-142">Vue d’ensemble de la création de contrôles</span><span class="sxs-lookup"><span data-stu-id="e9843-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="e9843-143">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="e9843-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="e9843-144">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="e9843-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
