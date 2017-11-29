---
title: Call, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Call, instruction (Visual Basic)
Transfère le contrôle à un `Function`, `Sub`, ou de la procédure de la bibliothèque de liens dynamiques (DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Composants  
 `procedureName`  
 Obligatoire. Nom de la procédure à appeler.  
  
 `argumentList`  
 Facultatif. Liste de variables ou d’expressions représentant les arguments passés à la procédure lorsqu’elle est appelée. Plusieurs arguments sont séparés par des virgules. Si vous incluez `argumentList`, vous devez le placer entre parenthèses.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser le `Call` mot clé lorsque vous appelez une procédure. Pour la plupart des appels de procédure, vous n’êtes pas obligé d’utiliser ce mot clé.  
  
 Vous utilisez généralement la `Call` mot clé lorsque l’expression appelée ne commence pas par un identificateur. Utilisation de la `Call` n’est pas recommandé de mot clé pour d’autres utilisations.  
  
 Si la procédure retourne une valeur, la `Call` instruction ignore.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre deux exemples où le `Call` mot clé est nécessaire pour appeler une procédure. Dans les deux exemples, l’expression appelée ne commence pas par un identificateur.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
