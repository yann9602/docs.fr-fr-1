---
title: "Littéraux (F#)"
description: "En savoir plus sur les types de littéral dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a>Littéraux

> [!NOTE]
Les liens de référence des API dans cet article vous permettront MSDN (pour l’instant).

Cette rubrique fournit une table qui montre comment spécifier le type d’un littéral en F #.

## <a name="literal-types"></a>Types de littéral
Le tableau suivant indique les types de littéraux en F #. Les caractères qui représentent des chiffres en notation hexadécimale ne sont pas la casse ; les caractères qui identifient le type respectent la casse.

|Type|Description|Préfixe ou suffixe|Exemples|
|----|-----------|----------------|--------|
|sbyte|Entier signé 8 bits|o|`86y`<br /><br />`0b00000101y`|
|byte|nombre non signé 8 bits|UY|`86uy`<br /><br />`0b00000101uy`|
|int16|Entier signé 16 bits.|s|`86s`|
|uint16|nombre non signé 16 bits|us|`86us`|
|int<br /><br />int32|Entier signé 32 bits|l ou none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|nombre de naturel 32 bits non signé|u ou ul|`86u`<br /><br />`86ul`|
|unativeint|pointeur natif sous forme de nombre naturel non signé|Annuler|`0x00002D3Fun`|
|int64|Entier signé 64 bits|L|`86L`|
|uint64|nombre non signé 64 bits|UL|`86UL`|
|float32 unique,|nombre à virgule flottante 32 bits|F ou f|`4.14F` ou `4.14f`|
|||saut de ligne|`0x00000000lf`|
|type float ; Double|nombre à virgule flottante 64 bits|aucun|`4.14`ou `2.3E+32` ou`2.3e+32`|
|||SAUT DE LIGNE|`0x0000000000000000LF`|
|bigint|entier non limité à la représentation sous forme de 64 bits|I|`9999999999999999999999999999I`|
|decimal|nombre de fractions de seconde représentée comme un point fixe ou d’un nombre rationnel|M ou m|`0.7833M` ou `0.7833m`|
|Char|caractère Unicode|aucun|`'a'`|
|Chaîne|chaîne Unicode|aucun|`"text\n"`<br /><br />ou<br /><br />`@"c:\filename"`<br /><br />ou<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />ou<br /><br />`"string1" + "string2"`<br /><br />Voir aussi [chaînes](Strings.md).|
|byte|Caractère ASCII|B|`'a'B`|
|byte[]|Chaîne ASCII|B|`"text"B`|
|[] String ou byte|chaîne textuelle|préfixe @|`@"\\server\share"`(Unicode)<br /><br />`@"\\server\share"B`(ASCII)|

## <a name="remarks"></a>Remarques
Chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivi d’un code hexadécimal 16 bits ou les encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivi d’un code hexadécimal 32 bits qui représente un Unicode paire de substitution.

À compter de F # 3.1, vous pouvez utiliser le `+` se connecter pour combiner des littéraux de chaîne. Vous pouvez également utiliser l’opérateur de bits ou (`|||`) opérateur pour combiner les indicateurs de l’enum. Par exemple, le code suivant est autorisé dans F # 3.1 :

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

L’utilisation d’autres opérateurs de bits n’est pas autorisée.


## <a name="named-literals"></a>Littéraux nommés
Les valeurs qui sont destinés à être des constantes peuvent être marquées avec le [littéral](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribut. Cet attribut a pour effet de provoquer une valeur doit être compilé en tant que constante.

Dans les expressions de critères spéciaux, les identificateurs qui commencent par les caractères minuscules sont toujours traités en tant que variables d’être lié, plutôt que comme des littéraux, par conséquent, vous devez généralement utiliser majuscules lorsque vous définissez des littéraux.

## <a name="integers-in-other-bases"></a>Nombres entiers dans d’autres Bases

Entiers signés de 32 bits peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide un `0x`, `0o` ou `0b` respectivement de préfixe.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Traits de soulignement dans les littéraux numériques

À compter de F # 4.1, vous pouvez séparer les chiffres par le caractère de soulignement (`_`).

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>Voir aussi

[Core.LiteralAttribute, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
