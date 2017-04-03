---
title: "=&gt;, opérateur (Informations de référence sur C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a75967e61d2c674e87e321de1fb6e4062cca4f19
ms.lasthandoff: 03/13/2017

---
# <a name="gt-operator-c-reference"></a>=&gt;, opérateur (Informations de référence sur C#)
Le jeton `=>` est appelé opérateur lambda. Il est utilisé dans les *expressions lambda* pour séparer les variables d’entrée du côté gauche et le corps lambda du côté droit. Les expressions lambda sont des expressions inline similaires aux méthodes anonymes, mais plus flexibles ; elles sont largement utilisées dans les requêtes LINQ qui sont exprimées dans la syntaxe des méthodes. Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 L’exemple suivant montre deux façons de rechercher et d’afficher la longueur de la chaîne la plus courte dans un tableau de chaînes. La première partie de l’exemple applique une expression lambda (`w => w.Length`) à chaque élément du tableau `words` puis utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour déterminer la plus petite longueur. À titre de comparaison, la deuxième partie de l’exemple montre une solution plus longue qui utilise la syntaxe de requête à faire la même chose.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="remarks"></a>Remarques  
 L’opérateur `=>` a la même priorité que l’opérateur d’affectation (`=`) et est associatif à droite.  
  
 Vous pouvez spécifier explicitement le type de la variable d’entrée ou laisser le compilateur l’inférer. Dans les deux cas, la variable est fortement typée à la compilation. Quand vous spécifiez un type, vous devez placer le nom de type et le nom de la variable entre parenthèses, comme le montre l’exemple suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment écrire une expression lambda pour la surcharge de l’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName>, qui prend deux arguments. Comme l’expression lambda a plusieurs paramètres, les paramètres doivent être placés entre parenthèses. Le deuxième paramètre, `index`, représente l’index de l’élément actif dans la collection. L’expression `Where` retourne toutes les chaînes dont les longueurs sont inférieures à leurs emplacements d’index dans le tableau.  
  
```cs  
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
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
