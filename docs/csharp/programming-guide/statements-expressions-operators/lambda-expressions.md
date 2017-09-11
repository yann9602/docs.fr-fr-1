---
title: Expressions lambda (Guide de programmation C#)
ms.date: 2017-03-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 64
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
ms.openlocfilehash: c952c72d9108775fbd0f824f82cacdab5ba91d09
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="05376-102">Expressions lambda (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="05376-102">Lambda Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="05376-103">Une expression lambda est une [fonction anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que vous pouvez utiliser pour créer des types [délégués](../../../csharp/programming-guide/delegates/using-delegates.md) ou des types d' [arborescence d'expression](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) .</span><span class="sxs-lookup"><span data-stu-id="05376-103">A lambda expression is an [anonymous function](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) that you can use to create [delegates](../../../csharp/programming-guide/delegates/using-delegates.md) or [expression tree](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) types.</span></span> <span data-ttu-id="05376-104">En utilisant des expressions lambda, vous pouvez écrire des fonctions locales qui peuvent être passées comme des arguments ou retournées comme la valeur d'appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="05376-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="05376-105">Les expressions lambda sont particulièrement utiles pour écrire des expressions de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="05376-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>  
  
 <span data-ttu-id="05376-106">Pour créer une expression lambda, vous spécifiez des paramètres d'entrée (le cas échéant) à gauche de l'opérateur lambda [=>](../../../csharp/language-reference/operators/lambda-operator.md), et vous placez l'expression ou le bloc d'instructions de l'autre côté.</span><span class="sxs-lookup"><span data-stu-id="05376-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="05376-107">Par exemple, l'expression lambda `x => x * x` spécifie un paramètre nommé `x` et retourne la valeur `x` élevée au carré.</span><span class="sxs-lookup"><span data-stu-id="05376-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="05376-108">Vous pouvez assigner cette expression à un type délégué, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="05376-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="05376-109">Pour créer un type d'arborescence d'expression :</span><span class="sxs-lookup"><span data-stu-id="05376-109">To create an expression tree type:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="05376-110">L'opérateur `=>` a la même priorité que l'assignation (`=`) et est de type [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (consultez la section « Associativité » de l'article Opérateurs).</span><span class="sxs-lookup"><span data-stu-id="05376-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="05376-111">Les lambdas sont utilisés dans les requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fondées sur une méthode en tant qu'arguments pour les méthodes d'opérateur de requête standard telles que <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="05376-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="05376-112">Lorsque vous utilisez la syntaxe fondée sur une méthode pour appeler la méthode <xref:System.Linq.Enumerable.Where%2A> dans la classe <xref:System.Linq.Enumerable> (de la même manière que dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]), le paramètre est un type délégué <xref:System.Func%602?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="05376-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=fullName>.</span></span> <span data-ttu-id="05376-113">Une expression lambda est la méthode la plus commode pour créer ce délégué.</span><span class="sxs-lookup"><span data-stu-id="05376-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="05376-114">Quand vous appelez la même méthode dans, par exemple, la classe <xref:System.Linq.Queryable?displayProperty=fullName> (comme vous le faites dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), le type de paramètre est <xref:System.Linq.Expressions.Expression?displayProperty=fullName><Func\>, où Func correspond à un délégué Func avec seize paramètres d'entrée maximum.</span><span class="sxs-lookup"><span data-stu-id="05376-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=fullName> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=fullName><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="05376-115">Une expression lambda est simplement une méthode très concise pour construire cette arborescence de l'expression.</span><span class="sxs-lookup"><span data-stu-id="05376-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="05376-116">Les lambdas font apparaître les appels `Where` comme semblables bien qu'en fait, le type d'objet créé à partir du lambda soit différent.</span><span class="sxs-lookup"><span data-stu-id="05376-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="05376-117">Dans l'exemple précédent, vous remarquez que la signature du délégué comporte un paramètre d'entrée implicitement typé `int`et retourne un `int`.</span><span class="sxs-lookup"><span data-stu-id="05376-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="05376-118">L'expression lambda peut être convertie en un délégué de ce type, car elle comporte également un paramètre d'entrée (`x`) et une valeur de retour que le compilateur peut convertir implicitement en type `int`.</span><span class="sxs-lookup"><span data-stu-id="05376-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="05376-119">(L'inférence de type est traitée plus en détail dans les sections suivantes.) Lorsque le délégué est appelé à l'aide d'un paramètre d'entrée de 5, il retourne un résultat de 25.</span><span class="sxs-lookup"><span data-stu-id="05376-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="05376-120">Les expressions lambda ne sont pas autorisées du côté gauche de l’opérateur [is](../../../csharp/language-reference/keywords/is.md) ou [as](../../../csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="05376-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="05376-121">Toutes les restrictions qui s'appliquent aux méthodes anonymes s'appliquent également aux expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="05376-122">Pour plus d’informations, consultez [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="05376-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="05376-123">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="05376-123">Expression Lambdas</span></span>  
 <span data-ttu-id="05376-124">Une expression lambda avec une expression du côté droit de l’opérateur => est appelée *expression lambda*.</span><span class="sxs-lookup"><span data-stu-id="05376-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="05376-125">Les expressions lambda sont utilisées en grand nombre dans la construction d’[arborescences d’expression](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span><span class="sxs-lookup"><span data-stu-id="05376-125">Expression lambdas are used extensively in the construction of [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span></span> <span data-ttu-id="05376-126">Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :</span><span class="sxs-lookup"><span data-stu-id="05376-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>  
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="05376-127">Les parenthèses sont facultatives uniquement si le lambda comporte un paramètre d'entrée ; sinon, elles sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="05376-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="05376-128">Les paramètres d'entrée sont séparés par des virgules entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="05376-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="05376-129">Il est parfois difficile, voire impossible, pour le compilateur de déduire les types d'entrée.</span><span class="sxs-lookup"><span data-stu-id="05376-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="05376-130">Dans ce cas, vous pouvez spécifier les types explicitement comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="05376-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="05376-131">Spécifiez des paramètres d'entrée de zéro avec des parenthèses vides :</span><span class="sxs-lookup"><span data-stu-id="05376-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="05376-132">Notez dans l'exemple précédent que le corps d'une expression lambda peut se composer d'un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="05376-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="05376-133">Toutefois, si vous créez des arborescences d'expressions évaluées en dehors de .NET Framework, comme dans SQL Server, vous ne devez pas utiliser les appels de méthode dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="05376-134">Les méthodes n'auront aucune signification en dehors du contexte du Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="05376-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="05376-135">Instructions lambda</span><span class="sxs-lookup"><span data-stu-id="05376-135">Statement Lambdas</span></span>  
 <span data-ttu-id="05376-136">Une instruction lambda ressemble à une expression lambda, mais l'instruction ou les instructions sont mises entre accolades :</span><span class="sxs-lookup"><span data-stu-id="05376-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="05376-137">(paramètres d’entrée) => { instruction ; }</span><span class="sxs-lookup"><span data-stu-id="05376-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="05376-138">Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.</span><span class="sxs-lookup"><span data-stu-id="05376-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
<span data-ttu-id="05376-139">[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="05376-139">[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]</span></span>

<span data-ttu-id="05376-140">[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="05376-140">[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]</span></span>

 <span data-ttu-id="05376-141">Les instructions lambda, comme les méthodes anonymes, ne peuvent pas être utilisées pour créer des arborescences d'expression.</span><span class="sxs-lookup"><span data-stu-id="05376-141">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="05376-142">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="05376-142">Async Lambdas</span></span>  
 <span data-ttu-id="05376-143">Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../../../csharp/language-reference/keywords/async.md) et [await](../../../csharp/language-reference/keywords/await.md) .</span><span class="sxs-lookup"><span data-stu-id="05376-143">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="05376-144">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="05376-144">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="05376-145">Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone.</span><span class="sxs-lookup"><span data-stu-id="05376-145">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="05376-146">Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="05376-146">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="05376-147">Pour plus d’informations sur la création et l’utilisation des méthodes asyncrones, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="05376-147">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="05376-148">Lambdas avec les opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="05376-148">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="05376-149">De nombreux opérateurs de requête standard comportent un paramètre d'entrée dont le type est l'un de la famille <xref:System.Func%602> de délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="05376-149">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="05376-150">Ces délégués utilisent des paramètres de type pour définir le nombre et les types de paramètres d'entrée, ainsi que le type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="05376-150">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="05376-151">Les délégués`Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources.</span><span class="sxs-lookup"><span data-stu-id="05376-151">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="05376-152">Considérons par exemple le type délégué suivant :</span><span class="sxs-lookup"><span data-stu-id="05376-152">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="05376-153">Ce délégué peut être instancié comme `Func<int,bool> myFunc` où `int` est un paramètre d'entrée et `bool` est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="05376-153">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="05376-154">La valeur de retour est toujours spécifiée dans le dernier paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="05376-154">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="05376-155">`Func<int, string, bool>` définit un délégué avec deux paramètres d'entrée, `int` et `string`et un type de retour de `bool`.</span><span class="sxs-lookup"><span data-stu-id="05376-155">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="05376-156">Le délégué `Func` suivant, lorsqu'il est appelé, retourne la valeur true ou false pour indiquer si le paramètre d'entrée est égal à 5 :</span><span class="sxs-lookup"><span data-stu-id="05376-156">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="05376-157">Vous pouvez également fournir une expression lambda lorsque le type d'argument est `Expression<Func>`, par exemple dans les opérateurs de requête standard définis dans System.Linq.Queryable.</span><span class="sxs-lookup"><span data-stu-id="05376-157">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="05376-158">Lorsque vous spécifiez un argument `Expression<Func>` , le lambda est compilé en une arborescence d'expression.</span><span class="sxs-lookup"><span data-stu-id="05376-158">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="05376-159">Opérateur de requête standard, la méthode <xref:System.Linq.Enumerable.Count%2A> , est illustré ici :</span><span class="sxs-lookup"><span data-stu-id="05376-159">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="05376-160">Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="05376-160">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="05376-161">Cette expression lambda particulière compte les entiers (`n`) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.</span><span class="sxs-lookup"><span data-stu-id="05376-161">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="05376-162">La ligne de code suivante produit une séquence qui contient tous les éléments du tableau `numbers` qui apparaissent à gauche du « 9 », car c'est le premier nombre de la séquence qui ne satisfait pas la condition :</span><span class="sxs-lookup"><span data-stu-id="05376-162">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="05376-163">Cet exemple indique comment spécifier plusieurs paramètres d'entrée en les mettant entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="05376-163">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="05376-164">La méthode retourne tous les éléments du tableau de nombres, jusqu'à ce que soit rencontré un nombre dont la valeur est inférieure à cette position.</span><span class="sxs-lookup"><span data-stu-id="05376-164">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="05376-165">Ne confondez pas l'opérateur lambda (`=>`) avec l'opérateur supérieur ou égal (`>=`).</span><span class="sxs-lookup"><span data-stu-id="05376-165">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="05376-166">Inférence de type dans les lambdas</span><span class="sxs-lookup"><span data-stu-id="05376-166">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="05376-167">Lorsque vous écrivez des lambdas, vous n'avez généralement pas à spécifier un type pour les paramètres d'entrée, car le compilateur peut déduire le type en fonction du corps du lambda, du type délégué du paramètre et d'autres facteurs décrits dans la spécification du langage C#.</span><span class="sxs-lookup"><span data-stu-id="05376-167">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="05376-168">Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source.</span><span class="sxs-lookup"><span data-stu-id="05376-168">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="05376-169">Donc, si vous interrogez un `IEnumerable<Customer>`, il en est déduit que la variable d'entrée est un objet `Customer` , ce qui signifie que vous avez accès à ses méthodes et propriétés :</span><span class="sxs-lookup"><span data-stu-id="05376-169">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="05376-170">Les règles générales pour les lambdas sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="05376-170">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="05376-171">Le lambda doit contenir le même nombre de paramètres que le type délégué.</span><span class="sxs-lookup"><span data-stu-id="05376-171">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="05376-172">Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="05376-172">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="05376-173">La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="05376-173">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="05376-174">Notez que les expressions lambda en elles-mêmes n'ont pas de type, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d'expression lambda ».</span><span class="sxs-lookup"><span data-stu-id="05376-174">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="05376-175">Toutefois, il est parfois commode de parler de manière informelle du « type » d'une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-175">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="05376-176">Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-176">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="05376-177">Portée variable dans les expressions lambda</span><span class="sxs-lookup"><span data-stu-id="05376-177">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="05376-178">Les expressions lambda peuvent faire référence à des *variables externes* (consultez [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) qui se trouvent dans l’étendue de la méthode qui définit la fonction lambda, ou dans l’étendue du type qui contient l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-178">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="05376-179">Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="05376-179">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="05376-180">Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="05376-180">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="05376-181">L'exemple suivant illustre ces règles :</span><span class="sxs-lookup"><span data-stu-id="05376-181">The following example demonstrates these rules:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="05376-182">Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="05376-182">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="05376-183">Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="05376-183">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="05376-184">Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode externe.</span><span class="sxs-lookup"><span data-stu-id="05376-184">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="05376-185">Une expression lambda ne peut pas capturer directement un paramètre `ref` ou `out` dans une méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="05376-185">A lambda expression cannot directly capture a `ref` or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="05376-186">Une instruction return dans une expression lambda ne provoque pas le retour de la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="05376-186">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="05376-187">Une expression lambda ne peut pas contenir une instruction `goto` , une instruction `break` , ou une instruction `continue` à l'intérieur de la fonction lambda si la cible de l'instruction de saut est hors du bloc.</span><span class="sxs-lookup"><span data-stu-id="05376-187">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="05376-188">C'est également une erreur d'avoir une instruction de saut en dehors du bloc de la fonction lambda si la cible est à l'intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="05376-188">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="05376-189">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="05376-189">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="05376-190">Chapitre proposé</span><span class="sxs-lookup"><span data-stu-id="05376-190">Featured Book Chapter</span></span>  
 <span data-ttu-id="05376-191">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="05376-191">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05376-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05376-192">See Also</span></span>  
 <span data-ttu-id="05376-193">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="05376-193">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="05376-194">[LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="05376-194">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="05376-195">[Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="05376-195">[Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
 <span data-ttu-id="05376-196">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="05376-196">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="05376-197">[Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) </span><span class="sxs-lookup"><span data-stu-id="05376-197">[Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) </span></span>  
 <span data-ttu-id="05376-198">[Exemples Visual Studio 2008 C# (voir les fichiers d’exemples de requêtes LINQ et le programme XQuery)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba) </span><span class="sxs-lookup"><span data-stu-id="05376-198">[Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba) </span></span>  
 [<span data-ttu-id="05376-199">Expressions lambda récursives</span><span class="sxs-lookup"><span data-stu-id="05376-199">Recursive lambda expressions</span></span>](http://go.microsoft.com/fwlink/?LinkId=112395)

