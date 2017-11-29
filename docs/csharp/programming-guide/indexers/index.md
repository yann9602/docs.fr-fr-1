---
title: Indexeurs (Guide de programmation C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: db49a602b83940cab3f87dea17accb92a2be825d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="86403-102">Indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="86403-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="86403-103">Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux.</span><span class="sxs-lookup"><span data-stu-id="86403-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="86403-104">La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="86403-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="86403-105">Les indexeurs s’apparentent aux [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="86403-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="86403-106">L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="86403-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="86403-107">La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="86403-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="86403-108">Pour plus d’exemples, consultez [Rubriques connexes](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="86403-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="86403-109">Définitions de corps d'expression</span><span class="sxs-lookup"><span data-stu-id="86403-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="86403-110">Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur.</span><span class="sxs-lookup"><span data-stu-id="86403-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="86403-111">Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="86403-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="86403-112">À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="86403-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="86403-113">Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="86403-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="86403-114">À partir de C# 7, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="86403-114">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="86403-115">Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="86403-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="86403-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="86403-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="86403-117">Vue d'ensemble des indexeurs</span><span class="sxs-lookup"><span data-stu-id="86403-117">Indexers Overview</span></span>  
  
-   <span data-ttu-id="86403-118">Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="86403-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="86403-119">Un accesseur `get` retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="86403-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="86403-120">Un accesseur `set` affecte une valeur.</span><span class="sxs-lookup"><span data-stu-id="86403-120">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="86403-121">Le mot clé [this](../../../csharp/language-reference/keywords/this.md) est utilisé pour définir l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="86403-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="86403-122">Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.</span><span class="sxs-lookup"><span data-stu-id="86403-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="86403-123">Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.</span><span class="sxs-lookup"><span data-stu-id="86403-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="86403-124">Les indexeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="86403-124">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="86403-125">Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="86403-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <span data-ttu-id="86403-126"><a name="BKMK_RelatedSections"></a> Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="86403-126"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="86403-127">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="86403-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="86403-128">Indexeurs dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="86403-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="86403-129">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="86403-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="86403-130">Restriction d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="86403-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="86403-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="86403-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86403-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86403-132">See Also</span></span>  
 [<span data-ttu-id="86403-133">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="86403-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="86403-134">Propriétés</span><span class="sxs-lookup"><span data-stu-id="86403-134">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
