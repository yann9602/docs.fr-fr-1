---
title: "Identificateurs de ligne, de fichier et de chemin d’accès source (F#)"
description: "Découvrez comment utiliser F # identificateur valeurs intégrées qui vous permettent d’accéder à la source de numéro de ligne, un répertoire et un nom de fichier dans votre code."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a>Identificateurs de ligne, de fichier et de chemin d’accès source

Les identificateurs `__LINE__`, `__SOURCE_DIRECTORY__` et `__SOURCE_FILE__` sont des valeurs intégrées qui vous permettent d’accéder à la ligne source nombre, les répertoires et les fichiers nom dans votre code.


## <a name="syntax"></a>Syntaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Remarques
Chacune de ces valeurs a le type `string`.

Le tableau suivant récapitule la ligne source, fichier et les identificateurs de chemin d’accès qui sont disponibles en F #. Ces identificateurs ne sont pas des macros de préprocesseur ; ils sont des valeurs intégrées qui sont reconnus par le compilateur.

|Identificateur prédéfini|Description|
|---------------------|-----------|
|`__LINE__`|Prend la valeur de numéro de ligne active, vous envisagez de `#line` directives.|
|`__SOURCE_DIRECTORY__`|Prend la valeur de chemin d’accès complet en cours du répertoire source, envisagez `#line` directives.|
|`__SOURCE_FILE__`|Donne le nom du fichier source et son chemin d’accès, vous envisagez de `#line` directives.|
Pour plus d’informations sur la `#line` directive, voir [Directives de compilateur](compiler-directives.md).

## <a name="example"></a>Exemple

L’exemple de code suivant illustre l’utilisation de ces valeurs.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Sortie :

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Voir aussi
[Directives de compilateur](compiler-directives.md)

[Informations de référence du langage F#](index.md)
