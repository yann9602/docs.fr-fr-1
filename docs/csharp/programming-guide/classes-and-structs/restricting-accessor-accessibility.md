---
title: "Restriction d’accessibilité de l’accesseur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 347fffa4f612c5cb674a6529e46c0b1785670c95
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="6475d-102">Restriction d’accessibilité de l’accesseur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6475d-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="6475d-103">Les parties [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) d’une propriété ou d’un indexeur sont appelées *accesseurs*.</span><span class="sxs-lookup"><span data-stu-id="6475d-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="6475d-104">Par défaut, ces accesseurs ont la même visibilité, ou niveau d’accès : celle de la propriété ou de l’indexeur auquel ils appartiennent.</span><span class="sxs-lookup"><span data-stu-id="6475d-104">By default these accessors have the same visibility, or access level: that of the property or indexer to which they belong.</span></span> <span data-ttu-id="6475d-105">Pour plus d’informations, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6475d-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="6475d-106">Toutefois, il peut parfois s’avérer utile de restreindre l’accès à l’un de ces accesseurs.</span><span class="sxs-lookup"><span data-stu-id="6475d-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="6475d-107">En général, cela implique de restreindre l’accessibilité de l’accesseur `set`, tout en gardant l’accesseur `get` publiquement accessible.</span><span class="sxs-lookup"><span data-stu-id="6475d-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="6475d-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6475d-108">For example:</span></span>  
  
 <span data-ttu-id="6475d-109">[!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6475d-109">[!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]</span></span>  
  
 <span data-ttu-id="6475d-110">Dans cet exemple, une propriété appelée `Name` définit un accesseur `get` et `set`.</span><span class="sxs-lookup"><span data-stu-id="6475d-110">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="6475d-111">L’accesseur `get` reçoit le niveau d’accessibilité de la propriété elle-même, `public` dans le cas présent, alors que l’accesseur `set` est restreint explicitement par l’application du modificateur d’accès [protected](../../../csharp/language-reference/keywords/protected.md) à l’accesseur lui-même.</span><span class="sxs-lookup"><span data-stu-id="6475d-111">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="6475d-112">Restrictions sur les modificateurs d’accès sur les accesseurs</span><span class="sxs-lookup"><span data-stu-id="6475d-112">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="6475d-113">L’utilisation de modificateurs d’accesseurs sur les propriétés ou les indexeurs est soumise aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="6475d-113">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="6475d-114">Vous ne pouvez pas utiliser de modificateurs d’accesseur sur une interface ou sur une implémentation de membre d’[interface](../../../csharp/language-reference/keywords/interface.md) explicite.</span><span class="sxs-lookup"><span data-stu-id="6475d-114">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="6475d-115">Vous pouvez utiliser les modificateurs d’accesseur uniquement si la propriété ou l’indexeur dispose à la fois d’accesseurs `set` et `get`.</span><span class="sxs-lookup"><span data-stu-id="6475d-115">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="6475d-116">Dans ce cas, le modificateur est autorisé uniquement sur l’un des deux accesseurs.</span><span class="sxs-lookup"><span data-stu-id="6475d-116">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="6475d-117">Si la propriété ou l’indexeur possède un modificateur [override](../../../csharp/language-reference/keywords/override.md), le modificateur d’accesseur doit correspondre à l’accesseur de l’accesseur substitué, le cas échant.</span><span class="sxs-lookup"><span data-stu-id="6475d-117">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="6475d-118">Le niveau d’accessibilité sur l’accesseur doit être plus restrictif que le niveau d’accessibilité sur la propriété ou l’indexeur eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="6475d-118">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="6475d-119">Modificateurs d’accès sur les accesseurs de substitution</span><span class="sxs-lookup"><span data-stu-id="6475d-119">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="6475d-120">Quand vous substituez une propriété ou un indexeur, les accesseurs remplacés doivent être accessibles au code de substitution.</span><span class="sxs-lookup"><span data-stu-id="6475d-120">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="6475d-121">Par ailleurs, le niveau d’accessibilité à la fois de la propriété et de l’indexeur, ainsi que celui des accesseurs doivent correspondre à la propriété/l’indexeur et aux accesseurs substitués correspondants.</span><span class="sxs-lookup"><span data-stu-id="6475d-121">Also, the accessibility level of both the property/indexer, and that of the accessors must match the corresponding overridden property/indexer and the accessors.</span></span> <span data-ttu-id="6475d-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6475d-122">For example:</span></span>  
  
 <span data-ttu-id="6475d-123">[!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6475d-123">[!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]</span></span>  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="6475d-124">Implémentation des interfaces</span><span class="sxs-lookup"><span data-stu-id="6475d-124">Implementing Interfaces</span></span>  
 <span data-ttu-id="6475d-125">Quand vous utilisez un accesseur pour implémenter une interface, l’accesseur peut ne pas avoir de modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="6475d-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="6475d-126">Toutefois, si vous implémentez l’interface à l’aide d’un accesseur, tel que `get`, l’autre accesseur peut avoir un modificateur d’accès, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6475d-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 <span data-ttu-id="6475d-127">[!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6475d-127">[!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]</span></span>  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="6475d-128">Domaine d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="6475d-128">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="6475d-129">Si vous utilisez un modificateur d’accès sur l’accesseur, le [domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) de l’accesseur est déterminé par ce modificateur.</span><span class="sxs-lookup"><span data-stu-id="6475d-129">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="6475d-130">Si vous n’avez pas utilisé un modificateur d’accès sur l’accesseur, le domaine d’accessibilité de l’accesseur est déterminé par le niveau d’accessibilité de la propriété ou de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="6475d-130">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6475d-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="6475d-131">Example</span></span>  
 <span data-ttu-id="6475d-132">L’exemple suivant contient trois classes, `BaseClass`, `DerivedClass` et `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="6475d-132">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="6475d-133">Il y a deux propriétés sur `BaseClass`, `Name` et `Id` sur les deux classes.</span><span class="sxs-lookup"><span data-stu-id="6475d-133">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="6475d-134">L’exemple montre comment la propriété `Id` sur `DerivedClass` peut être masquée par la propriété `Id` sur `BaseClass` quand vous utilisez un modificateur d’accès restrictif tel que [protected](../../../csharp/language-reference/keywords/protected.md) ou [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="6475d-134">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="6475d-135">Par conséquent, quand vous affectez des valeurs à cette propriété, la propriété sur la classe `BaseClass` est appelée à la place.</span><span class="sxs-lookup"><span data-stu-id="6475d-135">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="6475d-136">Le remplacement du modificateur d’accès par [public](../../../csharp/language-reference/keywords/public.md) rend la propriété accessible.</span><span class="sxs-lookup"><span data-stu-id="6475d-136">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="6475d-137">L’exemple montre également qu’un modificateur d’accès restrictif, tel que `private` ou `protected`, sur l’accesseur `set` de la propriété `Name` dans `DerivedClass` empêche l’accès à l’accesseur et génère une erreur quand vous lui affectez une valeur.</span><span class="sxs-lookup"><span data-stu-id="6475d-137">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 <span data-ttu-id="6475d-138">[!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6475d-138">[!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="6475d-139">Commentaires</span><span class="sxs-lookup"><span data-stu-id="6475d-139">Comments</span></span>  
 <span data-ttu-id="6475d-140">Notez que si vous remplacez la déclaration `new private string Id` par `new public string Id`, vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6475d-140">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="6475d-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6475d-141">See Also</span></span>  
 <span data-ttu-id="6475d-142">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6475d-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6475d-143">[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="6475d-143">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="6475d-144">[Indexeurs](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="6475d-144">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="6475d-145">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="6475d-145">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)

