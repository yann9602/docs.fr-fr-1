---
title: x:Type, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="6b3c2-102">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="6b3c2-102">x:Type Markup Extension</span></span>
<span data-ttu-id="6b3c2-103">Fournit le CLR <xref:System.Type> objet qui est le type sous-jacent pour un type XAML spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6b3c2-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="6b3c2-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="6b3c2-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="6b3c2-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6b3c2-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="6b3c2-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="6b3c2-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-107">Optional.</span></span> <span data-ttu-id="6b3c2-108">Un préfixe qui mappe un espace de noms XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="6b3c2-109">Définition d’un préfixe n’est généralement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="6b3c2-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="6b3c2-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-111">Required.</span></span> <span data-ttu-id="6b3c2-112">Un nom de type peut être résolu à l’espace de noms XAML par défaut en cours ; ou spécifié préfixe mappé si `prefix` est fourni.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b3c2-113">Notes</span><span class="sxs-lookup"><span data-stu-id="6b3c2-113">Remarks</span></span>  
 <span data-ttu-id="6b3c2-114">Le `x:Type` extension de balisage a une fonction semblable à la `typeof()` opérateur dans [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ou `GetType` opérateur dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b3c2-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="6b3c2-115">Le `x:Type` extension de balisage fournit un comportement de conversion de chaînes pour les propriétés qui prennent le type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="6b3c2-116">L’entrée est un type XAML.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-116">The input is a XAML type.</span></span> <span data-ttu-id="6b3c2-117">La relation entre le type XAML d’entrée et la sortie CLR <xref:System.Type> est que la sortie <xref:System.Type> est la <xref:System.Xaml.XamlType.UnderlyingType%2A> de l’entrée <xref:System.Xaml.XamlType>, après avoir recherché le nécessaire <xref:System.Xaml.XamlType> selon le contexte de schéma XAML et le <xref:System.Windows.Markup.IXamlTypeResolver>le contexte de service.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="6b3c2-118">Dans les Services XAML .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.TypeExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="6b3c2-119">Dans les implémentations d’infrastructure spécifiques, certaines propriétés qui acceptent <xref:System.Type> comme une valeur accepte directement le nom du type (la valeur de chaîne du type `Name`).</span><span class="sxs-lookup"><span data-stu-id="6b3c2-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="6b3c2-120">Toutefois, l’implémentation de ce comportement est un scénario complexe.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="6b3c2-121">Pour obtenir des exemples, consultez la section « Remarques sur l’utilisation WPF » qui suit.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="6b3c2-122">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="6b3c2-123">Le jeton de chaîne fourni après la chaîne d'identificateur `x:Type` est assigné en tant que valeur <xref:System.Windows.Markup.TypeExtension.TypeName%2A> de la classe d'extension <xref:System.Windows.Markup.TypeExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="6b3c2-124">Dans le contexte de schéma XAML par défaut pour les Services XAML .NET Framework, qui est basé sur les types CLR, la valeur de cet attribut est le <xref:System.Reflection.MemberInfo.Name%2A> du type souhaité, ou qui contient <xref:System.Reflection.MemberInfo.Name%2A> précédé d’un préfixe pour un espace de noms XAML par défaut mappage.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="6b3c2-125">Le `x:Type` extension de balisage peut être utilisée dans la syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="6b3c2-126">Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriété est requise pour initialiser correctement l’extension.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="6b3c2-127">Le `x:Type` extension de balisage peut également servir comme attribut brut ; toutefois cette utilisation n’est pas classique : `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="6b3c2-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="6b3c2-128">Notes d’utilisation WPF</span><span class="sxs-lookup"><span data-stu-id="6b3c2-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="6b3c2-129">Namespace XAML et le mappage de Type par défaut</span><span class="sxs-lookup"><span data-stu-id="6b3c2-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="6b3c2-130">L’espace de noms XAML par défaut pour la programmation WPF contient la plupart des types XAML, que vous avez besoin pour les scénarios XAML standard. Par conséquent, vous pouvez souvent éviter des préfixes lors du référencement de valeurs de type XAML.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="6b3c2-131">Vous devrez peut-être mapper un préfixe si vous référencez un type d’un assembly personnalisé ou pour les types qui existent dans un assembly WPF mais qui sont dans un espace de noms CLR qui n’a pas été mappé à l’espace de noms XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="6b3c2-132">Pour plus d’informations sur les préfixes d’espaces de noms XAML et les espaces de noms CLR mappage, consultez [espaces de noms XAML et mappage Namespace pour XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="6b3c2-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="6b3c2-133">Cette prise en charge Typename en tant que chaîne de propriétés de type</span><span class="sxs-lookup"><span data-stu-id="6b3c2-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="6b3c2-134">WPF prend en charge des techniques permettant la spécification de la valeur de certaines propriétés de type <xref:System.Type> sans nécessiter une `x:Type` extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="6b3c2-135">Au lieu de cela, vous pouvez spécifier la valeur sous forme de chaîne qui désigne le type.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="6b3c2-136">Des exemples sont <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> et <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b3c2-137">Prise en charge pour ce comportement n’est pas fournie par les convertisseurs de type ou les extensions de balisage.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="6b3c2-138">Au lieu de cela, il s’agit d’un comportement de report implémenté par le biais <xref:System.Windows.FrameworkElementFactory>.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="6b3c2-139">Silverlight prend en charge une convention similaire.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="6b3c2-140">En fait, Silverlight ne prend pas en charge `{x:Type}` dans sa prise en charge du langage XAML et n’accepte pas `{x:Type}` utilisations en dehors de quelques cas qui sont destinés à prendre en charge la migration de XAML WPF-Silverlight.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="6b3c2-141">Par conséquent, le comportement typename-as-string est intégré à l’évaluation de propriété native de Silverlight tous les où un <xref:System.Type> est la valeur.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="6b3c2-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="6b3c2-142">XAML 2009</span></span>  
 <span data-ttu-id="6b3c2-143">XAML 2009 fournit la prise en charge supplémentaire pour les types génériques et modifie le comportement de la fonctionnalité de `x:TypeArguments` et `x:Type` pour fournir cette prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="6b3c2-144">`x:TypeArguments`et l’élément objet associé pour une instanciation d’objet générique peut être sur des éléments autres que la racine.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="6b3c2-145">Pour plus d’informations, consultez la section « XAML 2009 » de [Directive x : TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="6b3c2-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="6b3c2-146">XAML 2009 prend en charge une syntaxe permettant de spécifier la contrainte d’un type générique dans le balisage.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="6b3c2-147">Cela peut être utilisé par `x:TypeArguments`, par `x:Type`, ou par les deux fonctionnalités conjointement.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="6b3c2-148">Implémentation XAML WPF lors du traitement de XAML 2009 pour le chargement ajoute également cette fonctionnalité pour le comportement de conversion de type implicite pour certaines propriétés d’infrastructure qui utilisent le type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="6b3c2-149">Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour XAML libre (XAML pas compilé par balisage).</span><span class="sxs-lookup"><span data-stu-id="6b3c2-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="6b3c2-150">Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="6b3c2-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3c2-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b3c2-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="6b3c2-152">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="6b3c2-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6b3c2-153">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="6b3c2-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="6b3c2-154">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="6b3c2-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
