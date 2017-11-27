---
title: "Surcharge d'opérateur (F#)"
description: "Découvrez comment surcharger des opérateurs arithmétiques dans une classe ou un type d’enregistrement et au niveau global dans F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 019277ed-f649-4fa5-ad43-097865f449d9
ms.openlocfilehash: 76ddab5339e11d71bb326b60d727017eb838ccf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="operator-overloading"></a>Surcharge d'opérateur

Cette rubrique décrit comment surcharger des opérateurs arithmétiques dans une classe ou un type d’enregistrement et au niveau global.


## <a name="syntax"></a>Syntaxe

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Remarques
Dans la syntaxe précédente, le *symbole d’opérateur* est un des `+`, `-`, `*`, `/`, `=`, et ainsi de suite. Le *la liste des paramètres* spécifie les opérandes dans l’ordre d’apparition dans la syntaxe standard pour cet opérateur. Le *corps de la méthode* construit la valeur résultante.

Les surcharges d’opérateur pour les opérateurs doivent être statiques. Surcharges d’opérateur pour les opérateurs unaires, telles que `+` et `-`, doivent utiliser un tilde (`~`) dans le *symbole d’opérateur* pour indiquer que l’opérateur est un opérateur unaire et non un opérateur binaire, comme indiqué dans les déclaration suivante.

```fsharp
static member (~-) (v : Vector)
```

Le code suivant illustre une classe de vecteur qui a uniquement deux opérateurs, un pour moins unaire et un pour la multiplication par un scalaire. Dans l’exemple, deux surcharges pour la multiplication scalaire sont nécessaires, car l’opérateur doit fonctionner indépendamment de l’ordre dans lequel le vecteur et le scalaire apparaissent.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Création d’opérateurs
Vous pouvez surcharger tous les opérateurs standards, mais vous pouvez également créer des opérateurs hors des séquences de certains caractères. Opérateur caractères autorisés sont `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, et `~`. Le `~` a une signification spéciale de la création d’un opérateur unaire du caractère et ne fait pas partie de la séquence de caractères d’opérateur. Tous les opérateurs ne peuvent être rendus unaires.

En fonction de la séquence de caractères exacte que vous utilisez, votre opérateur aura une certaine priorité et l’associativité. Peut être soit de gauche à droite ou de droite à gauche des opérateurs et associativité est utilisée chaque fois que les opérateurs ayant le même niveau de priorité apparaissent en séquence sans parenthèses.

Le caractère d’opérateur `.` n’affecte pas le niveau de priorité, afin que, par exemple, si vous souhaitez définir votre propre version de multiplication qui a la même priorité et associativité en tant que multiplication ordinaire, vous pouvez créer les opérateurs tels que `.*`.

Seuls les opérateurs `?` et `?<-` peut commencer par `?`.

Vous trouverez un tableau qui indique la priorité de tous les opérateurs en F # dans [référence des symboles et opérateur](symbol-and-operator-reference/index.md).


## <a name="overloaded-operator-names"></a>Noms d’opérateurs surchargés
Lorsque le compilateur F # compile une expression d’opérateur, il génère une méthode qui a un nom généré par le compilateur pour cet opérateur. C’est le nom qui apparaît dans le langage intermédiaire Microsoft (MSIL) pour la méthode et également dans la réflexion et IntelliSense. Normalement, vous n’avez pas besoin d’utiliser ces noms dans le code F #.

Le tableau suivant répertorie les opérateurs standard et les noms générés correspondants.



|Opérateur|Nom généré|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
Autres combinaisons de caractères d’opérateur qui ne sont pas répertoriées ici peuvent être utilisés comme opérateurs d’et ont des noms qui sont obtenus en concaténant les noms de caractères individuels dans le tableau suivant. Par exemple, + ! devient `op_PlusBang`.



|Caractère d’opérateur|Nom|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Opérateurs préfixés et infixe
*Préfixe* opérateurs sont supposés être placés devant un ou des opérandes, comme une fonction. *Infix* opérateurs sont supposés être placés entre les deux opérandes.

Seuls certains opérateurs peuvent être utilisés comme opérateurs de préfixe. Certains opérateurs sont toujours des opérateurs de préfixe, d’autres peuvent être infixes ou préfixes, et le reste sont toujours des opérateurs infixes. Les opérateurs qui commencent par `!`, à l’exception de `!=`et l’opérateur `~`, ou répétées de séquences de`~`, sont toujours des opérateurs de préfixe. Les opérateurs `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, et `%%` peuvent être des opérateurs préfixés ou des opérateurs infixes. Vous distinguez la version préfixée de ces opérateurs à partir de la version infix en ajoutant un `~` au début d’un opérateur préfixé lorsqu’il est défini. Le `~` n’est pas utilisé lorsque vous utilisez l’opérateur, uniquement lorsqu’il est défini.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de la surcharge d’opérateur pour implémenter un type de fraction. Une fraction est représentée par un numérateur et dénominateur. La fonction `hcf` est utilisée pour déterminer le facteur commun le plus élevé, qui est utilisé pour réduire les fractions.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Sortie :**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Opérateurs au niveau Global
Vous pouvez également définir des opérateurs au niveau global. Le code suivant définit un opérateur `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

La sortie du code ci-dessus est `12`.

Vous pouvez redéfinir les opérateurs arithmétiques standards de cette manière, car les règles de portée pour F # exigent que les opérateurs nouvellement définis sont prioritaires sur les opérateurs intégrés.

Le mot clé `inline` est souvent utilisé avec des opérateurs globaux, qui sont souvent des petites fonctions qu’il sont préférable d’intégrer dans le code appelant. Fonctions d’opérateur fabrication inline permettent également qu’elle fonctionne avec des paramètres de type résolus statiquement à produire du code générique résolu statiquement. Pour plus d’informations, consultez [les fonctions Inline](functions/inline-functions.md) et [résolus statiquement les paramètres de Type](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Voir aussi
[Membres](members/index.md)
