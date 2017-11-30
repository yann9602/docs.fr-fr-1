---
title: Types F#
description: "En savoir plus sur les types qui sont utilisés en F # et comment les types F # sont nommés et décrits."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c7272a0d-5ab6-4eae-bceb-e49af498b917
ms.openlocfilehash: 9b7235637f301f91ae2cc8fbc59adc27cdfd5bd0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="f-types"></a>Types F#

Cette rubrique décrit les types qui sont utilisés en F # et comment les types F # sont nommés et décrits.


## <a name="summary-of-f-types"></a>Résumé des Types F #
Certains types sont considérés comme *les types primitifs*, telles que le type booléen `bool` et les types intégraux et à virgule flottante de différentes tailles, qui incluent les types pour les octets et les caractères. Ces types sont décrits dans [les Types primitifs](primitive-types.md).

Les autres types qui sont intégrées au langage incluent les tuples, les listes, les tableaux, les séquences, enregistrements et les unions discriminées. Si vous avez expérience avec d’autres langages .NET et vous apprenez F #, vous devez lire les rubriques pour chacun de ces types. Des liens vers plus d’informations sur ces types sont inclus dans le [rubriques connexes](https://msdn.microsoft.com/library/#rel) section de cette rubrique. F #-types spécifiques prennent en charge les styles de programmation qui sont communes aux langages de programmation fonctionnelle. La plupart de ces types ont des modules associés dans la bibliothèque F # qui prennent en charge les opérations courantes sur ces types.

Le type d’une fonction inclut des informations sur les types de paramètres et type de retour.

Le .NET Framework est la source des types d’objet, types interface, types délégués et d’autres. Vous pouvez définir vos propres types d’objet comme vous le faites dans n’importe quel autre langage .NET.

Également, code F # peut définir des alias, qui sont nommées *abréviations de type*, qui sont d’autres noms pour les types. Vous pouvez utiliser les abréviations de type lorsque le type peut changer à l’avenir et que vous souhaitez éviter de modifier le code qui dépend du type. Ou bien, vous pouvez utiliser une abréviation de type comme un nom convivial pour un type qui peut rendre le code plus facile à lire et comprendre.

F # fournit des types de collection utile conçues avec la programmation fonctionnelle à l’esprit. L’utilisation de ces types de collections vous permet d’écrire du code qui est plus fonctionnel dans le style. Pour plus d’informations, consultez [Types de Collection F #](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Syntaxe pour les Types
Dans le code F #, vous devez souvent écrire les noms de types. Chaque type a une forme syntaxique, et vous utilisez ces formes syntaxiques dans les annotations de type, les déclarations de méthode abstraite, déclarations delegate, signatures et autres constructions. Chaque fois que vous déclarez une nouvelle construction de programme dans l’interpréteur, l’interpréteur imprime le nom de la construction et la syntaxe pour son type. Cette syntaxe peut être simplement un identificateur pour un type défini par l’utilisateur ou un identificateur intégré tels que les `int` ou `string`, mais pour des types complexes, la syntaxe est plus complexe.

Le tableau suivant montre les aspects de la syntaxe de type pour des types F #.



