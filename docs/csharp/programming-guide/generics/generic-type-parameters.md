---
title: "Paramètres de type générique (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b32db7eb6e7788167e110a91726e9dbfe19f31ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="69be5-102">Paramètres de type générique (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="69be5-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="69be5-103">Dans une définition de méthode ou un type générique, les paramètres de type représentent un espace réservé pour un type spécifique qu’un client indique quand il instancie une variable du type générique.</span><span class="sxs-lookup"><span data-stu-id="69be5-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="69be5-104">Une classe générique, telle que `GenericList<T>` répertoriée dans [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md), ne peut pas être utilisée en l’état car il ne s’agit pas vraiment d’un type, mais plutôt d’un modèle pour un type.</span><span class="sxs-lookup"><span data-stu-id="69be5-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="69be5-105">Pour utiliser `GenericList<T>`, le code client doit déclarer et instancier un type construit en spécifiant un argument de type à l’intérieur de crochets pointus.</span><span class="sxs-lookup"><span data-stu-id="69be5-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="69be5-106">L’argument de type pour cette classe particulière peut être tout type reconnu par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="69be5-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="69be5-107">Il est possible de créer un nombre quelconque d’instances de type construit, chacune avec un argument de type différent, comme suit :</span><span class="sxs-lookup"><span data-stu-id="69be5-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="69be5-108">Dans chacune de ces instances de `GenericList<T>`, chaque occurrence de `T` dans la classe sera substituée au moment de l’exécution avec l’argument de type.</span><span class="sxs-lookup"><span data-stu-id="69be5-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="69be5-109">Par cette substitution, nous avons créé trois objets distincts de type sécurisé et efficaces à l’aide d’une seule définition de classe.</span><span class="sxs-lookup"><span data-stu-id="69be5-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="69be5-110">Pour plus d’informations sur la façon dont cette substitution est exécutée par le CLR, consultez [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="69be5-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="69be5-111">Indications concernant l’attribution d’un nom aux paramètres de type</span><span class="sxs-lookup"><span data-stu-id="69be5-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="69be5-112">**Nommez** les paramètres de type générique avec des noms descriptifs, sauf si un nom composé d’une seule lettre est suffisamment évocateur et qu’un nom descriptif n’apporte rien de plus.</span><span class="sxs-lookup"><span data-stu-id="69be5-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="69be5-113">**Envisagez** l’utilisation de T comme nom de paramètre de type pour les types ayant un paramètre de type d’une seule lettre.</span><span class="sxs-lookup"><span data-stu-id="69be5-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="69be5-114">**Préfixez** les noms des paramètres de type descriptifs avec « T ».</span><span class="sxs-lookup"><span data-stu-id="69be5-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="69be5-115">**Pensez** à indiquer les contraintes placées sur un paramètre de type dans le nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="69be5-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="69be5-116">Par exemple, un paramètre limité à `ISession` peut être appelé `TSession`.</span><span class="sxs-lookup"><span data-stu-id="69be5-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69be5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69be5-117">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="69be5-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="69be5-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="69be5-119">Génériques</span><span class="sxs-lookup"><span data-stu-id="69be5-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="69be5-120">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="69be5-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
