---
title: Tuples dans Visual Basic
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="9e096-102">Tuples (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e096-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="9e096-103">À partir de Visual Basic 2017, du langage Visual Basic propose une prise en charge intégrée pour les tuples qui permet de créer des tuples et accéder aux éléments de tuples plus facile.</span><span class="sxs-lookup"><span data-stu-id="9e096-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="9e096-104">Un tuple est une structure de données de légers qui a un nombre spécifique et une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9e096-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="9e096-105">Lorsque vous instanciez le tuple, vous définissez le nombre et le type de données de chaque valeur (ou élément).</span><span class="sxs-lookup"><span data-stu-id="9e096-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="9e096-106">Par exemple, un objet de 2 tuples (ou paire) a deux éléments.</span><span class="sxs-lookup"><span data-stu-id="9e096-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="9e096-107">La première peut être un `Boolean` valeur, alors que le second est un `String`.</span><span class="sxs-lookup"><span data-stu-id="9e096-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="9e096-108">Étant donné que les tuples permettent de stocker plusieurs valeurs dans un objet unique, ils sont souvent utilisés comme une solution légère pour retourner plusieurs valeurs à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e096-109">Prise en charge de tuple nécessite le <xref:System.ValueTuple> type.</span><span class="sxs-lookup"><span data-stu-id="9e096-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="9e096-110">Si le 4.7 Framework .NET n’est pas installé, vous devez ajouter le package NuGet `System.ValueTuple`, qui est disponible sur la galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="9e096-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="9e096-111">Sans ce package, vous pouvez obtenir une erreur de compilation semblable à « Type prédéfini 'ValueTuple(Of,,,)' n’est pas défini ou importé. »</span><span class="sxs-lookup"><span data-stu-id="9e096-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="9e096-112">Instanciation et l’utilisation d’un tuple</span><span class="sxs-lookup"><span data-stu-id="9e096-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="9e096-113">Vous instanciez un tuple en mettant ses parenthèses de messagerie instantanée de valeurs délimitées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9e096-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="9e096-114">Chacune de ces valeurs devient alors un champ du tuple.</span><span class="sxs-lookup"><span data-stu-id="9e096-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="9e096-115">Par exemple, le code suivant définit une triple (ou un objet de 3 tuples) avec un `Date` comme première valeur, un `String` en tant que le second et un `Boolean` en tant que son troisième.</span><span class="sxs-lookup"><span data-stu-id="9e096-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="9e096-116">Par défaut, le nom de chaque champ dans un tuple se compose de la chaîne `Item` , ainsi que la basée sur une position dans le tuple.</span><span class="sxs-lookup"><span data-stu-id="9e096-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="9e096-117">Pour cet objet de 3 tuples, les `Date` champ est `Item1`, le `String` champ est `Item2`et le `Boolean` champ est `Item3`.</span><span class="sxs-lookup"><span data-stu-id="9e096-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="9e096-118">L’exemple suivant affiche les valeurs des champs du tuple instanciée dans la ligne de code précédente</span><span class="sxs-lookup"><span data-stu-id="9e096-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="9e096-119">Les champs d’un tuple Visual Basic sont en lecture-écriture ; une fois que vous avez instancié un tuple, vous pouvez modifier ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="9e096-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="9e096-120">L’exemple suivant modifie deux des trois champs de tuple créés dans l’exemple précédent et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="9e096-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="9e096-121">Instanciation et l’utilisation d’un tuple nommé</span><span class="sxs-lookup"><span data-stu-id="9e096-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="9e096-122">Au lieu d’utiliser des noms par défaut pour les champs d’un tuple, vous pouvez instancier un *nommé tuple* en assignant vos propres noms pour les éléments du tuple.</span><span class="sxs-lookup"><span data-stu-id="9e096-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="9e096-123">Les champs du tuple sont ensuite accessible par leurs noms attribués *ou* par leurs noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="9e096-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="9e096-124">L’exemple suivant instancie le tuple de 3 même comme précédemment, à ceci près qu’il nomme explicitement le premier champ `EventDate`, le deuxième `Name`et la troisième `IsHoliday`.</span><span class="sxs-lookup"><span data-stu-id="9e096-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="9e096-125">Il affiche les valeurs de champ, les modifie et affiche les valeurs de champ à nouveau.</span><span class="sxs-lookup"><span data-stu-id="9e096-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="9e096-126">Noms d’élément de tuple déduit</span><span class="sxs-lookup"><span data-stu-id="9e096-126">Inferred tuple element names</span></span>

<span data-ttu-id="9e096-127">À partir de Visual Basic 15.3, Visual Basic peut déduire les noms d’éléments de tuple ; vous n’avez pas à les assigner explicitement.</span><span class="sxs-lookup"><span data-stu-id="9e096-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="9e096-128">Les noms de tuple déduits sont utiles lorsque vous initialisez un tuple à partir d’un ensemble de variables, et vous souhaitez que le nom d’élément de tuple pour être le même que le nom de variable.</span><span class="sxs-lookup"><span data-stu-id="9e096-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="9e096-129">L’exemple suivant crée un `stateInfo` tuple qui contient trois explicitement des éléments, nommés `state`, `stateName`, et `capital`.</span><span class="sxs-lookup"><span data-stu-id="9e096-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="9e096-130">Notez que, dans les éléments d’affectation de noms, l’instruction d’initialisation de tuple attribue simplement les éléments nommés les valeurs des variables portant le même nommés.</span><span class="sxs-lookup"><span data-stu-id="9e096-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="9e096-131">Étant donné que les éléments et les variables ont le même nom, le compilateur Visual Basic peut déduire les noms des champs, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9e096-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="9e096-132">Pour activer les noms d’élément de tuple interred, vous devez définir la version du compilateur Visual Basic à utiliser dans votre projet Visual Basic (\*.vbproj) fichier :</span><span class="sxs-lookup"><span data-stu-id="9e096-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="9e096-133">Tuples comme valeurs de retour de méthode</span><span class="sxs-lookup"><span data-stu-id="9e096-133">Tuples as method return values</span></span>

<span data-ttu-id="9e096-134">Une méthode peut retourner une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="9e096-134">A method can return only a single value.</span></span> <span data-ttu-id="9e096-135">Souvent, cependant, vous aimeriez un appel de méthode pour retourner plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="9e096-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="9e096-136">Il existe plusieurs façons de contourner cette limitation :</span><span class="sxs-lookup"><span data-stu-id="9e096-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="9e096-137">Vous pouvez créer une classe personnalisée ou une structure dont les propriétés ou champs représentent les valeurs retournées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="9e096-138">Par conséquent, est une solution de haute densité. Il requiert que vous définissez un type personnalisé dont seul objectif consiste à récupérer les valeurs à partir d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="9e096-139">Vous pouvez retourner une valeur unique à partir de la méthode et renvoyer les valeurs restantes en les passant par référence à la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="9e096-140">Cela implique la surcharge de l’instanciation d’une variable et les risques par inadvertance en remplaçant la valeur de la variable que vous passez par référence.</span><span class="sxs-lookup"><span data-stu-id="9e096-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="9e096-141">Vous pouvez utiliser un tuple, qui fournit une solution légère pour la récupération de plusieurs valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="9e096-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="9e096-142">Par exemple, le **TryParse** méthodes de retour de .NET un `Boolean` valeur qui indique si l’opération d’analyse a réussi.</span><span class="sxs-lookup"><span data-stu-id="9e096-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="9e096-143">Le résultat de l’opération d’analyse est retourné dans une variable passée par référence à la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="9e096-144">Normalement, un appel à l’une méthode d’analyse comme <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> présente l’aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="9e096-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="9e096-145">Nous pouvons retourner un tuple à partir de l’opération d’analyse, si nous encapsulent l’appel à la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode dans votre propre méthode.</span><span class="sxs-lookup"><span data-stu-id="9e096-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="9e096-146">Dans l’exemple suivant, `NumericLibrary.ParseInteger` appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode et retourne un tuple nommé avec deux éléments.</span><span class="sxs-lookup"><span data-stu-id="9e096-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="9e096-147">Vous pouvez ensuite appeler la méthode avec un code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="9e096-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="9e096-148">Les tuples de Visual Basic et les tuples dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9e096-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="9e096-149">Un tuple de Visual Basic est une instance de l’un de le **System.ValueTuple** des types génériques qui ont été introduits dans le 4.7 Framework .NET.</span><span class="sxs-lookup"><span data-stu-id="9e096-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="9e096-150">Le .NET Framework inclut également un ensemble de génériques **System.Tuple** classes.</span><span class="sxs-lookup"><span data-stu-id="9e096-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="9e096-151">Ces classes, toutefois, diffèrent des tuples de Visual Basic et le **System.ValueTuple** des types génériques dans de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="9e096-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="9e096-152">Les éléments de la **Tuple** les classes sont des propriétés nommées `Item1`, `Item2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="9e096-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="9e096-153">Dans Visual Basic tuples et **ValueTuple** types d’éléments de tuple, sont des champs.</span><span class="sxs-lookup"><span data-stu-id="9e096-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="9e096-154">Vous ne pouvez attribuer des noms explicites pour les éléments d’un **Tuple** instance ou d’un **ValueTuple** instance.</span><span class="sxs-lookup"><span data-stu-id="9e096-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="9e096-155">Visual Basic vous permet d’attribuer des noms qui communiquent la signification des champs.</span><span class="sxs-lookup"><span data-stu-id="9e096-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="9e096-156">Les propriétés d’un **Tuple** instance sont en lecture seule ; les tuples sont immuables.</span><span class="sxs-lookup"><span data-stu-id="9e096-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="9e096-157">Dans Visual Basic tuples et **ValueTuple** , types de champs de tuple sont en lecture-écriture ; les tuples sont mutables.</span><span class="sxs-lookup"><span data-stu-id="9e096-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="9e096-158">Le type générique **Tuple** types sont des types référence.</span><span class="sxs-lookup"><span data-stu-id="9e096-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="9e096-159">L’utilisation de ces **Tuple** types signifie que de l’allocation d’objets.</span><span class="sxs-lookup"><span data-stu-id="9e096-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="9e096-160">Sur des chemins réactifs, cela peut avoir un impact mesurable sur les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="9e096-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="9e096-161">Visual Basic tuples et **ValueTuple** types sont des types valeur.</span><span class="sxs-lookup"><span data-stu-id="9e096-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="9e096-162">Méthodes d’extension dans le <xref:System.TupleExtensions> classe facilitent la conversion entre des tuples de Visual Basic et .NET **Tuple** objets.</span><span class="sxs-lookup"><span data-stu-id="9e096-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="9e096-163">Le **ToTuple** méthode convertit un tuple de Visual Basic .NET **Tuple** objet et le **ToValueTuple** méthode convertit un .NET **Tuple** objet à un tuple de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e096-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="9e096-164">L’exemple suivant crée un tuple, le convertit en un .NET **Tuple** objet et convertit le retour à un tuple de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e096-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="9e096-165">L’exemple compare ensuite ce tuple avec celui d’origine pour vous assurer qu’ils sont égaux.</span><span class="sxs-lookup"><span data-stu-id="9e096-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9e096-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e096-166">See also</span></span>

[<span data-ttu-id="9e096-167">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e096-167">Visual Basic Language Reference</span></span>](index.md)  
