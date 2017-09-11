---
title: "Comment : diviser et combiner des instructions dans le Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ca281035a0bd81a9b52cdd60f2bc59724852709
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="5f88e-102">Procédure : diviser et combiner des instructions dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f88e-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="5f88e-103">Lorsque vous écrivez votre code, vous pouvez parfois créer longues instructions qui vous imposent un défilement horizontal dans l’éditeur de Code.</span><span class="sxs-lookup"><span data-stu-id="5f88e-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="5f88e-104">Bien que cela n’affecte pas la façon votre code s’exécute, elle rend difficile pour vous, ou quiconque de lire le code tel qu’il apparaît sur le moniteur.</span><span class="sxs-lookup"><span data-stu-id="5f88e-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="5f88e-105">Dans ce cas, vous devez envisager de diviser cette instruction longue en plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="5f88e-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="5f88e-106">Arrêt d’une instruction unique en plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="5f88e-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="5f88e-107">Utilisez le caractère de continuation de ligne, qui est un trait de soulignement (`_`), au point auquel vous souhaitez que la saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="5f88e-108">Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne (retour chariot).</span><span class="sxs-lookup"><span data-stu-id="5f88e-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f88e-109">Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic implicitement continue l’instruction sur la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="5f88e-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="5f88e-110">Pour une liste des éléments de syntaxe pour laquelle vous pouvez omettre le caractère de continuation de ligne, consultez « Continuation de ligne implicite » dans [instructions](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="5f88e-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="5f88e-111">Dans l’exemple suivant, l’instruction est divisée en quatre caractères de continuation terminant toutes les lignes, mais la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     <span data-ttu-id="5f88e-112">[!code-vb[VbVbcnConventions&#20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5f88e-112">[!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span></span>  
  
     <span data-ttu-id="5f88e-113">À l’aide de cette séquence rend votre code plus facile à lire, en ligne et lorsque l’impression.</span><span class="sxs-lookup"><span data-stu-id="5f88e-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="5f88e-114">Le caractère de continuation de ligne doit être le dernier caractère d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="5f88e-115">Vous ne peut pas faire suivre tout le reste sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-115">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="5f88e-116">Il existe des restrictions à l’endroit où vous pouvez utiliser le caractère de continuation de ligne ; par exemple, vous ne pouvez pas l’utiliser au milieu d’un nom d’argument.</span><span class="sxs-lookup"><span data-stu-id="5f88e-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="5f88e-117">Vous pouvez interrompre une liste d’arguments avec le caractère de continuation de ligne, mais les noms respectifs des arguments doivent rester intactes.</span><span class="sxs-lookup"><span data-stu-id="5f88e-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="5f88e-118">Vous ne pouvez pas continuer un commentaire à l’aide d’un caractère de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="5f88e-119">Le compilateur n’examine les caractères dans un commentaire pour une signification spéciale.</span><span class="sxs-lookup"><span data-stu-id="5f88e-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="5f88e-120">Pour un commentaire de plusieurs lignes, répétez le symbole de commentaire (`'`) sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="5f88e-121">Bien que de placer chaque instruction sur une ligne distincte est la méthode recommandée, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous permet également de placer plusieurs instructions sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="5f88e-121">Although placing each statement on a separate line is the recommended method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="5f88e-122">Pour placer plusieurs instructions sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="5f88e-122">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="5f88e-123">Séparez les instructions par un signe deux-points (`:`), comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5f88e-123">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     <span data-ttu-id="5f88e-124">[!code-vb[VbVbcnConventions&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5f88e-124">[!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f88e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f88e-125">See Also</span></span>  
 <span data-ttu-id="5f88e-126">[Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="5f88e-126">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="5f88e-127"> [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="5f88e-127"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>
