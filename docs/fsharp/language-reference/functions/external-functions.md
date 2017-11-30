---
title: Fonctions externes (F#)
description: 'Obtenir des informations sur la prise en charge de langage F # pour appeler des fonctions dans le code natif.'
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c26b6124-ceaa-471c-9dc9-861b4dfa332a
ms.openlocfilehash: 4f525b2b750c2ce42230c61aa0e72f957739b206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="external-functions"></a>Fonctions externes

Cette rubrique décrit F # prise en charge linguistique pour appeler des fonctions dans le code natif.

## <a name="syntax"></a>Syntaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Remarques

Dans la syntaxe précédente, *arguments* représente les arguments fournis à la `System.Runtime.InteropServices.DllImportAttribute` attribut. Le premier argument est une chaîne qui représente le nom de la DLL qui contient cette fonction, sans l’extension .dll. Arguments supplémentaires peuvent être fournis pour une des propriétés publiques de la `System.Runtime.InteropServices.DllImportAttribute` (classe), telles que la convention d’appel.

Vous possédez une DLL C++ qui contient la fonction exportée suivante natif.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Vous pouvez appeler cette fonction à partir de F # en utilisant le code suivant.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Interopérabilité avec du code natif est appelée *non managé* et est une fonctionnalité du CLR. Pour plus d’informations, consultez [Interopération avec du code non managé](https://msdn.microsoft.com/library/sd10k43k.aspx). Les informations contenues dans cette section sont applique à F #.


## <a name="see-also"></a>Voir aussi

[Fonctions](index.md)
