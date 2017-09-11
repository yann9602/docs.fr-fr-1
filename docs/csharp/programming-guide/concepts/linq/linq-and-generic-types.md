---
title: "LINQ et types génériques (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 177db64491d58b31ca50cef0bb2eda8c2cb65078
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="linq-and-generic-types-c"></a><span data-ttu-id="ebd06-102">LINQ et types génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd06-102">LINQ and Generic Types (C#)</span></span>
<span data-ttu-id="ebd06-103">Les requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sont basées sur des types génériques, qui ont été introduits dans la version 2.0 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebd06-103">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries are based on generic types, which were introduced in version 2.0 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="ebd06-104">Vous ne devez pas avoir une connaissance approfondie des génériques avant de commencer à écrire des requêtes.</span><span class="sxs-lookup"><span data-stu-id="ebd06-104">You do not need an in-depth knowledge of generics before you can start writing queries.</span></span> <span data-ttu-id="ebd06-105">Il peut cependant être important de comprendre deux concepts de base :</span><span class="sxs-lookup"><span data-stu-id="ebd06-105">However, you may want to understand two basic concepts:</span></span>  
  
1.  <span data-ttu-id="ebd06-106">Quand vous créez une instance d’une classe de collection générique comme <xref:System.Collections.Generic.List%601>, vous remplacez le « T » par le type des objets contenus dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ebd06-106">When you create an instance of a generic collection class such as <xref:System.Collections.Generic.List%601>, you replace the "T" with the type of objects that the list will hold.</span></span> <span data-ttu-id="ebd06-107">Par exemple, une liste de chaînes est exprimée sous la forme `List<string>`, et une liste d’objets `Customer` est exprimée sous la forme `List<Customer>`.</span><span class="sxs-lookup"><span data-stu-id="ebd06-107">For example, a list of strings is expressed as `List<string>`, and a list of `Customer` objects is expressed as `List<Customer>`.</span></span> <span data-ttu-id="ebd06-108">Une liste générique est fortement typée et offre de nombreux avantages par rapport aux collections qui stockent leurs éléments en tant que <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ebd06-108">A generic list is strongly typed and provides many benefits over collections that store their elements as <xref:System.Object>.</span></span> <span data-ttu-id="ebd06-109">Si vous essayez d’ajouter un `Customer` à un `List<string>`, vous obtenez une erreur à la compilation.</span><span class="sxs-lookup"><span data-stu-id="ebd06-109">If you try to add a `Customer` to a `List<string>`, you will get an error at compile time.</span></span> <span data-ttu-id="ebd06-110">Il est facile d’utiliser des collections génériques, car vous ne devez pas effectuer un cast de type à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ebd06-110">It is easy to use generic collections because you do not have to perform run-time type-casting.</span></span>  
  
2.  <span data-ttu-id="ebd06-111"><xref:System.Collections.Generic.IEnumerable%601> est l’interface qui permet l’énumération des classes de collection génériques avec l’instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="ebd06-111"><xref:System.Collections.Generic.IEnumerable%601> is the interface that enables generic collection classes to be enumerated by using the `foreach` statement.</span></span> <span data-ttu-id="ebd06-112">Les classes de collection génériques prennent en charge <xref:System.Collections.Generic.IEnumerable%601> de la même façon que les classes de collection non génériques telles que <xref:System.Collections.ArrayList> prennent en charge <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="ebd06-112">Generic collection classes support <xref:System.Collections.Generic.IEnumerable%601> just as non-generic collection classes such as <xref:System.Collections.ArrayList> support <xref:System.Collections.IEnumerable>.</span></span>  
  
 <span data-ttu-id="ebd06-113">Pour plus d’informations sur les génériques, consultez [Génériques](../../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebd06-113">For more information about generics, see [Generics](../../../../csharp/programming-guide/generics/index.md).</span></span>  
  
## <a name="ienumerablet-variables-in-linq-queries"></a><span data-ttu-id="ebd06-114">Variables IEnumerable<T\> dans les requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="ebd06-114">IEnumerable<T\> variables in LINQ Queries</span></span>  
 <span data-ttu-id="ebd06-115">Les variables de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sont de type <xref:System.Collections.Generic.IEnumerable%601> ou d’un type dérivé tel que <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="ebd06-115">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query variables are typed as <xref:System.Collections.Generic.IEnumerable%601> or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="ebd06-116">Quand vous voyez une variable de requête typée en `IEnumerable<Customer>`, cela signifie simplement que la requête génère à l’exécution une séquence de zéro ou plusieurs objets `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ebd06-116">When you see a query variable that is typed as `IEnumerable<Customer>`, it just means that the query, when it is executed, will produce a sequence of zero or more `Customer` objects.</span></span>  
  
 <span data-ttu-id="ebd06-117">[!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebd06-117">[!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]</span></span>  
  
 <span data-ttu-id="ebd06-118">Pour plus d’informations, consultez [Relations des types dans des opérations de requête LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ebd06-118">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a><span data-ttu-id="ebd06-119">Laisser le compilateur gérer les déclarations de types génériques</span><span class="sxs-lookup"><span data-stu-id="ebd06-119">Letting the Compiler Handle Generic Type Declarations</span></span>  
 <span data-ttu-id="ebd06-120">Si vous préférez, vous pouvez éviter une syntaxe générique en utilisant le mot clé [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="ebd06-120">If you prefer, you can avoid generic syntax by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword.</span></span> <span data-ttu-id="ebd06-121">Le mot clé `var` indique au compilateur d’inférer le type d’une variable de requête en examinant la source de données spécifiée dans la clause `from`.</span><span class="sxs-lookup"><span data-stu-id="ebd06-121">The `var` keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the `from` clause.</span></span> <span data-ttu-id="ebd06-122">L’exemple suivant génère le même code compilé que l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="ebd06-122">The following example produces the same compiled code as the previous example:</span></span>  
  
 <span data-ttu-id="ebd06-123">[!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebd06-123">[!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]</span></span>  
  
 <span data-ttu-id="ebd06-124">Le mot clé `var` est utile quand le type de la variable est évident ou quand il est particulièrement important de spécifier explicitement des types génériques imbriqués, comme ceux qui sont produits par des requêtes de groupe.</span><span class="sxs-lookup"><span data-stu-id="ebd06-124">The `var` keyword is useful when the type of the variable is obvious or when it is not that important to explicitly specify nested generic types such as those that are produced by group queries.</span></span> <span data-ttu-id="ebd06-125">D’une façon générale, si vous utilisez `var`, sachez qu’il peut rendre votre code plus difficile à lire par d’autres développeurs.</span><span class="sxs-lookup"><span data-stu-id="ebd06-125">In general, we recommend that if you use `var`, realize that it can make your code more difficult for others to read.</span></span> <span data-ttu-id="ebd06-126">Pour plus d’informations, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ebd06-126">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd06-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebd06-127">See Also</span></span>  
 <span data-ttu-id="ebd06-128">[Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="ebd06-128">[Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 [<span data-ttu-id="ebd06-129">Génériques</span><span class="sxs-lookup"><span data-stu-id="ebd06-129">Generics</span></span>](../../../../csharp/programming-guide/generics/index.md)

