---
title: "Expressions lambda (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressions lambda (C#)"
  - "variables externes (C#)"
  - "lambda-instruction (C#)"
  - "lambda-expression (C#)"
  - "expressions [C#], lambda"
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 64
caps.handback.revision: 64
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Expressions lambda (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression lambda est une [fonction anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que vous pouvez utiliser pour créer des types [délégués](../../../csharp/programming-guide/delegates/using-delegates.md) ou des types d'[arborescence d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md). En utilisant des expressions lambda, vous pouvez écrire des fonctions locales qui peuvent être passées comme des arguments ou retournées comme la valeur d'appels de fonction. Les expressions lambda sont particulièrement utiles pour écrire des expressions de requête LINQ.  
  
 Pour créer une expression lambda, vous spécifiez des paramètres d'entrée \(le cas échéant\) à gauche de l'opérateur lambda [\=\>](../../../csharp/language-reference/operators/lambda-operator.md), et vous placez l'expression ou le bloc d'instructions de l'autre côté. Par exemple, l'expression lambda `x => x * x` spécifie un paramètre nommé `x` et retourne la valeur `x` élevée au carré. Vous pouvez assigner cette expression à un type délégué, comme dans l'exemple suivant :  
  
```c#  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Pour créer un type d'arborescence d'expression :  
  
```c#  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 L'opérateur `=>` a la même priorité que l'assignation \(`=`\) et est de type [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) \(voir la section « Associativité » de l'article Opérateurs\).  
  
 Les lambdas sont utilisés dans les requêtes [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] fondées sur une méthode en tant qu'arguments pour les méthodes d'opérateur de requête standard telles que <xref:System.Linq.Enumerable.Where%2A>.  
  
 Lorsque vous utilisez la syntaxe fondée sur une méthode pour appeler la méthode <xref:System.Linq.Enumerable.Where%2A> dans la classe <xref:System.Linq.Enumerable> \(de la même manière que dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] to Objects et [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]\), le paramètre est un type délégué <xref:System.Func%602?displayProperty=fullName>. Une expression lambda est la méthode la plus commode pour créer ce délégué. Lorsque vous appelez la même méthode dans, par exemple, la classe <xref:System.Linq.Queryable?displayProperty=fullName> \(comme vous le faites dans [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)]\), le type de paramètre est un <xref:System.Linq.Expressions.Expression?displayProperty=fullName>\<Func\>, où Func correspond à un délégué Func comportant seize paramètres d'entrée maximum. Une expression lambda est simplement une méthode très concise pour construire cette arborescence de l'expression. Les lambdas font apparaître les appels `Where` comme semblables bien qu'en fait, le type d'objet créé à partir du lambda soit différent.  
  
 Dans l'exemple précédent, vous remarquez que la signature du délégué comporte un paramètre d'entrée implicitement typé `int` et retourne un `int`. L'expression lambda peut être convertie en un délégué de ce type, car elle comporte également un paramètre d'entrée \(`x`\) et une valeur de retour que le compilateur peut convertir implicitement en type `int`. \(L'inférence de type est traitée plus en détail dans les sections suivantes.\) Lorsque le délégué est appelé à l'aide d'un paramètre d'entrée de 5, il retourne un résultat de 25.  
  
 Les expressions lambda ne sont pas autorisées sur le côté gauche de l'opérateur [is](../../../csharp/language-reference/keywords/is.md) ou [as](../../../csharp/language-reference/keywords/as.md).  
  
 Toutes les restrictions qui s'appliquent aux méthodes anonymes s'appliquent également aux expressions lambda. Pour plus d'informations, consultez [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## Expressions lambda  
 Une expression lambda avec une expression sur le côté droit de l'opération \=\> est appelée *expression lambda*. Les expressions lambda sont utilisées en grand nombre dans la construction d’[Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md). Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Les parenthèses sont facultatives uniquement si le lambda comporte un paramètre d'entrée ; sinon, elles sont obligatoires. Les paramètres d'entrée sont séparés par des virgules entre parenthèses :  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Il est parfois difficile, voire impossible, pour le compilateur de déduire les types d'entrée. Dans ce cas, vous pouvez spécifier les types explicitement comme indiqué dans l'exemple suivant :  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Spécifiez des paramètres d'entrée de zéro avec des parenthèses vides :  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Notez dans l'exemple précédent que le corps d'une expression lambda peut se composer d'un appel de méthode. Toutefois, si vous créez des arborescences d'expressions évaluées en dehors de .NET Framework, comme dans SQL Server, vous ne devez pas utiliser les appels de méthode dans les expressions lambda. Les méthodes n'auront aucune signification en dehors du contexte du Common Language Runtime .NET.  
  
## Instructions lambda  
 Une instruction lambda ressemble à une expression lambda, mais l'instruction ou les instructions sont mises entre accolades :  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Les instructions lambda, comme les méthodes anonymes, ne peuvent pas être utilisées pour créer des arborescences d'expression.  
  
## Lambdas asynchrones  
 Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../../../csharp/language-reference/keywords/async.md) et [await](../../../csharp/language-reference/keywords/await.md). Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone. Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Pour plus d’informations sur la création et l’utilisation des méthodes asynchrones, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Lambdas avec les opérateurs de requête standard  
 De nombreux opérateurs de requête standard comportent un paramètre d'entrée dont le type est l'un de la famille <xref:System.Func%602> de délégués génériques. Ces délégués utilisent des paramètres de type pour définir le nombre et les types de paramètres d'entrée, ainsi que le type de retour du délégué. Les délégués `Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources. Considérons par exemple le type délégué suivant :  
  
