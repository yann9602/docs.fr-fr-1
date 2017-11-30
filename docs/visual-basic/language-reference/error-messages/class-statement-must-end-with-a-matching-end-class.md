---
title: '&#39; Classe &#39; instruction doit se terminer par une correspondance &#39; Classe de fin &#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords: BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8643a0a5b55e220ca8dd53065500fe4b1e473d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="720ad-102">&#39; Classe &#39; instruction doit se terminer par une correspondance &#39; Classe de fin &#39;</span><span class="sxs-lookup"><span data-stu-id="720ad-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="720ad-103">`Class`permet de lancer un `Class` bloquer ; par conséquent, elle ne peut apparaître au début du bloc, avec une mise en correspondance `End Class` instruction termine le bloc.</span><span class="sxs-lookup"><span data-stu-id="720ad-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="720ad-104">Soit vous avez un redondant `Class` instruction, ou vous n’avez pas terminé votre `Class` bloc avec `End Class`.</span><span class="sxs-lookup"><span data-stu-id="720ad-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="720ad-105">**ID d’erreur :** BC30481</span><span class="sxs-lookup"><span data-stu-id="720ad-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="720ad-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="720ad-106">To correct this error</span></span>  
  
-   <span data-ttu-id="720ad-107">Recherchez et supprimez l’inutiles `Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="720ad-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="720ad-108">Conclure le `Class` bloc avec une mise en correspondance `End Class`.</span><span class="sxs-lookup"><span data-stu-id="720ad-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720ad-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="720ad-109">See Also</span></span>  
 [<span data-ttu-id="720ad-110">Fin \<mot clé > instruction</span><span class="sxs-lookup"><span data-stu-id="720ad-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)  
 [<span data-ttu-id="720ad-111">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="720ad-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
