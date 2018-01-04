---
title: x:Arguments, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb1f5986a0d9f9eb69ade0228925ec06164cee4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xarguments-directive"></a><span data-ttu-id="d7906-102">x:Arguments, directive</span><span class="sxs-lookup"><span data-stu-id="d7906-102">x:Arguments Directive</span></span>
<span data-ttu-id="d7906-103">Arguments de construction de packages pour une déclaration d’élément objet constructeur personnalisé en XAML, ou pour une déclaration d’objet de fabrique (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7906-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="d7906-104">Utilisation des éléments XAML (constructeur non défini par défaut)</span><span class="sxs-lookup"><span data-stu-id="d7906-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="d7906-105">Utilisation des éléments XAML (méthode de fabrique)</span><span class="sxs-lookup"><span data-stu-id="d7906-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d7906-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="d7906-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="d7906-107">Un ou plusieurs éléments objet qui spécifient les arguments à passer à la méthode de constructeur ou de la fabrique par défaut de stockage.</span><span class="sxs-lookup"><span data-stu-id="d7906-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="d7906-108">Utilisation typique consiste à utiliser le texte d’initialisation dans les éléments de l’objet pour spécifier les valeurs de l’argument réel.</span><span class="sxs-lookup"><span data-stu-id="d7906-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="d7906-109">Consultez la section Exemples.</span><span class="sxs-lookup"><span data-stu-id="d7906-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="d7906-110">L’ordre des éléments est significatif.</span><span class="sxs-lookup"><span data-stu-id="d7906-110">The order of the elements is significant.</span></span> <span data-ttu-id="d7906-111">Les types XAML dans l’ordre doivent correspondent aux types et ordre de type de la surcharge de méthode de constructeur ou de la fabrique de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="d7906-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="d7906-112">Le nom de la méthode de fabrique qui doit traiter tous `x:Arguments` arguments.</span><span class="sxs-lookup"><span data-stu-id="d7906-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="d7906-113">Dépendances</span><span class="sxs-lookup"><span data-stu-id="d7906-113">Dependencies</span></span>  
 <span data-ttu-id="d7906-114">`x:FactoryMethod`peut modifier l’étendue et le comportement où `x:Arguments` s’applique.</span><span class="sxs-lookup"><span data-stu-id="d7906-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="d7906-115">Si aucun `x:FactoryMethod` est spécifié, `x:Arguments` s’applique pour alterner des signatures des constructeurs de sauvegarde (et non par défaut).</span><span class="sxs-lookup"><span data-stu-id="d7906-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="d7906-116">Si `x:FactoryMethod` est spécifié, `x:Arguments` s’applique à une surcharge de la méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="d7906-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7906-117">Notes</span><span class="sxs-lookup"><span data-stu-id="d7906-117">Remarks</span></span>  
 <span data-ttu-id="d7906-118">XAML 2006 peut prendre en charge l’initialisation par défaut dans le texte de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="d7906-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="d7906-119">Toutefois, l’application pratique d’une technique de construction de texte d’initialisation est limitée.</span><span class="sxs-lookup"><span data-stu-id="d7906-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="d7906-120">Texte d’initialisation est traité comme une chaîne de texte unique ; Par conséquent, il ajoute uniquement la fonctionnalité pour l’initialisation d’un paramètre unique, sauf si un convertisseur de type est défini pour le comportement de construction qui peut analyser des éléments personnalisés des informations et les délimiteurs personnalisés à partir de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d7906-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="d7906-121">En outre, la chaîne de texte à la logique de l’objet est potentiellement convertisseur de type natif par défaut d’un analyseur XAML donnée pour la gestion des primitives de chaîne true.</span><span class="sxs-lookup"><span data-stu-id="d7906-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="d7906-122">Le `x:Arguments` l’utilisation de XAML n’est pas utilisation des éléments de propriété dans le sens classique, étant donné que le balisage de la directive ne référence pas de type de l’élément objet contenant.</span><span class="sxs-lookup"><span data-stu-id="d7906-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="d7906-123">Il est plus apparenté à d’autres directives telles que `x:Code` où l’élément dénote une plage dans laquelle la balise doit être interprétée comme autre que la valeur par défaut pour le contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="d7906-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="d7906-124">Dans ce cas, le type de chaque élément d’objet XAML communique des informations sur les types d’arguments, qui sont utilisées par les analyseurs XAML pour déterminer la signature de méthode de fabrique constructeur spécifique un `x:Arguments` tente de référencer l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d7906-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="d7906-125">`x:Arguments`un élément de l’objet en cours de construction doit précéder toutes les autres éléments de propriété, le contenu, texte interne ou des chaînes d’initialisation de l’élément objet.</span><span class="sxs-lookup"><span data-stu-id="d7906-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="d7906-126">Les éléments de l’objet au sein de `x:Arguments` peut inclure des attributs et des chaînes d’initialisation, comme autorisé par ce type XAML et sa méthode de constructeur ou de la fabrique de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="d7906-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="d7906-127">Pour l’objet ou les arguments, vous pouvez spécifier les types XAML personnalisés ou les types XAML qui sont sinon en dehors de l’espace de noms XAML par défaut en référençant les mappages de préfixe établis.</span><span class="sxs-lookup"><span data-stu-id="d7906-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="d7906-128">Processeurs XAML utilisent les instructions suivantes pour déterminer la façon dont les arguments spécifiés dans `x:Arguments` doit être utilisé pour construire un objet.</span><span class="sxs-lookup"><span data-stu-id="d7906-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="d7906-129">Si `x:FactoryMethod` est spécifié, les informations sont comparées à l’objet `x:FactoryMethod` (Notez que la valeur de `x:FactoryMethod` est le nom de méthode et la méthode nommée ont des surcharges.</span><span class="sxs-lookup"><span data-stu-id="d7906-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="d7906-130">Si `x:FactoryMethod` n’est pas spécifié, les informations sont comparées à l’ensemble de toutes les surcharges de constructeur public de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d7906-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="d7906-131">Logique de traitement XAML puis compare le nombre de paramètres et sélectionne la surcharge avec l’arité correspondante.</span><span class="sxs-lookup"><span data-stu-id="d7906-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="d7906-132">S’il existe plusieurs correspondances, le processeur XAML doit comparer les types des paramètres basés sur les types XAML d’éléments de l’objet fourni.</span><span class="sxs-lookup"><span data-stu-id="d7906-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="d7906-133">Si plus d’une correspondance est trouvée, le comportement du processeur XAML est indéfini.</span><span class="sxs-lookup"><span data-stu-id="d7906-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="d7906-134">Si un `x:FactoryMethod` est spécifié, mais la méthode ne peut pas être résolue, un processeur XAML doit lever une exception.</span><span class="sxs-lookup"><span data-stu-id="d7906-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="d7906-135">Une utilisation d’attributs XAML `<x:Arguments>string</x:Arguments>` est techniquement possible.</span><span class="sxs-lookup"><span data-stu-id="d7906-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="d7906-136">Toutefois, cela ne fournit aucun fonctionnalités au-delà de ce qui peut être fait sinon via des convertisseurs de texte et le type de l’initialisation, et à l’aide de cette syntaxe n’est pas l’intention de la conception des fonctionnalités de méthode de fabrique XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="d7906-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d7906-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="d7906-137">Examples</span></span>  
 <span data-ttu-id="d7906-138">L’exemple suivant montre un constructeur par défaut de signature, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.</span><span class="sxs-lookup"><span data-stu-id="d7906-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 <span data-ttu-id="d7906-139">L’exemple suivant montre une signature de méthode de fabrique cible, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.</span><span class="sxs-lookup"><span data-stu-id="d7906-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7906-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7906-140">See Also</span></span>  
 [<span data-ttu-id="d7906-141">Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7906-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="d7906-142">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d7906-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
