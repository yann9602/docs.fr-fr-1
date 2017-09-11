---
title: "this (référence C#)"
description: "this, mot clé (référence C#)"
keywords: "this (C#) ; this, mot clé (C#) ; this, mot clé (référence C#) ; this, mot clé (référence du langage C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.openlocfilehash: 1e764bbd85d06a3b1898f6574064b2844f6d6813
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="this-c-reference"></a><span data-ttu-id="9241e-104">this (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9241e-104">this (C# Reference)</span></span>
<span data-ttu-id="9241e-105">Le mot clé `this` fait référence à l’instance actuelle de la classe et est également utilisé comme modificateur du premier paramètre d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="9241e-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9241e-106">Cet article traite de l’utilisation de `this` avec des instances de classe.</span><span class="sxs-lookup"><span data-stu-id="9241e-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="9241e-107">Pour plus d’informations sur son utilisation dans les méthodes d’extension, consultez [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9241e-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="9241e-108">Voici quelques utilisations courantes de `this` :</span><span class="sxs-lookup"><span data-stu-id="9241e-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="9241e-109">Pour qualifier des membres masqués par des noms similaires, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9241e-109">To qualify members hidden by similar names, for example:</span></span>  
  
 <span data-ttu-id="9241e-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9241e-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span></span>  
  
-   <span data-ttu-id="9241e-111">Pour passer un objet comme paramètre à d’autres méthodes, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9241e-111">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="9241e-112">Pour déclarer des indexeurs, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9241e-112">To declare indexers, for example:</span></span>  
  
 <span data-ttu-id="9241e-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9241e-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span></span>  
  
 <span data-ttu-id="9241e-114">Les fonctions membres statiques, car ils existent au niveau de la classe et non comme faisant partie d’un objet, n’ont pas de pointeur `this`.</span><span class="sxs-lookup"><span data-stu-id="9241e-114">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="9241e-115">Une erreur consiste à faire référence à `this` dans une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9241e-115">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9241e-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="9241e-116">Example</span></span>  
 <span data-ttu-id="9241e-117">Dans cet exemple, `this` est utilisé pour qualifier les membres de la classe `Employee`, `name` et `alias`, qui sont masqués par des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="9241e-117">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="9241e-118">Il est également utilisé pour passer un objet à la méthode `CalcTax`, qui appartient à une autre classe.</span><span class="sxs-lookup"><span data-stu-id="9241e-118">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 <span data-ttu-id="9241e-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9241e-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9241e-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9241e-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9241e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9241e-121">See Also</span></span>  
 <span data-ttu-id="9241e-122">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9241e-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9241e-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9241e-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9241e-124">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9241e-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9241e-125">[base](../../../csharp/language-reference/keywords/base.md) </span><span class="sxs-lookup"><span data-stu-id="9241e-125">[base](../../../csharp/language-reference/keywords/base.md) </span></span>  
 [<span data-ttu-id="9241e-126">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9241e-126">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

