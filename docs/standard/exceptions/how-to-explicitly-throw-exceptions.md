---
title: "Comment : lever explicitement des exceptions"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3fce332263dac3f9906d33fe3bd2590050b86f8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="d3b99-102">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="d3b99-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="d3b99-103">Vous pouvez lever explicitement une exception à l’aide de l’instruction `throw`.</span><span class="sxs-lookup"><span data-stu-id="d3b99-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="d3b99-104">Vous pouvez aussi lever de nouveau une exception interceptée à l’aide de l’instruction `throw`.</span><span class="sxs-lookup"><span data-stu-id="d3b99-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="d3b99-105">En codage, il est conseillé d’ajouter des informations à une exception levée une deuxième fois pour fournir plus d’informations durant le débogage.</span><span class="sxs-lookup"><span data-stu-id="d3b99-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="d3b99-106">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.IO.FileNotFoundException> possible.</span><span class="sxs-lookup"><span data-stu-id="d3b99-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="d3b99-107">À la suite du bloc `try`, un bloc `catch` intercepte l’exception <xref:System.IO.FileNotFoundException> et écrit un message dans la console si le fichier de données est introuvable.</span><span class="sxs-lookup"><span data-stu-id="d3b99-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="d3b99-108">L’instruction suivante est `throw`, qui lève une nouvelle exception <xref:System.IO.FileNotFoundException> et ajoute des informations de texte à l’exception.</span><span class="sxs-lookup"><span data-stu-id="d3b99-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="d3b99-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3b99-109">See Also</span></span>  
[<span data-ttu-id="d3b99-110">Exceptions</span><span class="sxs-lookup"><span data-stu-id="d3b99-110">Exceptions</span></span>](index.md)
