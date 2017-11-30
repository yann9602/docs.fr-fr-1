---
title: "Référence des mots clés (F#)"
description: "Trouver des liens vers des informations sur tous les mots-clés du langage F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: cdfdd86843acf05a8b33647823f934a161f6d885
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="keyword-reference"></a>Référence des mots clés

Cette rubrique contient des liens vers des informations sur tous les mots clés du langage F #.

## <a name="f-keyword-table"></a>Table de mot clé F #

Le tableau suivant affiche tous les mots-clés F # dans l’ordre alphabétique, ainsi que de brèves descriptions et des liens vers les rubriques qui contiennent des informations supplémentaires.

|Mot clé|Link|Description|
|-------|----|-----------|
|`abstract`|[Membres](members/index.md)<br /><br />[Classes abstraites](abstract-classes.md)|Indique une méthode qui n’a aucune implémentation dans le type dans lequel il est déclaré ou qui est virtuelle et a une implémentation par défaut.|
|`and`|[`let`Liaisons](functions/let-bindings.md)<br /><br />[Membres](members/index.md)<br /><br />[Contraintes](generics/constraints.md)|Utilisé dans les liaisons mutuellement récursives, dans les déclarations de propriété et avec plusieurs contraintes sur les paramètres génériques.|
|`as`|[Classes](classes.md)<br /><br />[Critères spéciaux](Pattern-Matching.md)|Utilisé pour permettre à l’objet de classe actuel à un nom d’objet. Également utilisé pour donner un nom à un modèle entier dans une correspondance de modèle.|
|`assert`|[Assertions](assertions.md)|Utilisé pour vérifier le code pendant le débogage.|
|`base`|[Classes](classes.md)<br /><br />[Héritage](inheritance.md)|Utilisé comme nom de l’objet de classe de base.|
|`begin`|[Syntaxe détaillée](verbose-syntax.md)|Dans la syntaxe détaillée, indique le début d’un bloc de code.|
|`class`|[Classes](classes.md)|Dans la syntaxe détaillée, indique le début d’une définition de classe.|
|`default`|[Membres](members/index.md)|Indique une implémentation d’une méthode abstraite. utilisé avec une déclaration de méthode abstraite pour créer une méthode virtuelle.|
|`delegate`|[Délégués](delegates.md)|Utilisé pour déclarer un délégué.|
|`do`|[Liaisons do](functions/do-bindings.md)<br /><br />[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression `for...in`](loops-for-in-expression.md)<br /><br />[Boucles : expression `while...do`](loops-while-do-expression.md)|Utilisé dans les constructions en boucle ou pour exécuter du code impératif.|
|`done`|[Syntaxe détaillée](verbose-syntax.md)|Dans la syntaxe détaillée indique la fin d’un bloc de code dans une expression en boucle.|
|`downcast`|[Casts et conversions](casting-and-conversions.md)|Utilisé pour convertir un type de niveau inférieur dans la chaîne d’héritage.|
|`downto`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Dans un `for` expression, utilisée lors du comptage dans l’ordre inverse.|
|`elif`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans le branchement conditionnel. Forme abrégée de `else if`.|
|`else`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans le branchement conditionnel.|
|`end`|[Structures](structures.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Enregistrements](records.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Dans les définitions de type et extensions de type, indique la fin d’une section de définitions de membre.<br /><br />Dans la syntaxe détaillée, utilisée pour spécifier la fin d’un bloc de code qui commence par le `begin` (mot clé).|
|`exception`|[Gestion des exceptions](exception-handling/index.md)<br /><br />[Types d'exceptions](exception-handling/exception-types.md)|Utilisé pour déclarer un type d’exception.|
|`extern`|[Fonctions externes](functions/external-functions.md)|Indique qu’un élément de programme déclaré est défini dans un autre binaire ou assembly.|
|`false`|[Types primitifs](primitive-types.md)|Utilisé comme littéral booléen.|
|`finally`|[Exceptions : expression `try...finally`](exception-handling/the-try-finally-expression.md)|Utilisé conjointement avec `try` pour introduire un bloc de code qui s’exécute indépendamment de si une exception se produit.|
|`fixed`|[Fixe](fixed.md)|Utilisé pour « épingler » un pointeur sur la pile pour empêcher le garbage collecté.|
|`for`|[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression for...in](loops-for-in-expression.md)|Utilisée dans les constructions de bouclage.|
|`fun`|[Expressions lambda : Le `fun` (mot clé)](functions/lambda-expressions-the-fun-keyword.md)|Utilisé dans les expressions lambda, également appelées fonctions anonymes.|
|`function`|[Expressions match](match-expressions.md)<br /><br />[Expressions lambda : Mot clé fun](functions/lambda-expressions-the-fun-keyword.md)|Utilisé comme une alternative plus courte pour le `fun` (mot clé) et un `match` expression dans une expression lambda qui a des critères spéciaux sur un argument unique.|
|`global`|[Espaces de noms](namespaces.md)|Utilisé pour référencer l’espace de noms .NET niveau supérieur.|
|`if`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans les constructions de branchement conditionnelles.|
|`in`|[Boucles : expression for...in](loops-for-in-expression.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Utilisé pour les expressions de séquence et, dans la syntaxe détaillée pour séparer les expressions à partir des liaisons.|
|`inherit`|[Héritage](inheritance.md)|Permet de spécifier une classe de base ou l’interface de base.|
|`inline`|[Fonctions](functions/index.md)<br /><br />[Fonctions inline](functions/inline-functions.md)|Utilisé pour indiquer une fonction qui doit être intégrée directement dans le code de l’appelant.|
|`interface`|[Interfaces](interfaces.md)|Utilisé pour déclarer et implémenter des interfaces.|
|`internal`|[Contrôle d'accès](access-control.md)|Permet de spécifier qu’un membre est visible à l’intérieur d’un assembly, mais pas à l’extérieur.|
|`lazy`|[Calculs tardifs](lazy-computations.md)|Utilisé pour spécifier un calcul qui doit être effectuée uniquement lorsqu’un résultat est nécessaire.|
|`let`|[`let`Liaisons](functions/let-bindings.md)|Utilisé pour associer ou lier, un nom à une valeur ou une fonction.|
|`let!`|[Flux de travail asynchrones](asynchronous-workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé dans le flux de travail asynchrone pour lier un nom pour le résultat d’un calcul asynchrone, ou, dans d’autres expressions de calcul, utilisées pour lier un nom à un résultat, qui est du type de calcul.|
|`match`|[Expressions match](match-expressions.md)|Utilisé pour créer une branche en comparant une valeur à un modèle.|
|`member`|[Membres](members/index.md)|Utilisé pour déclarer une propriété ou une méthode dans un type d’objet.|
|`module`|[Modules](modules.md)|Utilisé pour associer un nom à un groupe de types connexes, les valeurs et les fonctions, pour le séparer logiquement depuis un autre code.|
|`mutable`|[Liaisons let](functions/let-bindings.md)|Utilisé pour déclarer une variable, autrement dit, une valeur qui peut être modifiée.|
|`namespace`|[Espaces de noms](namespaces.md)|Utilisé pour associer un nom à un groupe de types associés et modules, pour le séparer logiquement depuis un autre code.|
|`new`|[Constructeurs](members/constructors.md)<br /><br />[Contraintes](generics/constraints.md)|Utilisé pour déclarer, définir ou appeler un constructeur qui crée ou qui peut créer un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique pour indiquer qu’un type doit avoir un certain constructeur.|
|`not`|[Informations de référence des symboles et opérateurs](symbol-and-operator-reference/index.md)<br /><br />[Contraintes](generics/constraints.md)|Pas réellement un mot clé. Toutefois, `not struct` en combinaison est utilisée comme une contrainte de paramètre générique.|
|`null`|[Valeurs Null](values/null-values.md)<br /><br />[Contraintes](generics/constraints.md)|Indique l’absence d’un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique.|
|`of`|[Unions discriminées](discriminated-unions.md)<br /><br />[Délégués](delegates.md)<br /><br />[Types d'exceptions](exception-handling/exception-types.md)|Utilisé dans les unions discriminées pour indiquer le type de catégories de valeurs et dans les déclarations de délégué et d’exception.|
|`open`|[Déclarations d’importation : mot clé `open`](import-declarations-the-open-keyword.md)|Utilisé pour rendre le contenu d’un espace de noms ou un module disponibles sans qualification.|
|`or`|[Informations de référence des symboles et opérateurs](symbol-and-operator-reference/index.md)<br /><br />[Contraintes](generics/constraints.md)|Utilisé avec des conditions booléennes en tant que valeur booléenne `or` opérateur. Équivalent à »||`.<br /><br />Également utilisé dans les contraintes de membre.|
|`override`|[Membres](members/index.md)|Utilisé pour implémenter une version d’une méthode abstraite ou virtuelle qui diffère de la version de base.|
|`private`|[Contrôle d'accès](access-control.md)|Limite l’accès à un membre au code dans le même type ou module.|
|`public`|[Contrôle d'accès](access-control.md)|Autorise l’accès à un membre en dehors du type.|
|`rec`|[Fonctions](functions/index.md)|Utilisé pour indiquer qu’une fonction est récursive.|
|`return`|[Flux de travail asynchrones](Asynchronous-Workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé pour indiquer une valeur à fournir comme résultat d’une expression de calcul.|
|`return!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Permet d’indiquer une expression de calcul qui, lors de l’évaluation, fournit le résultat de l’expression de calcul qui le contient.|
|`select`|[Expressions de requête](query-expressions.md)|Utilisé dans les expressions de requête pour spécifier les champs ou les colonnes à extraire. Notez qu’il s’agit d’un mot clé contextuel, ce qui signifie qu’il n’est pas réellement un mot réservé et il agit uniquement comme un mot clé dans le contexte approprié.|
|`static`|[Membres](members/index.md)|Utilisé pour indiquer une méthode ou propriété qui peut être appelée sans une instance d’un type ou membre qui est partagé entre toutes les instances d’un type valeur.|
|`struct`|[Structures](structures.md)<br /><br />[Contraintes](generics/constraints.md)|Utilisé pour déclarer un type structure.<br /><br />Également utilisé dans les contraintes de paramètre générique.<br /><br />Utilisé pour la compatibilité avec OCaml dans les définitions de module.|
|`then`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Constructeurs](members/constructors.md)|Utilisé dans les expressions conditionnelles.<br /><br />Également utilisé pour exécuter des effets secondaires après la construction d’objet.|
|`to`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Utilisé dans `for` boucles pour indiquer une plage.|
|`true`|[Types primitifs](primitive-types.md)|Utilisé comme littéral booléen.|
|`try`|[Exceptions : L’Expression try... with](exception-handling/the-try-with-expression.md)<br /><br />[Exceptions : Try... finally Expression](exception-handling/the-try-finally-expression.md)|Utilisé pour introduire un bloc de code qui peut générer une exception. Utilisé conjointement avec `with` ou `finally`.|
|`type`|[Types F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Enregistrements](records.md)<br /><br />[Structures](structures.md)<br /><br />[Énumérations](enumerations.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Abréviations de types](type-abbreviations.md)<br /><br />[Unités de mesure](units-of-measure.md)|Utilisé pour déclarer une classe d’enregistrement, structure, union discriminée, type d’énumération, unité de mesure ou l’abréviation de type.|
|`upcast`|[Casts et conversions](casting-and-conversions.md)|Permet de convertir en un type qui est plus élevé dans la chaîne d’héritage.|
|`use`|[Gestion des ressources : mot clé `use`](resource-management-the-use-keyword.md)|Utilisée au lieu de `let` pour les valeurs qui nécessitent `Dispose` à être appelée pour libérer des ressources.|
|`use!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Utilisée au lieu de `let!` dans le flux de travail asynchrones et autres expressions de calcul pour les valeurs qui nécessitent `Dispose` à être appelée pour libérer des ressources.|
|`val`|[Champs explicites : mot clé `val`](members/explicit-fields-the-val-keyword.md)<br /><br />[Signatures](signatures.md)<br /><br />[Membres](members/index.md)|Utilisé dans une signature pour indiquer une valeur, ou dans un type pour déclarer un membre, dans des situations limitées.|
|`void`|[Types primitifs](primitive-types.md)|Indique le .NET `void` type. Utilisé lors de l’interaction avec d’autres langages .NET.|
|`when`|[Contraintes](generics/constraints.md)|Utilisé pour les conditions booléennes (*lorsque gardes*) sur des critères spéciaux et pour introduire une clause de contrainte pour un paramètre de type générique.|
|`while`|[Boucles : expression `while...do`](loops-while-do-expression.md)|Introduit une construction en boucle.|
|`with`|[Expressions match](match-expressions.md)<br /><br />[Expressions d'objet](object-expressions.md)<br /><br />[Copie et mise à jour des expressions d’enregistrement](copy-and-update-record-expressions.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Exceptions : expression `try...with`](exception-handling/the-try-with-expression.md)|Utilisé conjointement avec le `match` mot clé dans les expressions de critères spéciaux. Également utilisé dans les expressions d’objet, copie les expressions d’enregistrement et extensions de type pour introduire des définitions de membres et d’introduire des gestionnaires d’exceptions.|
|`yield`|[Séquences](sequences.md)|Utilisé dans une expression de séquence pour produire une valeur pour une séquence.|
|`yield!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Utilisé dans une expression de calcul pour ajouter le résultat d’une expression de calcul donné à la collection des résultats de l’expression de calcul qui le contient.|

Les jetons suivants sont réservés en F #, car ils sont des mots clés dans le langage OCaml :

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Si vous utilisez la `--mlcompatibility` option du compilateur, les mots clés ci-dessus sont disponibles pour une utilisation en tant qu’identificateurs.

Les jetons suivants sont réservés en tant que mots clés pour une future extension du langage F # :

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `fixed`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Informations de référence des symboles et opérateurs](symbol-and-operator-reference/index.md)

[Options du compilateur](compiler-options.md)
