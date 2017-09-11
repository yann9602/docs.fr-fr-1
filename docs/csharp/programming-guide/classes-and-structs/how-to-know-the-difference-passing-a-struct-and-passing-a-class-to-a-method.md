---
title: "Guide pratique pour différencier le passage d’un struct et le passage d’une référence de classe à une méthode (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
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
ms.openlocfilehash: 1a4508c8765ac678fd371180cb0c3ece3e1d9a44
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a><span data-ttu-id="f1612-102">Guide pratique pour différencier le passage d’un struct et le passage d’une référence de classe à une méthode (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f1612-102">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method (C# Programming Guide)</span></span>
<span data-ttu-id="f1612-103">L’exemple suivant montre comment le passage d’un [struct](../../../csharp/language-reference/keywords/struct.md) à une méthode diffère du passage d’une instance de [classe](../../../csharp/language-reference/keywords/class.md) à une méthode.</span><span class="sxs-lookup"><span data-stu-id="f1612-103">The following example demonstrates how passing a [struct](../../../csharp/language-reference/keywords/struct.md) to a method differs from passing a [class](../../../csharp/language-reference/keywords/class.md) instance to a method.</span></span> <span data-ttu-id="f1612-104">Dans l’exemple, les deux arguments (struct et instance de classe) sont passés par valeur, tandis que les deux méthodes changent la valeur d’un champ de l’argument.</span><span class="sxs-lookup"><span data-stu-id="f1612-104">In the example, both of the arguments (struct and class instance) are passed by value, and both methods change the value of one field of the argument.</span></span> <span data-ttu-id="f1612-105">Toutefois, les résultats des deux méthodes ne sont pas identiques, car ce qui est passé quand vous passez un struct diffère de ce qui est passé quand vous passez une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="f1612-105">However, the results of the two methods are not the same because what is passed when you pass a struct differs from what is passed when you pass an instance of a class.</span></span>  
  
 <span data-ttu-id="f1612-106">Étant donné qu’un struct est un [type valeur](../../../csharp/language-reference/keywords/value-types.md), quand vous [passez un struct par valeur](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) à une méthode, la méthode reçoit et traite une copie de l’argument struct.</span><span class="sxs-lookup"><span data-stu-id="f1612-106">Because a struct is a [value type](../../../csharp/language-reference/keywords/value-types.md), when you [pass a struct by value](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) to a method, the method receives and operates on a copy of the struct argument.</span></span> <span data-ttu-id="f1612-107">La méthode n’a pas accès au struct d’origine dans la méthode d’appel, et ne peut donc pas le modifier de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="f1612-107">The method has no access to the original struct in the calling method and therefore can't change it in any way.</span></span> <span data-ttu-id="f1612-108">La méthode peut modifier uniquement la copie.</span><span class="sxs-lookup"><span data-stu-id="f1612-108">The method can change only the copy.</span></span>  
  
 <span data-ttu-id="f1612-109">Une instance de classe est un [type référence](../../../csharp/language-reference/keywords/reference-types.md), pas un type valeur.</span><span class="sxs-lookup"><span data-stu-id="f1612-109">A class instance is a [reference type](../../../csharp/language-reference/keywords/reference-types.md), not a value type.</span></span> <span data-ttu-id="f1612-110">Quand [un type référence est passé par valeur](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) à une méthode, celle-ci reçoit une copie de la référence à l’instance de classe.</span><span class="sxs-lookup"><span data-stu-id="f1612-110">When [a reference type is passed by value](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) to a method, the method receives a copy of the reference to the class instance.</span></span> <span data-ttu-id="f1612-111">Autrement dit, la méthode reçoit une copie de l’adresse de l’instance, et non pas une copie de l’instance elle-même.</span><span class="sxs-lookup"><span data-stu-id="f1612-111">That is, the method receives a copy of the address of the instance, not a copy of the instance itself.</span></span> <span data-ttu-id="f1612-112">L’instance de classe dans la méthode d’appel a une adresse, le paramètre dans la méthode appelée a une copie de l’adresse, et les deux adresses font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="f1612-112">The class instance in the calling method has an address, the parameter in the called method has a copy of the address, and both addresses refer to the same object.</span></span> <span data-ttu-id="f1612-113">Étant donné que le paramètre contient uniquement une copie de l’adresse, la méthode appelée ne peut pas modifier l’adresse de l’instance de la classe dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="f1612-113">Because the parameter contains only a copy of the address, the called method cannot change the address of the class instance in the calling method.</span></span> <span data-ttu-id="f1612-114">Toutefois, la méthode appelée peut utiliser l’adresse pour accéder aux membres de classe qui font à la fois référence à l’adresse d’origine et à la copie.</span><span class="sxs-lookup"><span data-stu-id="f1612-114">However, the called method can use the address to access the class members that both the original address and the copy reference.</span></span> <span data-ttu-id="f1612-115">Si la méthode appelée modifie un membre de classe, l’instance de classe d’origine dans la méthode d’appel change également.</span><span class="sxs-lookup"><span data-stu-id="f1612-115">If the called method changes a class member, the original class instance in the calling method also changes.</span></span>  
  
 <span data-ttu-id="f1612-116">La sortie de l’exemple suivant illustre la différence.</span><span class="sxs-lookup"><span data-stu-id="f1612-116">The output of the following example illustrates the difference.</span></span> <span data-ttu-id="f1612-117">La valeur du champ `willIChange` de l’instance de classe est changée par l’appel à la méthode `ClassTaker`, car la méthode utilise l’adresse mentionnée dans le paramètre pour rechercher le champ spécifié de l’instance de classe.</span><span class="sxs-lookup"><span data-stu-id="f1612-117">The value of the `willIChange` field of the class instance is changed by the call to method `ClassTaker` because the method uses the address in the parameter to find the specified field of the class instance.</span></span> <span data-ttu-id="f1612-118">Le champ `willIChange` du struct de la méthode d’appel n’est pas changé par l’appel à la méthode `StructTaker`, car la valeur de l’argument est une copie du struct lui-même, et non pas une copie de son adresse.</span><span class="sxs-lookup"><span data-stu-id="f1612-118">The `willIChange` field of the struct in the calling method is not changed by the call to method `StructTaker` because the value of the argument is a copy of the struct itself, not a copy of its address.</span></span> <span data-ttu-id="f1612-119">`StructTaker` change la copie, et cette dernière est perdue quand l’appel à `StructTaker` est terminé.</span><span class="sxs-lookup"><span data-stu-id="f1612-119">`StructTaker` changes the copy, and the copy is lost when the call to `StructTaker` is completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1612-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="f1612-120">Example</span></span>  
 <span data-ttu-id="f1612-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1612-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1612-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1612-122">See Also</span></span>  
 <span data-ttu-id="f1612-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1612-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f1612-124">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span><span class="sxs-lookup"><span data-stu-id="f1612-124">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span></span>  
 <span data-ttu-id="f1612-125">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="f1612-125">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 [<span data-ttu-id="f1612-126">Passage de paramètres</span><span class="sxs-lookup"><span data-stu-id="f1612-126">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)

