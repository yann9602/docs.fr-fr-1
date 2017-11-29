---
title: "this (référence C#)"
description: "this, mot clé (référence C#)"
keywords: "this (C#) ; this, mot clé (C#) ; this, mot clé (référence C#) ; this, mot clé (référence du langage C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords: this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="237b3-104">this (référence C#)</span><span class="sxs-lookup"><span data-stu-id="237b3-104">this (C# Reference)</span></span>
<span data-ttu-id="237b3-105">Le mot clé `this` fait référence à l’instance actuelle de la classe et est également utilisé comme modificateur du premier paramètre d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="237b3-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="237b3-106">Cet article traite de l’utilisation de `this` avec des instances de classe.</span><span class="sxs-lookup"><span data-stu-id="237b3-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="237b3-107">Pour plus d’informations sur son utilisation dans les méthodes d’extension, consultez [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="237b3-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="237b3-108">Voici quelques utilisations courantes de `this` :</span><span class="sxs-lookup"><span data-stu-id="237b3-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="237b3-109">Pour qualifier des membres masqués par des noms similaires, par exemple :</span><span class="sxs-lookup"><span data-stu-id="237b3-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="237b3-110">Pour passer un objet comme paramètre à d’autres méthodes, par exemple :</span><span class="sxs-lookup"><span data-stu-id="237b3-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="237b3-111">Pour déclarer des indexeurs, par exemple :</span><span class="sxs-lookup"><span data-stu-id="237b3-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="237b3-112">Les fonctions membres statiques, car ils existent au niveau de la classe et non comme faisant partie d’un objet, n’ont pas de pointeur `this`.</span><span class="sxs-lookup"><span data-stu-id="237b3-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="237b3-113">Une erreur consiste à faire référence à `this` dans une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="237b3-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="237b3-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="237b3-114">Example</span></span>  
 <span data-ttu-id="237b3-115">Dans cet exemple, `this` est utilisé pour qualifier les membres de la classe `Employee`, `name` et `alias`, qui sont masqués par des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="237b3-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="237b3-116">Il est également utilisé pour passer un objet à la méthode `CalcTax`, qui appartient à une autre classe.</span><span class="sxs-lookup"><span data-stu-id="237b3-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="237b3-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="237b3-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="237b3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="237b3-118">See Also</span></span>  
 [<span data-ttu-id="237b3-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="237b3-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="237b3-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="237b3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="237b3-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="237b3-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="237b3-122">base</span><span class="sxs-lookup"><span data-stu-id="237b3-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="237b3-123">Méthodes</span><span class="sxs-lookup"><span data-stu-id="237b3-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
