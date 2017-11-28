---
title: "interface (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: interface_CSharpKeyword
helpviewer_keywords: interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a><span data-ttu-id="089f1-102">interface (référence C#)</span><span class="sxs-lookup"><span data-stu-id="089f1-102">interface (C# Reference)</span></span>
<span data-ttu-id="089f1-103">Une interface contient uniquement des signatures de [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), de [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), d’[événements](../../../csharp/programming-guide/events/index.md) ou d’[indexeurs](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="089f1-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="089f1-104">Une classe ou un struct qui implémente l’interface doit implémenter les membres de l’interface qui sont spécifiés dans la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="089f1-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="089f1-105">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="089f1-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="089f1-106">Pour plus d’informations et d’exemples, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="089f1-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="089f1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="089f1-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="089f1-108">Une interface peut être membre d’un espace de noms ou d’une classe, et peut contenir les signatures des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="089f1-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="089f1-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="089f1-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="089f1-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="089f1-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="089f1-111">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="089f1-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="089f1-112">Événements</span><span class="sxs-lookup"><span data-stu-id="089f1-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="089f1-113">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="089f1-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="089f1-114">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="089f1-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="089f1-115">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="089f1-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="089f1-116">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="089f1-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="089f1-117">Pour plus d’informations et plus d’exemples sur l’implémentation explicite des interfaces, consultez [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="089f1-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="089f1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="089f1-118">Example</span></span>  
 <span data-ttu-id="089f1-119">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="089f1-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="089f1-120">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="089f1-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="089f1-121">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="089f1-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="089f1-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="089f1-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="089f1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="089f1-123">See Also</span></span>  
 [<span data-ttu-id="089f1-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="089f1-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="089f1-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="089f1-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="089f1-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="089f1-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="089f1-127">Types référence</span><span class="sxs-lookup"><span data-stu-id="089f1-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="089f1-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="089f1-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="089f1-129">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="089f1-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="089f1-130">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="089f1-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="089f1-131">class</span><span class="sxs-lookup"><span data-stu-id="089f1-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="089f1-132">struct</span><span class="sxs-lookup"><span data-stu-id="089f1-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="089f1-133">Interfaces</span><span class="sxs-lookup"><span data-stu-id="089f1-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
