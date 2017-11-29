---
title: Fin d'instruction attendue
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords: BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="9c827-102">Fin d'instruction attendue</span><span class="sxs-lookup"><span data-stu-id="9c827-102">End of statement expected</span></span>
<span data-ttu-id="9c827-103">L’instruction est syntaxiquement complète, mais un élément de programmation supplémentaire suit l’élément qui termine l’instruction.</span><span class="sxs-lookup"><span data-stu-id="9c827-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="9c827-104">Un terminateur de ligne est requis à la fin de chaque instruction.</span><span class="sxs-lookup"><span data-stu-id="9c827-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="9c827-105">Un terminateur de ligne divise les caractères d’un fichier source Visual Basic en lignes.</span><span class="sxs-lookup"><span data-stu-id="9c827-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="9c827-106">Exemples d’indicateurs de fin de ligne sont le Unicode chariot retour (& HD), le Unicode saut de ligne (& HA), et le suivi du caractère de saut de ligne Unicode des caractères de retour chariot Unicode.</span><span class="sxs-lookup"><span data-stu-id="9c827-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="9c827-107">Pour plus d’informations sur les indicateurs de fin de ligne, consultez la [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c827-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="9c827-108">**ID d’erreur :** BC30205</span><span class="sxs-lookup"><span data-stu-id="9c827-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c827-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9c827-109">To correct this error</span></span>
  
1.  <span data-ttu-id="9c827-110">Vérifiez si deux instructions différentes ont été placées par inadvertance sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="9c827-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="9c827-111">Insérer une marque de fin de ligne après l’élément qui termine l’instruction.</span><span class="sxs-lookup"><span data-stu-id="9c827-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9c827-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c827-112">See Also</span></span>  
 [<span data-ttu-id="9c827-113">Guide pratique : diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="9c827-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="9c827-114">Instructions</span><span class="sxs-lookup"><span data-stu-id="9c827-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
