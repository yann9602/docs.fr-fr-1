---
title: "extern alias (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="19666-102">extern alias (référence C#)</span><span class="sxs-lookup"><span data-stu-id="19666-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="19666-103">Il se peut que vous deviez référencer deux versions d’assemblys qui ont le même nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="19666-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="19666-104">Par exemple, vous pourriez avoir à utiliser plusieurs versions d’un assembly dans la même application.</span><span class="sxs-lookup"><span data-stu-id="19666-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="19666-105">En utilisant un alias d’assembly externe, vous pouvez encapsuler les espaces de noms de chaque assembly dans des espaces de noms racines nommés par l’alias, ce qui permet de les utiliser dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="19666-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19666-106">Le mot clé [extern](../../../csharp/language-reference/keywords/extern.md) est également utilisé comme modificateur de méthode, déclarant une méthode écrite en code non managé.</span><span class="sxs-lookup"><span data-stu-id="19666-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="19666-107">Pour référencer deux assemblys portant le même nom de type qualifié complet, vous devez spécifier un alias à l’invite de commandes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="19666-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="19666-108">Cela crée les alias externes `GridV1` et `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="19666-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="19666-109">Pour utiliser ces alias à partir d’un programme, référencez-les en utilisant le mot clé `extern`.</span><span class="sxs-lookup"><span data-stu-id="19666-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="19666-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="19666-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="19666-111">Chaque déclaration d’alias externe introduit un espace de noms racine supplémentaire qui est parallèle à l’espace de noms global (mais n’est pas compris dedans).</span><span class="sxs-lookup"><span data-stu-id="19666-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="19666-112">Ainsi, vous pouvez référencer les types de chaque assembly sans ambiguïté en utilisant leur nom qualifié complet, enraciné dans l’alias d’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="19666-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="19666-113">Dans l’exemple précédent, `GridV1::Grid` serait le contrôle de grille de `grid.dll`, et `GridV2::Grid` serait le contrôle de grille de `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="19666-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="19666-114">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="19666-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19666-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19666-115">See Also</span></span>  
 [<span data-ttu-id="19666-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="19666-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="19666-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="19666-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="19666-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="19666-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="19666-119">Mots clés d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="19666-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="19666-120">:: (opérateur)</span><span class="sxs-lookup"><span data-stu-id="19666-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="19666-121">/reference (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="19666-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
