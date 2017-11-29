---
title: Gestion des exceptions (F#)
description: "Découvrez les principes fondamentaux de la gestion des exceptions dans F # et des liens vers des expressions et des fonctions de gestion des exceptions."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="1344f-104">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="1344f-104">Exception Handling</span></span>

<span data-ttu-id="1344f-105">Cette section contient des informations sur la prise en charge de la gestion des exceptions en langage F#.</span><span class="sxs-lookup"><span data-stu-id="1344f-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="1344f-106">Concepts de base de la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="1344f-106">Exception Handling Basics</span></span>
<span data-ttu-id="1344f-107">La gestion des exceptions constitue le moyen standard de gérer les conditions d’erreur dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1344f-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="1344f-108">Par conséquent, tout langage .NET doit prendre en charge ce mécanisme, notamment F#.</span><span class="sxs-lookup"><span data-stu-id="1344f-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="1344f-109">Une *exception* est un objet qui encapsule des informations sur une erreur.</span><span class="sxs-lookup"><span data-stu-id="1344f-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="1344f-110">Quand des erreurs se produisent, des exceptions sont déclenchées et l’exécution normale s’arrête.</span><span class="sxs-lookup"><span data-stu-id="1344f-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="1344f-111">Le runtime recherche alors un gestionnaire approprié pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="1344f-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="1344f-112">La recherche démarre dans la fonction active et remonte dans la pile en passant par les couches d’appelants jusqu’à ce qu’un gestionnaire correspondant soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="1344f-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="1344f-113">Le gestionnaire est ensuite exécuté.</span><span class="sxs-lookup"><span data-stu-id="1344f-113">Then the handler is executed.</span></span>

<span data-ttu-id="1344f-114">De plus, à mesure que la pile est déroulée, le runtime exécute le code présent dans les blocs `finally` pour garantir que les objets sont nettoyés correctement pendant le processus de déroulement.</span><span class="sxs-lookup"><span data-stu-id="1344f-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="1344f-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="1344f-115">Related Topics</span></span>

|<span data-ttu-id="1344f-116">Titre</span><span class="sxs-lookup"><span data-stu-id="1344f-116">Title</span></span>|<span data-ttu-id="1344f-117">Description</span><span class="sxs-lookup"><span data-stu-id="1344f-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="1344f-118">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="1344f-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="1344f-119">Décrit comment déclarer un type d’exception.</span><span class="sxs-lookup"><span data-stu-id="1344f-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="1344f-120">Exceptions : expression `try...with`</span><span class="sxs-lookup"><span data-stu-id="1344f-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="1344f-121">Décrit la construction de langage qui prend en charge la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="1344f-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="1344f-122">Exceptions : expression `try...finally`</span><span class="sxs-lookup"><span data-stu-id="1344f-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="1344f-123">Décrit la construction de langage qui vous permet d’exécuter du code de nettoyage à mesure que la pile se déroule quand une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="1344f-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="1344f-124">Exceptions : fonction `raise`</span><span class="sxs-lookup"><span data-stu-id="1344f-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="1344f-125">Décrit comment lever un objet exception.</span><span class="sxs-lookup"><span data-stu-id="1344f-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="1344f-126">Exceptions : fonction `failwith`</span><span class="sxs-lookup"><span data-stu-id="1344f-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="1344f-127">Décrit comment générer une exception F# générale.</span><span class="sxs-lookup"><span data-stu-id="1344f-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="1344f-128">Exceptions : fonction `invalidArg`</span><span class="sxs-lookup"><span data-stu-id="1344f-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="1344f-129">Décrit comment générer une exception d’argument non valide.</span><span class="sxs-lookup"><span data-stu-id="1344f-129">Describes how to generate an invalid argument exception.</span></span>|
