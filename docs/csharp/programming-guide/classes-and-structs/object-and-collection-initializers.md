---
title: "Initialiseurs d’objet et de collection (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: 27
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
ms.openlocfilehash: c4144f383d539129b4e03d5cad262e5a7b9e6b34
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="2db85-102">Initialiseurs d’objet et de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2db85-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="2db85-103">Les initialiseurs d'objet vous permettent d'affecter des valeurs aux champs ou propriétés accessibles d'un objet, au moment de sa création, sans devoir appeler un constructeur suivi de ses lignes d'instructions d'assignation.</span><span class="sxs-lookup"><span data-stu-id="2db85-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="2db85-104">La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre (et la syntaxe de parenthèses).</span><span class="sxs-lookup"><span data-stu-id="2db85-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="2db85-105">L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2db85-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="2db85-106">Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`.</span><span class="sxs-lookup"><span data-stu-id="2db85-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="2db85-107">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2db85-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="2db85-108">[!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-108">[!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]</span></span>  
  
 <span data-ttu-id="2db85-109">[!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-109">[!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]</span></span>  
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="2db85-110">Initialiseurs d'objet avec des types anonymes</span><span class="sxs-lookup"><span data-stu-id="2db85-110">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="2db85-111">Les initialiseurs d’objet peuvent être utilisés dans tous les contextes, mais ils sont particulièrement utiles dans les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2db85-111">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="2db85-112">Les expressions de requête utilisent souvent des [types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), qui peuvent uniquement être initialisés à l’aide d’un initialiseur d’objet, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="2db85-112">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="2db85-113">Les types anonymes permettent à la clause `select` d’une expression de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de transformer les objets de la séquence d’origine en objets dont la valeur et la forme peuvent différer de l’original.</span><span class="sxs-lookup"><span data-stu-id="2db85-113">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="2db85-114">Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="2db85-114">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="2db85-115">Dans l'exemple suivant, supposons qu'un objet de produit (`p`) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.</span><span class="sxs-lookup"><span data-stu-id="2db85-115">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 <span data-ttu-id="2db85-116">[!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-116">[!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]</span></span>  
  
 <span data-ttu-id="2db85-117">Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="2db85-117">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="2db85-118">Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l'objet d'origine.</span><span class="sxs-lookup"><span data-stu-id="2db85-118">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="2db85-119">Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.</span><span class="sxs-lookup"><span data-stu-id="2db85-119">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="2db85-120">Initialiseurs d'objets avec les types Nullable</span><span class="sxs-lookup"><span data-stu-id="2db85-120">Object initializers with nullable types</span></span>  
 <span data-ttu-id="2db85-121">C'est une erreur au moment de la compilation que d'utiliser un initialiseur d'objet avec un struct Nullable.</span><span class="sxs-lookup"><span data-stu-id="2db85-121">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="2db85-122">Initialiseurs de collection</span><span class="sxs-lookup"><span data-stu-id="2db85-122">Collection initializers</span></span>  
 <span data-ttu-id="2db85-123">Les initialiseurs de collection vous permettent de spécifier un ou plusieurs initialiseurs d’élément quand vous initialisez un type de collection qui implémente <xref:System.Collections.IEnumerable> et qui utilise `Add` comme méthode d’instance ou méthode d’extension avec la signature appropriée.</span><span class="sxs-lookup"><span data-stu-id="2db85-123">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="2db85-124">Les initialiseurs d'élément peuvent être une valeur simple, une expression ou un initialiseur d'objet.</span><span class="sxs-lookup"><span data-stu-id="2db85-124">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="2db85-125">En utilisant un initialiseur de collection, il n'est pas nécessaire de spécifier plusieurs appels à la méthode `Add` de la classe dans votre code source ; le compilateur ajoute les appels.</span><span class="sxs-lookup"><span data-stu-id="2db85-125">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="2db85-126">Les exemples suivants présentent deux initialiseurs de collection simples :</span><span class="sxs-lookup"><span data-stu-id="2db85-126">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="2db85-127">L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="2db85-127">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="2db85-128">Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="2db85-128">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 <span data-ttu-id="2db85-129">[!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-129">[!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]</span></span>  
  
 <span data-ttu-id="2db85-130">Vous pouvez spécifier [Null](../../../csharp/language-reference/keywords/null.md) comme élément dans un initialiseur de collection si la méthode `Add` de la collection l’autorise.</span><span class="sxs-lookup"><span data-stu-id="2db85-130">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 <span data-ttu-id="2db85-131">[!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-131">[!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]</span></span>  
  
 <span data-ttu-id="2db85-132">Vous pouvez spécifier des éléments indexés si la collection prend en charge l’indexation.</span><span class="sxs-lookup"><span data-stu-id="2db85-132">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a><span data-ttu-id="2db85-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="2db85-133">Example</span></span>  
 <span data-ttu-id="2db85-134">[!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2db85-134">[!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db85-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db85-135">See Also</span></span>  
 <span data-ttu-id="2db85-136">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2db85-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2db85-137">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="2db85-137">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="2db85-138">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="2db85-138">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

