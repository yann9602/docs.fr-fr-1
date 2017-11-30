---
title: "=&gt;, opérateur (Informations de référence sur C#)"
ms.date: 10/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="8ed91-102">=&gt;, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="8ed91-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="8ed91-103">Le `=>` opérateur peut être utilisé de deux façons dans c# :</span><span class="sxs-lookup"><span data-stu-id="8ed91-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="8ed91-104">Comme le [opérateur lambda](#lamba-operator) dans un [expression lambda](../../lambda-expressions.md), elle sépare les variables d’entrée à partir du corps du lambda.</span><span class="sxs-lookup"><span data-stu-id="8ed91-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="8ed91-105">Dans un [définition du corps d’expression](#expression-body-definition), elle sépare un nom de membre de l’implémentation d’un membre.</span><span class="sxs-lookup"><span data-stu-id="8ed91-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="8ed91-106">Opérateur lambda</span><span class="sxs-lookup"><span data-stu-id="8ed91-106">Lambda operator</span></span>

<span data-ttu-id="8ed91-107">Le jeton `=>` est appelé opérateur lambda.</span><span class="sxs-lookup"><span data-stu-id="8ed91-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="8ed91-108">Il est utilisé dans les *expressions lambda* pour séparer les variables d’entrée du côté gauche et le corps lambda du côté droit.</span><span class="sxs-lookup"><span data-stu-id="8ed91-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="8ed91-109">Les expressions lambda sont des expressions inline similaires aux méthodes anonymes, mais plus flexibles ; elles sont largement utilisées dans les requêtes LINQ qui sont exprimées dans la syntaxe des méthodes.</span><span class="sxs-lookup"><span data-stu-id="8ed91-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="8ed91-110">Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8ed91-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="8ed91-111">L’exemple suivant montre deux façons de rechercher et d’afficher la longueur de la chaîne la plus courte dans un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="8ed91-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="8ed91-112">La première partie de l’exemple applique une expression lambda (`w => w.Length`) à chaque élément du tableau `words`, puis utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour rechercher la plus petite longueur.</span><span class="sxs-lookup"><span data-stu-id="8ed91-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="8ed91-113">À titre de comparaison, la deuxième partie de l’exemple montre une solution plus longue qui utilise la syntaxe de requête à faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="8ed91-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="8ed91-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ed91-114">Remarks</span></span>  
 <span data-ttu-id="8ed91-115">L’opérateur `=>` a la même priorité que l’opérateur d’affectation (`=`) et est associatif à droite.</span><span class="sxs-lookup"><span data-stu-id="8ed91-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="8ed91-116">Vous pouvez spécifier explicitement le type de la variable d’entrée ou laisser le compilateur l’inférer. Dans les deux cas, la variable est fortement typée à la compilation.</span><span class="sxs-lookup"><span data-stu-id="8ed91-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="8ed91-117">Quand vous spécifiez un type, vous devez placer le nom de type et le nom de la variable entre parenthèses, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8ed91-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="8ed91-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ed91-118">Example</span></span>  
 <span data-ttu-id="8ed91-119">L’exemple suivant montre comment écrire une expression lambda pour la surcharge de l’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>, qui prend deux arguments.</span><span class="sxs-lookup"><span data-stu-id="8ed91-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="8ed91-120">Comme l’expression lambda a plusieurs paramètres, les paramètres doivent être placés entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="8ed91-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="8ed91-121">Le deuxième paramètre, `index`, représente l’index de l’élément actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="8ed91-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="8ed91-122">L’expression `Where` retourne toutes les chaînes dont les longueurs sont inférieures à leurs emplacements d’index dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="8ed91-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="8ed91-123">Définition du corps d’expression</span><span class="sxs-lookup"><span data-stu-id="8ed91-123">Expression body definition</span></span>

<span data-ttu-id="8ed91-124">Une définition de corps d’expression fournit l’implémentation d’un membre dans un formulaire hautement condensée, accessible en lecture.</span><span class="sxs-lookup"><span data-stu-id="8ed91-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="8ed91-125">Il présente la syntaxe générale suivante :</span><span class="sxs-lookup"><span data-stu-id="8ed91-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="8ed91-126">où *expression* est une expression valide.</span><span class="sxs-lookup"><span data-stu-id="8ed91-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="8ed91-127">Notez que *expression* peut être un *expression d’instruction* uniquement si le membre de retour du type est `void`, ou si le membre est un constructeur ou un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="8ed91-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="8ed91-128">Définitions de corps d’expression pour les méthodes et les instructions get de propriété sont pris en charge dans c# 6.</span><span class="sxs-lookup"><span data-stu-id="8ed91-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="8ed91-129">Définitions de corps d’expression pour les constructeurs, les finaliseurs, instructions set de propriété et indexeurs sont pris en charge à partir de C# 7.</span><span class="sxs-lookup"><span data-stu-id="8ed91-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="8ed91-130">Voici une définition de corps d’expression pour un `Person.ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="8ed91-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="8ed91-131">Il s’agit d’une version raccourcie de la définition de méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="8ed91-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="8ed91-132">Pour plus d’informations sur les définitions de corps d’expression, consultez [pulvérisés d’Expression de membres](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="8ed91-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ed91-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ed91-133">See Also</span></span>  
<span data-ttu-id="8ed91-134">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ed91-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="8ed91-135">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ed91-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="8ed91-136">[Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="8ed91-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="8ed91-137">[Membres de l’expression-pulvérisés](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="8ed91-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>