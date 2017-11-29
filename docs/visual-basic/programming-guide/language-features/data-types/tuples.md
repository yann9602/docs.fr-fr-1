---
title: Tuples dans Visual Basic
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be50b22e9acca9ff8cfbde798d78869ee1c72634
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tuples-visual-basic"></a>Tuples (Visual Basic)

À partir de Visual Basic 2017, du langage Visual Basic propose une prise en charge intégrée pour les tuples qui permet de créer des tuples et accéder aux éléments de tuples plus facile. Un tuple est une structure de données de légers qui a un nombre spécifique et une séquence de valeurs. Lorsque vous instanciez le tuple, vous définissez le nombre et le type de données de chaque valeur (ou élément). Par exemple, un objet de 2 tuples (ou paire) a deux éléments. La première peut être un `Boolean` valeur, alors que le second est un `String`. Étant donné que les tuples permettent de stocker plusieurs valeurs dans un objet unique, ils sont souvent utilisés comme une solution légère pour retourner plusieurs valeurs à partir d’une méthode.

> [!IMPORTANT]
> Prise en charge de tuple nécessite le <xref:System.ValueTuple> type. Si le 4.7 Framework .NET n’est pas installé, vous devez ajouter le package NuGet `System.ValueTuple`, qui est disponible sur la galerie NuGet. Sans ce package, vous pouvez obtenir une erreur de compilation semblable à « Type prédéfini 'ValueTuple(Of,,,)' n’est pas défini ou importé. »

## <a name="instantiating-and-using-a-tuple"></a>Instanciation et l’utilisation d’un tuple

Vous instanciez un tuple en mettant ses parenthèses de messagerie instantanée de valeurs délimitées par des virgules. Chacune de ces valeurs devient alors un champ du tuple. Par exemple, le code suivant définit une triple (ou un objet de 3 tuples) avec un `Date` comme première valeur, un `String` en tant que le second et un `Boolean` en tant que son troisième.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Par défaut, le nom de chaque champ dans un tuple se compose de la chaîne `Item` , ainsi que la basée sur une position dans le tuple. Pour cet objet de 3 tuples, les `Date` champ est `Item1`, le `String` champ est `Item2`et le `Boolean` champ est `Item3`. L’exemple suivant affiche les valeurs des champs du tuple instanciée dans la ligne de code précédente

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Les champs d’un tuple Visual Basic sont en lecture-écriture ; une fois que vous avez instancié un tuple, vous pouvez modifier ses valeurs. L’exemple suivant modifie deux des trois champs de tuple créés dans l’exemple précédent et affiche le résultat.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Instanciation et l’utilisation d’un tuple nommé

Au lieu d’utiliser des noms par défaut pour les champs d’un tuple, vous pouvez instancier un *nommé tuple* en assignant vos propres noms pour les éléments du tuple. Les champs du tuple sont ensuite accessible par leurs noms attribués *ou* par leurs noms par défaut. L’exemple suivant instancie le tuple de 3 même comme précédemment, à ceci près qu’il nomme explicitement le premier champ `EventDate`, le deuxième `Name`et la troisième `IsHoliday`. Il affiche les valeurs de champ, les modifie et affiche les valeurs de champ à nouveau.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="tuples-versus-structures"></a>Tuples et structures

Un tuple de Visual Basic est un type valeur qui est une instance de l’un de l’un **System.ValueTuple** types génériques. Par exemple, le `holiday` tuple défini dans l’exemple précédent est une instance de la <xref:System.ValueTuple%603> structure. Il est conçu pour être un conteneur léger pour les données. Étant donné que le tuple vise pour faciliter la création d’un objet avec plusieurs éléments de données, il ne dispose pas de certaines fonctionnalités susceptibles de présenter une structure personnalisée. Elles incluent notamment :

- Les membres des clients. Vous ne pouvez pas définir vos propres propriétés, méthodes ou événements pour un tuple.

- Validation. Impossible de valider les données assignées à des champs.

- Immuabilité. Les tuples Visual Basic sont mutables. En revanche, une structure personnalisée permet de vous contrôler si une instance est mutable ou immuable.

Si des membres personnalisés, la propriété et la validation de champ ou que l’immuabilité est importante, vous devez utiliser Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) instruction afin de définir un type de valeur personnalisée.

Un tuple de Visual Basic n’hérite pas les membres de sa **ValueTuple** type. En plus de ses champs, notamment les méthodes suivantes :

| Membre | Description |
| ---|---|
| CompareTo | Compare le tuple actif à un autre tuple avec le même nombre d’éléments. |
| Equals | Détermine si le tuple actif est égal à un autre objet ou tuple. |
| GetHashCode | Calcule le code de hachage pour l’instance actuelle. |
| ToString | Retourne la représentation sous forme de chaîne de ce tuple, qui prend la forme `(Item1, Item2...)`, où `Item1` et `Item2` représentent les valeurs des champs du tuple. |

En outre, le **ValueTuple** types implémentent <xref:System.Collections.IStructuralComparable> et <xref:System.Collections.IStructuralEquatable> interfaces, ce qui vous permet de définir des comparateurs de client.

## <a name="assignment-and-tuples"></a>Affectation et tuples

