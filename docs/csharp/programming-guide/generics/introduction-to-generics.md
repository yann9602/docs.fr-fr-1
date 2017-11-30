---
title: "Introduction aux génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="75e16-102">Introduction aux génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="75e16-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="75e16-103">Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques.</span><span class="sxs-lookup"><span data-stu-id="75e16-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="75e16-104">Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux.</span><span class="sxs-lookup"><span data-stu-id="75e16-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="75e16-105">La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection génériques.</span><span class="sxs-lookup"><span data-stu-id="75e16-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="75e16-106">Il est recommandé que toutes les applications qui ciblent le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 et versions ultérieures utilisent les nouvelles classes de collection générique au lieu d’équivalents non génériques plus anciens tels que <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="75e16-106">It is recommended that all applications that target the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="75e16-107">Pour plus d’informations, consultez [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="75e16-107">For more information, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="75e16-108">Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="75e16-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="75e16-109">L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="75e16-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="75e16-110">(Dans la plupart des cas, vous devez utiliser le <xref:System.Collections.Generic.List%601> classe fournie par la bibliothèque de classes .NET Framework au lieu de créer votre propre.) Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste.</span><span class="sxs-lookup"><span data-stu-id="75e16-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="75e16-111">Il est utilisé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="75e16-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="75e16-112">Comme le type d’un paramètre de méthode dans la méthode`AddHead`.</span><span class="sxs-lookup"><span data-stu-id="75e16-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="75e16-113">Comme le type de retour de la méthode publique `GetNext` et de la propriété `Data` de la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="75e16-113">As the return type of the public method `GetNext` and the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="75e16-114">Comme le type des données de membre privé de la classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="75e16-114">As the type of the private member data in the nested class.</span></span>  
  
 <span data-ttu-id="75e16-115">Notez que T est disponible pour la classe imbriquée `Node`.</span><span class="sxs-lookup"><span data-stu-id="75e16-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="75e16-116">Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.</span><span class="sxs-lookup"><span data-stu-id="75e16-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="75e16-117">L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="75e16-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="75e16-118">En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :</span><span class="sxs-lookup"><span data-stu-id="75e16-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="75e16-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75e16-119">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="75e16-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="75e16-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="75e16-121">Génériques</span><span class="sxs-lookup"><span data-stu-id="75e16-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
