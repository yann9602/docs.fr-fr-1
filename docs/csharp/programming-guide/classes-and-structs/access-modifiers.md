---
title: "Modificateurs d’accès (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
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
ms.openlocfilehash: 38b259b4d85d54467cd15cd49e5987f6198e8d99
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="63692-102">Modificateurs d’accès (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="63692-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="63692-103">Tous les types et membres de type ont un niveau d’accessibilité, qui détermine s’ils peuvent être utilisés à partir d’un autre code de votre assembly ou d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="63692-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="63692-104">Utilisez les modificateurs d’accès suivants pour spécifier l’accessibilité d’un type ou d’un membre au moment où vous le déclarez :</span><span class="sxs-lookup"><span data-stu-id="63692-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="63692-105">public</span><span class="sxs-lookup"><span data-stu-id="63692-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 <span data-ttu-id="63692-106">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="63692-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>  
  
 [<span data-ttu-id="63692-107">private</span><span class="sxs-lookup"><span data-stu-id="63692-107">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 <span data-ttu-id="63692-108">Seul du code de la même classe ou du même struct peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="63692-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="63692-109">protected</span><span class="sxs-lookup"><span data-stu-id="63692-109">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 <span data-ttu-id="63692-110">Seul du code de la même classe ou du même struct, ou du code d’une classe dérivée de cette classe, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="63692-110">The type or member can be accessed only by code in the same class or struct, or in a class that is derived from that class.</span></span>  
  
 [<span data-ttu-id="63692-111">internal</span><span class="sxs-lookup"><span data-stu-id="63692-111">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="63692-112">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="63692-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 `protected internal`  
 <span data-ttu-id="63692-113">Tout code de l’assembly dans lequel le type ou le membre est déclaré, ou d’une classe dérivée dans un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="63692-113">The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> <span data-ttu-id="63692-114">L’accès à partir d’un autre assembly doit s’effectuer dans une déclaration de classe qui dérive de la classe dans laquelle l’élément protected internal est déclaré, et cet accès doit se faire par le biais d’une instance du type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="63692-114">Access from another assembly must take place within a class declaration that derives from the class in which the protected internal element is declared, and it must take place through an instance of the derived class type.</span></span>  
  
 <span data-ttu-id="63692-115">Les exemples suivants montrent comment spécifier des modificateurs d’accès sur un type et un membre :</span><span class="sxs-lookup"><span data-stu-id="63692-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 <span data-ttu-id="63692-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="63692-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span></span>  
  
 <span data-ttu-id="63692-117">Les modificateurs d’accès ne peuvent pas tous être utilisés par tous les types ou membres dans tous les contextes. De plus, dans certains cas, l’accessibilité d’un membre de type est limitée par l’accessibilité de son type conteneur.</span><span class="sxs-lookup"><span data-stu-id="63692-117">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="63692-118">Les sections suivantes fournissent plus de détails sur l’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="63692-118">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="63692-119">Accessibilité des classes et des structs</span><span class="sxs-lookup"><span data-stu-id="63692-119">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="63692-120">Les classes et les structs qui sont déclarés directement dans un espace de noms (autrement dit, qui ne sont pas imbriqués dans d’autres classes ou structs) peuvent être déclarés comme public ou internal.</span><span class="sxs-lookup"><span data-stu-id="63692-120">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="63692-121">Le niveau d’accès par défaut est internal si aucun modificateur d’accès n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="63692-121">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="63692-122">Les membres de struct, y compris les classes et structs imbriqués, peuvent être déclarés comme public, internal ou private.</span><span class="sxs-lookup"><span data-stu-id="63692-122">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="63692-123">Les membres de classe, y compris les classes et structs imbriqués, peuvent être public, protected internal, protected, internal ou private.</span><span class="sxs-lookup"><span data-stu-id="63692-123">Class members, including nested classes and structs, can be public, protected internal, protected, internal, or private.</span></span> <span data-ttu-id="63692-124">Le niveau d’accès pour les membres de classe et de struct, y compris les classes et structs imbriqués, est private par défaut.</span><span class="sxs-lookup"><span data-stu-id="63692-124">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="63692-125">L’accès aux types imbriqués private n’est pas possible hors du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="63692-125">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="63692-126">Les classes dérivées ne peuvent pas avoir une accessibilité supérieure à celle de leurs types de base.</span><span class="sxs-lookup"><span data-stu-id="63692-126">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="63692-127">Vous ne pouvez donc pas avoir une classe public `B` qui dérive d’une classe internal `A`.</span><span class="sxs-lookup"><span data-stu-id="63692-127">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="63692-128">Si cela était autorisé, cela aurait pour effet de rendre `A` public, car tous les membres protected ou internal de `A` seraient accessibles à partir de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="63692-128">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="63692-129">Vous pouvez utiliser InternalsVisibleToAttribute pour autoriser d’autres assemblys spécifiques à accéder à vos types internal.</span><span class="sxs-lookup"><span data-stu-id="63692-129">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="63692-130">Pour plus d’informations, consultez [Assemblys friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="63692-130">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="63692-131">Accessibilité des membres de classe et de struct</span><span class="sxs-lookup"><span data-stu-id="63692-131">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="63692-132">Les membres de classe (y compris les classes et structs imbriqués) peuvent être déclarés avec l’un des cinq types d’accès.</span><span class="sxs-lookup"><span data-stu-id="63692-132">Class members (including nested classes and structs) can be declared with any of the five types of access.</span></span> <span data-ttu-id="63692-133">Les membres de struct ne peuvent pas être déclarés comme protected, car les structs ne prennent pas en charge l’héritage.</span><span class="sxs-lookup"><span data-stu-id="63692-133">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="63692-134">Normalement, l’accessibilité d’un membre ne peut pas être supérieure à l’accessibilité du type qui le contient.</span><span class="sxs-lookup"><span data-stu-id="63692-134">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="63692-135">Toutefois, un membre public d’une classe internal est accessible hors de l’assembly si le membre implémente des méthodes d’interface ou substitue des méthodes virtuelles qui sont définies dans une classe de base public.</span><span class="sxs-lookup"><span data-stu-id="63692-135">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="63692-136">Le type d’un membre qui est un champ, une propriété ou un événement doit être au moins aussi accessible que le membre lui-même.</span><span class="sxs-lookup"><span data-stu-id="63692-136">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="63692-137">De la même façon, le type de retour et les types de paramètres d’un membre qui est une méthode, un indexeur ou un délégué doivent être au moins aussi accessibles que le membre lui-même.</span><span class="sxs-lookup"><span data-stu-id="63692-137">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="63692-138">Par exemple, vous ne pouvez pas avoir une méthode public `M` qui retourne une classe `C`, sauf si `C` est également public.</span><span class="sxs-lookup"><span data-stu-id="63692-138">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="63692-139">Vous ne pouvez pas non plus avoir une propriété protected de type `A` si `A` est déclaré comme private.</span><span class="sxs-lookup"><span data-stu-id="63692-139">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="63692-140">Les opérateurs définis par l’utilisateur doivent toujours être déclarés comme public.</span><span class="sxs-lookup"><span data-stu-id="63692-140">User-defined operators must always be declared as public.</span></span> <span data-ttu-id="63692-141">Pour plus d’informations, consultez [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="63692-141">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
 <span data-ttu-id="63692-142">Les finaliseurs ne peuvent pas avoir de modificateurs d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="63692-142">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="63692-143">Pour définir le niveau d’accès pour un membre de classe ou de struct, ajoutez le mot clé approprié à la déclaration du membre, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="63692-143">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="63692-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="63692-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63692-145">Le niveau d’accessibilité protected internal signifie protected OU internal, et non protected ET internal.</span><span class="sxs-lookup"><span data-stu-id="63692-145">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="63692-146">Cela signifie qu’un membre protected internal est accessible à partir de n’importe quelle classe dans le même assembly, y compris des classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="63692-146">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="63692-147">Pour limiter l’accessibilité uniquement aux classes dérivées du même assembly, déclarez la classe de base comme internal et ses membres comme protected.</span><span class="sxs-lookup"><span data-stu-id="63692-147">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="63692-148">Autres types</span><span class="sxs-lookup"><span data-stu-id="63692-148">Other Types</span></span>  
 <span data-ttu-id="63692-149">Les interfaces qui sont déclarées directement dans un espace de noms peuvent être déclarées comme public ou internal et, comme les classes et les structs, les interfaces ont le niveau d’accès internal par défaut.</span><span class="sxs-lookup"><span data-stu-id="63692-149">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="63692-150">Les membres d’interface sont toujours public, car une interface est censée permettre à d’autres types d’accéder à une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="63692-150">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="63692-151">Il n’est pas possible d’appliquer des modificateurs d’accès aux membres d’interface.</span><span class="sxs-lookup"><span data-stu-id="63692-151">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="63692-152">Les membres d’énumération sont toujours public, et aucun modificateur d’accès ne peut leur être appliqué.</span><span class="sxs-lookup"><span data-stu-id="63692-152">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="63692-153">Les délégués se comportent comme des classes et des structs.</span><span class="sxs-lookup"><span data-stu-id="63692-153">Delegates behave like classes and structs.</span></span> <span data-ttu-id="63692-154">Par défaut, ils ont un accès internal quand ils sont déclarés directement dans un espace de noms, et un accès private quand ils sont imbriqués.</span><span class="sxs-lookup"><span data-stu-id="63692-154">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="63692-155">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="63692-155">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63692-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63692-156">See Also</span></span>  
 <span data-ttu-id="63692-157">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="63692-157">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="63692-158">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="63692-158">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="63692-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="63692-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="63692-160">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="63692-160">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="63692-161">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="63692-161">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="63692-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="63692-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="63692-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="63692-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 <span data-ttu-id="63692-164">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="63692-164">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="63692-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="63692-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="63692-166">interface</span><span class="sxs-lookup"><span data-stu-id="63692-166">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