Visual Basic prend en charge l’assignation entre les types de tuple qui ont le même nombre de champs. Les types de champs peuvent être converties si une des conditions suivantes est remplie :

- Le champ source et cible sont du même type.

- Une conversion étendue (ou implicite) du type de source pour le type de cible est définie. 

- `Option Strict`est `On`, et une conversion restrictive (ou explicite) du type de source pour le type de cible est définie. Cette conversion peut lever une exception si la valeur source est en dehors de la plage du type cible.

Les autres conversions ne sont pas prises en compte pour les affectations. Examinons les types d’affectation qui sont autorisés entre les types tuple.

Prenez en compte les variables utilisées dans les exemples suivants :

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

Les deux premières variables `unnamed` et `anonymous`, n’ont pas de noms sémantiques fournies pour les champs. Leurs noms de champ sont la valeur par défaut `Item1` et `Item2`. Les deux dernières variables `named` et `differentName` ont des noms de champ de sémantique. Notez que ces deux tuples ont des noms différents pour les champs.

Les quatre de ces tuples ont le même nombre de champs (également appelé « arité ») et les types de ces champs sont identiques. Par conséquent, toutes ces affectations fonctionnent :

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notez que les noms des tuples ne sont pas affectés. Les valeurs des champs sont affectées suivant l’ordre des champs dans le tuple.

Enfin, notez que nous pouvons attribuer le `named` tuple à la `conversion` tuple, même si le premier champ de `named` est un `Integer`et le premier champ de `conversion` est un `Long`. Cette attribution a réussi, car la conversion d’un `Integer` à un `Long` est une conversion étendue.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples avec différents nombres de champs ne sont pas être assignés :

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuples comme valeurs de retour de méthode

Une méthode peut retourner une seule valeur. Souvent, cependant, vous aimeriez un appel de méthode pour retourner plusieurs valeurs. Il existe plusieurs façons de contourner cette limitation :

- Vous pouvez créer une classe personnalisée ou une structure dont les propriétés ou champs représentent les valeurs retournées par la méthode. Par conséquent, est une solution de haute densité. Il requiert que vous définissez un type personnalisé dont seul objectif consiste à récupérer les valeurs à partir d’un appel de méthode.

- Vous pouvez retourner une valeur unique à partir de la méthode et renvoyer les valeurs restantes en les passant par référence à la méthode. Cela implique la surcharge de l’instanciation d’une variable et les risques par inadvertance en remplaçant la valeur de la variable que vous passez par référence.

- Vous pouvez utiliser un tuple, qui fournit une solution légère pour la récupération de plusieurs valeurs de retour.

Par exemple, le **TryParse** méthodes de retour de .NET un `Boolean` valeur qui indique si l’opération d’analyse a réussi. Le résultat de l’opération d’analyse est retourné dans une variable passée par référence à la méthode. Normalement, un appel à l’une méthode d’analyse comme <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> présente l’aspect suivant :

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Nous pouvons retourner un tuple à partir de l’opération d’analyse, si nous encapsulent l’appel à la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode dans votre propre méthode. Dans l’exemple suivant, `NumericLibrary.ParseInteger` appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode et retourne un tuple nommé avec deux éléments. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Vous pouvez ensuite appeler la méthode avec un code semblable au suivant :

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Les tuples de Visual Basic et les tuples dans le .NET Framework

Un tuple de Visual Basic est une instance de l’un de le **System.ValueTuple** des types génériques qui ont été introduits dans le 4.7 Framework .NET. Le .NET Framework inclut également un ensemble de génériques **System.Tuple** classes. Ces classes, toutefois, diffèrent des tuples de Visual Basic et le **System.ValueTuple** des types génériques dans de plusieurs façons :

- Les éléments de la **Tuple** les classes sont des propriétés nommées `Item1`, `Item2`, et ainsi de suite. Dans Visual Basic tuples et **ValueTuple** types d’éléments de tuple, sont des champs.

- Vous ne pouvez attribuer des noms explicites pour les éléments d’un **Tuple** instance ou d’un **ValueTuple** instance. Visual Basic vous permet d’attribuer des noms qui communiquent la signification des champs.

- Les propriétés d’un **Tuple** instance sont en lecture seule ; les tuples sont immuables. Dans Visual Basic tuples et **ValueTuple** , types de champs de tuple sont en lecture-écriture ; les tuples sont mutables.

- Le type générique **Tuple** types sont des types référence. L’utilisation de ces **Tuple** types signifie que de l’allocation d’objets. Sur des chemins réactifs, cela peut avoir un impact mesurable sur les performances de votre application. Visual Basic tuples et **ValueTuple** types sont des types valeur.

Méthodes d’extension dans le <xref:System.TupleExtensions> classe facilitent la conversion entre des tuples de Visual Basic et .NET **Tuple** objets. Le **ToTuple** méthode convertit un tuple de Visual Basic .NET **Tuple** objet et le **ToValueTuple** méthode convertit un .NET **Tuple** objet à un tuple de Visual Basic.

L’exemple suivant crée un tuple, le convertit en un .NET **Tuple** objet et convertit le retour à un tuple de Visual Basic. L’exemple compare ensuite ce tuple avec celui d’origine pour vous assurer qu’ils sont égaux.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage Visual Basic](index.md)  
