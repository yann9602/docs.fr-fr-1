---
title: "params (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5999911b96d17c710096e74c8f3da65223e778fc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="params-c-reference"></a><span data-ttu-id="d60c6-102">params (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d60c6-102">params (C# Reference)</span></span>
<span data-ttu-id="d60c6-103">Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](../../../csharp/language-reference/keywords/method-parameters.md) qui prend un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="d60c6-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="d60c6-104">Vous pouvez envoyer une liste séparée par des virgules d’arguments du type spécifié dans la déclaration du paramètre ou envoyer un tableau d’arguments du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d60c6-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="d60c6-105">Vous pouvez aussi ne pas envoyer d’arguments.</span><span class="sxs-lookup"><span data-stu-id="d60c6-105">You also can send no arguments.</span></span> <span data-ttu-id="d60c6-106">Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="d60c6-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="d60c6-107">Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.</span><span class="sxs-lookup"><span data-stu-id="d60c6-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60c6-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d60c6-108">Example</span></span>  
 <span data-ttu-id="d60c6-109">L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.</span><span class="sxs-lookup"><span data-stu-id="d60c6-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 <span data-ttu-id="d60c6-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d60c6-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d60c6-111">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d60c6-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d60c6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d60c6-112">See Also</span></span>  
 <span data-ttu-id="d60c6-113">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d60c6-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d60c6-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d60c6-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d60c6-115">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d60c6-115">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="d60c6-116">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="d60c6-116">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

