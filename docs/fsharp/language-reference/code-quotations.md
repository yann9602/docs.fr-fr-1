---
title: Quotations de code (F#)
description: "En savoir plus sur F # quotations de code, une fonctionnalité de langage qui vous permet de générer et d’utiliser des expressions de code F # par programmation."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4559e659-2b04-48bd-8a0b-8527920eec95
ms.openlocfilehash: f7a08013bc6487b570a62576bb01ca2dd65ce8b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="code-quotations"></a>Quotations de code

> [!NOTE]
Le lien des informations de référence sur les API pointe vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette rubrique décrit *quotations de code*, une fonctionnalité de langage qui vous permet de générer et d’utiliser des expressions de code F # par programmation. Cette fonctionnalité vous permet de générer une arborescence de syntaxe abstraite qui représente le code F #. L’arborescence de syntaxe abstraite peut ensuite être parcouru et traité en fonction des besoins de votre application. Par exemple, vous pouvez utiliser l’arborescence pour générer du code F # ou générer du code dans un autre langage.


## <a name="quoted-expressions"></a>Expressions entre guillemets
A *entre guillemets expression* est une expression F # dans votre code qui est délimitée de sorte qu’il n’est pas compilé dans le cadre de votre programme, mais au lieu de cela est compilé dans un objet qui représente une expression F #. Vous pouvez marquer une expression entre guillemets de deux manières : avec des informations de type ou sans informations de type. Si vous souhaitez inclure des informations de type, vous utilisez les symboles `<@` et `@>` pour délimiter l’expression entre guillemets. Si vous n’avez pas besoin d’informations de type, vous utilisez les symboles `<@@` et `@@>`. Le code suivant montre les quotations typées et non typées.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Parcourir une grande arborescence d’expression est plus rapide si vous n’incluez pas les informations de type. Le type résultant d’une expression entre guillemets avec les symboles typés est `Expr<'T>`, où le paramètre de type a le type de l’expression, comme déterminé par l’algorithme d’inférence de type du compilateur F #. Lorsque vous utilisez des quotations de code sans informations de type, le type de l’expression entre guillemets est le type non générique [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Vous pouvez appeler la [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) propriété typées `Expr` classe pour obtenir la non typé `Expr` objet.

Il existe une multitude de méthodes statiques qui vous permettent de générer des objets expression F # par programmation dans le `Expr` classe sans utiliser les expressions quotées.

Notez qu’une quotation de code doit inclure une expression complète. Pour un `let` de liaison, par exemple, vous devez la définition du nom lié et d’une expression supplémentaire qui utilise la liaison. Dans la syntaxe détaillée, il s’agit d’une expression qui suit le `in` (mot clé). Au niveau supérieur dans un module, il s’agit simplement l’expression suivante dans le module, mais dans une quotation, elle est explicitement obligatoire.

Par conséquent, l’expression suivante n’est pas valide.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

En revanche, les expressions suivantes sont valides.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Pour utiliser des quotations de code, vous devez ajouter une déclaration d’importation (à l’aide de la `open` mot clé) qui ouvre le [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) espace de noms.

F # PowerPack fournit la prise en charge pour l’évaluation et de l’exécution d’objets expression F #.


## <a name="expr-type"></a>Type expr
Une instance de la `Expr` type représente une expression F #. Génériques et non génériques `Expr` types sont documentés dans la documentation de la bibliothèque F #. Pour plus d’informations, consultez [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) et [Quotations.expr, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).


## <a name="splicing-operators"></a>L’ajout d’opérateurs
L’ajout de vous permet de combiner les quotations de code littéral avec les expressions que vous avez créé par programme ou à partir d’une autre quotation de code. Le `%` et `%%` opérateurs activent vous permet d’ajouter un objet expression F # dans une quotation de code. Vous utilisez la `%` opérateur pour insérer un objet expression typé dans une quotation typée ; si vous utilisez la `%%` opérateur pour insérer un objet d’expression non typé dans une quotation non typée. Les deux opérateurs sont des opérateurs préfixés unaires. Par conséquent, si `expr` est une expression non typée de type `Expr`, le code suivant est valid.

```fsharp
<@@ 1 + %%expr @@>
```

Et si `expr` est une quotation typée de type `Expr<int>`, le code suivant est valid.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description
L’exemple suivant illustre l’utilisation de quotations de code pour placer le code F # dans un objet d’expression, puis imprimer le code F # qui représente l’expression. Une fonction `println` est définie qui contient une fonction récursive `print` qui affiche un objet expression F # (de type `Expr`) dans un format convivial. Il existe plusieurs modèles actifs dans le [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) et [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules qui peuvent être utilisés pour analyser des objets expression. Cet exemple n’inclut pas tous les modèles possibles susceptibles d’apparaître dans une expression F #. Un modèle non reconnu déclenche une correspondance au modèle de caractère générique (`_`) et est rendu à l’aide de la `ToString` (méthode), qui, sur le `Expr` de type, vous permet de connaître le modèle actif à ajouter à votre expression de correspondance.


### <a name="code"></a>Code
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>Sortie

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description
Vous pouvez également utiliser les trois modèles actifs dans le [module ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) pour parcourir les arborescences d’expression avec moins de modèles actifs. Ces modèles actifs peuvent être utiles lorsque vous souhaitez parcourir une arborescence, mais vous n’avez pas besoin de toutes les informations dans la plupart des nœuds. Lorsque vous utilisez ces modèles, toute expression F # correspond à l’un des trois modèles suivants : `ShapeVar` si l’expression est une variable, `ShapeLambda` si l’expression est une expression lambda, ou `ShapeCombination` si l’expression est autre chose. Si vous parcourez une arborescence d’expression en utilisant les modèles actifs comme dans l’exemple de code précédent, vous devez utiliser beaucoup plus de modèles pour gérer tous les types d’expression F # possibles et votre code sera plus complexe. Pour plus d’informations, consultez [ExprShape.ShapeVar &#124; ShapeLambda &#124; ShapeCombination, modèle actif](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

L’exemple de code suivant peut être utilisé comme base pour le parcours plus complexes. Dans ce code, une arborescence d’expression est créée pour une expression qui implique un appel de fonction, `add`. Le [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) (modèle actif) est utilisé pour détecter tout appel à `add` dans l’arborescence d’expression. Ce modèle actif assigne les arguments de l’appel à la `exprList` valeur. Dans ce cas, il ne étant que deux, ils sont extraits et la fonction est appelée de manière récursive sur les arguments. Les résultats sont insérés dans une quotation de code qui représente un appel à `mul` à l’aide de l’opérateur d’ajout (`%%`). Le `println` fonction de l’exemple précédent est utilisée pour afficher les résultats.

Le code dans les autres branches de modèle actif régénère simplement la même arborescence d’expression, donc la seule modification dans l’expression résultante est la modification à partir de `add` à `mul`.


### <a name="code"></a>Code
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>Sortie

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

