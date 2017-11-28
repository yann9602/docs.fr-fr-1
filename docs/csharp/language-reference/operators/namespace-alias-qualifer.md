---
title: "::, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f489d-102">::, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f489d-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="f489d-103">Le qualificateur d’alias d’espace de noms (`::`) s’utilise pour rechercher les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="f489d-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="f489d-104">Il se place toujours entre deux identificateurs, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="f489d-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f489d-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="f489d-105">Remarks</span></span>  
 <span data-ttu-id="f489d-106">Le qualificateur d’alias d’espace de noms peut être `global`.</span><span class="sxs-lookup"><span data-stu-id="f489d-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="f489d-107">Il appelle alors une recherche dans l’espace de noms global, plutôt que dans un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="f489d-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="f489d-108">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="f489d-108">For More Information</span></span>  
 <span data-ttu-id="f489d-109">Pour obtenir un exemple d’utilisation de l’opérateur `::`, consultez la section suivante :</span><span class="sxs-lookup"><span data-stu-id="f489d-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="f489d-110">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="f489d-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f489d-111">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f489d-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f489d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f489d-112">See Also</span></span>  
 [<span data-ttu-id="f489d-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f489d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f489d-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f489d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f489d-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="f489d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f489d-116">Mots clés d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="f489d-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="f489d-117">. Opérateur</span><span class="sxs-lookup"><span data-stu-id="f489d-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="f489d-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="f489d-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
