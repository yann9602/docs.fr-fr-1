---
title: "Évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
dev_langs:
- VB
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b861b5c6c151c5d3aeec2810c7f2a228f22fdf6e
ms.lasthandoff: 03/13/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré
Évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré. Pour réactiver l’évaluation de fonction, pas à pas, ou redémarrer le débogage.  
  
 Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre version d’évaluation a expiré.  
  
 Causes possibles d’un appel de procédure pour le délai d’attente sont une boucle infinie ou *boucle sans fin*. Pour plus d’informations, consultez la page [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Un cas particulier d’une boucle infinie est *récursivité*. Pour plus d’informations, consultez [procédures récursives](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID d’erreur :** BC30957  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Si possible, déterminez ce que l’évaluation de fonction précédente a été et à cause de son délai d’attente. Sinon, vous pouvez rencontrer cette erreur à nouveau.  
  
2.  Soit à nouveau, l’étape du débogueur ou arrêter et redémarrer le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [Naviguer dans le code avec le débogueur](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)
