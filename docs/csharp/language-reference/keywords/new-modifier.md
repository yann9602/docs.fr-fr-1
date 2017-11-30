---
title: "new, modificateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28124c2f3ecef01fd4bc43fe7cfc975dd6466506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="a27b2-102">new, modificateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a27b2-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="a27b2-103">En cas d'utilisation comme un modificateur de déclaration, le mot clé `new` masque explicitement un membre qui est hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="a27b2-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="a27b2-104">Lorsque vous masquez un membre hérité, la version dérivée du membre remplace la version de classe de base.</span><span class="sxs-lookup"><span data-stu-id="a27b2-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="a27b2-105">Bien que vous puissiez masquer des membres sans utiliser le modificateur `new`, vous obtenez un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a27b2-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="a27b2-106">Si vous utilisez `new` pour masquer explicitement un membre, il supprime cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="a27b2-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="a27b2-107">Pour masquer un membre hérité, déclarez-le dans la classe dérivée en utilisant le même nom de membre, puis modifiez-le à l'aide du mot-clé `new`.</span><span class="sxs-lookup"><span data-stu-id="a27b2-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="a27b2-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a27b2-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="a27b2-109">Dans cet exemple, `BaseC.Invoke` est masqué par `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="a27b2-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="a27b2-110">Le champ `x` n'est pas affecté parce qu'il n'est pas masqué par un nom semblable.</span><span class="sxs-lookup"><span data-stu-id="a27b2-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="a27b2-111">Le masquage de noms par le biais de l'héritage peut prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a27b2-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="a27b2-112">En général, une constante, un champ, une propriété ou un type qui est introduit dans une classe ou une structure masque tous les membres de la classe de base qui partagent son nom.</span><span class="sxs-lookup"><span data-stu-id="a27b2-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="a27b2-113">Il existe des cas spéciaux.</span><span class="sxs-lookup"><span data-stu-id="a27b2-113">There are special cases.</span></span>  <span data-ttu-id="a27b2-114">Par exemple, si vous déclarez un nouveau champ avec le nom `N` pour avoir un type qui n'est pas invocable, et qu'un type de base déclare `N` en tant que méthode, le nouveau champ ne masquera pas la déclaration de base dans la syntaxe d'appel.</span><span class="sxs-lookup"><span data-stu-id="a27b2-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="a27b2-115">Consultez le [spécification du langage c# 5.0](http://go.microsoft.com/fwlink/?LinkId=199552) pour plus d’informations (voir la section « Recherche de membres » dans la section « Expressions »).</span><span class="sxs-lookup"><span data-stu-id="a27b2-115">See the [C# 5.0 language specification](http://go.microsoft.com/fwlink/?LinkId=199552) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="a27b2-116">Une méthode introduite dans une classe ou une structure masque les propriétés, les champs et les types qui partagent ce nom, dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a27b2-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="a27b2-117">Cela masque également toutes les méthodes de la classe de base ayant la même signature.</span><span class="sxs-lookup"><span data-stu-id="a27b2-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="a27b2-118">Un indexeur introduit dans une classe ou un struct masque tous les indexeurs de la classe de base ayant la même signature.</span><span class="sxs-lookup"><span data-stu-id="a27b2-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="a27b2-119">L’utilisation des opérateurs `new` et [override](../../../csharp/language-reference/keywords/override.md) sur le même membre est une erreur, car ces deux modificateurs ont des significations qui s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="a27b2-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="a27b2-120">Le modificateur `new` crée un nouveau membre avec le même nom et entraîne le masquage du membre d'origine.</span><span class="sxs-lookup"><span data-stu-id="a27b2-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="a27b2-121">Le modificateur `override` étend l'implémentation pour un membre hérité.</span><span class="sxs-lookup"><span data-stu-id="a27b2-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="a27b2-122">L'utilisation du modificateur `new` dans une déclaration qui ne masque pas un membre hérité génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a27b2-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a27b2-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="a27b2-123">Example</span></span>  
 <span data-ttu-id="a27b2-124">Dans cet exemple, une classe de base, `BaseC` et une classe dérivée, `DerivedC`, utilisent le même nom de champ `x`, masquant ainsi la valeur du champ hérité.</span><span class="sxs-lookup"><span data-stu-id="a27b2-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="a27b2-125">Cet exemple illustre l'utilisation du modificateur `new`.</span><span class="sxs-lookup"><span data-stu-id="a27b2-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="a27b2-126">Il montre aussi comment accéder aux membres masqués de la classe de base en utilisant leurs noms complets.</span><span class="sxs-lookup"><span data-stu-id="a27b2-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="a27b2-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="a27b2-127">Example</span></span>  
 <span data-ttu-id="a27b2-128">Dans cet exemple, une classe imbriquée masque une classe du même nom dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a27b2-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="a27b2-129">Cet exemple illustre l'utilisation du modificateur `new` pour éliminer le message d'avertissement, ainsi que l'accès aux membres de la classe masquée à l'aide de leurs noms complets.</span><span class="sxs-lookup"><span data-stu-id="a27b2-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="a27b2-130">Si vous supprimez le modificateur `new`, le programme peut encore être compilé et exécuté, mais vous obtiendrez l'avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="a27b2-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="a27b2-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a27b2-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a27b2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a27b2-132">See Also</span></span>  
 [<span data-ttu-id="a27b2-133">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a27b2-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a27b2-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a27b2-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a27b2-135">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a27b2-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a27b2-136">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="a27b2-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="a27b2-137">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="a27b2-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="a27b2-138">Versioning avec les mots clés override et new</span><span class="sxs-lookup"><span data-stu-id="a27b2-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="a27b2-139">Savoir quand utiliser les mots clés override et new</span><span class="sxs-lookup"><span data-stu-id="a27b2-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
