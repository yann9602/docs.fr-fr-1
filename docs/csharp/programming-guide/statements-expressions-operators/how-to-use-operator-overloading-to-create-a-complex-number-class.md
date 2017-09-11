---
title: "Guide pratique pour utiliser la surcharge d’opérateur pour créer une classe de nombres complexes (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
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
ms.openlocfilehash: 2ce629320744d46787aaabba48740f05c917fdcb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="24360-102">Guide pratique pour utiliser la surcharge d’opérateur pour créer une classe de nombres complexes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="24360-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="24360-103">Cet exemple montre comment utiliser la surcharge d’opérateur pour créer une classe de nombres complexes `Complex` qui définit une addition complexe.</span><span class="sxs-lookup"><span data-stu-id="24360-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="24360-104">Le programme affiche les parties imaginaire et réelle des nombres et le résultat de l’addition en utilisant un remplacement de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="24360-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24360-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="24360-105">Example</span></span>  
 <span data-ttu-id="24360-106">[!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="24360-106">[!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24360-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24360-107">See Also</span></span>  
 <span data-ttu-id="24360-108">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="24360-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="24360-109">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="24360-109">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="24360-110">[operator (référence C#)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="24360-110">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 <span data-ttu-id="24360-111">Article [Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383)</span><span class="sxs-lookup"><span data-stu-id="24360-111">[Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383)</span></span>

