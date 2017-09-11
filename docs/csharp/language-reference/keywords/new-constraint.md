---
title: "new, contrainte (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
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
ms.openlocfilehash: 762941794184605f90443ed8f36c88ecfa50aa84
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="e3668-102">new, contrainte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e3668-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="e3668-103">La contrainte `new` spécifie que tout argument de type dans une déclaration de classe générique doit avoir un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="e3668-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="e3668-104">Pour utiliser la contrainte new, le type ne doit pas être abstract.</span><span class="sxs-lookup"><span data-stu-id="e3668-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3668-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3668-105">Example</span></span>  
 <span data-ttu-id="e3668-106">Appliquez la contrainte `new` à un paramètre de type quand votre classe générique crée des instances du type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e3668-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 <span data-ttu-id="e3668-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e3668-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3668-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3668-108">Example</span></span>  
 <span data-ttu-id="e3668-109">Si vous utilisez la contrainte `new()` avec d’autres contraintes, spécifiez-la en dernier :</span><span class="sxs-lookup"><span data-stu-id="e3668-109">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 <span data-ttu-id="e3668-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e3668-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="e3668-111">Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e3668-111">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e3668-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e3668-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3668-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3668-113">See Also</span></span>  
 <span data-ttu-id="e3668-114"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="e3668-114"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="e3668-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3668-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e3668-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3668-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e3668-117">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3668-117">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e3668-118">[Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="e3668-118">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="e3668-119">Génériques</span><span class="sxs-lookup"><span data-stu-id="e3668-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

