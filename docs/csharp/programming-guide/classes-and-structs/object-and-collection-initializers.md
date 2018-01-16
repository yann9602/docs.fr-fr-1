---
title: "Initialiseurs d’objet et de collection (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 628f08aaebfa209fc9cb7cfb2b506fc67d5424f9
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="737c4-102">Initialiseurs d’objet et de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="737c4-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="737c4-103">Les initialiseurs d'objet vous permettent d'affecter des valeurs aux champs ou propriétés accessibles d'un objet, au moment de sa création, sans devoir appeler un constructeur suivi de ses lignes d'instructions d'assignation.</span><span class="sxs-lookup"><span data-stu-id="737c4-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="737c4-104">La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre (et la syntaxe de parenthèses).</span><span class="sxs-lookup"><span data-stu-id="737c4-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="737c4-105">L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="737c4-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="737c4-106">Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`.</span><span class="sxs-lookup"><span data-stu-id="737c4-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="737c4-107">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="737c4-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="737c4-108">La syntaxe des initialiseurs d’objet vous permet de créer une instance qui assigne l’objet nouvellement créé, avec ses propriétés, à la variable dans l’assignation.</span><span class="sxs-lookup"><span data-stu-id="737c4-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="737c4-109">Initialiseurs d'objet avec des types anonymes</span><span class="sxs-lookup"><span data-stu-id="737c4-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="737c4-110">Les initialiseurs d’objet peuvent être utilisés dans tous les contextes, mais ils sont particulièrement utiles dans les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="737c4-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="737c4-111">Les expressions de requête utilisent souvent des [types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), qui peuvent uniquement être initialisés à l’aide d’un initialiseur d’objet, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="737c4-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="737c4-112">Les types anonymes permettent à la clause `select` d’une expression de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de transformer les objets de la séquence d’origine en objets dont la valeur et la forme peuvent différer de l’original.</span><span class="sxs-lookup"><span data-stu-id="737c4-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="737c4-113">Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="737c4-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="737c4-114">Dans l'exemple suivant, supposons qu'un objet de produit (`p`) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.</span><span class="sxs-lookup"><span data-stu-id="737c4-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="737c4-115">Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="737c4-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="737c4-116">Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l'objet d'origine.</span><span class="sxs-lookup"><span data-stu-id="737c4-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="737c4-117">Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.</span><span class="sxs-lookup"><span data-stu-id="737c4-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="737c4-118">Initialiseurs d'objets avec les types Nullable</span><span class="sxs-lookup"><span data-stu-id="737c4-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="737c4-119">C'est une erreur au moment de la compilation que d'utiliser un initialiseur d'objet avec un struct Nullable.</span><span class="sxs-lookup"><span data-stu-id="737c4-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="737c4-120">Initialiseurs de collection</span><span class="sxs-lookup"><span data-stu-id="737c4-120">Collection initializers</span></span>  
 <span data-ttu-id="737c4-121">Les initialiseurs de collection vous permettent de spécifier un ou plusieurs initialiseurs d’élément quand vous initialisez un type de collection qui implémente <xref:System.Collections.IEnumerable> et qui utilise `Add` comme méthode d’instance ou méthode d’extension avec la signature appropriée.</span><span class="sxs-lookup"><span data-stu-id="737c4-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="737c4-122">Les initialiseurs d'élément peuvent être une valeur simple, une expression ou un initialiseur d'objet.</span><span class="sxs-lookup"><span data-stu-id="737c4-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="737c4-123">En utilisant un initialiseur de collection, il n'est pas nécessaire de spécifier plusieurs appels à la méthode `Add` de la classe dans votre code source ; le compilateur ajoute les appels.</span><span class="sxs-lookup"><span data-stu-id="737c4-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="737c4-124">Les exemples suivants présentent deux initialiseurs de collection simples :</span><span class="sxs-lookup"><span data-stu-id="737c4-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="737c4-125">L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="737c4-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="737c4-126">Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="737c4-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="737c4-127">Vous pouvez spécifier [Null](../../../csharp/language-reference/keywords/null.md) comme élément dans un initialiseur de collection si la méthode `Add` de la collection l’autorise.</span><span class="sxs-lookup"><span data-stu-id="737c4-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="737c4-128">Vous pouvez spécifier des éléments indexés si la collection prend en charge l’indexation.</span><span class="sxs-lookup"><span data-stu-id="737c4-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="737c4-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="737c4-129">Examples</span></span>

 <span data-ttu-id="737c4-130">L’exemple suivant combine les concepts d’initialiseurs d’objet et de collection.</span><span class="sxs-lookup"><span data-stu-id="737c4-130">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="737c4-131">Comme indiqué dans l’exemple suivant, un objet qui implémente <xref:System.Collections.IEnumerable> contenant une méthode `Add` avec plusieurs paramètres permet la collection d’initialiseurs avec plusieurs éléments dans la liste correspondant à la signature de la méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="737c4-131">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="737c4-132">Les méthodes `Add` peuvent utiliser le mot clé `params` pour sélectionner un nombre variable d’arguments, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="737c4-132">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="737c4-133">Cet exemple montre l’implémentation personnalisée d’un indexeur pour initialiser une collection à l’aide de plusieurs index.</span><span class="sxs-lookup"><span data-stu-id="737c4-133">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="737c4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="737c4-134">See Also</span></span>  
 [<span data-ttu-id="737c4-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="737c4-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="737c4-136">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="737c4-136">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="737c4-137">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="737c4-137">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
