---
title: "value (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
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
ms.openlocfilehash: 012cf622091687996fec477a8b5b821b190bbc29
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="value-c-reference"></a><span data-ttu-id="bbdd4-102">value (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bbdd4-102">value (C# Reference)</span></span>
<span data-ttu-id="bbdd4-103">Le mot clé contextuel `value` est utilisé dans l’accesseur set de déclarations de propriété ordinaires.</span><span class="sxs-lookup"><span data-stu-id="bbdd4-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="bbdd4-104">Il est similaire à un paramètre d’entrée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="bbdd4-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="bbdd4-105">Le mot `value` fait référence à la valeur que le code client tente d’assigner à la propriété.</span><span class="sxs-lookup"><span data-stu-id="bbdd4-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="bbdd4-106">Dans l’exemple suivant, `MyDerivedClass` a une propriété appelée `Name` qui utilise le paramètre `value` pour assigner une nouvelle chaîne au `name` du champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="bbdd4-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="bbdd4-107">Du point de vue du code client, l’opération est écrite comme une assignation simple.</span><span class="sxs-lookup"><span data-stu-id="bbdd4-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 <span data-ttu-id="bbdd4-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbdd4-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span></span>  
  
 <span data-ttu-id="bbdd4-109">Pour plus d’informations sur l’utilisation de `value`, consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="bbdd4-109">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbdd4-110">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bbdd4-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbdd4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbdd4-111">See Also</span></span>  
 <span data-ttu-id="bbdd4-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbdd4-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bbdd4-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbdd4-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="bbdd4-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="bbdd4-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

