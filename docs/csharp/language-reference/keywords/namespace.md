---
title: "namespace (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a><span data-ttu-id="6318b-102">namespace (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6318b-102">namespace (C# Reference)</span></span>
<span data-ttu-id="6318b-103">Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="6318b-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="6318b-104">Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.</span><span class="sxs-lookup"><span data-stu-id="6318b-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="6318b-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="6318b-105">Remarks</span></span>  
 <span data-ttu-id="6318b-106">Dans un espace de noms, vous pouvez déclarer un ou plusieurs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="6318b-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="6318b-107">autre espace de noms</span><span class="sxs-lookup"><span data-stu-id="6318b-107">another namespace</span></span>  
  
-   [<span data-ttu-id="6318b-108">class</span><span class="sxs-lookup"><span data-stu-id="6318b-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="6318b-109">interface</span><span class="sxs-lookup"><span data-stu-id="6318b-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="6318b-110">struct</span><span class="sxs-lookup"><span data-stu-id="6318b-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="6318b-111">enum</span><span class="sxs-lookup"><span data-stu-id="6318b-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="6318b-112">delegate</span><span class="sxs-lookup"><span data-stu-id="6318b-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="6318b-113">Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="6318b-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="6318b-114">Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="6318b-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="6318b-115">Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="6318b-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="6318b-116">Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="6318b-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="6318b-117">Consultez [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6318b-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="6318b-118">Il est possible de définir un espace de noms dans deux déclarations ou plus.</span><span class="sxs-lookup"><span data-stu-id="6318b-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="6318b-119">Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="6318b-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="6318b-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="6318b-120">Example</span></span>  
 <span data-ttu-id="6318b-121">L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="6318b-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="6318b-122">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="6318b-122">For More Information</span></span>  
 <span data-ttu-id="6318b-123">Pour plus d’informations sur l’utilisation des espaces de noms, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6318b-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6318b-124">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="6318b-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="6318b-125">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="6318b-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="6318b-126">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="6318b-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6318b-127">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6318b-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6318b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6318b-128">See Also</span></span>  
 [<span data-ttu-id="6318b-129">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6318b-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6318b-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6318b-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6318b-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="6318b-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6318b-132">Mots clés d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="6318b-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="6318b-133">using</span><span class="sxs-lookup"><span data-stu-id="6318b-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
