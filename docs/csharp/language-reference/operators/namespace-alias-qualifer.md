---
title: "::, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
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
ms.openlocfilehash: 97b9fa706669244ac579602a107c092e8593567d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="68c8d-102">::, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="68c8d-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="68c8d-103">Le qualificateur d’alias d’espace de noms (`::`) s’utilise pour rechercher les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="68c8d-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="68c8d-104">Il se place toujours entre deux identificateurs, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="68c8d-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 <span data-ttu-id="68c8d-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="68c8d-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68c8d-106">Notes</span><span class="sxs-lookup"><span data-stu-id="68c8d-106">Remarks</span></span>  
 <span data-ttu-id="68c8d-107">Le qualificateur d’alias d’espace de noms peut être `global`.</span><span class="sxs-lookup"><span data-stu-id="68c8d-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="68c8d-108">Il appelle alors une recherche dans l’espace de noms global, plutôt que dans un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="68c8d-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="68c8d-109">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="68c8d-109">For More Information</span></span>  
 <span data-ttu-id="68c8d-110">Pour obtenir un exemple d’utilisation de l’opérateur `::`, consultez la section suivante :</span><span class="sxs-lookup"><span data-stu-id="68c8d-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="68c8d-111">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="68c8d-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="68c8d-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="68c8d-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68c8d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68c8d-113">See Also</span></span>  
 <span data-ttu-id="68c8d-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="68c8d-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="68c8d-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="68c8d-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="68c8d-116">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="68c8d-116">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="68c8d-117">[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="68c8d-117">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="68c8d-118">[. , opérateur](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="68c8d-118">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 [<span data-ttu-id="68c8d-119">extern alias</span><span class="sxs-lookup"><span data-stu-id="68c8d-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)

