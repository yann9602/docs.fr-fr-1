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
# <a name="gt-operator-c-reference"></a>=&gt;, opérateur (Informations de référence sur C#)

Le `=>` opérateur peut être utilisé de deux façons dans c# :

- Comme le [opérateur lambda](#lamba-operator) dans un [expression lambda](../../lambda-expressions.md), elle sépare les variables d’entrée à partir du corps du lambda.
 
- Dans un [définition du corps d’expression](#expression-body-definition), elle sépare un nom de membre de l’implémentation d’un membre. 

## <a name="lambda-operator"></a>Opérateur lambda

Le jeton `=>` est appelé opérateur lambda. Il est utilisé dans les *expressions lambda* pour séparer les variables d’entrée du côté gauche et le corps lambda du côté droit. Les expressions lambda sont des expressions inline similaires aux méthodes anonymes, mais plus flexibles ; elles sont largement utilisées dans les requêtes LINQ qui sont exprimées dans la syntaxe des méthodes. Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 L’exemple suivant montre deux façons de rechercher et d’afficher la longueur de la chaîne la plus courte dans un tableau de chaînes. La première partie de l’exemple applique une expression lambda (`w => w.Length`) à chaque élément du tableau `words`, puis utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour rechercher la plus petite longueur. À titre de comparaison, la deuxième partie de l’exemple montre une solution plus longue qui utilise la syntaxe de requête à faire la même chose.  
  
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
  
### <a name="remarks"></a>Remarques  
 L’opérateur `=>` a la même priorité que l’opérateur d’affectation (`=`) et est associatif à droite.  
  
 Vous pouvez spécifier explicitement le type de la variable d’entrée ou laisser le compilateur l’inférer. Dans les deux cas, la variable est fortement typée à la compilation. Quand vous spécifiez un type, vous devez placer le nom de type et le nom de la variable entre parenthèses, comme le montre l’exemple suivant.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment écrire une expression lambda pour la surcharge de l’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>, qui prend deux arguments. Comme l’expression lambda a plusieurs paramètres, les paramètres doivent être placés entre parenthèses. Le deuxième paramètre, `index`, représente l’index de l’élément actif dans la collection. L’expression `Where` retourne toutes les chaînes dont les longueurs sont inférieures à leurs emplacements d’index dans le tableau.  
  
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
## <a name="expression-body-definition"></a>Définition du corps d’expression

Une définition de corps d’expression fournit l’implémentation d’un membre dans un formulaire hautement condensée, accessible en lecture. Il présente la syntaxe générale suivante :

```csharp
member => expression;
```
où *expression* est une expression valide. Notez que *expression* peut être un *expression d’instruction* uniquement si le membre de retour du type est `void`, ou si le membre est un constructeur ou un finaliseur.

Définitions de corps d’expression pour les méthodes et les instructions get de propriété sont pris en charge dans c# 6. Définitions de corps d’expression pour les constructeurs, les finaliseurs, instructions set de propriété et indexeurs sont pris en charge à partir de C# 7.

Voici une définition de corps d’expression pour un `Person.ToString` méthode :

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Il s’agit d’une version raccourcie de la définition de méthode suivante :

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Pour plus d’informations sur les définitions de corps d’expression, consultez [pulvérisés d’Expression de membres](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Voir aussi  
[Informations de référence sur C#](../../../csharp/language-reference/index.md)   
[Guide de programmation C#](../../../csharp/programming-guide/index.md)   
[Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
[Membres de l’expression-pulvérisés](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).