```c#  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Ce délégué peut être instancié comme `Func<int,bool> myFunc` où `int` est un paramètre d'entrée et `bool` est la valeur de retour. La valeur de retour est toujours spécifiée dans le dernier paramètre de type.`Func<int, string, bool>` définit un délégué avec deux paramètres d'entrée, `int` et `string` et un type de retour de `bool`. Le délégué `Func` suivant, lorsqu'il est appelé, retourne la valeur true ou false pour indiquer si le paramètre d'entrée est égal à 5 :  
  
```c#  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Vous pouvez également fournir une expression lambda lorsque le type d'argument est `Expression<Func>`, par exemple dans les opérateurs de requête standard définis dans System.Linq.Queryable. Lorsque vous spécifiez un argument `Expression<Func>`, le lambda est compilé en une arborescence d'expression.  
  
 Opérateur de requête standard, la méthode <xref:System.Linq.Enumerable.Count%2A>, est illustré ici :  
  
```c#  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement. Cette expression lambda particulière compte les entiers \(`n`\) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.  
  
 La ligne de code suivante produit une séquence qui contient tous les éléments du tableau `numbers` qui apparaissent à gauche du « 9 », car c'est le premier nombre de la séquence qui ne satisfait pas la condition :  
  
```c#  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Cet exemple indique comment spécifier plusieurs paramètres d'entrée en les mettant entre parenthèses. La méthode retourne tous les éléments du tableau de nombres, jusqu'à ce que soit rencontré un nombre dont la valeur est inférieure à cette position. Ne confondez pas l'opérateur lambda \(`=>`\) avec l'opérateur supérieur ou égal \(`>=`\).  
  
```c#  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## Inférence de type dans les lambdas  
 Lorsque vous écrivez des lambdas, vous n'avez généralement pas à spécifier un type pour les paramètres d'entrée, car le compilateur peut déduire le type en fonction du corps du lambda, du type délégué du paramètre et d'autres facteurs décrits dans la spécification du langage C\#. Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source. Donc, si vous interrogez un `IEnumerable<Customer>`, il en est déduit que la variable d'entrée est un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et propriétés :  
  
```c#  
customers.Where(c => c.City == "London");  
```  
  
 Les règles générales pour les lambdas sont les suivantes :  
  
-   Le lambda doit contenir le même nombre de paramètres que le type délégué.  
  
-   Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.  
  
-   La valeur de retour du lambda \(le cas échéant\) doit être implicitement convertible en type de retour du délégué.  
  
 Notez que les expressions lambda en elles\-mêmes n'ont pas de type, car le système de type commun \(CTS, Common Type System\) ne comporte aucun concept intrinsèque « d'expression lambda ». Toutefois, il est parfois commode de parler de manière informelle du « type » d'une expression lambda. Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.  
  
## Portée variable dans les expressions lambda  
 Les expressions lambda peuvent faire référence aux *variables externes* \(voir [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)\) qui se trouvent dans la portée de la méthode qui définit la fonction lambda, ou dans la portée du type qui contient l’expression lambda. Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector. Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda. L'exemple suivant illustre ces règles :  
  
```c#  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
  
```  
  
 Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :  
  
-   Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.  
  
-   Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode externe.  
  
-   Une expression lambda ne peut pas capturer directement un paramètre `ref` ou `out` dans une méthode englobante.  
  
-   Une instruction return dans une expression lambda ne provoque pas le retour de la méthode englobante.  
  
-   Une expression lambda ne peut pas contenir une instruction `goto`, une instruction `break`, ou une instruction `continue` à l'intérieur de la fonction lambda si la cible de l'instruction de saut est hors du bloc. C'est également une erreur d'avoir une instruction de saut en dehors du bloc de la fonction lambda si la cible est à l'intérieur du bloc.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Chapitre proposé  
 [Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) \(Délégués, événements et expressions lambda\) dans [C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Exemples Visual Studio 2008 C\# \(voir les fichiers d’exemples de requêtes LINQ et le programme XQuery\)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)   
 [Expressions lambda récursives](http://go.microsoft.com/fwlink/?LinkId=112395)