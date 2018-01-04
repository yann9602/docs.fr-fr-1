---
title: Choix entre classe et structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68a3d2c7335ff15706925f9a7986164e6d9c0c36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="ce559-102">Choix entre classe et structure</span><span class="sxs-lookup"><span data-stu-id="ce559-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="ce559-103">Les décisions de conception de base que fait face à chaque concepteur framework consiste à concevoir un type en tant que classe (type référence) ou en tant que struct (un type valeur).</span><span class="sxs-lookup"><span data-stu-id="ce559-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="ce559-104">Bien comprendre les différences dans le comportement des types référence et les types de valeur est vitale pour rendre ce choix.</span><span class="sxs-lookup"><span data-stu-id="ce559-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="ce559-105">La première différence entre les types référence et les types de valeur nous étudierons est que les types référence sont alloués sur le tas et le garbage collector, tandis que les types valeur sont alloués sur la pile ou inline dans les types et libérée lorsque la pile déroule ou lorsque son type conteneur obtient désallouée.</span><span class="sxs-lookup"><span data-stu-id="ce559-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="ce559-106">Par conséquent, les allocations et désallocations de types valeur sont en général moins cher que les allocations et désallocations de types référence.</span><span class="sxs-lookup"><span data-stu-id="ce559-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="ce559-107">Ensuite, les tableaux de référence sont des types allouée hors ligne, ce qui signifie que le tableau d’éléments sont simplement les références aux instances du type référence résidant sur le tas.</span><span class="sxs-lookup"><span data-stu-id="ce559-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="ce559-108">Les tableaux de types valeur sont allouées en ligne, ce qui signifie que les éléments du tableau sont les instances réelles du type valeur.</span><span class="sxs-lookup"><span data-stu-id="ce559-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="ce559-109">Par conséquent, les allocations et désallocations de tableaux de type valeur sont beaucoup moins coûteuse que les allocations et désallocations de tableaux de type référence.</span><span class="sxs-lookup"><span data-stu-id="ce559-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="ce559-110">En outre, dans la majorité des cas de tableaux de type valeur présentent bien une meilleure localité de référence.</span><span class="sxs-lookup"><span data-stu-id="ce559-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="ce559-111">La différence suivante concerne l’utilisation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="ce559-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="ce559-112">Types valeur obtient convertie (boxed) lors de la conversion vers un type référence ou d’une des interfaces qu’ils implémentent.</span><span class="sxs-lookup"><span data-stu-id="ce559-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="ce559-113">Ils obtiennent unboxed lors de la conversion vers le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="ce559-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="ce559-114">Étant donné que les zones sont des objets qui sont alloués sur le tas et sont par le garbage collector, trop boxing et unboxing peut avoir un impact négatif sur le tas, le garbage collector et, finalement, les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="ce559-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="ce559-115">En revanche, pas de boxing se produit comme types référence sont convertis.</span><span class="sxs-lookup"><span data-stu-id="ce559-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="ce559-116">Ensuite, les assignations de type référence copier la référence, alors que les assignations de type valeur copiez la valeur entière.</span><span class="sxs-lookup"><span data-stu-id="ce559-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="ce559-117">Par conséquent, des types référence volumineux sont moins cher que les affectations de types de valeur élevée.</span><span class="sxs-lookup"><span data-stu-id="ce559-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="ce559-118">Enfin, les types référence sont passés par référence, tandis que les types valeur sont passés par valeur.</span><span class="sxs-lookup"><span data-stu-id="ce559-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="ce559-119">Modifications apportées à une instance d’un type référence affectent toutes les références pointant vers l’instance.</span><span class="sxs-lookup"><span data-stu-id="ce559-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="ce559-120">Instances de type valeur sont copiés lorsqu’ils sont passés par valeur.</span><span class="sxs-lookup"><span data-stu-id="ce559-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="ce559-121">Lorsqu’une instance d’un type valeur est modifiée, elle naturellement n’affecte pas un de ses copies.</span><span class="sxs-lookup"><span data-stu-id="ce559-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="ce559-122">Étant donné que les copies ne sont pas créés explicitement par l’utilisateur, mais sont créés implicitement lorsque les arguments sont passés ou retournent les valeurs sont retournées, les types de valeur qui peuvent être modifiés peuvent être déconcertant pour de nombreux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ce559-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="ce559-123">Par conséquent, les types valeur doivent être immuables.</span><span class="sxs-lookup"><span data-stu-id="ce559-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="ce559-124">En règle générale, la plupart des types dans une infrastructure doit-elle être des classes.</span><span class="sxs-lookup"><span data-stu-id="ce559-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="ce559-125">Toutefois, il existe certaines situations dans lesquelles les caractéristiques d’un type valeur qu’il est plus approprié à utiliser les structures.</span><span class="sxs-lookup"><span data-stu-id="ce559-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="ce559-126">**✓ Envisagez** définition d’un struct au lieu d’une classe si les instances du type sont généralement de courte durée et de petite taille ou sont généralement incorporés dans d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="ce559-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="ce559-127">**X Évitez** définition d’un struct, sauf si le type possède toutes les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce559-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="ce559-128">Il représente logiquement une seule valeur, semblable aux types primitifs (`int`, `double`, etc..).</span><span class="sxs-lookup"><span data-stu-id="ce559-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="ce559-129">Il a une taille d’instance inférieure à 16 octets.</span><span class="sxs-lookup"><span data-stu-id="ce559-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="ce559-130">Il est immuable.</span><span class="sxs-lookup"><span data-stu-id="ce559-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="ce559-131">Il n’aura pas à être convertie (boxed) fréquemment.</span><span class="sxs-lookup"><span data-stu-id="ce559-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="ce559-132">Dans tous les autres cas, vous devez définir vos types en tant que classes.</span><span class="sxs-lookup"><span data-stu-id="ce559-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="ce559-133">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="ce559-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ce559-134">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ce559-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce559-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce559-135">See Also</span></span>  
 [<span data-ttu-id="ce559-136">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="ce559-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="ce559-137">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce559-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
