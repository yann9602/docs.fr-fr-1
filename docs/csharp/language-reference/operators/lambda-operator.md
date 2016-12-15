---
title: "Op&#233;rateur =&gt; (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "=>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "opérateur lamdba [C#]"
  - "opérateur => [C#]"
  - "expressions lambda [C#], opérateur =>"
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Op&#233;rateur =&gt; (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le jeton `=>` est appelé « opérateur lambda ».  Il est utilisé dans *les expressions lambda* pour séparer les variables d'entrée à gauche du corps lambda à droite.  Les expressions lambda sont des expressions inline semblables aux méthodes anonymes, mais plus souples ; elles sont largement utilisées dans les requêtes LINQ qui sont exprimées dans la syntaxe de méthode.  Pour plus d'informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 L'exemple suivant illustre deux méthodes de recherche et afficher la longueur de la chaîne la plus courte d'un tableau de chaînes.  La première partie de l'exemple applique une expression lambda \(`w => w.Length`\) à chaque élément du tableau d' `words` puis utilise la méthode de <xref:System.Linq.Enumerable.Min%2A> pour rechercher la plus petite taille.  Pour la comparaison, la deuxième partie de l'exemple indique qu'une plus longue solution que syntaxe de requête d'utilisations faisait le même.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## Notes  
 L'opérateur `=>` a la même priorité que l'opérateur d'assignation \(`=`\) et est associatif à droite.  
  
 Vous pouvez spécifier le type de la variable d'entrée explicitement ou laissez le compilateur déduire ; dans les deux cas, la variable est fortement typée au moment de la compilation.  Lorsque vous spécifiez un type, vous devez attacher le nom de type et le nom de variable entre parenthèses, comme indiqué dans l'exemple suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## Exemple  
 L'exemple suivant montre comment écrire une expression lambda pour la surcharge de l' <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> d'opérateur de requête standard qui prend deux arguments.  Étant donné que l'expression lambda a plusieurs paramètres, les paramètres doivent être placés entre parenthèses.  Le deuxième paramètre, `index`, représente l'index de l'élément actuel dans la collection.  L'expression d' `Where` retourne toutes les chaînes dont les longueurs sont inférieures leurs emplacements d'index dans le tableau.  
  
```c#  
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
  
    // Compare the following code, which arrives at the same list of short  
    // digits but takes more work to get there.  
    Console.WriteLine("\nExample that uses a for loop:");  
    List<string> shortDigits2 = new List<string>();  
    for (var i = 0; i < digits.Length; i++)  
    {  
        if (digits[i].Length < i)  
            shortDigits2.Add(digits[i]);  
    }  
  
    foreach (var d in shortDigits2)  
    {  
        Console.WriteLine(d);  
    }  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
  
    // Example that uses a for loop:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)