---
title: x:Array, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2304ba68956b705904c72e29a17bdac4536c79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="f51a3-102">x:Array, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="f51a3-102">x:Array Markup Extension</span></span>
<span data-ttu-id="f51a3-103">Fournit la prise en charge générale pour les tableaux d’objets en XAML via une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="f51a3-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="f51a3-104">Cela correspond à la `x:ArrayExtension` type XAML [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="f51a3-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="f51a3-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="f51a3-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f51a3-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="f51a3-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="f51a3-107">Le nom du type que votre `x:Array` contiendra.</span><span class="sxs-lookup"><span data-stu-id="f51a3-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="f51a3-108">`typeName`peut être (et est souvent) comme préfixe pour un XAML définitions de type espace de noms qui contient le code XAML.</span><span class="sxs-lookup"><span data-stu-id="f51a3-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="f51a3-109">Le contenu d’éléments est affecté à la fonction intrinsèque `ArrayExtension.Items` propriété.</span><span class="sxs-lookup"><span data-stu-id="f51a3-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="f51a3-110">En règle générale, ces éléments sont spécifiés en tant qu’un ou plusieurs éléments objet contenus dans le `x:Array` balises ouvrantes et fermantes.</span><span class="sxs-lookup"><span data-stu-id="f51a3-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="f51a3-111">Les objets spécifiés ici sont supposés être assigné au type XAML spécifié dans `typeName`.</span><span class="sxs-lookup"><span data-stu-id="f51a3-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f51a3-112">Notes</span><span class="sxs-lookup"><span data-stu-id="f51a3-112">Remarks</span></span>  
 <span data-ttu-id="f51a3-113">`Type`est un attribut obligatoire pour tous les `x:Array` éléments objet.</span><span class="sxs-lookup"><span data-stu-id="f51a3-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="f51a3-114">A `Type` la valeur du paramètre n’a pas besoin d’utiliser un `x:Type` extension de balisage ; court nom du type est un type XAML, qui peut être spécifié sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f51a3-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="f51a3-115">Dans l’implémentation de Services XAML .NET Framework, la relation entre le type XAML d’entrée et la sortie CLR <xref:System.Type> du tableau créé sont influencées par le contexte de service pour les extensions de balisage.</span><span class="sxs-lookup"><span data-stu-id="f51a3-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="f51a3-116">La sortie <xref:System.Type> est la <xref:System.Xaml.XamlType.UnderlyingType%2A> du type XAML d’entrée, après avoir recherché le nécessaire <xref:System.Xaml.XamlType> selon le contexte de schéma XAML et le <xref:System.Windows.Markup.IXamlTypeResolver> le contexte de service.</span><span class="sxs-lookup"><span data-stu-id="f51a3-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="f51a3-117">Lors du traitement, le contenu du tableau est affecté à la `ArrayExtension.Items` propriété intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="f51a3-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="f51a3-118">Dans le <xref:System.Windows.Markup.ArrayExtension> implémentation, il est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f51a3-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f51a3-119">Dans l’implémentation de Services XAML .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.ArrayExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="f51a3-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="f51a3-120"><xref:System.Windows.Markup.ArrayExtension>n’est pas scellé et peut être utilisé comme base pour une implémentation d’extension de balisage pour un type de tableau personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f51a3-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="f51a3-121">`x:Array`est que plus destiné au grand extensibilité de langage dans XAML.</span><span class="sxs-lookup"><span data-stu-id="f51a3-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="f51a3-122">Mais `x:Array` peut également être utile pour spécifier des valeurs XAML de certaines propriétés qui prennent des collections de prise en charge de XAML en tant que contenu de propriété structuré.</span><span class="sxs-lookup"><span data-stu-id="f51a3-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="f51a3-123">Par exemple, vous pouvez spécifier le contenu d’un <xref:System.Collections.IEnumerable> propriété avec une `x:Array` l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="f51a3-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="f51a3-124">`x:Array` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="f51a3-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="f51a3-125">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="f51a3-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f51a3-126">`x:Array`est partiellement une exception à cette règle, car au lieu de fournir un traitement de valeur d’attribut de remplacement, `x:Array` fournit un autre traitement de son contenu de texte interne.</span><span class="sxs-lookup"><span data-stu-id="f51a3-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="f51a3-127">Ce comportement permet aux types qui ne peuvent pas être pris en charge par un modèle de contenu existant d’être regroupées dans un tableau et référencés plus loin dans le code-behind en accédant au tableau nommé ; Vous pouvez appeler <xref:System.Array> méthodes pour obtenir des éléments de tableau individuels.</span><span class="sxs-lookup"><span data-stu-id="f51a3-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="f51a3-128">Toutes les extensions de balisage en XAML utilisent les accolades ({,}`)` dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="f51a3-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="f51a3-129">Pour plus d’informations sur les extensions de balisage en général, consultez [convertisseurs de Type et Extensions de balisage pour XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f51a3-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="f51a3-130">Dans XAML 2009, `x:Array` est défini en tant que langage primitif au lieu d’une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="f51a3-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="f51a3-131">Pour plus d’informations, consultez [Types intégrés pour les Primitives de langage XAML commun](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="f51a3-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="f51a3-132">Notes d’utilisation WPF</span><span class="sxs-lookup"><span data-stu-id="f51a3-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="f51a3-133">En règle générale, les éléments objet qui remplissent un `x:Array` ne sont pas des éléments qui existent dans le [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] espace de noms XAML et requièrent un mappage de préfixe pour un espace de noms XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="f51a3-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="f51a3-134">Par exemple, Voici un tableau simple de deux chaînes, avec le `sys` préfixe (et également `x`) définie au niveau du tableau.</span><span class="sxs-lookup"><span data-stu-id="f51a3-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="f51a3-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="f51a3-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="f51a3-136">Pour les types personnalisés qui sont utilisés comme éléments de tableau, la classe doit également en charge la configuration requise pour être instancié en XAML en tant qu’éléments de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f51a3-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="f51a3-137">Pour plus d’informations, consultez [XAML et Classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="f51a3-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51a3-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51a3-138">See Also</span></span>  
 [<span data-ttu-id="f51a3-139">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="f51a3-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="f51a3-140">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="f51a3-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
