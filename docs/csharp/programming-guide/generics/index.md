---
title: "Génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
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
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="3e8c8-102">Génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3e8c8-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="3e8c8-103">Les génériques ont été ajoutés à la version 2.0 du langage C# et du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3e8c8-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="3e8c8-104">Les génériques introduisent le concept des paramètres de type dans .NET Framework, qui permettent de concevoir des classes et des méthodes qui diffèrent la spécification d’un ou de plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instanciée par le code client.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="3e8c8-105">Par exemple, à l’aide d’un paramètre de type générique T, vous pouvez écrire une seule classe qui peut être utilisée par un autre code client sans impliquer le coût ou le risque des casts ou des opérations de boxing à l’exécution, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="3e8c8-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 <span data-ttu-id="3e8c8-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3e8c8-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="generics-overview"></a><span data-ttu-id="3e8c8-107">Vue d’ensemble des génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-107">Generics Overview</span></span>  
  
-   <span data-ttu-id="3e8c8-108">Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-108">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="3e8c8-109">L’utilisation la plus courante des génériques est de créer des classes de collection.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-109">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="3e8c8-110">La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-110">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="3e8c8-111">Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-111">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="3e8c8-112">Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-112">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="3e8c8-113">Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-113">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="3e8c8-114">Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3e8c8-114">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e8c8-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3e8c8-115">Related Sections</span></span>  
 <span data-ttu-id="3e8c8-116">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="3e8c8-116">For more information:</span></span>  
  
-   [<span data-ttu-id="3e8c8-117">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="3e8c8-118">Avantages des génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-118">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="3e8c8-119">Paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="3e8c8-119">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="3e8c8-120">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="3e8c8-120">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="3e8c8-121">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-121">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="3e8c8-122">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-122">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="3e8c8-123">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-123">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="3e8c8-124">Délégués génériques</span><span class="sxs-lookup"><span data-stu-id="3e8c8-124">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="3e8c8-125">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="3e8c8-125">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="3e8c8-126">Génériques et réflexion</span><span class="sxs-lookup"><span data-stu-id="3e8c8-126">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="3e8c8-127">Génériques dans le runtime</span><span class="sxs-lookup"><span data-stu-id="3e8c8-127">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="3e8c8-128">Génériques dans la bibliothèque de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e8c8-128">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3e8c8-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3e8c8-129">C# Language Specification</span></span>  
 <span data-ttu-id="3e8c8-130">Pour plus d'informations, voir la [spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e8c8-130">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8c8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e8c8-131">See Also</span></span>  
 <span data-ttu-id="3e8c8-132"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="3e8c8-132"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="3e8c8-133">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e8c8-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3e8c8-134">[Types](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e8c8-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="3e8c8-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span><span class="sxs-lookup"><span data-stu-id="3e8c8-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span></span>  
 [<span data-ttu-id="3e8c8-136">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="3e8c8-136">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