|Type|Syntaxe de type|Exemples|
|----|-----------|--------|
|type primitif|*nom de type*|`int`<br /><br />`float`<br /><br />`string`|
|type d’agrégation (classe, structure, union, enregistrement, enum et ainsi de suite)|*nom de type*|`System.DateTime`<br /><br />`Color`|
|abréviation de type|*nom de l’abréviation de type*|`bigint`|
|type qualifié complet|*nom de Namespaces.type*<br /><br />ou<br /><br />*nom de modules.type*<br /><br />ou<br /><br />*nom de Namespaces.modules.type*|`System.IO.StreamWriter`|
|array|*nom de type*[] ou<br /><br />*nom de type* tableau|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|Tableau à deux dimensions|*nom de type*[,]|`int[,]`<br /><br />`float[,]`|
|Tableau à trois dimensions|*nom de type*[,]|`float[,,]`|
|tuple|*type-nom1* &#42; *nom2 de type* ...|Par exemple, `(1,'b',3)` a un type`int * char * int`|
|type générique|*paramètre de type* *nom de type générique*<br /><br />ou<br /><br />*nom de type générique*&lt;*liste de paramètres de type*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|type (un type générique qui a un argument de type spécifique fourni) construit|*argument de type* *nom de type générique*<br /><br />ou<br /><br />*nom de type générique*&lt;*liste d’arguments type*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|type de fonction qui a un paramètre unique|*paramètre-type1*  - &gt; *type de retour*|Une fonction qui accepte une `int` et retourne un `string` a un type`int -> string`|
|type de fonction qui a plusieurs paramètres|*paramètre-type1*  - &gt; *paramètre-type2*  - &gt; ... -&gt; *type de retour*|Une fonction qui accepte une `int` et un `float` et retourne un `string` a un type`int -> float -> string`|
|fonction d’ordre supérieur en tant que paramètre|(*type de fonction*)|`List.map`a un type`('a -> 'b) -> 'a list -> 'b list`|
|délégué|délégué de *type de fonction*|`delegate of unit -> int`|
|type flexible|#*nom de type*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Rubriques connexes


|Rubrique|Description|
|-----|-----------|
|[Types primitifs](primitive-types.md)|Décrit les types intégrés simples tels que les types intégraux, le type booléen et les types de caractères.|
|[Type d’unité](unit-type.md)|Décrit la `unit` type, un type qui a une valeur et qui est indiqué par () ; équivalent au `void` en c# et `Nothing` en Visual Basic.|
|[Tuples](tuples.md)|Décrit le type de tuple, un type qui se compose de valeurs associées de n’importe quel type groupées en paires, triples, quadruples et ainsi de suite.|
|[Options](options.md)|Décrit le type d’option, un type qui peut avoir une valeur ou être vide.|
|[Listes](lists.md)|Décrit les listes, qui sont des séries immuables et ordonnée d’éléments du même type.|
|[Tableaux](arrays.md)|Décrit les tableaux, qui sont des jeux ordonnés d’éléments mutables du même type qui occupent un bloc contigu de mémoire et qui sont de taille fixe.|
|[Séquences](sequences.md)|Décrit le type de séquence, ce qui représente une série logique de valeurs ; les valeurs individuelles sont calculées uniquement si nécessaire.|
|[Enregistrements](records.md)|Décrit le type d’enregistrement, un petit agrégat de valeurs nommées.|
|[Unions discriminées](discriminated-unions.md)|Décrit le type d’union discriminé, un type dont les valeurs peuvent être l’un d’un ensemble de types possibles.|
|[Fonctions](functions/index.md)|Décrit les valeurs de la fonction.|
|[Classes](classes.md)|Décrit le type de classe, un type d’objet qui correspond à un type référence .NET. Types de classe peuvent contenir des membres, les propriétés, les interfaces implémentées et un type de base.|
|[Structures](structures.md)|Décrit la `struct` type, un type d’objet qui correspond à un type valeur .NET. Le `struct` type représente généralement un petit agrégat de données.|
|[Interfaces](interfaces.md)|Décrit les types interface, qui sont des types qui représentent un jeu de membres qui fournissent certaines fonctionnalités, mais qui contiennent pas de données. Un type d’interface doit être implémenté par un type d’objet pour être utile.|
|[Délégués](delegates.md)|Décrit le type délégué, qui représente une fonction en tant qu’objet.|
|[Énumérations](enumerations.md)|Décrit les types énumération, dont les valeurs appartiennent à un ensemble de valeurs nommées.|
|[Attributs](attributes.md)|Décrit les attributs qui sont utilisés pour spécifier des métadonnées pour un autre type.|
|[Types d'exceptions](exception-handling/exception-types.md)|Décrit les exceptions, qui spécifient des informations sur l’erreur.|
