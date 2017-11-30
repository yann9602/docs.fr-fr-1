---
title: "Comment : utiliser des exceptions spécifiques dans un bloc catch"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="485e7-102">L’utilisation d’exceptions spécifiques dans un bloc catch</span><span class="sxs-lookup"><span data-stu-id="485e7-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="485e7-103">En général, il est conseillé d’intercepter un type spécifique d’exception au lieu d’utiliser un base `catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="485e7-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="485e7-104">Quand une exception se produit, elle remonte la pile et chaque bloc catch a la possibilité de la gérer.</span><span class="sxs-lookup"><span data-stu-id="485e7-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="485e7-105">L’ordre des instructions catch est important.</span><span class="sxs-lookup"><span data-stu-id="485e7-105">The order of catch statements is important.</span></span> <span data-ttu-id="485e7-106">Placez les blocs catch ciblés sur des exceptions spécifiques avant un bloc catch d’exceptions générales, sinon le compilateur peut générer une erreur.</span><span class="sxs-lookup"><span data-stu-id="485e7-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="485e7-107">Le bloc catch approprié est déterminé en mettant en correspondance le type de l’exception avec le nom de l’exception spécifiée dans le bloc catch.</span><span class="sxs-lookup"><span data-stu-id="485e7-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="485e7-108">S’il n’existe aucun bloc catch spécifique, l’exception est interceptée par un bloc catch général, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="485e7-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="485e7-109">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="485e7-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="485e7-110">L’exemple crée une classe appelée `Employee` avec une propriété unique, le niveau de l’employé (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="485e7-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="485e7-111">Une méthode `PromoteEmployee` prend un objet et incrémente le niveau de l’employé.</span><span class="sxs-lookup"><span data-stu-id="485e7-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="485e7-112">Une exception <xref:System.InvalidCastException> se produit quand une instance <xref:System.DateTime> est passée à la méthode `PromoteEmployee`.</span><span class="sxs-lookup"><span data-stu-id="485e7-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="485e7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="485e7-113">See Also</span></span>  
[<span data-ttu-id="485e7-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="485e7-114">Exceptions</span></span>](index.md)
