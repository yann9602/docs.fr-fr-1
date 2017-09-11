---
title: "Méthodes génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
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
ms.openlocfilehash: 14461773303bafc098f79c3686b1f76827f11005
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="ebc87-102">Méthodes génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ebc87-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="ebc87-103">Une méthode générique est une méthode qui est déclarée avec des paramètres de type, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ebc87-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 <span data-ttu-id="ebc87-104">[!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-104">[!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-105">L’exemple de code suivant montre une manière d’appeler la méthode, avec `int` comme argument de type :</span><span class="sxs-lookup"><span data-stu-id="ebc87-105">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 <span data-ttu-id="ebc87-106">[!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-106">[!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-107">Vous pouvez également omettre l’argument de type et le compilateur le déduira.</span><span class="sxs-lookup"><span data-stu-id="ebc87-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="ebc87-108">L’appel suivant à `Swap` est équivalent à l’appel précédent :</span><span class="sxs-lookup"><span data-stu-id="ebc87-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 <span data-ttu-id="ebc87-109">[!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-109">[!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-110">Les mêmes règles d’inférence de type s’appliquent aux méthodes statiques et aux méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="ebc87-110">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="ebc87-111">Le compilateur peut déduire les paramètres de type d’après les arguments de méthode que vous passez. Il ne peut pas déduire les paramètres de type uniquement à partir d’une valeur de contrainte ou de retour.</span><span class="sxs-lookup"><span data-stu-id="ebc87-111">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="ebc87-112">Par conséquent, l’inférence de type ne fonctionne pas avec les méthodes qui n’ont pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="ebc87-112">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="ebc87-113">L’inférence de type se produit au moment de la compilation avant que le compilateur n’essaie de résoudre toute signature de méthode surchargée.</span><span class="sxs-lookup"><span data-stu-id="ebc87-113">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="ebc87-114">Le compilateur applique la logique d’inférence de type à toutes les méthodes génériques qui partagent le même nom.</span><span class="sxs-lookup"><span data-stu-id="ebc87-114">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="ebc87-115">À l’étape de résolution de la surcharge, le compilateur inclut uniquement les méthodes génériques sur lesquelles l’inférence de type a réussi.</span><span class="sxs-lookup"><span data-stu-id="ebc87-115">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="ebc87-116">Dans une classe générique, les méthodes non génériques peuvent accéder aux paramètres de type de niveau classe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ebc87-116">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 <span data-ttu-id="ebc87-117">[!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-117">[!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-118">Si vous définissez une méthode générique qui accepte les mêmes paramètres de type que la classe conteneur, le compilateur génère l’avertissement CS0693, car l’argument fourni à l’intérieur de la portée de la méthode pour le `T` interne masque l’argument fourni pour le `T` externe.</span><span class="sxs-lookup"><span data-stu-id="ebc87-118">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="ebc87-119">Si vous avez éventuellement besoin d’appeler une méthode de classe générique avec des arguments de type différents de ceux qui ont été fournis quand la classe a été instanciée, envisagez de fournir un autre identificateur pour le paramètre de type de la méthode, comme indiqué dans `GenericList2<T>` dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ebc87-119">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 <span data-ttu-id="ebc87-120">[!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-120">[!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-121">Utilisez des contraintes pour permettre des opérations plus spécialisées sur les paramètres de type dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="ebc87-121">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="ebc87-122">Cette version de `Swap<T>`, maintenant appelée `SwapIfGreater<T>`, peut être utilisée avec des arguments de type qui implémentent <xref:System.IComparable%601> uniquement.</span><span class="sxs-lookup"><span data-stu-id="ebc87-122">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 <span data-ttu-id="ebc87-123">[!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-123">[!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]</span></span>  
  
 <span data-ttu-id="ebc87-124">Les méthodes génériques peuvent être surchargées sur plusieurs paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="ebc87-124">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="ebc87-125">Par exemple, les méthodes suivantes peuvent toutes être dans la même classe :</span><span class="sxs-lookup"><span data-stu-id="ebc87-125">For example, the following methods can all be located in the same class:</span></span>  
  
 <span data-ttu-id="ebc87-126">[!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc87-126">[!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ebc87-127">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ebc87-127">C# Language Specification</span></span>  
 <span data-ttu-id="ebc87-128">Pour plus d'informations, consultez la [spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebc87-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc87-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebc87-129">See Also</span></span>  
 <span data-ttu-id="ebc87-130"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="ebc87-130"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="ebc87-131">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ebc87-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ebc87-132">[Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="ebc87-132">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 [<span data-ttu-id="ebc87-133">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ebc87-133">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

