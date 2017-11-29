---
title: Assertions (F#)
description: "Découvrez comment utiliser l’expression 'assert' comme une fonctionnalité de débogage pour tester des expressions dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a><span data-ttu-id="db09e-104">Assertions</span><span class="sxs-lookup"><span data-stu-id="db09e-104">Assertions</span></span>

<span data-ttu-id="db09e-105">Le `assert` expression est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression.</span><span class="sxs-lookup"><span data-stu-id="db09e-105">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="db09e-106">En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.</span><span class="sxs-lookup"><span data-stu-id="db09e-106">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="db09e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db09e-107">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="db09e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="db09e-108">Remarks</span></span>

<span data-ttu-id="db09e-109">Le `assert` l’expression est de type `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="db09e-109">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="db09e-110">Dans la syntaxe précédente, *condition* représente une expression booléenne qui doit être testée.</span><span class="sxs-lookup"><span data-stu-id="db09e-110">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="db09e-111">Si l’expression prend la valeur `true`, l’exécution se poursuit normalement.</span><span class="sxs-lookup"><span data-stu-id="db09e-111">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="db09e-112">Si elle a la valeur `false`, une boîte de dialogue d’erreur système est générée.</span><span class="sxs-lookup"><span data-stu-id="db09e-112">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="db09e-113">La boîte de dialogue d’erreur comprend une légende qui contient la chaîne **Échec de l’Assertion**.</span><span class="sxs-lookup"><span data-stu-id="db09e-113">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="db09e-114">La boîte de dialogue contient une trace de pile qui indique où l’échec d’assertion s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db09e-114">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="db09e-115">La vérification des assertions est activée uniquement lorsque vous compilez en mode débogage ; Autrement dit, si la constante `DEBUG` est défini.</span><span class="sxs-lookup"><span data-stu-id="db09e-115">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="db09e-116">Dans le système de projet, par défaut, le `DEBUG` constante est définie dans la configuration Debug, mais pas dans la configuration Release.</span><span class="sxs-lookup"><span data-stu-id="db09e-116">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="db09e-117">Erreur d’échec de l’assertion ne peut pas être intercepté à l’aide de la gestion des exceptions) (F #.</span><span class="sxs-lookup"><span data-stu-id="db09e-117">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="db09e-118">Le `assert` fonction correspond à <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db09e-118">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="db09e-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="db09e-119">Example</span></span>

<span data-ttu-id="db09e-120">L’exemple de code suivant illustre l’utilisation de la `assert` expression.</span><span class="sxs-lookup"><span data-stu-id="db09e-120">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="db09e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db09e-121">See Also</span></span>

[<span data-ttu-id="db09e-122">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="db09e-122">F# Language Reference</span></span>](index.md)
