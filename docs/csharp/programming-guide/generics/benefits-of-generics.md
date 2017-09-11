---
title: "Avantages des génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8b05a3a695064764618564293e6ccd92e2ce60be
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="benefits-of-generics-c-programming-guide"></a><span data-ttu-id="34b01-102">Avantages des génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="34b01-102">Benefits of Generics (C# Programming Guide)</span></span>
<span data-ttu-id="34b01-103">Les génériques constituent la solution à une limitation dans les versions antérieures du Common Language Runtime et du langage C# dans lesquelles la généralisation s’effectue par un cast de types vers et depuis le type de base universel <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="34b01-103">Generics provide the solution to a limitation in earlier versions of the common language runtime and the C# language in which generalization is accomplished by casting types to and from the universal base type <xref:System.Object>.</span></span> <span data-ttu-id="34b01-104">En créant une classe générique, vous pouvez créer une collection qui est de type sécurisé au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="34b01-104">By creating a generic class, you can create a collection that is type-safe at compile-time.</span></span>  
  
 <span data-ttu-id="34b01-105">Les restrictions relatives à l’utilisation de classes de collections non génériques peuvent être illustrées par l’écriture d’un programme court qui utilise la classe de collection <xref:System.Collections.ArrayList> de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34b01-105">The limitations of using non-generic collection classes can be demonstrated by writing a short program that uses the <xref:System.Collections.ArrayList> collection class from the .NET Framework class library.</span></span> <span data-ttu-id="34b01-106"><xref:System.Collections.ArrayList> est une classe de collection très pratique qui peut être utilisée sans modification pour stocker tout type référence ou valeur.</span><span class="sxs-lookup"><span data-stu-id="34b01-106"><xref:System.Collections.ArrayList> is a highly convenient collection class that can be used without modification to store any reference or value type.</span></span>  
  
 <span data-ttu-id="34b01-107">[!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="34b01-107">[!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]</span></span>  
  
 <span data-ttu-id="34b01-108">Mais cette commodité a un coût.</span><span class="sxs-lookup"><span data-stu-id="34b01-108">But this convenience comes at a cost.</span></span> <span data-ttu-id="34b01-109">Tout type référence ou valeur qui est ajouté à un <xref:System.Collections.ArrayList> est implicitement upcasté en <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="34b01-109">Any reference or value type that is added to an <xref:System.Collections.ArrayList> is implicitly upcast to <xref:System.Object>.</span></span> <span data-ttu-id="34b01-110">Si les éléments sont des types valeur, ils doivent faire l’objet d’un boxing quand ils sont ajoutés à la liste, et d’un unboxing quand ils sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="34b01-110">If the items are value types, they must be boxed when they are added to the list, and unboxed when they are retrieved.</span></span> <span data-ttu-id="34b01-111">Les opérations de casting aussi bien que les opérations de boxing/unboxing affectent les performances. L’effet du boxing et de l’unboxing peut être très significatif quand vous devez itérer au sein de collections volumineuses.</span><span class="sxs-lookup"><span data-stu-id="34b01-111">Both the casting and the boxing and unboxing operations decrease performance; the effect of boxing and unboxing can be very significant in scenarios where you must iterate over large collections.</span></span>  
  
 <span data-ttu-id="34b01-112">L’autre limitation réside dans le manque de vérification au moment de la compilation. Étant donné que <xref:System.Collections.ArrayList> effectue un cast de tous les éléments en <xref:System.Object>, il n’existe aucun moyen d’empêcher le code client de procéder comme suit au moment de la compilation :</span><span class="sxs-lookup"><span data-stu-id="34b01-112">The other limitation is lack of compile-time type checking; because an <xref:System.Collections.ArrayList> casts everything to <xref:System.Object>, there is no way at compile-time to prevent client code from doing something such as this:</span></span>  
  
 <span data-ttu-id="34b01-113">[!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="34b01-113">[!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]</span></span>  
  
 <span data-ttu-id="34b01-114">Bien que parfaitement acceptable et parfois intentionnelle si vous créez une collection hétérogène, la combinaison de chaînes et de `ints` dans un seul <xref:System.Collections.ArrayList> est plus vraisemblablement une erreur de programmation, et cette erreur ne sera pas détectée avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="34b01-114">Although perfectly acceptable and sometimes intentional if you are creating a heterogeneous collection, combining strings and `ints` in a single <xref:System.Collections.ArrayList> is more likely to be a programming error, and this error will not be detected until runtime.</span></span>  
  
 <span data-ttu-id="34b01-115">Dans les versions 1.0 et 1.1 du langage C#, le seul moyen d’éviter les dangers du code généralisé dans les classes de collections de bibliothèques de classes de base .NET Framework était d’écrire vos propres collections spécifiques à un type.</span><span class="sxs-lookup"><span data-stu-id="34b01-115">In versions 1.0 and 1.1 of the C# language, you could avoid the dangers of generalized code in the .NET Framework base class library collection classes only by writing your own type specific collections.</span></span> <span data-ttu-id="34b01-116">Bien sûr, puisqu’une classe de ce genre n’est pas réutilisable pour plusieurs types de données, vous perdez les avantages de la généralisation, et vous devez réécrire la classe pour chaque type qui sera stocké.</span><span class="sxs-lookup"><span data-stu-id="34b01-116">Of course, because such a class is not reusable for more than one data type, you lose the benefits of generalization, and you have to rewrite the class for each type that will be stored.</span></span>  
  
 <span data-ttu-id="34b01-117">Ce dont <xref:System.Collections.ArrayList> et d’autres classes semblables ont vraiment besoin est un moyen permettant au code client de spécifier, pour chaque instance, le type de données particulier qu’elles ont l’intention d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="34b01-117">What <xref:System.Collections.ArrayList> and other similar classes really need is a way for client code to specify, on a per-instance basis, the particular data type that they intend to use.</span></span> <span data-ttu-id="34b01-118">Cela élimine la nécessité d’effectuer un upcast en `T:System.Object` et permettrait également au compilateur d’effectuer un contrôle de type.</span><span class="sxs-lookup"><span data-stu-id="34b01-118">That would eliminate the need for the upcast to `T:System.Object` and would also make it possible for the compiler to do type checking.</span></span> <span data-ttu-id="34b01-119">En d’autres termes, <xref:System.Collections.ArrayList> a besoin d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="34b01-119">In other words, <xref:System.Collections.ArrayList> needs a type parameter.</span></span> <span data-ttu-id="34b01-120">C’est exactement ce que fournissent les génériques.</span><span class="sxs-lookup"><span data-stu-id="34b01-120">That is exactly what generics provide.</span></span> <span data-ttu-id="34b01-121">Dans la collection <xref:System.Collections.Generic.List%601> générique, dans l’espace de noms `N:System.Collections.Generic`, la même opération d’ajout d’éléments à la collection ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="34b01-121">In the generic <xref:System.Collections.Generic.List%601> collection, in the `N:System.Collections.Generic` namespace, the same operation of adding items to the collection resembles this:</span></span>  
  
 <span data-ttu-id="34b01-122">[!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="34b01-122">[!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]</span></span>  
  
 <span data-ttu-id="34b01-123">Pour le code client, la seule syntaxe ajoutée avec <xref:System.Collections.Generic.List%601> par rapport à <xref:System.Collections.ArrayList> est l’argument de type dans la déclaration et l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="34b01-123">For client code, the only added syntax with <xref:System.Collections.Generic.List%601> compared to <xref:System.Collections.ArrayList> is the type argument in the declaration and instantiation.</span></span> <span data-ttu-id="34b01-124">En échange de cette complexité de codage légèrement supérieure, vous pouvez créer une liste qui est non seulement plus sûre qu’<xref:System.Collections.ArrayList>, mais également considérablement plus rapide, surtout quand les éléments de la liste sont des types valeur.</span><span class="sxs-lookup"><span data-stu-id="34b01-124">In return for this slightly more coding complexity, you can create a list that is not only safer than <xref:System.Collections.ArrayList>, but also significantly faster, especially when the list items are value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b01-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34b01-125">See Also</span></span>  
 <span data-ttu-id="34b01-126"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="34b01-126"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="34b01-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="34b01-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="34b01-128">[Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="34b01-128">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="34b01-129">[Boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md) </span><span class="sxs-lookup"><span data-stu-id="34b01-129">[Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md) </span></span>  
 [<span data-ttu-id="34b01-130">Bonnes pratiques relatives aux collections</span><span class="sxs-lookup"><span data-stu-id="34b01-130">Collections Best Practices</span></span>](http://go.microsoft.com/fwlink/?LinkId=112403)

