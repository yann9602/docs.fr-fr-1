---
title: "Fonctionnalités C# qui prennent en charge LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="b7971-102">Fonctionnalités C# qui prennent en charge LINQ</span><span class="sxs-lookup"><span data-stu-id="b7971-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="b7971-103">La section suivante présente de nouvelles constructions de langage qui sont apparues avec C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="b7971-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="b7971-104">Même si ces nouvelles fonctionnalités sont toutes plus ou moins utilisées avec les requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], elles ne sont pas limitées à [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] et peuvent être utilisées dans n’importe quel contexte.</span><span class="sxs-lookup"><span data-stu-id="b7971-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="b7971-105">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="b7971-105">Query Expressions</span></span>  
 <span data-ttu-id="b7971-106">Les expressions de requête utilisent une syntaxe déclarative similaire à SQL ou XQuery pour interroger les collections IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="b7971-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="b7971-107">Au moment de la compilation, la syntaxe de requête est convertie en appels de méthode à l’implémentation de méthodes d’extension d’opérateur de requête standard d’un fournisseur [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7971-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="b7971-108">Les applications contrôlent les opérateurs de requête standard qui se trouvent dans la portée en spécifiant l’espace de noms approprié avec une directive `using`.</span><span class="sxs-lookup"><span data-stu-id="b7971-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="b7971-109">L’expression de requête suivante accepte un tableau de chaînes, regroupe les chaînes qui commencent par le même caractère, puis trie ces groupes de chaînes.</span><span class="sxs-lookup"><span data-stu-id="b7971-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="b7971-110">Pour plus d’informations, consultez [Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="b7971-111">Variables implicitement typées (var)</span><span class="sxs-lookup"><span data-stu-id="b7971-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="b7971-112">Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez utiliser le modificateur [var](../../../../csharp/language-reference/keywords/var.md) pour indiquer au compilateur qu’il doit déduire et assigner le type, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="b7971-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="b7971-113">Les variables déclarées comme `var` sont aussi fortement typées que les variables dont vous spécifiez explicitement le type.</span><span class="sxs-lookup"><span data-stu-id="b7971-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="b7971-114">`var` permet de créer des types anonymes, mais peut être utilisé pour toutes les variables locales.</span><span class="sxs-lookup"><span data-stu-id="b7971-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="b7971-115">Les tableaux peuvent également être déclarés avec un typage implicite.</span><span class="sxs-lookup"><span data-stu-id="b7971-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="b7971-116">Pour plus d’informations, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="b7971-117">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="b7971-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="b7971-118">Les initialiseurs d’objets et de collections permettent d’initialiser un objet sans appeler explicitement un constructeur pour cet objet.</span><span class="sxs-lookup"><span data-stu-id="b7971-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="b7971-119">Les initialiseurs sont généralement utilisés dans les expressions de requête pour projeter la source de données en un nouveau type de données.</span><span class="sxs-lookup"><span data-stu-id="b7971-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="b7971-120">En supposant une classe nommée `Customer` avec les propriétés publiques `Name` et `Phone`, l’initialiseur d’objet peut être utilisé, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b7971-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="b7971-121">Pour plus d’informations, consultez [Initialiseurs d’objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="b7971-122">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="b7971-122">Anonymous Types</span></span>  
 <span data-ttu-id="b7971-123">Un type anonyme est construit par le compilateur et le nom du type est uniquement disponible pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b7971-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="b7971-124">Les types anonymes permettent de regrouper facilement des propriétés de manière temporaire dans un résultat de requête, sans avoir à définir un type nommé distinct.</span><span class="sxs-lookup"><span data-stu-id="b7971-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="b7971-125">Les types anonymes sont initialisés avec une nouvelle expression et un initialiseur d’objet, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="b7971-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="b7971-126">Pour plus d’informations, consultez [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="b7971-127">méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="b7971-127">Extension Methods</span></span>  
 <span data-ttu-id="b7971-128">Une méthode d’extension est une méthode statique qui peut être associée à un type, de manière à être appelée comme une méthode d’instance de ce type.</span><span class="sxs-lookup"><span data-stu-id="b7971-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="b7971-129">Cette fonctionnalité permet d’ajouter de nouvelles méthodes aux types existants sans les modifier.</span><span class="sxs-lookup"><span data-stu-id="b7971-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="b7971-130">Les opérateurs de requête standard sont un ensemble de méthodes d’extension qui fournissent des fonctionnalités de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b7971-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="b7971-131">Pour plus d’informations, consultez la page [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="b7971-132">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="b7971-132">Lambda Expressions</span></span>  
 <span data-ttu-id="b7971-133">Une expression lambda est une fonction inline qui utilise l’opérateur => pour séparer les paramètres d’entrée du corps de la fonction, et qui peut être convertie au moment de la compilation en un délégué ou une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="b7971-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="b7971-134">En programmation [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous rencontrerez des expressions lambda quand vous effectuerez des appels de méthode directs aux opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="b7971-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="b7971-135">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b7971-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b7971-136">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="b7971-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="b7971-137">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="b7971-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="b7971-138">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="b7971-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="b7971-139">Propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="b7971-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="b7971-140">Les propriétés implémentées automatiquement rendent la déclaration de propriétés plus concise.</span><span class="sxs-lookup"><span data-stu-id="b7971-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="b7971-141">Quand vous déclarez une propriété comme indiqué dans l’exemple suivant, le compilateur crée un champ de stockage privé et anonyme, uniquement accessible via les méthodes getter et setter de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b7971-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="b7971-142">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b7971-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7971-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7971-143">See Also</span></span>  
 [<span data-ttu-id="b7971-144">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="b7971-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
