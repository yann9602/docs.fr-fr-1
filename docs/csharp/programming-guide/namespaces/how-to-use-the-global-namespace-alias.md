---
title: "Guide pratique pour utiliser l’alias de l’espace de noms global (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: 23
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
ms.openlocfilehash: 1252fc107d46b1d3a1cbef0a61708edc57253910
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="6c246-102">Guide pratique pour utiliser l’alias de l’espace de noms global (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6c246-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="6c246-103">La possibilité d’accéder à un membre dans l’[espace de noms ](../../../csharp/language-reference/keywords/namespace.md) global est utile quand le membre peut être masqué par une autre entité de même nom.</span><span class="sxs-lookup"><span data-stu-id="6c246-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="6c246-104">Par exemple, dans le code suivant, `Console` est résolu en `TestApp.Console` plutôt qu’en type `Console` dans l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="6c246-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 <span data-ttu-id="6c246-105">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-105">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]</span></span>  
  
 <span data-ttu-id="6c246-106">[!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-106">[!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]</span></span>  
  
 <span data-ttu-id="6c246-107">L’utilisation de `System.Console` continue de générer une erreur, car l’espace de noms `System` est masqué par la classe `TestApp.System` :</span><span class="sxs-lookup"><span data-stu-id="6c246-107">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 <span data-ttu-id="6c246-108">[!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-108">[!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]</span></span>  
  
 <span data-ttu-id="6c246-109">Cependant, vous pouvez contourner cette erreur en utilisant `global::System.Console`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="6c246-109">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 <span data-ttu-id="6c246-110">[!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-110">[!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]</span></span>  
  
 <span data-ttu-id="6c246-111">Quand l’identificateur de gauche est `global`, la recherche de l’identificateur de droite débute dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="6c246-111">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="6c246-112">Par exemple, la déclaration suivante fait référence à `TestApp` en tant que membre de l’espace global.</span><span class="sxs-lookup"><span data-stu-id="6c246-112">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 <span data-ttu-id="6c246-113">[!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-113">[!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]</span></span>  
  
 <span data-ttu-id="6c246-114">Bien entendu, il n’est pas recommandé de créer des espaces de noms personnalisés sous le nom `System`, et il est peu probable que vous en rencontriez dans du code.</span><span class="sxs-lookup"><span data-stu-id="6c246-114">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="6c246-115">Cependant, dans les projets à grande échelle, il est tout à fait possible qu’un espace de noms soit dupliqué d’une façon ou d’une autre.</span><span class="sxs-lookup"><span data-stu-id="6c246-115">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="6c246-116">En pareil cas, le qualificateur d’espace de noms global est la garantie que vous pouvez spécifier l’espace de noms racine.</span><span class="sxs-lookup"><span data-stu-id="6c246-116">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c246-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c246-117">Example</span></span>  
 <span data-ttu-id="6c246-118">Dans cet exemple, l’espace de noms `System` est utilisé pour inclure la classe `TestClass`. De ce fait, `global::System.Console` doit être utilisé pour faire référence à la classe `System.Console`, qui est masquée par l’espace de noms `System`.</span><span class="sxs-lookup"><span data-stu-id="6c246-118">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="6c246-119">Par ailleurs, l’alias `colAlias` est utilisé pour faire référence à l’espace de noms `System.Collections` ; par conséquent, l’instance d’un <xref:System.Collections.Hashtable?displayProperty=fullName> a été créée en utilisant cet alias plutôt que l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6c246-119">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=fullName> was created using this alias instead of the namespace.</span></span>  
  
 <span data-ttu-id="6c246-120">[!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c246-120">[!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]</span></span>  
  
 <span data-ttu-id="6c246-121">**A 1**</span><span class="sxs-lookup"><span data-stu-id="6c246-121">**A 1**</span></span>  
<span data-ttu-id="6c246-122">**B 2**</span><span class="sxs-lookup"><span data-stu-id="6c246-122">**B 2**</span></span>  
<span data-ttu-id="6c246-123">**C 3**</span><span class="sxs-lookup"><span data-stu-id="6c246-123">**C 3**</span></span>   
## <a name="see-also"></a><span data-ttu-id="6c246-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c246-124">See Also</span></span>  
 <span data-ttu-id="6c246-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6c246-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6c246-126">[Espaces de noms](../../../csharp/programming-guide/namespaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="6c246-126">[Namespaces](../../../csharp/programming-guide/namespaces/index.md) </span></span>  
 <span data-ttu-id="6c246-127">[. , opérateur](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6c246-127">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 <span data-ttu-id="6c246-128">[::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="6c246-128">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="6c246-129">extern</span><span class="sxs-lookup"><span data-stu-id="6c246-129">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)

