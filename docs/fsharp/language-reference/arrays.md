---
title: Tableaux (F#)
description: "Découvrez comment créer et utiliser des tableaux dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 61fa9084-abdc-4cf5-8213-91ec1211866b
ms.openlocfilehash: 7c9d8405230f4d765d3afdeaa154ddc598d0d1ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="arrays"></a>Tableaux

> [!NOTE]
Le lien des informations de référence sur les API pointe vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Les tableaux sont des collections de taille fixe, de base zéro et mutables d’éléments de données consécutifs qui sont tous du même type.

## <a name="creating-arrays"></a>Création de tableaux
Vous pouvez créer des tableaux de plusieurs façons. Vous pouvez créer un petit tableau en répertoriant des valeurs consécutives entre `[|` et `|]` et séparées par des points-virgules, comme illustré dans les exemples suivants.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

Vous pouvez également placer chaque élément sur une ligne distincte, auquel cas le point-virgule de séparation est facultatif.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

Le type des éléments du tableau est déduit des littéraux utilisés et doit être cohérent. Le code suivant génère une erreur, car 1.0 est une valeur float et 2 et 3 sont des entiers.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Vous pouvez également utiliser des expressions de séquence pour créer des tableaux. Voici un exemple qui crée un tableau des carrés des entiers de 1 à 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

Pour créer un tableau dans lequel tous les éléments sont initialisés à zéro, utilisez `Array.zeroCreate`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a>L’accès aux éléments

Vous pouvez accéder à des éléments de tableau à l’aide d’un opérateur point (`.`) et des crochets (`[` et `]`).

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

Index de tableau commencent à 0.

Vous pouvez également accéder à des éléments de tableau à l’aide de notation de découpage, ce qui vous permet de spécifier une sous-plage du tableau. Voici quelques exemples de notation de découpage.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

Lors de la notation de découpage est utilisée, une nouvelle copie du tableau est créée.


## <a name="array-types-and-modules"></a>Modules et Types de tableau
Le type de tous les tableaux F # est le type .NET Framework <xref:System.Array?displayProperty=nameWithType>. Par conséquent, les tableaux F # prennent en charge toutes les fonctionnalités disponibles dans <xref:System.Array?displayProperty=nameWithType>.

Le module de bibliothèque [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) prend en charge les opérations sur les tableaux unidimensionnels. Les modules `Array2D`, `Array3D`, et `Array4D` contiennent des fonctions qui prennent en charge les opérations sur les tableaux de deux, trois et quatre dimensions, respectivement. Vous pouvez créer des tableaux de rang supérieur à quatre à l’aide de <xref:System.Array?displayProperty=nameWithType>.

### <a name="simple-functions"></a>Fonctions simples
[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Obtient un élément. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)donne la longueur d’un tableau. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)définit un élément à une valeur spécifiée. L’exemple de code suivant illustre l’utilisation de ces fonctions.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

La sortie est la suivante.

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Fonctions qui créent des tableaux

Plusieurs fonctions de créer des tableaux sans nécessiter un tableau existant. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)Crée un tableau qui ne contient-elle pas d’éléments. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Crée un tableau d’une taille spécifiée et affecte tous les éléments de valeurs fournies. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)Crée un tableau, en fonction d’une dimension et une fonction pour générer les éléments. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)Crée un tableau dans lequel tous les éléments sont initialisés à la valeur zéro pour le type du tableau. Le code suivant illustre ces fonctions.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

La sortie est la suivante.

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Crée un tableau qui contient des éléments copiés à partir d’un tableau existant. Notez que la copie est une copie superficielle, ce qui signifie que si le type d’élément est un type référence, uniquement la référence est copiée, pas l’objet sous-jacent. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

La sortie du code précédent est la suivante :

```
[|Test1; Test2; |]
[|; Test2; |]
```

La chaîne `Test1` s’affiche uniquement dans le premier tableau parce que l’opération de création d’un nouvel élément remplace la référence dans `firstArray` mais n’affecte ne pas la référence d’origine à une chaîne vide est toujours présente dans `secondArray`. La chaîne `Test2` s’affiche dans les deux tableaux, car le `Insert` opération sur le <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affecte sous-jacent <xref:System.Text.StringBuilder?displayProperty=nameWithType> objet, qui est référencé dans les deux tableaux.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)génère un nouveau tableau à partir d’une sous-plage d’un tableau. Vous spécifiez la sous-plage en fournissant l’index de départ et la longueur. Le code suivant montre l'utilisation de `Array.sub`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

La sortie indique que le sous-tableau démarre à l’élément 5 et contienne 10 éléments.

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)Crée un nouveau tableau combinant deux tableaux existants.

Le code suivant montre comment **Array.append**.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

La sortie du code précédent est comme suit.

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)Sélectionne les éléments d’un tableau à inclure dans un nouveau tableau. Le code suivant montre comment `Array.choose`. Notez que le type d’élément du tableau n’est pas nécessairement correspond au type de la valeur retournée dans le type d’option. Dans cet exemple, le type d’élément est `int` et l’option est le résultat d’une fonction polynomiale, `elem*elem - 1`, comme flottante point nombre.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

