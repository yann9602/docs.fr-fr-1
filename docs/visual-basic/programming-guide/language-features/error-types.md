---
title: "Types d’erreurs (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: d48756b74baf757f043e68124d8b65c2f613e595
ms.lasthandoff: 03/13/2017

---
# <a name="error-types-visual-basic"></a>Types d'erreurs (Visual Basic)
Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], les erreurs (également appelé *exceptions*) se répartissent en trois catégories : erreurs de syntaxe, erreurs d’exécution et erreurs de logique.  
  
## <a name="syntax-errors"></a>Erreurs de syntaxe  
 *Erreurs de syntaxe* sont celles qui apparaissent lorsque vous écrivez du code. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]vérifie votre code en cours de frappe dans les **éditeur de Code** fenêtre et vous avertit si vous commettez une erreur, comme un mot mal orthographié ou l’utilisation incorrecte d’un élément de langage. Erreurs de syntaxe sont le type le plus courant d’erreurs. Vous pouvez les résoudre facilement dans l’environnement de codage dès qu’elles se produisent.  
  
> [!NOTE]
>  La `Option Explicit` instruction est d’éviter les erreurs de syntaxe. Il vous oblige à déclarer à l’avance toutes les variables à utiliser dans l’application. Par conséquent, lorsque ces variables sont utilisées dans le code, les erreurs typographiques sont décelées immédiatement et peuvent être résolus.  
  
## <a name="run-time-errors"></a>Erreurs d’exécution  
 *Erreurs d’exécution* sont celles qui apparaissent uniquement lorsque vous compilez et exécutez votre code. Ces impliquent du code qui semble être correct dans la mesure où il ne comporte aucune erreur de syntaxe, mais qui ne s’exécutera pas. Par exemple, vous pouvez écrire correctement une ligne de code pour ouvrir un fichier. Mais si le fichier est endommagé, l’application ne peut pas exécuter la `Open` et s’arrête en cours d’exécution. Vous pouvez résoudre la plupart des erreurs d’exécution en réécrivant le code erroné, puis recompiler et exécuter à nouveau.  
  
## <a name="logic-errors"></a>Erreurs de logique  
 *Erreurs de logique* sont celles qui apparaissent lorsque l’application est en cours d’utilisation. Il s’agit de la plupart des résultats souvent indésirables ou inattendus en réponse aux actions de l’utilisateur. Par exemple, une mauvaise touche ou une influence extérieure risque de votre application pour cesser de fonctionner dans les paramètres prévus ou complètement. Erreurs de logique sont les plus difficiles à résoudre, car il n’est pas toujours évident de déterminer leur origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Principes de base du débogueur](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)
