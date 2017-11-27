---
title: "Unités de mesure (F#)"
description: "Découvrez comment flottantes et des valeurs de l’entier signé en F # peuvent être associée à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume et en série."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a>Unités de mesure

Virgule flottante et valeurs de l’entier signé en F # peut avoir associé à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume, en série, et ainsi de suite. À l’aide de quantités avec des unités, vous activez le compilateur de vérifier que les relations arithmétiques ont les bonnes unités, qui permet d’éviter les erreurs de programmation.


## <a name="syntax"></a>Syntaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Remarques
La syntaxe précédente définit *-nom de l’unité* en tant qu’unité de mesure. La partie facultative est utilisée pour définir une nouvelle mesure en termes d’unités précédemment définies. Par exemple, la ligne suivante définit la mesure `cm` (centimètre).

```fsharp
[<Measure>] type cm
```

La ligne suivante définit la mesure `ml` (millilitre) comme un centimètre cube (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

Dans la syntaxe précédente, *mesure* est une formule qui implique des unités. Dans les formules qui impliquent des unités, les puissances intégrales sont prises en charge (positives et négatives), des espaces entre les unités indiquent un produit des deux unités, `*` indique également un produit d’unités, et `/` indique un quotient d’unités. Pour une unité réciproque, vous pouvez utiliser une puissance entière négative ou un `/` qui indique une séparation entre le numérateur et le dénominateur d’une formule d’unité. Plusieurs unités dans le dénominateur doivent être placées entre parenthèses. Unités séparant par des espaces après un `/` sont interprétées comme faisant partie du dénominateur, mais n’importe quelle unité suivant un `*` sont interprétées comme faisant partie du numérateur.

Vous pouvez utiliser 1 dans les expressions d’unité, soit seul pour indiquer une quantité sans dimension, ou avec d’autres unités, comme dans le numérateur. Par exemple, les unités pour un taux est écrit en tant que `1/s`, où `s` indique les secondes. Parenthèses ne sont pas utilisées dans les formules d’unité. Vous ne spécifiez pas de constantes de conversion numériques dans les formules d’unité ; Toutefois, vous pouvez définir séparément des constantes de conversion avec des unités et les utiliser dans les calculs de vérification des unités.

Les formules d’unité qui ont la même signification peuvent être écrites de plusieurs façons équivalentes. Par conséquent, le compilateur convertit les formules d’unité dans un format cohérent, qui convertit des puissances négatives réciproques, unités de groupes dans un seul numérateur et dénominateur et trie par ordre alphabétique les unités dans le numérateur et dénominateur.

Par exemple, les formules d’unité `kg m s^-2` et `m /s s * kg` sont converties en `kg m/s^2`.

Vous utilisez des unités de mesure dans les expressions virgule flottante. À l’aide de nombres à virgule flottante avec les unités associées de mesure ajoute un autre niveau de sécurité de type, et permet d’éviter les erreurs d’incompatibilité unité qui peuvent se produire dans les formules lorsque vous utilisez des nombres à virgule flottante faiblement typée. Si vous écrivez flottante point expression qui utilise les unités, les unités dans l’expression doivent correspondre.

Vous pouvez annoter des littéraux avec une formule d’unité figurant entre crochets, comme indiqué dans les exemples suivants.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Vous ne placez pas d’espace entre le nombre et le crochet pointu ; Toutefois, vous pouvez inclure un suffixe littéral comme `f`, comme dans l’exemple suivant.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Une telle annotation modifie le type du littéral de son type primitif (tel que `float`) en un type dimensionné, tel que `float<cm>` ou, dans ce cas, `float<miles/hour>`. Une annotation d’unité `<1>` indique une quantité sans dimension et son type équivaut au type primitif sans paramètre d’unité.

Le type d’une unité de mesure est une virgule flottante ou un type intégral avec une annotation d’unité supplémentaire, indiquée entre crochets signé. Par conséquent, lorsque vous écrivez le type d’une conversion de `g` (g) à `kg` (kg), vous décrivez les types comme suit.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Unités de mesure sont utilisées pour la vérification des unités de compilation, mais ne sont pas conservées dans l’environnement d’exécution. Par conséquent, ils n’affectent pas les performances.

Unités de mesure peuvent être appliquées à n’importe quel type, pas seulement types à virgule flottante ; Toutefois, seuls les types virgule flottante, signé types intégraux et les types décimaux prise en charge dimensionné quantités. Par conséquent, il convient uniquement pour les unités de mesure sur les types primitifs et les agrégats qui contiennent ces types primitifs.

L’exemple suivant illustre l’utilisation d’unités de mesure.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
L’exemple de code suivant illustre comment convertir à partir d’un nombre à virgule flottante sans dimension en une valeur à virgule flottante dimensionnée. Vous multipliez simplement par 1.0, appliquant les dimensions à la version 1.0. Vous pouvez l’abstraite dans une fonction comme `degreesFahrenheit`.

En outre, lorsque vous passez des valeurs dimensionnées à des fonctions qui attendent des nombres à virgule flottante sans dimension, vous devez annuler les unités ou castée en `float` à l’aide de la `float` opérateur. Dans cet exemple, vous divisez par `1.0<degC>` pour les arguments de `printf` car `printf` attend des quantités sans dimension.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

La session de l’exemple suivant montre les sorties et les entrées à ce code.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Utilisation d’unités génériques
Vous pouvez écrire des fonctions génériques qui fonctionnent sur les données associées à une unité de mesure. Cela en spécifiant un type avec une unité générique comme paramètre de type, comme illustré dans l’exemple de code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>Création de Types d’agrégation avec des unités génériques
Le code suivant montre comment créer un type d’agrégation qui se compose de valeurs à virgule flottante individuelles avec des unités génériques. Ainsi, un seul type qui fonctionne avec un large éventail d’unités doit être créé. Unités génériques conservent également, la sécurité de type en veillant à ce qu’un type générique qui a un jeu d’unités est un autre type que le même type générique avec un autre ensemble d’unités. La base de cette technique est que le `Measure` attribut peut être appliqué au paramètre de type.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>Unités lors de l’exécution
Unités de mesure sont utilisées pour la vérification de type statique. Lorsque des valeurs à virgule flottante sont compilées, les unités de mesure sont éliminées, les unités sont perdues au moment de l’exécution. Par conséquent, toute tentative d’implémenter des fonctionnalités qui dépendent de la vérification des unités au moment de l’exécution n’est pas possible. Par exemple, la mise en œuvre un `ToString` pour imprimer les unités (fonction) n’est pas possible.


## <a name="conversions"></a>Conversions
Pour convertir un type qui a des unités (par exemple, `float<'u>`) à un type qui n’a pas d’unités, vous pouvez utiliser la fonction de conversion standard. Par exemple, vous pouvez utiliser `float` pour convertir un `float` valeur qui n’a pas d’unités, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Pour convertir une valeur sans unité en une valeur qui a des unités, vous pouvez multiplier par une valeur 1 ou 1.0 annotée avec les unités appropriées. Toutefois, pour écrire des couches d’interopérabilité, il existe également certaines fonctions explicites que vous pouvez utiliser pour convertir des valeurs sans unité en valeurs avec des unités. Ils se trouvent dans le [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module. Par exemple, pour convertir un sans unité `float` à un `float<cm>`, utilisez [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), comme illustré dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>Unités de mesure dans le F # Power Pack
Une bibliothèque d’unités est disponible dans le F # PowerPack. La bibliothèque d’unités inclut des unités SI et des constantes physiques.


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