La sortie du code précédent est comme suit.

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)exécute une fonction spécifiée sur chaque élément du tableau d’un tableau existant puis collecte les éléments générés par la fonction et les combine dans un nouveau tableau. Le code suivant montre comment `Array.collect`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

La sortie du code précédent est comme suit.

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)prend une séquence de tableaux et les combine dans un tableau. Le code suivant montre comment `Array.concat`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

La sortie du code précédent est comme suit.

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)prend une fonction de condition booléenne et génère un nouveau tableau qui contient uniquement les éléments du tableau d’entrée pour lesquels la condition est remplie. Le code suivant montre comment `Array.filter`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

La sortie du code précédent est comme suit.

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)génère un nouveau tableau en inversant l’ordre d’un tableau existant. Le code suivant montre comment `Array.rev`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

La sortie du code précédent est comme suit.

```
"Hello world!"
```

Vous pouvez facilement combiner des fonctions du module array qui transforment les tableaux à l’aide de l’opérateur de pipeline (`|>`), comme illustré dans l’exemple suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

La sortie est la suivante :

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Tableaux multidimensionnels

Un tableau multidimensionnel peut être créé, mais il n’existe aucune syntaxe pour l’écriture d’un littéral de tableau multidimensionnel. Utilisez l’opérateur [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) pour créer un tableau à partir d’une séquence de séquences d’éléments de tableau. Les séquences peuvent être des littéraux de tableau ou de liste. Par exemple, le code suivant crée un tableau à deux dimensions.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

Vous pouvez également utiliser la fonction [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) pour initialiser des tableaux de deux dimensions et même des fonctions sont disponibles pour les tableaux de trois et quatre dimensions. Ces fonctions acceptent une fonction qui est utilisée pour créer les éléments. Pour créer un tableau à deux dimensions qui contient les éléments pour définir une valeur initiale au lieu de spécifier une fonction, utilisez la [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) (fonction), qui est également disponible pour les tableaux jusqu'à quatre dimensions. L’exemple de code suivant tout d’abord comment créer un tableau de tableaux qui contiennent les éléments souhaités, puis utilise `Array2D.init` pour générer le tableau à deux dimensions souhaité.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

Tableau d’indexation et de découpage de syntaxe est prise en charge pour les tableaux jusqu'à rang 4. Lorsque vous spécifiez un index dans plusieurs dimensions, vous utilisez des virgules pour séparer les index, comme illustré dans l’exemple de code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
Le type d’un tableau à deux dimensions est écrit en tant que `<type>[,]` (par exemple, `int[,]`, `double[,]`), et le type d’un tableau tridimensionnel est écrit en tant que `<type>[,,]`, et ainsi de suite pour les tableaux de dimensions supérieures.

Uniquement un sous-ensemble des fonctions disponibles pour les tableaux unidimensionnels est également disponible pour les tableaux multidimensionnels. Pour plus d’informations, consultez [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), et [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Le découpage de tableau et les tableaux multidimensionnels

Dans un tableau à deux dimensions (matrice), vous pouvez extraire une matrice sous-chemin en spécifiant des plages et à l’aide d’un caractère générique (`*`) pour spécifier des lignes entières ou des colonnes.

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

À compter de F # 3.1, vous pouvez décomposer un tableau multidimensionnel sous-tableaux de la dimension égale ou inférieure. Par exemple, vous pouvez obtenir un vecteur à partir d’une matrice en spécifiant une seule ligne ou colonne.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Vous pouvez utiliser cette syntaxe pour les types qui implémentent les opérateurs d’accès élément et d’une surcharge de découpage `GetSlice` méthodes. Par exemple, le code suivant crée un type de matrice qui encapsule le tableau 2D F #, implémente une propriété d’élément pour prendre en charge l’indexation de tableau et trois versions de `GetSlice`. Si vous pouvez utiliser ce code en tant que modèle pour vos types de matrice, vous pouvez utiliser toutes les opérations de découpage décrites dans cette section.

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>Fonctions booléennes sur les tableaux

Les fonctions [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) et [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) tester des éléments dans un ou deux tableaux, respectivement. Ces fonctions acceptent une fonction de test et de retour `true` s’il existe un élément (ou des paires d’éléments pour `Array.exists2`) qui satisfait la condition.

Le code suivant illustre l’utilisation de `Array.exists` et `Array.exists2`. Dans ces exemples, les nouvelles fonctions sont créées en appliquant un des arguments, dans ces cas, l’argument de fonction uniquement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

La sortie du code précédent est comme suit.

```
true
false
false
true
```

De même, la fonction [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) teste un tableau pour déterminer si chaque élément satisfait à une condition booléenne. La variation [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) produit la même chose à l’aide d’une fonction booléenne qui implique les éléments de deux tableaux de longueur égale. Le code suivant illustre l’utilisation de ces fonctions.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

Le résultat de ces exemples est comme suit.

```
false
true
true
false
```

### <a name="searching-arrays"></a>Recherche dans les tableaux

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)prend une fonction booléenne et retourne le premier élément pour lequel la fonction retourne `true`, ou déclenche un <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> si aucun élément qui satisfait la condition n’a été trouvé. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)est semblable à `Array.find`, sauf qu’il retourne l’index de l’élément au lieu de l’élément lui-même.

