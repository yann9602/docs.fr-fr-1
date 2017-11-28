---
title: "Comment : utiliser la surcharge d'opérateur pour créer une classe de nombres complexes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2053684a9b20c3ec8f4d8ac275832516b3f2c265
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="1d4ba-102">Comment : utiliser la surcharge d'opérateur pour créer une classe de nombres complexes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1d4ba-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="1d4ba-103">Cet exemple montre comment utiliser la surcharge d’opérateur pour créer une classe de nombres complexes `Complex` qui définit une addition complexe.</span><span class="sxs-lookup"><span data-stu-id="1d4ba-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="1d4ba-104">Le programme affiche les parties imaginaire et réelle des nombres et le résultat de l’addition en utilisant un remplacement de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="1d4ba-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d4ba-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d4ba-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1d4ba-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d4ba-106">See Also</span></span>  
 [<span data-ttu-id="1d4ba-107">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1d4ba-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1d4ba-108">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="1d4ba-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="1d4ba-109">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1d4ba-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 <span data-ttu-id="1d4ba-110">Article [Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383)</span><span class="sxs-lookup"><span data-stu-id="1d4ba-110">[Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383)</span></span>
