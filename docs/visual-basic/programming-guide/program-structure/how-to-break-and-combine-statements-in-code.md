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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 840036a91f430f72e0258b8be466770f2855a58f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Procédure : diviser et combiner des instructions dans le code (Visual Basic)
Lorsque vous écrivez votre code, vous pouvez parfois créer longues instructions qui vous imposent un défilement horizontal dans l’éditeur de Code. Bien que cela n’affecte pas la façon votre code s’exécute, elle rend difficile pour vous, ou quiconque de lire le code tel qu’il apparaît sur le moniteur. Dans ce cas, vous devez envisager de diviser cette instruction longue en plusieurs lignes.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Arrêt d’une instruction unique en plusieurs lignes  
  
-   Utilisez le caractère de continuation de ligne, qui est un trait de soulignement (`_`), au point auquel vous souhaitez que la saut de ligne. Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne (retour chariot).  
  
    > [!NOTE]
    >  Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic implicitement continue l’instruction sur la ligne de code suivante. Pour une liste des éléments de syntaxe pour laquelle vous pouvez omettre le caractère de continuation de ligne, consultez « Continuation de ligne implicite » dans [instructions](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     Dans l’exemple suivant, l’instruction est divisée en quatre caractères de continuation terminant toutes les lignes, mais la dernière ligne.  
  
     [!code-vb[VbVbcnConventions&#20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     À l’aide de cette séquence rend votre code plus facile à lire, en ligne et lorsque l’impression.  
  
     Le caractère de continuation de ligne doit être le dernier caractère d’une ligne. Vous ne peut pas faire suivre tout le reste sur la même ligne.  
  
     Il existe des restrictions à l’endroit où vous pouvez utiliser le caractère de continuation de ligne ; par exemple, vous ne pouvez pas l’utiliser au milieu d’un nom d’argument. Vous pouvez interrompre une liste d’arguments avec le caractère de continuation de ligne, mais les noms respectifs des arguments doivent rester intactes.  
  
     Vous ne pouvez pas continuer un commentaire à l’aide d’un caractère de continuation de ligne. Le compilateur n’examine les caractères dans un commentaire pour une signification spéciale. Pour un commentaire de plusieurs lignes, répétez le symbole de commentaire (`'`) sur chaque ligne.  
  
 Bien que de placer chaque instruction sur une ligne distincte est la méthode recommandée, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous permet également de placer plusieurs instructions sur la même ligne.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Pour placer plusieurs instructions sur la même ligne  
  
-   Séparez les instructions par un signe deux-points (`:`), comme dans l’exemple suivant.  
  
     [!code-vb[VbVbcnConventions&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
