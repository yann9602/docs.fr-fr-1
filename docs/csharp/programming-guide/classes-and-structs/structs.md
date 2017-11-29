---
title: Structures (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="28e7b-102">Structures (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="28e7b-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="28e7b-103">Les structs sont définis à l’aide du mot clé [struct](../../../csharp/language-reference/keywords/struct.md), par exemple :</span><span class="sxs-lookup"><span data-stu-id="28e7b-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="28e7b-104">Les structs partagent presque tous la même syntaxe que les classes, bien qu'ils soient plus limités que ces dernières :</span><span class="sxs-lookup"><span data-stu-id="28e7b-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="28e7b-105">Au sein d’une déclaration de struct, les champs ne peuvent pas être initialisés à moins d’être déclarés comme étant de type const ou static.</span><span class="sxs-lookup"><span data-stu-id="28e7b-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="28e7b-106">Un struct ne peut pas déclarer de constructeur par défaut (un constructeur sans paramètre) ni de finaliseur.</span><span class="sxs-lookup"><span data-stu-id="28e7b-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="28e7b-107">Les structs sont copiés lors de l'assignation.</span><span class="sxs-lookup"><span data-stu-id="28e7b-107">Structs are copied on assignment.</span></span> <span data-ttu-id="28e7b-108">Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine.</span><span class="sxs-lookup"><span data-stu-id="28e7b-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="28e7b-109">Il est important de s’en souvenir lors de l’utilisation de collections de types valeur comme Dictionary\<string, myStruct>.</span><span class="sxs-lookup"><span data-stu-id="28e7b-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="28e7b-110">Les structs sont des types valeur et les classes des types référence.</span><span class="sxs-lookup"><span data-stu-id="28e7b-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="28e7b-111">Contrairement aux classes, il est possible d’instancier les structs sans avoir recours à un opérateur `new`.</span><span class="sxs-lookup"><span data-stu-id="28e7b-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="28e7b-112">Les structs peuvent déclarer des constructeurs qui ont des paramètres.</span><span class="sxs-lookup"><span data-stu-id="28e7b-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="28e7b-113">Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe.</span><span class="sxs-lookup"><span data-stu-id="28e7b-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="28e7b-114">Tous les structs héritent directement de `System.ValueType`, qui hérite de `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="28e7b-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="28e7b-115">Un struct peut implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="28e7b-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="28e7b-116">Un struct peut être utilisé comme un type Nullable et peut avoir une valeur null.</span><span class="sxs-lookup"><span data-stu-id="28e7b-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="28e7b-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="28e7b-117">Related Sections</span></span>  
 <span data-ttu-id="28e7b-118">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="28e7b-118">For more information:</span></span>  
  
-   [<span data-ttu-id="28e7b-119">Utilisation de structs</span><span class="sxs-lookup"><span data-stu-id="28e7b-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="28e7b-120">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="28e7b-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="28e7b-121">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="28e7b-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="28e7b-122">Comment : différencier le passage d’un struct et le passage d’une référence de classe à une méthode</span><span class="sxs-lookup"><span data-stu-id="28e7b-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="28e7b-123">Comment : implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="28e7b-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="28e7b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28e7b-124">See Also</span></span>  
 [<span data-ttu-id="28e7b-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="28e7b-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="28e7b-126">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="28e7b-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="28e7b-127">Classes</span><span class="sxs-lookup"><span data-stu-id="28e7b-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
