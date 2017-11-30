---
title: "Comment : utiliser le bloc Try-Catch pour intercepter des Exceptions"
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
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a72a21085c37bed4d84518810f69a013d515189
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="a230a-102">Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions</span><span class="sxs-lookup"><span data-stu-id="a230a-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="a230a-103">Placez les sections de code qui peuvent lever des exceptions dans un bloc `try` et placez le code qui gère les exceptions dans un bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="a230a-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="a230a-104">Le bloc `catch` est une série d’instructions qui commencent par le mot clé `catch`, suivi d’un type d’exception et d’une action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="a230a-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="a230a-105">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception possible.</span><span class="sxs-lookup"><span data-stu-id="a230a-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="a230a-106">La méthode `Main` contient un bloc `try` avec une instruction <xref:System.IO.StreamReader> qui ouvre un fichier de données appelé `data.txt` et écrit une chaîne à partir du fichier.</span><span class="sxs-lookup"><span data-stu-id="a230a-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="a230a-107">À la suite du bloc `try`, un bloc `catch` intercepte toute exception qui résulte du bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="a230a-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="a230a-108">Le Common Language Runtime intercepte les exceptions qui ne sont pas interceptées par un bloc catch.</span><span class="sxs-lookup"><span data-stu-id="a230a-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="a230a-109">Selon la configuration du runtime, une boîte de dialogue de débogage s’affiche, le programme s’arrête et une boîte de dialogue s’affiche avec des informations sur l’exception, ou une erreur est imprimée dans STDERR.</span><span class="sxs-lookup"><span data-stu-id="a230a-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="a230a-110">Presque toutes les lignes de code peuvent provoquer une exception, en particulier les exceptions levées par le Common Language Runtime lui-même, comme <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="a230a-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="a230a-111">La plupart des applications n’ont pas à traiter ces exceptions, mais vous devez être conscient de cette possibilité quand vous écrivez des bibliothèques destinées à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a230a-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="a230a-112">Afin d’obtenir des suggestions pour savoir quand définir du code dans un bloc Try, consultez les [Bonnes pratiques pour les exceptions](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a230a-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a230a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a230a-113">See Also</span></span>  
[<span data-ttu-id="a230a-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="a230a-114">Exceptions</span></span>](index.md)
