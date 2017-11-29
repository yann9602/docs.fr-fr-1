---
title: "L’instruction ne peut pas se terminer un bloc en dehors d’une ligne &#39; si &#39; instruction"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords: BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="fc602-102">L’instruction ne peut pas se terminer un bloc en dehors d’une ligne &#39; si &#39; instruction</span><span class="sxs-lookup"><span data-stu-id="fc602-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="fc602-103">Une seule ligne `If` instruction contient plusieurs instructions séparées par un signe deux-points ( :), y compris un `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If`.</span><span class="sxs-lookup"><span data-stu-id="fc602-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="fc602-104">Une ligne `If` instructions n’utilisent pas la `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="fc602-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="fc602-105">**ID d’erreur :** BC32005</span><span class="sxs-lookup"><span data-stu-id="fc602-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fc602-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="fc602-106">To correct this error</span></span>  
  
-   <span data-ttu-id="fc602-107">Déplacer la ligne unique `If` instruction en dehors du bloc de contrôle qui contient le `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="fc602-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc602-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc602-108">See Also</span></span>  
 [<span data-ttu-id="fc602-109">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="fc602-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
