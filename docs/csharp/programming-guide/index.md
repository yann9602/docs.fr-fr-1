---
title: "Guide de programmation C#"
ms.date: 2017-05-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.langref
dev_langs:
- CSharp
helpviewer_keywords:
- reference tables [C#]
- C# language, programming guide
- Visual C#, programming concepts
- C# language, concepts
ms.assetid: ac0f23a2-6bf3-4077-be99-538ae5fd3bc5
caps.latest.revision: 45
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
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 0c95459f21aebf1d5efe1482e74ca2724d283821
ms.contentlocale: fr-fr
ms.lasthandoff: 09/02/2017

---
# <a name="c-programming-guide"></a><span data-ttu-id="c1fbd-102">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c1fbd-102">C# programming guide</span></span>
<span data-ttu-id="c1fbd-103">Cette section fournit des informations détaillées sur les fonctionnalités et fonctions clés du langage C# accessibles par .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1fbd-103">This section provides detailed information on key C# language features and features accessible to C# through the .NET Framework.</span></span>  
  
 <span data-ttu-id="c1fbd-104">La majeure partie de cette section suppose que vous connaissez déjà en partie C# et les concepts de programmation généraux.</span><span class="sxs-lookup"><span data-stu-id="c1fbd-104">Most of this section assumes that you already know something about C# and general programming concepts.</span></span> <span data-ttu-id="c1fbd-105">Si vous débutez en programmation ou avec C#, vous pouvez consulter le didacticiel interactif [Bien démarrer avec C#](https://www.microsoft.com/net/tutorials/csharp/getting-started), où aucune connaissance préalable de la programmation n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c1fbd-105">If you are a complete beginner with programming or with C#, you might want to visit the [Getting Started with C#](https://www.microsoft.com/net/tutorials/csharp/getting-started) interactive tutorial, where no prior programming knowledge is required.</span></span>  
  
 <span data-ttu-id="c1fbd-106">Pour plus d’informations sur des mots clés, opérateurs et directives de préprocesseur en particulier, consultez la page [Informations de référence sur C#](../../csharp/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="c1fbd-106">For information about specific keywords, operators and preprocessor directives, see [C# Reference](../../csharp/language-reference/index.md).</span></span> <span data-ttu-id="c1fbd-107">Pour plus d’informations sur la spécification du langage C#, consultez la page [Spécification du langage C#](../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c1fbd-107">For information about the C# Language Specification, see [C# Language Specification](../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="program-sections"></a><span data-ttu-id="c1fbd-108">Sections du programme</span><span class="sxs-lookup"><span data-stu-id="c1fbd-108">Program sections</span></span>

[<span data-ttu-id="c1fbd-109">À l’intérieur d’un programme C#</span><span class="sxs-lookup"><span data-stu-id="c1fbd-109">Inside a C# Program</span></span>](../../csharp/programming-guide/inside-a-program/index.md)  
  
[<span data-ttu-id="c1fbd-110">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c1fbd-110">Main() and Command-Line Arguments</span></span>](../../csharp/programming-guide/main-and-command-args/index.md)  
 
## <a name="language-sections"></a><span data-ttu-id="c1fbd-111">Sections du langage</span><span class="sxs-lookup"><span data-stu-id="c1fbd-111">Language Sections</span></span>  
[<span data-ttu-id="c1fbd-112">Instructions, expressions et opérateurs</span><span class="sxs-lookup"><span data-stu-id="c1fbd-112">Statements, Expressions, and Operators</span></span>](../../csharp/programming-guide/statements-expressions-operators/index.md)  

 [<span data-ttu-id="c1fbd-113">Types</span><span class="sxs-lookup"><span data-stu-id="c1fbd-113">Types</span></span>](../../csharp/programming-guide/types/index.md)  

 [<span data-ttu-id="c1fbd-114">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="c1fbd-114">Classes and Structs</span></span>](../../csharp/programming-guide/classes-and-structs/index.md)  
  
 [<span data-ttu-id="c1fbd-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c1fbd-115">Interfaces</span></span>](../../csharp/programming-guide/interfaces/index.md)  

 [<span data-ttu-id="c1fbd-116">Types d’énumération</span><span class="sxs-lookup"><span data-stu-id="c1fbd-116">Enumeration Types</span></span>](../../csharp/programming-guide/enumeration-types.md)  
  
 [<span data-ttu-id="c1fbd-117">Délégués</span><span class="sxs-lookup"><span data-stu-id="c1fbd-117">Delegates</span></span>](../../csharp/programming-guide/delegates/index.md)  
 
 [<span data-ttu-id="c1fbd-118">Tableaux</span><span class="sxs-lookup"><span data-stu-id="c1fbd-118">Arrays</span></span>](../../csharp/programming-guide/arrays/index.md)  
  
 [<span data-ttu-id="c1fbd-119">Chaînes</span><span class="sxs-lookup"><span data-stu-id="c1fbd-119">Strings</span></span>](../../csharp/programming-guide/strings/index.md)  
  
 [<span data-ttu-id="c1fbd-120">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c1fbd-120">Properties</span></span>](../../csharp/programming-guide/classes-and-structs/properties.md)  
  
 [<span data-ttu-id="c1fbd-121">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="c1fbd-121">Indexers</span></span>](../../csharp/programming-guide/indexers/index.md)  
  
 [<span data-ttu-id="c1fbd-122">Événements</span><span class="sxs-lookup"><span data-stu-id="c1fbd-122">Events</span></span>](../../csharp/programming-guide/events/index.md)  
  
 [<span data-ttu-id="c1fbd-123">Génériques</span><span class="sxs-lookup"><span data-stu-id="c1fbd-123">Generics</span></span>](../../csharp/programming-guide/generics/index.md)  
  
 [<span data-ttu-id="c1fbd-124">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="c1fbd-124">Iterators</span></span>](../../csharp/programming-guide/concepts/iterators.md)
  
 [<span data-ttu-id="c1fbd-125">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="c1fbd-125">LINQ Query Expressions</span></span>](../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="c1fbd-126">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="c1fbd-126">Lambda Expressions</span></span>](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
 [<span data-ttu-id="c1fbd-127">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c1fbd-127">Namespaces</span></span>](../../csharp/programming-guide/namespaces/index.md)  
  
 [<span data-ttu-id="c1fbd-128">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="c1fbd-128">Nullable Types</span></span>](../../csharp/programming-guide/nullable-types/index.md)  
  
 [<span data-ttu-id="c1fbd-129">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="c1fbd-129">Unsafe Code and Pointers</span></span>](../../csharp/programming-guide/unsafe-code-pointers/index.md)  
  
 [<span data-ttu-id="c1fbd-130">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="c1fbd-130">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
  
## <a name="platform-sections"></a><span data-ttu-id="c1fbd-131">Sections de la plateforme</span><span class="sxs-lookup"><span data-stu-id="c1fbd-131">Platform Sections</span></span>  
 [<span data-ttu-id="c1fbd-132">Domaines d’application (C# et Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1fbd-132">Application Domains (C# and Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/1bc2939a-79db-4a4a-a677-4a2ce6de2b1e)  
  
 [<span data-ttu-id="c1fbd-133">Assemblys et le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c1fbd-133">Assemblies and the Global Assembly Cache</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
  
 [<span data-ttu-id="c1fbd-134">Attributs</span><span class="sxs-lookup"><span data-stu-id="c1fbd-134">Attributes</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)  
  
 [<span data-ttu-id="c1fbd-135">Collections</span><span class="sxs-lookup"><span data-stu-id="c1fbd-135">Collections</span></span>](../../csharp/programming-guide/concepts/collections.md)  
  
 [<span data-ttu-id="c1fbd-136">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="c1fbd-136">Exceptions and Exception Handling</span></span>](../../csharp/programming-guide/exceptions/index.md)  
  
 [<span data-ttu-id="c1fbd-137">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c1fbd-137">File System and the Registry (C# Programming Guide)</span></span>](../../csharp/programming-guide/file-system/index.md)  
  
 [<span data-ttu-id="c1fbd-138">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c1fbd-138">Interoperability</span></span>](../../csharp/programming-guide/interop/index.md)  
  
 [<span data-ttu-id="c1fbd-139">Réflexion</span><span class="sxs-lookup"><span data-stu-id="c1fbd-139">Reflection</span></span>](../../csharp/programming-guide/concepts/reflection.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1fbd-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1fbd-140">See Also</span></span>  
 <span data-ttu-id="c1fbd-141">[Informations de référence sur C#](../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1fbd-141">[C# Reference](../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="c1fbd-142">C#</span><span class="sxs-lookup"><span data-stu-id="c1fbd-142">C#</span></span>](../../csharp/index.md)

