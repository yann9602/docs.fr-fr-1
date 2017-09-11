---
title: "try-catch-finally (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
dev_langs:
- CSharp
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
caps.latest.revision: 21
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
ms.openlocfilehash: 05b2e0075aae79f85fba26d64690eefadaa166cd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="07f9e-102">try-catch-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="07f9e-102">try-catch-finally (C# Reference)</span></span>
<span data-ttu-id="07f9e-103">`catch` et `finally` sont souvent utilisés ensemble pour obtenir et utiliser des ressources dans un bloc `try`, pour traiter des circonstances exceptionnelles dans un bloc `catch` et pour libérer les ressources dans le bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="07f9e-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>  
  
 <span data-ttu-id="07f9e-104">Pour plus d’informations et des exemples sur la génération répétée d’exceptions, consultez [try-catch](../../../csharp/language-reference/keywords/try-catch.md) et [Génération d’exceptions](https://msdn.microsoft.com/library/xhcbs8fz).</span><span class="sxs-lookup"><span data-stu-id="07f9e-104">For more information and examples on re-throwing exceptions, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md) and [Throwing Exceptions](https://msdn.microsoft.com/library/xhcbs8fz).</span></span> <span data-ttu-id="07f9e-105">Pour plus d’informations sur le bloc `finally`, consultez [try-finally](../../../csharp/language-reference/keywords/try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="07f9e-105">For more information about the `finally` block, see [try-finally](../../../csharp/language-reference/keywords/try-finally.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07f9e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="07f9e-106">Example</span></span>  
 <span data-ttu-id="07f9e-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07f9e-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="07f9e-108">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="07f9e-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07f9e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07f9e-109">See Also</span></span>  
 <span data-ttu-id="07f9e-110">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="07f9e-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="07f9e-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="07f9e-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="07f9e-112">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="07f9e-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="07f9e-113">[Instructions try, throw et catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span><span class="sxs-lookup"><span data-stu-id="07f9e-113">[try, throw, and catch Statements (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span></span>  
 <span data-ttu-id="07f9e-114">[Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="07f9e-114">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 <span data-ttu-id="07f9e-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span><span class="sxs-lookup"><span data-stu-id="07f9e-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span></span>  
 <span data-ttu-id="07f9e-116">[Guide pratique pour lever explicitement des exceptions](https://msdn.microsoft.com/library/xhcbs8fz) </span><span class="sxs-lookup"><span data-stu-id="07f9e-116">[How to: Explicitly Throw Exceptions](https://msdn.microsoft.com/library/xhcbs8fz) </span></span>  
 [<span data-ttu-id="07f9e-117">using, instruction</span><span class="sxs-lookup"><span data-stu-id="07f9e-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

