---
title: "Chaînes (F#)"
description: "Découvrez comment le type 'string') (F # représente le texte immuable en tant que séquence de caractères Unicode."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a>Chaînes

> [!NOTE]
Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Le `string` type représente le texte immuable en tant que séquence de caractères Unicode. `string` est un alias pour `System.String` dans le .NET Framework.

## <a name="remarks"></a>Remarques
Littéraux de chaîne sont délimités par le caractère guillemet ("). Le caractère barre oblique inverse (\) est utilisé pour encoder certains caractères spéciaux. La barre oblique inverse et le caractère suivant forment sont appelés un *séquence d’échappement*. Prise en charge dans les littéraux sont affichés dans le tableau suivant de chaîne F # de séquences d’échappement.

|Caractère|Séquence d'échappement|
|---------|---------------|
|Retour arrière|\b|
|Saut de ligne|\n|
|Retour chariot|\r|
|Onglet|\t|
|Barre oblique inverse|\\|
|Guillemet|\"|
|Apostrophe|\'|
|caractère Unicode|\u*XXXX* ou \U*XXXXXXXX* (où *X* indique un chiffre hexadécimal)|

Si précédé par le symbole @, le littéral est une chaîne textuelle. Cela signifie que les séquences d’échappement sont ignorés, sauf que deux caractères de guillemet sont interprétés comme un guillemet.

En outre, une chaîne peut être placé entre guillemets triples. Dans ce cas, toutes les séquences d’échappement sont ignorés, y compris les caractères de guillemet double. Pour spécifier une chaîne qui contient un élément incorporé chaîne entre guillemets, vous pouvez utiliser une chaîne textuelle ou une chaîne à guillemets triples. Si vous utilisez une chaîne textuelle, vous devez spécifier deux guillemets pour indiquer un caractère de guillemet. Si vous utilisez une chaîne à guillemets triples, vous pouvez utiliser les caractères de guillemet simple sans les analysé en tant que la fin de la chaîne. Cette technique peut être utile lorsque vous travaillez avec XML ou d’autres structures qui incluent des guillemets incorporés.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Dans le code, les chaînes qui ont des sauts de ligne sont acceptées et les sauts de ligne sont interprétées littéralement en tant que nouvelles lignes, sauf si un caractère de barre oblique inverse est le dernier caractère avant le saut de ligne. Espaces de début de la ligne suivante est ignoré lorsque le caractère de barre oblique inverse est utilisé. Le code suivant produit une chaîne `str1` qui a la valeur `"abc\n     def"` et une chaîne `str2` qui a la valeur `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Vous pouvez accéder à des caractères individuels dans une chaîne à l’aide de la syntaxe de type tableau, comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Le résultat est `b`.

Ou vous pouvez extraire des sous-chaînes à l’aide de la syntaxe de tranche tableau, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

La sortie est la suivante.

```
abc
def
```

Vous pouvez représenter les chaînes ASCII par des tableaux d’octets non signés, de type `byte[]`. Vous ajoutez le suffixe `B` à un littéral de chaîne pour indiquer qu’il s’agit d’une chaîne ASCII. Les littéraux de chaîne ASCII utilisés avec les tableaux d’octets prend en charge les séquences d’échappement même sous forme de chaînes Unicode à l’exception des séquences d’échappement Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>Opérateurs de chaîne
Il existe deux façons de concaténer des chaînes : à l’aide de la `+` opérateur ou à l’aide de la `^` opérateur. Le `+` opérateur assure la compatibilité avec la chaîne .NET Framework de la gestion des fonctionnalités.

L’exemple suivant illustre la concaténation de chaînes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>Classe de chaîne
Car le type de chaîne en F # est réellement un .NET Framework `System.String` de type, tous les `System.String` membres sont disponibles. Cela inclut la `+` opérateur, qui est utilisé pour concaténer des chaînes, la `Length` propriété et le `Chars` propriété, qui retourne la chaîne sous la forme d’un tableau de caractères Unicode. Pour plus d’informations sur les chaînes, consultez `System.String`.

À l’aide de la `Chars` propriété du `System.String`, vous pouvez accéder à des caractères individuels dans une chaîne en spécifiant un index, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>Module de chaîne
Fonctionnalités supplémentaires pour la gestion des chaînes sont incluses dans le `String` module dans le `FSharp.Core` espace de noms. Pour plus d’informations, consultez [Core.String, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
