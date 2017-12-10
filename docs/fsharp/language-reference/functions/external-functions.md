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
ms.openlocfilehash: 69b73983a91bc6c7cc38fa34484a3c89fc01858f
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="external-functions"></a><span data-ttu-id="c04a7-104">Fonctions externes</span><span class="sxs-lookup"><span data-stu-id="c04a7-104">External Functions</span></span>

<span data-ttu-id="c04a7-105">Cette rubrique décrit F # prise en charge linguistique pour appeler des fonctions dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="c04a7-105">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c04a7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c04a7-106">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="c04a7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c04a7-107">Remarks</span></span>

<span data-ttu-id="c04a7-108">Dans la syntaxe précédente, *arguments* représente les arguments fournis à la `System.Runtime.InteropServices.DllImportAttribute` attribut.</span><span class="sxs-lookup"><span data-stu-id="c04a7-108">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="c04a7-109">Le premier argument est une chaîne qui représente le nom de la DLL qui contient cette fonction, sans l’extension .dll.</span><span class="sxs-lookup"><span data-stu-id="c04a7-109">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="c04a7-110">Arguments supplémentaires peuvent être fournis pour une des propriétés publiques de la `System.Runtime.InteropServices.DllImportAttribute` (classe), telles que la convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="c04a7-110">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="c04a7-111">Vous possédez une DLL C++ qui contient la fonction exportée suivante natif.</span><span class="sxs-lookup"><span data-stu-id="c04a7-111">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="c04a7-112">Vous pouvez appeler cette fonction à partir de F # en utilisant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="c04a7-112">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="c04a7-113">Interopérabilité avec du code natif est appelée *non managé* et est une fonctionnalité du CLR.</span><span class="sxs-lookup"><span data-stu-id="c04a7-113">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="c04a7-114">Pour plus d’informations, consultez [Interopération avec du code non managé](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="c04a7-114">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="c04a7-115">Les informations contenues dans cette section sont applique à F #.</span><span class="sxs-lookup"><span data-stu-id="c04a7-115">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="c04a7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c04a7-116">See Also</span></span>

[<span data-ttu-id="c04a7-117">Fonctions</span><span class="sxs-lookup"><span data-stu-id="c04a7-117">Functions</span></span>](index.md)
