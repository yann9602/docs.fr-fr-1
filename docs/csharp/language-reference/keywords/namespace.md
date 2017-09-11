---
title: "namespace (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
dev_langs:
- CSharp
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
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
ms.openlocfilehash: d2cef3949d9a41db36406db059218f7a204172ea
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="namespace-c-reference"></a><span data-ttu-id="bd7fd-102">namespace (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bd7fd-102">namespace (C# Reference)</span></span>
<span data-ttu-id="bd7fd-103">Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="bd7fd-104">Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 <span data-ttu-id="bd7fd-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd7fd-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd7fd-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="bd7fd-106">Remarks</span></span>  
 <span data-ttu-id="bd7fd-107">Dans un espace de noms, vous pouvez déclarer un ou plusieurs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="bd7fd-107">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="bd7fd-108">autre espace de noms</span><span class="sxs-lookup"><span data-stu-id="bd7fd-108">another namespace</span></span>  
  
-   [<span data-ttu-id="bd7fd-109">class</span><span class="sxs-lookup"><span data-stu-id="bd7fd-109">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="bd7fd-110">interface</span><span class="sxs-lookup"><span data-stu-id="bd7fd-110">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="bd7fd-111">struct</span><span class="sxs-lookup"><span data-stu-id="bd7fd-111">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="bd7fd-112">enum</span><span class="sxs-lookup"><span data-stu-id="bd7fd-112">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="bd7fd-113">delegate</span><span class="sxs-lookup"><span data-stu-id="bd7fd-113">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="bd7fd-114">Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="bd7fd-115">Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="bd7fd-116">Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="bd7fd-117">Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="bd7fd-118">Consultez [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="bd7fd-119">Il est possible de définir un espace de noms dans deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="bd7fd-120">Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="bd7fd-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 <span data-ttu-id="bd7fd-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd7fd-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd7fd-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd7fd-122">Example</span></span>  
 <span data-ttu-id="bd7fd-123">L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="bd7fd-123">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 <span data-ttu-id="bd7fd-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd7fd-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="bd7fd-125">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="bd7fd-125">For More Information</span></span>  
 <span data-ttu-id="bd7fd-126">Pour plus d’informations sur l’utilisation des espaces de noms, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd7fd-126">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="bd7fd-127">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="bd7fd-127">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="bd7fd-128">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="bd7fd-128">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="bd7fd-129">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="bd7fd-129">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bd7fd-130">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bd7fd-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd7fd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd7fd-131">See Also</span></span>  
 <span data-ttu-id="bd7fd-132">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd7fd-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bd7fd-133">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd7fd-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bd7fd-134">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd7fd-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="bd7fd-135">[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="bd7fd-135">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 [<span data-ttu-id="bd7fd-136">using</span><span class="sxs-lookup"><span data-stu-id="bd7fd-136">using</span></span>](../../../csharp/language-reference/keywords/using.md)

