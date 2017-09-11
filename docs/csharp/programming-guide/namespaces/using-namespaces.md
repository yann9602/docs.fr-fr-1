---
title: Utilisation d'espaces de noms (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.names
dev_langs:
- CSharp
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
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
ms.openlocfilehash: 61b5d78f1c4924e3858c14876d36e52d4ee46ceb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="83d7e-102">Utilisation d'espaces de noms (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="83d7e-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="83d7e-103">Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes.</span><span class="sxs-lookup"><span data-stu-id="83d7e-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="83d7e-104">En premier lieu, les classes .NET Framework utilisent les espaces de noms à des fins d’organisation.</span><span class="sxs-lookup"><span data-stu-id="83d7e-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="83d7e-105">En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.</span><span class="sxs-lookup"><span data-stu-id="83d7e-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="83d7e-106">Accès aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="83d7e-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="83d7e-107">La plupart des applications C# commencent par une section de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="83d7e-108">Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.</span><span class="sxs-lookup"><span data-stu-id="83d7e-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="83d7e-109">Par exemple, en incluant la ligne :</span><span class="sxs-lookup"><span data-stu-id="83d7e-109">For example, by including the line:</span></span>  
  
 <span data-ttu-id="83d7e-110">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-110">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-111">Au début d’un programme, le programmeur peut utiliser le code :</span><span class="sxs-lookup"><span data-stu-id="83d7e-111">At the start of a program, the programmer can use the code:</span></span>  
  
 <span data-ttu-id="83d7e-112">[!code-cs[csProgGuide #31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-112">[!code-cs[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-113">À la place de :</span><span class="sxs-lookup"><span data-stu-id="83d7e-113">Instead of:</span></span>  
  
 <span data-ttu-id="83d7e-114">[!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-114">[!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]</span></span>  
  
## <a name="namespace-aliases"></a><span data-ttu-id="83d7e-115">Alias d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="83d7e-115">Namespace Aliases</span></span>  
 <span data-ttu-id="83d7e-116">La [directive using](../../../csharp/language-reference/keywords/using-directive.md) peut aussi servir à créer un alias pour un [espace de noms](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="83d7e-116">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="83d7e-117">Par exemple, si vous utilisez un espace de noms écrit précédemment qui contient des espaces de noms imbriqués, vous pouvez déclarer un alias pour offrir un moyen rapide d’en référencer un en particulier, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="83d7e-117">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 <span data-ttu-id="83d7e-118">[!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-118">[!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]</span></span>  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="83d7e-119">Utilisation d’espaces de noms pour contrôler la portée</span><span class="sxs-lookup"><span data-stu-id="83d7e-119">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="83d7e-120">Le mot clé `namespace` est utilisé pour déclarer une portée.</span><span class="sxs-lookup"><span data-stu-id="83d7e-120">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="83d7e-121">La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques.</span><span class="sxs-lookup"><span data-stu-id="83d7e-121">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="83d7e-122">Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre.</span><span class="sxs-lookup"><span data-stu-id="83d7e-122">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="83d7e-123">L’[opérateur .](../../../csharp/language-reference/operators/member-access-operator.md) est utilisé pour différencier la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="83d7e-123">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 <span data-ttu-id="83d7e-124">[!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-124">[!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="83d7e-125">Noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="83d7e-125">Fully Qualified Names</span></span>  
 <span data-ttu-id="83d7e-126">Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique.</span><span class="sxs-lookup"><span data-stu-id="83d7e-126">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="83d7e-127">Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.</span><span class="sxs-lookup"><span data-stu-id="83d7e-127">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="83d7e-128">Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="83d7e-128">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="83d7e-129">Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.</span><span class="sxs-lookup"><span data-stu-id="83d7e-129">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 <span data-ttu-id="83d7e-130">[!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-130">[!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-131">Dans le segment de code précédent :</span><span class="sxs-lookup"><span data-stu-id="83d7e-131">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="83d7e-132">L’espace de noms `N1` est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="83d7e-132">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="83d7e-133">Son nom qualifié complet est `N1`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-133">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="83d7e-134">L’espace de noms `N2` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-134">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="83d7e-135">Son nom qualifié complet est `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-135">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="83d7e-136">La classe `C1` est un membre de `N1`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-136">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="83d7e-137">Son nom qualifié complet est `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-137">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="83d7e-138">Le nom de classe `C2` est utilisé deux fois dans ce code.</span><span class="sxs-lookup"><span data-stu-id="83d7e-138">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="83d7e-139">En revanche, les noms qualifiés complets sont uniques.</span><span class="sxs-lookup"><span data-stu-id="83d7e-139">However, the fully qualified names are unique.</span></span> <span data-ttu-id="83d7e-140">La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-140">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="83d7e-141">La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-141">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="83d7e-142">À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="83d7e-142">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 <span data-ttu-id="83d7e-143">[!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-143">[!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-144">En règle générale, utilisez `::` pour faire référence à un alias d’espace de noms ou `global::` pour faire référence à l’espace de noms global et `.` pour qualifier les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="83d7e-144">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="83d7e-145">C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="83d7e-145">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="83d7e-146">Exemple :</span><span class="sxs-lookup"><span data-stu-id="83d7e-146">For example:</span></span>  
  
 <span data-ttu-id="83d7e-147">[!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-147">[!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-148">[!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-148">[!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-149">Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière.</span><span class="sxs-lookup"><span data-stu-id="83d7e-149">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="83d7e-150">Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-150">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="83d7e-151">L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias.</span><span class="sxs-lookup"><span data-stu-id="83d7e-151">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="83d7e-152">Par exemple, la ligne suivante génère l’avertissement :</span><span class="sxs-lookup"><span data-stu-id="83d7e-152">For example, the following line generates the warning:</span></span>  
  
 <span data-ttu-id="83d7e-153">[!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-153">[!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-154">Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="83d7e-154">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="83d7e-155">Par exemple, prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="83d7e-155">For example, consider this example:</span></span>  
  
 <span data-ttu-id="83d7e-156">[!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-156">[!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-157">[!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]</span><span class="sxs-lookup"><span data-stu-id="83d7e-157">[!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]</span></span>  
  
 <span data-ttu-id="83d7e-158">Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type.</span><span class="sxs-lookup"><span data-stu-id="83d7e-158">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="83d7e-159">L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.</span><span class="sxs-lookup"><span data-stu-id="83d7e-159">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="83d7e-160">Consultez la rubrique [Guide pratique pour utiliser l’alias d’espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) pour plus d’informations sur l’alias `global`.</span><span class="sxs-lookup"><span data-stu-id="83d7e-160">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d7e-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d7e-161">See Also</span></span>  
 <span data-ttu-id="83d7e-162">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="83d7e-162">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="83d7e-163">[Espaces de noms](../../../csharp/programming-guide/namespaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="83d7e-163">[Namespaces](../../../csharp/programming-guide/namespaces/index.md) </span></span>  
 <span data-ttu-id="83d7e-164">[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="83d7e-164">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="83d7e-165">[. , opérateur](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="83d7e-165">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 <span data-ttu-id="83d7e-166">[::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="83d7e-166">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="83d7e-167">extern</span><span class="sxs-lookup"><span data-stu-id="83d7e-167">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)

