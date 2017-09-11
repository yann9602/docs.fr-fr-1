---
title: "Classes et méthodes partielles (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 35
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
ms.openlocfilehash: 41b07af83faa6af23695f3719aae29183c35a417
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="89779-102">Classes et méthodes partielles (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="89779-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="89779-103">Il est possible de fractionner la définition d’une [classe](../../../csharp/language-reference/keywords/class.md), d’un [struct](../../../csharp/language-reference/keywords/struct.md), d’une [interface](../../../csharp/language-reference/keywords/interface.md) ou d’une méthode entre deux fichiers sources ou plus.</span><span class="sxs-lookup"><span data-stu-id="89779-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="89779-104">Chaque fichier source contient une section de la définition de méthode ou de type, et toutes les parties sont combinées au moment où l’application est compilée.</span><span class="sxs-lookup"><span data-stu-id="89779-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="89779-105">Classes partielles</span><span class="sxs-lookup"><span data-stu-id="89779-105">Partial Classes</span></span>  
 <span data-ttu-id="89779-106">Il peut être utile de fractionner une définition de classe dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="89779-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="89779-107">Dans des projets volumineux, le fractionnement d’une classe entre plusieurs fichiers distincts permet à plusieurs programmeurs d’y travailler simultanément.</span><span class="sxs-lookup"><span data-stu-id="89779-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="89779-108">Quand vous utilisez une source générée automatiquement, vous pouvez ajouter du code à la classe sans avoir à recréer le fichier source.</span><span class="sxs-lookup"><span data-stu-id="89779-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="89779-109">Visual Studio suit cette approche pour créer des formulaires Windows Forms, du code wrapper de service web, etc.</span><span class="sxs-lookup"><span data-stu-id="89779-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="89779-110">Vous pouvez écrire du code qui utilise ces classes sans avoir à modifier le fichier créé par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89779-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="89779-111">Pour fractionner une définition de classe, utilisez le modificateur de mot clé [partial](../../../csharp/language-reference/keywords/partial-type.md), comme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="89779-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 <span data-ttu-id="89779-112">[!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-112">[!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="89779-113">Le mot clé `partial` indique que d’autres parties de la classe, du struct ou de l’interface peuvent être définies dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="89779-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="89779-114">Toutes les parties doivent utiliser le mot clé `partial`.</span><span class="sxs-lookup"><span data-stu-id="89779-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="89779-115">Toutes les parties doivent être disponibles à la compilation pour former le type final.</span><span class="sxs-lookup"><span data-stu-id="89779-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="89779-116">Toutes les parties doivent avoir la même accessibilité : `public`, `private`, etc.</span><span class="sxs-lookup"><span data-stu-id="89779-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="89779-117">Si une partie est déclarée comme abstract, l’ensemble du type est considéré comme abstract.</span><span class="sxs-lookup"><span data-stu-id="89779-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="89779-118">Si une partie est déclarée comme sealed, l’ensemble du type est considéré comme sealed.</span><span class="sxs-lookup"><span data-stu-id="89779-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="89779-119">Si une partie déclare un type de base, l’ensemble du type hérite de cette classe.</span><span class="sxs-lookup"><span data-stu-id="89779-119">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="89779-120">Toutes les parties qui spécifient une classe de base doivent être en accord, mais les parties qui omettent une classe de base héritent tout de même du type de base.</span><span class="sxs-lookup"><span data-stu-id="89779-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="89779-121">Les parties peuvent spécifier des interfaces de base différentes. Le type final implémente alors toutes les interfaces indiquées dans toutes les déclarations partielles.</span><span class="sxs-lookup"><span data-stu-id="89779-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="89779-122">Tous les membres de classe, de struct ou d’interface déclarés dans une définition partielle sont disponibles pour toutes les autres parties.</span><span class="sxs-lookup"><span data-stu-id="89779-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="89779-123">Le type final est la combinaison de toutes les parties au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="89779-123">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89779-124">Le modificateur `partial` n’est pas disponible sur les déclarations de délégué ou d’énumération.</span><span class="sxs-lookup"><span data-stu-id="89779-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="89779-125">L’exemple suivant montre que les types imbriqués peuvent être partiels, même si le type dans lequel ils sont imbriqués n’est pas partiel lui-même.</span><span class="sxs-lookup"><span data-stu-id="89779-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 <span data-ttu-id="89779-126">[!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-126">[!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="89779-127">Au moment de la compilation, les attributs de définitions de type partiel sont fusionnés.</span><span class="sxs-lookup"><span data-stu-id="89779-127">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="89779-128">Observez, par exemple, les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="89779-128">For example, consider the following declarations:</span></span>  
  
 <span data-ttu-id="89779-129">[!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-129">[!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]</span></span>  
  
 <span data-ttu-id="89779-130">Elles sont équivalentes aux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="89779-130">They are equivalent to the following declarations:</span></span>  
  
 <span data-ttu-id="89779-131">[!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-131">[!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="89779-132">Les éléments suivants sont fusionnés à partir de toutes les définitions de type partiel :</span><span class="sxs-lookup"><span data-stu-id="89779-132">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="89779-133">commentaires XML</span><span class="sxs-lookup"><span data-stu-id="89779-133">XML comments</span></span>  
  
-   <span data-ttu-id="89779-134">interfaces</span><span class="sxs-lookup"><span data-stu-id="89779-134">interfaces</span></span>  
  
-   <span data-ttu-id="89779-135">attributs de paramètre de type générique</span><span class="sxs-lookup"><span data-stu-id="89779-135">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="89779-136">attributs de classe</span><span class="sxs-lookup"><span data-stu-id="89779-136">class attributes</span></span>  
  
-   <span data-ttu-id="89779-137">membres</span><span class="sxs-lookup"><span data-stu-id="89779-137">members</span></span>  
  
 <span data-ttu-id="89779-138">Observez, par exemple, les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="89779-138">For example, consider the following declarations:</span></span>  
  
 <span data-ttu-id="89779-139">[!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-139">[!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]</span></span>  
  
 <span data-ttu-id="89779-140">Elles sont équivalentes aux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="89779-140">They are equivalent to the following declarations:</span></span>  
  
 <span data-ttu-id="89779-141">[!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-141">[!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]</span></span>  
  
### <a name="restrictions"></a><span data-ttu-id="89779-142">Restrictions</span><span class="sxs-lookup"><span data-stu-id="89779-142">Restrictions</span></span>  
 <span data-ttu-id="89779-143">Il y a plusieurs règles à respecter quand vous utilisez des définitions de classe partielle :</span><span class="sxs-lookup"><span data-stu-id="89779-143">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="89779-144">Toutes les définitions de type partiel conçues comme des parties du même type doivent être modifiées avec `partial`.</span><span class="sxs-lookup"><span data-stu-id="89779-144">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="89779-145">Par exemple, les déclarations de classe suivantes génèrent une erreur :</span><span class="sxs-lookup"><span data-stu-id="89779-145">For example, the following class declarations generate an error:</span></span>  
  
     <span data-ttu-id="89779-146">[!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-146">[!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]</span></span>  
  
-   <span data-ttu-id="89779-147">Le modificateur `partial` peut uniquement être placé juste avant les mots clés `class`, `struct` ou `interface`.</span><span class="sxs-lookup"><span data-stu-id="89779-147">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="89779-148">Les types partiels imbriqués sont autorisés dans les définitions de type partiel, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="89779-148">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     <span data-ttu-id="89779-149">[!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-149">[!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]</span></span>  
  
-   <span data-ttu-id="89779-150">Toutes les définitions de type partiel conçues comme des parties du même type doivent être définies dans le même assembly et dans le même module (fichier .exe ou .dll).</span><span class="sxs-lookup"><span data-stu-id="89779-150">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="89779-151">Les définitions partielles ne peuvent pas être fractionnées entre plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="89779-151">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="89779-152">Le nom de classe et les paramètres de type générique doivent correspondre dans toutes les définitions de type partiel.</span><span class="sxs-lookup"><span data-stu-id="89779-152">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="89779-153">Les types génériques peuvent être partiels.</span><span class="sxs-lookup"><span data-stu-id="89779-153">Generic types can be partial.</span></span> <span data-ttu-id="89779-154">Chaque déclaration partielle doit utiliser les mêmes noms de paramètres, dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="89779-154">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="89779-155">Les mots clés suivants sont facultatifs dans une définition de type partiel. S’ils sont utilisés dans une définition de type partiel, ils ne doivent pas être en conflit avec les mots clés spécifiés dans une autre définition partielle pour le même type :</span><span class="sxs-lookup"><span data-stu-id="89779-155">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="89779-156">public</span><span class="sxs-lookup"><span data-stu-id="89779-156">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="89779-157">private</span><span class="sxs-lookup"><span data-stu-id="89779-157">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="89779-158">protected</span><span class="sxs-lookup"><span data-stu-id="89779-158">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="89779-159">internal</span><span class="sxs-lookup"><span data-stu-id="89779-159">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="89779-160">abstract</span><span class="sxs-lookup"><span data-stu-id="89779-160">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="89779-161">sealed</span><span class="sxs-lookup"><span data-stu-id="89779-161">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="89779-162">classe de base</span><span class="sxs-lookup"><span data-stu-id="89779-162">base class</span></span>  
  
    -   <span data-ttu-id="89779-163">modificateur [new](../../../csharp/language-reference/keywords/new.md) (parties imbriquées)</span><span class="sxs-lookup"><span data-stu-id="89779-163">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="89779-164">contraintes génériques</span><span class="sxs-lookup"><span data-stu-id="89779-164">generic constraints</span></span>  
  
         <span data-ttu-id="89779-165">Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="89779-165">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="89779-166">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="89779-166">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="89779-167">Description</span><span class="sxs-lookup"><span data-stu-id="89779-167">Description</span></span>  
 <span data-ttu-id="89779-168">Dans l’exemple suivant, les champs et le constructeur de la classe `CoOrds` sont déclarés dans une définition de classe partielle, et le membre `PrintCoOrds` est déclaré dans une autre définition de classe partielle.</span><span class="sxs-lookup"><span data-stu-id="89779-168">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89779-169">Code</span><span class="sxs-lookup"><span data-stu-id="89779-169">Code</span></span>  
 <span data-ttu-id="89779-170">[!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-170">[!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="89779-171">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="89779-171">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="89779-172">Description</span><span class="sxs-lookup"><span data-stu-id="89779-172">Description</span></span>  
 <span data-ttu-id="89779-173">L’exemple suivant montre que vous pouvez également développer des interfaces et des structs partiels.</span><span class="sxs-lookup"><span data-stu-id="89779-173">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89779-174">Code</span><span class="sxs-lookup"><span data-stu-id="89779-174">Code</span></span>  
 <span data-ttu-id="89779-175">[!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="89779-175">[!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="89779-176">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="89779-176">Partial Methods</span></span>  
 <span data-ttu-id="89779-177">Une classe partielle ou un struct partiel peut contenir une méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="89779-177">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="89779-178">Une partie de la classe contient la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="89779-178">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="89779-179">Une implémentation facultative peut être définie dans la même partie ou dans une autre partie.</span><span class="sxs-lookup"><span data-stu-id="89779-179">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="89779-180">Si l’implémentation n’est pas fournie, la méthode et tous les appels à cette méthode sont supprimés au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="89779-180">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="89779-181">Les méthodes partielles permettent à l’implémenteur d’une partie d’une classe de définir une méthode, comme pour un événement.</span><span class="sxs-lookup"><span data-stu-id="89779-181">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="89779-182">L’implémenteur de l’autre partie de la classe peut décider s’il faut implémenter la méthode ou non.</span><span class="sxs-lookup"><span data-stu-id="89779-182">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="89779-183">Si la méthode n’est pas implémentée, le compilateur supprime la signature de méthode et tous les appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="89779-183">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="89779-184">Les appels à la méthode, y compris tous les résultats retournés par l’évaluation des arguments dans les appels, n’ont aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="89779-184">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="89779-185">C’est pourquoi le code dans la classe partielle peut utiliser librement une méthode partielle, même si l’implémentation n’est pas fournie.</span><span class="sxs-lookup"><span data-stu-id="89779-185">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="89779-186">Aucune erreur de compilation ou d’exécution n’est générée si la méthode est appelée, mais qu’elle n’est pas finalement implémentée.</span><span class="sxs-lookup"><span data-stu-id="89779-186">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="89779-187">Les méthodes partielles sont particulièrement utiles pour personnaliser le code généré.</span><span class="sxs-lookup"><span data-stu-id="89779-187">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="89779-188">Elles permettent de réserver un nom et une signature de méthode. Ainsi, le code généré peut appeler la méthode, mais le développeur peut décider d’implémenter ou non la méthode.</span><span class="sxs-lookup"><span data-stu-id="89779-188">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="89779-189">En grande partie comme les classes partielles, les méthodes partielles permettent d’utiliser conjointement du code créé par un générateur de code et du code créé manuellement par un développeur sans impact sur le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="89779-189">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="89779-190">Une déclaration de méthode partielle se compose de deux parties : la définition et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="89779-190">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="89779-191">Celles-ci peuvent être situées dans des parties distinctes ou dans la même partie d’une classe partielle.</span><span class="sxs-lookup"><span data-stu-id="89779-191">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="89779-192">En l’absence de déclaration d’implémentation, le compilateur optimise à la fois la déclaration de définition et tous les appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="89779-192">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="89779-193">Une déclaration de méthode partielle doit commencer par le mot clé contextuel [partial](../../../csharp/language-reference/keywords/partial-type.md), et la méthode doit retourner [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="89779-193">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="89779-194">Les méthodes partielles peuvent avoir des paramètres [ref](../../../csharp/language-reference/keywords/ref.md), mais pas [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="89779-194">Partial methods can have [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
-   <span data-ttu-id="89779-195">Les méthodes partielles sont implicitement [private](../../../csharp/language-reference/keywords/private.md) et, par conséquent, elles ne peuvent pas être [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="89779-195">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="89779-196">Les méthodes partielles ne peuvent pas être [extern](../../../csharp/language-reference/keywords/extern.md), car la présence du corps détermine si elles sont utilisées pour la définition ou pour l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="89779-196">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="89779-197">Les méthodes partielles peuvent avoir des modificateurs [static](../../../csharp/language-reference/keywords/static.md) et [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="89779-197">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="89779-198">Les méthodes partielles peuvent être génériques.</span><span class="sxs-lookup"><span data-stu-id="89779-198">Partial methods can be generic.</span></span> <span data-ttu-id="89779-199">Les contraintes sont placées sur la déclaration de méthode partielle de définition et peuvent être répétées facultativement sur la déclaration d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="89779-199">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="89779-200">Les noms de paramètre et de paramètre de type ne doivent pas obligatoirement être identiques dans la déclaration d’implémentation et la déclaration de définition.</span><span class="sxs-lookup"><span data-stu-id="89779-200">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="89779-201">Vous pouvez créer un [délégué](../../../csharp/language-reference/keywords/delegate.md) pour une méthode partielle qui a été définie et implémentée, mais pas pour une méthode partielle qui a uniquement été définie.</span><span class="sxs-lookup"><span data-stu-id="89779-201">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="89779-202">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="89779-202">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89779-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89779-203">See Also</span></span>  
 <span data-ttu-id="89779-204">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="89779-204">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="89779-205">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span><span class="sxs-lookup"><span data-stu-id="89779-205">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span></span>  
 <span data-ttu-id="89779-206">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="89779-206">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 <span data-ttu-id="89779-207">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="89779-207">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="89779-208">partial (type)</span><span class="sxs-lookup"><span data-stu-id="89779-208">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)

