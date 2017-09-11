---
title: "=&gt;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
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
ms.openlocfilehash: 45d4753724ed094408e8cbc5353998a67071b0e4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="e662b-102">=&gt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e662b-102">=&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="e662b-103">Le jeton `=>` est appelé opérateur lambda.</span><span class="sxs-lookup"><span data-stu-id="e662b-103">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="e662b-104">Il est utilisé dans les *expressions lambda* pour séparer les variables d’entrée du côté gauche et le corps lambda du côté droit.</span><span class="sxs-lookup"><span data-stu-id="e662b-104">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="e662b-105">Les expressions lambda sont des expressions inline similaires aux méthodes anonymes, mais plus flexibles ; elles sont largement utilisées dans les requêtes LINQ qui sont exprimées dans la syntaxe des méthodes.</span><span class="sxs-lookup"><span data-stu-id="e662b-105">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="e662b-106">Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e662b-106">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e662b-107">L’exemple suivant montre deux façons de rechercher et d’afficher la longueur de la chaîne la plus courte dans un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e662b-107">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="e662b-108">La première partie de l’exemple applique une expression lambda (`w => w.Length`) à chaque élément du tableau `words`, puis utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour rechercher la plus petite longueur.</span><span class="sxs-lookup"><span data-stu-id="e662b-108">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="e662b-109">À titre de comparaison, la deuxième partie de l’exemple montre une solution plus longue qui utilise la syntaxe de requête à faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="e662b-109">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="e662b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e662b-110">Remarks</span></span>  
 <span data-ttu-id="e662b-111">L’opérateur `=>` a la même priorité que l’opérateur d’affectation (`=`) et est associatif à droite.</span><span class="sxs-lookup"><span data-stu-id="e662b-111">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="e662b-112">Vous pouvez spécifier explicitement le type de la variable d’entrée ou laisser le compilateur l’inférer. Dans les deux cas, la variable est fortement typée à la compilation.</span><span class="sxs-lookup"><span data-stu-id="e662b-112">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="e662b-113">Quand vous spécifiez un type, vous devez placer le nom de type et le nom de la variable entre parenthèses, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e662b-113">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
## <a name="example"></a><span data-ttu-id="e662b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="e662b-114">Example</span></span>  
 <span data-ttu-id="e662b-115">L’exemple suivant montre comment écrire une expression lambda pour la surcharge de l’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName>, qui prend deux arguments.</span><span class="sxs-lookup"><span data-stu-id="e662b-115">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> that takes two arguments.</span></span> <span data-ttu-id="e662b-116">Comme l’expression lambda a plusieurs paramètres, les paramètres doivent être placés entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="e662b-116">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="e662b-117">Le deuxième paramètre, `index`, représente l’index de l’élément actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e662b-117">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="e662b-118">L’expression `Where` retourne toutes les chaînes dont les longueurs sont inférieures à leurs emplacements d’index dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e662b-118">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e662b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e662b-119">See Also</span></span>  
 <span data-ttu-id="e662b-120">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e662b-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e662b-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e662b-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="e662b-122">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="e662b-122">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

