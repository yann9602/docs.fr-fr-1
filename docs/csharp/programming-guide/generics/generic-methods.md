---
title: "Méthodes génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63252dbe4307889f57d35e23eb0575f84358d737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="39b06-102">Méthodes génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="39b06-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="39b06-103">Une méthode générique est une méthode qui est déclarée avec des paramètres de type, comme suit :</span><span class="sxs-lookup"><span data-stu-id="39b06-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="39b06-104">L’exemple de code suivant montre une manière d’appeler la méthode, avec `int` comme argument de type :</span><span class="sxs-lookup"><span data-stu-id="39b06-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="39b06-105">Vous pouvez également omettre l’argument de type et le compilateur le déduira.</span><span class="sxs-lookup"><span data-stu-id="39b06-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="39b06-106">L’appel suivant à `Swap` est équivalent à l’appel précédent :</span><span class="sxs-lookup"><span data-stu-id="39b06-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="39b06-107">Les mêmes règles d’inférence de type s’appliquent aux méthodes statiques et aux méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="39b06-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="39b06-108">Le compilateur peut déduire les paramètres de type d’après les arguments de méthode que vous passez. Il ne peut pas déduire les paramètres de type uniquement à partir d’une valeur de contrainte ou de retour.</span><span class="sxs-lookup"><span data-stu-id="39b06-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="39b06-109">Par conséquent, l’inférence de type ne fonctionne pas avec les méthodes qui n’ont pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="39b06-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="39b06-110">L’inférence de type se produit au moment de la compilation avant que le compilateur n’essaie de résoudre toute signature de méthode surchargée.</span><span class="sxs-lookup"><span data-stu-id="39b06-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="39b06-111">Le compilateur applique la logique d’inférence de type à toutes les méthodes génériques qui partagent le même nom.</span><span class="sxs-lookup"><span data-stu-id="39b06-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="39b06-112">À l’étape de résolution de la surcharge, le compilateur inclut uniquement les méthodes génériques sur lesquelles l’inférence de type a réussi.</span><span class="sxs-lookup"><span data-stu-id="39b06-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="39b06-113">Dans une classe générique, les méthodes non génériques peuvent accéder aux paramètres de type de niveau classe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="39b06-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="39b06-114">Si vous définissez une méthode générique qui accepte les mêmes paramètres de type que la classe conteneur, le compilateur génère l’avertissement CS0693, car l’argument fourni à l’intérieur de la portée de la méthode pour le `T` interne masque l’argument fourni pour le `T` externe.</span><span class="sxs-lookup"><span data-stu-id="39b06-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="39b06-115">Si vous avez éventuellement besoin d’appeler une méthode de classe générique avec des arguments de type différents de ceux qui ont été fournis quand la classe a été instanciée, envisagez de fournir un autre identificateur pour le paramètre de type de la méthode, comme indiqué dans `GenericList2<T>` dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="39b06-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="39b06-116">Utilisez des contraintes pour permettre des opérations plus spécialisées sur les paramètres de type dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="39b06-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="39b06-117">Cette version de `Swap<T>`, maintenant appelée `SwapIfGreater<T>`, peut être utilisée avec des arguments de type qui implémentent <xref:System.IComparable%601> uniquement.</span><span class="sxs-lookup"><span data-stu-id="39b06-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="39b06-118">Les méthodes génériques peuvent être surchargées sur plusieurs paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="39b06-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="39b06-119">Par exemple, les méthodes suivantes peuvent toutes être dans la même classe :</span><span class="sxs-lookup"><span data-stu-id="39b06-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="39b06-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="39b06-120">C# Language Specification</span></span>  
 <span data-ttu-id="39b06-121">Pour plus d'informations, voir la [spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="39b06-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b06-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39b06-122">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="39b06-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="39b06-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39b06-124">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="39b06-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="39b06-125">Méthodes</span><span class="sxs-lookup"><span data-stu-id="39b06-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