Le code suivant utilise `Array.find` et `Array.findIndex` pour trouver un nombre qui est un carré et un cube parfait.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

La sortie est la suivante.

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)est semblable à `Array.find`, sauf que son résultat est un type d’option, et elle retourne `None` si aucun élément n’est trouvé. `Array.tryFind`doit être utilisé à la place de `Array.find` lorsque vous ne connaissez pas si un élément correspondant est dans le tableau. De même, [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) est similaire à [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) , sauf que le type d’option est la valeur de retour. Si aucun élément n’est trouvé, l’option est `None`.

Le code suivant montre l'utilisation de `Array.tryFind`. Ce code varie selon le code précédent.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

La sortie est la suivante.

```
Found an element: 1
Found an element: 729
```

Utilisez [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) lorsque vous devez transformer un élément en plus de la trouver. Le résultat est le premier élément pour lequel la fonction retourne l’élément transformé comme valeur d’option, ou `None` si aucun élément correspondant n’est trouvé.

Le code suivant illustre l'utilisation de `Array.tryPick`. Dans ce cas, au lieu d’une expression lambda, plusieurs fonctions d’assistance locales sont définies pour simplifier le code.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

La sortie est la suivante.

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>Effectuer des calculs sur des tableaux

Le [ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) fonction retourne la moyenne de chaque élément dans un tableau. Il est limité aux types d’éléments qui prennent en charge la division exacte par un entier, ce qui inclut les types virgule flottante, mais pas les types intégraux. Le [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) fonction retourne la moyenne des résultats de l’appel d’une fonction sur chaque élément. Pour un tableau de type intégral, vous pouvez utiliser `Array.averageBy` et que la fonction convertisse chaque élément flottante type pour le calcul de point.

Utilisez [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) ou [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) pour obtenir l’élément minimale ou maximale, si le type d’élément prend en charge. De même, [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) et [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) permettent à une fonction à exécuter tout d’abord, par exemple, pour transformer un type qui prend en charge la comparaison.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)Ajoute les éléments d’un tableau, et [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) appelle une fonction sur chaque élément et additionne les résultats.

Pour exécuter une fonction sur chaque élément dans un tableau sans stocker les valeurs de retour, utilisez [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). Pour une fonction qui implique deux tableaux de longueur égale, utilisez [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Si vous devez également garder un tableau des résultats de la fonction, utilisez [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) ou [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), qui fonctionne sur deux tableaux à la fois.

Les variantes [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) et [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) permettre à l’index de l’élément à être impliqué dans le calcul ; vaut également pour [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) et [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).

Les fonctions [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), et [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) exécutent des algorithmes qui impliquent tous les éléments d’un tableau. De même, les variations [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) et [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) effectuer des calculs sur deux tableaux.

Ces fonctions pour effectuer des calculs correspondent aux fonctions du même nom dans la [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Pour obtenir des exemples, consultez [répertorie](lists.md).

### <a name="modifying-arrays"></a>Modification de tableaux

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)définit un élément à une valeur spécifiée. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)définit une plage d’éléments dans un tableau à une valeur spécifiée. Le code suivant fournit un exemple de `Array.fill`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

La sortie est la suivante.

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Vous pouvez utiliser [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) pour copier une sous-section d’un tableau à un autre tableau.

### <a name="converting-to-and-from-other-types"></a>Conversion vers et depuis d’autres Types

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)Crée un tableau à partir d’une liste. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)Crée un tableau à partir d’une séquence. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)et [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convertir ces autres types de collection à partir du type de tableau.

### <a name="sorting-arrays"></a>Tri de tableaux

Utilisez [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) pour trier un tableau à l’aide de la fonction de comparaison générique. Utilisez [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) pour spécifier une fonction qui génère une valeur, appelé un *clé*, pour trier à l’aide de la fonction de comparaison générique sur la clé. Utilisez [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) si vous souhaitez fournir une fonction de comparaison personnalisée. `Array.sort`, `Array.sortBy`, et `Array.sortWith` retournent toutes le tableau trié comme nouveau tableau. Les variantes [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), et [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modifient le tableau existant au lieu de retourner un nouveau.

### <a name="arrays-and-tuples"></a>Tableaux et Tuples

Les fonctions [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) et [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convertissent des tableaux de paires de tuples en tuples de tableaux et vice versa. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)et [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) sont similaires à ceci près qu’ils fonctionnent avec des tuples de trois éléments ou des tuples de trois tableaux.

## <a name="parallel-computations-on-arrays"></a>Calculs parallèles sur les tableaux

Le module [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contient des fonctions permettant d’effectuer les calculs parallèles sur les tableaux. Ce module n’est pas disponible dans les applications qui ciblent des versions du .NET Framework antérieures à la version 4.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[F #; Types de](fsharp-types.md)
