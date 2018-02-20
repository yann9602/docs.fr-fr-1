---
title: Expressions de calcul (F#)
description: "Découvrez comment créer la syntaxe pour l’écriture de calculs en F # qui peuvent être séquencés et combinés à l’aide de liaisons et constructions de flux de contrôle."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: c4ff998c65f3a5c458f36312f6887d869569d814
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="computation-expressions"></a>Expressions de calcul

En F #, les expressions de calcul fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de liaisons et constructions de flux de contrôle. Elles peuvent servir à fournir une syntaxe pratique pour *monades*, une fonctionnalité de programmation fonctionnelle qui peut être utilisée pour gérer les données, le contrôle et les effets secondaires dans les programmes fonctionnels.


## <a name="built-in-workflows"></a>Flux de travail intégrés
Expressions de séquence sont un exemple d’expression de calcul, comme les flux de travail asynchrones et les expressions de requête. Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [les Expressions de requête](query-expressions.md).

Certaines fonctionnalités communes aux expressions de séquence et flux de travail asynchrones et illustrent la syntaxe de base pour une expression de calcul :

```fsharp
builder-name { expression }
```

La syntaxe précédente spécifie que l’expression donnée est une expression de calcul d’un type spécifié par *-nom du Générateur de*. L’expression de calcul peut être un flux de travail intégré, tel que `seq` ou `async`, ou il peut être quelque chose que vous définissez. Le *-nom du Générateur de* est l’identificateur pour une instance d’un type spécial appelé le *type de générateur*. Le type de générateur est un type de classe qui définit des méthodes spéciales qui régissent la façon des que fragments de l’expression de calcul sont combinées, autrement dit, code qui contrôle la façon dont l’expression s’exécute. Une autre pour décrire une classe de générateur consiste à dire qu’il vous permet de personnaliser l’opération de nombreuses constructions F #, telles que les boucles et les liaisons.

Dans les expressions de calcul, les deux formes sont disponibles pour certaines constructions de langage commun. Vous pouvez appeler les constructions de type variant en utilisant un ! (bang) sur certains mots clés, le suffixe tel que `let!`, `do!`, et ainsi de suite. Ces formulaires spéciaux forcent certaines fonctions définies dans la classe de générateur à remplacer le comportement intégré ordinaire de ces opérations. Ces formes ressemblent à la `yield!` formulaire de la `yield` mot clé qui est utilisée dans les expressions de séquence. Pour plus d’informations, consultez [séquences](sequences.md).


## <a name="creating-a-new-type-of-computation-expression"></a>Création d’un nouveau Type d’Expression de calcul
Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de générateur et en définissant certaines méthodes spéciales sur la classe. La classe de générateur peut éventuellement définir les méthodes, comme indiqué dans le tableau suivant.

Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de générateur de flux de travail.


|**Méthode**|**Typiques**|**Description**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Appelé pour `let!` et `do!` dans les expressions de calcul.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Encapsule une expression de calcul en tant que fonction.|
|`Return`|`'T -> M<'T>`|Appelé pour `return` dans les expressions de calcul.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Appelé pour `return!` dans les expressions de calcul.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Exécute une expression de calcul.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Appelée pour le séquencement dans les expressions de calcul.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Appelé pour `for...do` expressions dans les expressions de calcul.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Appelé pour `try...finally` expressions dans les expressions de calcul.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Appelé pour `try...with` expressions dans les expressions de calcul.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Appelé pour `use` liaisons dans les expressions de calcul.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Appelé pour `while...do` expressions dans les expressions de calcul.|
|`Yield`|`'T -> M<'T>`|Appelé pour `yield` expressions dans les expressions de calcul.|
|`YieldFrom`|`M<'T> -> M<'T>`|Appelé pour `yield!` expressions dans les expressions de calcul.|
|`Zero`|`unit -> M<'T>`|Appelé pour vide `else` branches de `if...then` expressions dans les expressions de calcul.|
La plupart des méthodes dans une classe de générateur utilisent et renvoyer un `M<'T>` construction, qui est généralement un type défini séparément qui caractérise le genre des calculs combinés, par exemple, `Async<'T>` pour les flux de travail asynchrones et `Seq<'T>` pour les workflows de la séquence. Les signatures de ces méthodes pouvoir être combinées et imbriquées avec d’autres, afin que l’objet de flux de travail retourné d’une construction permettre être passée à la suivante. Le compilateur, lorsqu’il analyse une expression de calcul, convertit l’expression en une série d’appels de fonction imbriqués en utilisant les méthodes dans le tableau précédent et le code dans l’expression de calcul.

L’expression imbriquée a la forme suivante :

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Dans le code ci-dessus, les appels à `Run` et `Delay` sont omis s’ils ne sont pas définis dans la classe de générateur d’expression de calcul. Le corps de l’expression de calcul, désignée ici comme `{| cexpr |}`, est traduite en appels de méthodes de la classe de générateur par les traductions décrites dans le tableau suivant. L’expression de calcul `{| cexpr |}` est définie de manière récursive en fonction de ces traductions où `expr` est une expression F # et `cexpr` est une expression de calcul.



|Expression|Traduction|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
Dans le tableau précédent, `other-expr` décrit une expression qui ne figure pas dans le cas contraire dans la table. Une classe de générateur n’a pas besoin d’implémenter toutes les méthodes et de prendre en charge toutes les traductions répertoriées dans le tableau précédent. Ces constructions qui ne sont pas implémentées ne sont pas disponibles dans les expressions de calcul de ce type. Par exemple, si vous ne souhaitez pas prendre en charge la `use` mot clé dans les expressions de calcul, vous pouvez omettre la définition de `Use` dans votre classe de générateur.

L’exemple de code suivant montre une expression de calcul qui encapsule un calcul, telle qu’une série d’étapes qui peut être évaluée une seule étape à la fois. Un type d’union, de différencier `OkOrException`, encode l’état d’erreur de l’expression, telle qu’évaluée jusqu'à présent. Ce code illustre plusieurs modèles communs que vous pouvez utiliser dans vos expressions de calcul, telles que des implémentations de certaines méthodes de générateur réutilisable.

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

Une expression de calcul possède un type sous-jacent, ce qui renvoie de l’expression. Le type sous-jacent peut représenter un résultat calculées ou un calcul retardé qui peut être effectué, ou elle peut fournir un moyen pour une itération au sein d’un type de collection. Dans l’exemple précédent, le type sous-jacent a été **finalement**. Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pour une expression de requête, le type sous-jacent est <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Pour un flux de travail asynchrone, le type sous-jacent est [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). Le `Async` objet représente le travail à effectuer pour calculer le résultat. Par exemple, vous appelez [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pour exécuter un calcul et de retourner le résultat.

## <a name="custom-operations"></a>Opérations personnalisées
Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée en tant qu’opérateur dans une expression de calcul. Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête. Lorsque vous définissez une opération personnalisée, vous devez définir le taux de rendement et les méthodes dans l’expression de calcul. Pour définir une opération personnalisée, placée dans une classe de générateur pour l’expression de calcul, puis appliquez le [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Cet attribut prend une chaîne en tant qu’argument, qui est le nom à utiliser dans une opération personnalisée. Ce nom est fourni dans la portée au début de l’accolade ouvrante de l’expression de calcul. Par conséquent, vous ne devez pas utiliser des identificateurs qui ont le même nom qu’une opération personnalisée dans ce bloc. Par exemple, évitez l’utilisation des identificateurs comme `all` ou `last` dans les expressions de requête.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Flux de travail asynchrones](asynchronous-workflows.md)

[Séquences](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Expressions de requête](query-expressions.md)
