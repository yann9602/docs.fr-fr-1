---
title: "return (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
dev_langs:
- CSharp
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
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
ms.openlocfilehash: 596375a1cba8f5ecbad636a6829c1a0599f8c0f4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="return-c-reference"></a><span data-ttu-id="dc0e0-102">return (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dc0e0-102">return (C# Reference)</span></span>
<span data-ttu-id="dc0e0-103">L’instruction `return` met un terme à l’exécution de la méthode dans laquelle elle apparaît et retourne le contrôle à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="dc0e0-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="dc0e0-104">Elle peut également retourner une valeur facultative.</span><span class="sxs-lookup"><span data-stu-id="dc0e0-104">It can also return an optional value.</span></span> <span data-ttu-id="dc0e0-105">Si la méthode est un type `void`, l’instruction `return` peut être omise.</span><span class="sxs-lookup"><span data-stu-id="dc0e0-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="dc0e0-106">Si l’instruction return est à l’intérieur d’un bloc `try`, le bloc `finally`, le cas échéant, est exécuté avant que le contrôle retourne à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="dc0e0-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc0e0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc0e0-107">Example</span></span>  
 <span data-ttu-id="dc0e0-108">Dans l’exemple suivant, la méthode `A()` retourne la variable `Area` en tant que valeur [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e0-108">In the following example, the method `A()` returns the variable `Area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 <span data-ttu-id="dc0e0-109">[!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc0e0-109">[!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc0e0-110">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dc0e0-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc0e0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc0e0-111">See Also</span></span>  
 <span data-ttu-id="dc0e0-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0e0-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dc0e0-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0e0-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dc0e0-114">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0e0-114">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="dc0e0-115">[return, instruction](/cpp/cpp/return-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="dc0e0-115">[return Statement](/cpp/cpp/return-statement-cpp) </span></span>  
 [<span data-ttu-id="dc0e0-116">Instructions de saut</span><span class="sxs-lookup"><span data-stu-id="dc0e0-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

