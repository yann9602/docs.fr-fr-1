---
title: Indexeurs (Guide de programmation C#)
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
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
ms.openlocfilehash: 784308f3073114cd0c07cf15edae527a2654edec
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="c3e43-102">Indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c3e43-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="c3e43-103">Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux.</span><span class="sxs-lookup"><span data-stu-id="c3e43-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="c3e43-104">La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="c3e43-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="c3e43-105">Les indexeurs s’apparentent aux [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="c3e43-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="c3e43-106">L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="c3e43-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="c3e43-107">La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="c3e43-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 <span data-ttu-id="c3e43-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3e43-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3e43-109">Pour plus d’exemples, consultez [Rubriques connexes](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="c3e43-109">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="c3e43-110">Définitions de corps d'expression</span><span class="sxs-lookup"><span data-stu-id="c3e43-110">Expression Body Definitions</span></span>  
 
<span data-ttu-id="c3e43-111">Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur.</span><span class="sxs-lookup"><span data-stu-id="c3e43-111">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="c3e43-112">Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="c3e43-112">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="c3e43-113">À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c3e43-113">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

<span data-ttu-id="c3e43-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3e43-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span></span>  

<span data-ttu-id="c3e43-115">Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="c3e43-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="c3e43-116">À partir de C# 7, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="c3e43-116">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="c3e43-117">Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="c3e43-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="c3e43-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c3e43-118">For example:</span></span>

<span data-ttu-id="c3e43-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3e43-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span></span>  
  
## <a name="indexers-overview"></a><span data-ttu-id="c3e43-120">Vue d'ensemble des indexeurs</span><span class="sxs-lookup"><span data-stu-id="c3e43-120">Indexers Overview</span></span>  
  
-   <span data-ttu-id="c3e43-121">Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="c3e43-121">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="c3e43-122">Un accesseur `get` retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="c3e43-122">A `get` accessor returns a value.</span></span> <span data-ttu-id="c3e43-123">Un accesseur `set` affecte une valeur.</span><span class="sxs-lookup"><span data-stu-id="c3e43-123">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="c3e43-124">Le mot clé [this](../../../csharp/language-reference/keywords/this.md) est utilisé pour définir l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="c3e43-124">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="c3e43-125">Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.</span><span class="sxs-lookup"><span data-stu-id="c3e43-125">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="c3e43-126">Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.</span><span class="sxs-lookup"><span data-stu-id="c3e43-126">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="c3e43-127">Les indexeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="c3e43-127">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="c3e43-128">Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="c3e43-128">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <span data-ttu-id="c3e43-129"><a name="BKMK_RelatedSections"></a> Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c3e43-129"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="c3e43-130">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="c3e43-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="c3e43-131">Indexeurs dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="c3e43-131">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="c3e43-132">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="c3e43-132">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="c3e43-133">Restriction d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="c3e43-133">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c3e43-134">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c3e43-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3e43-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3e43-135">See Also</span></span>  
 <span data-ttu-id="c3e43-136">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3e43-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="c3e43-137">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c3e43-137">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

