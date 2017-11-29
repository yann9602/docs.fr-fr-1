---
title: "Convention d’appel de DLL incorrecte"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>Convention d’appel de DLL incorrecte
Arguments passés à une bibliothèque de liens dynamiques (DLL) doivent correspondre exactement à ceux attendus par la routine. Conventions d’appel traitent nombre, type et ordre des arguments. Votre programme peut appeler une routine dans une DLL qui est passée du type incorrect ou le nombre d’arguments.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que tous les types d’argument correspondent à ceux spécifiés dans la déclaration de la routine que vous appelez.  
  
2.  Vérifiez que vous passez le même nombre d’arguments indiqué dans la déclaration de la routine que vous appelez.  
  
3.  Si la routine DLL attend des arguments par valeur, vérifiez que `ByVal` est spécifié pour ces arguments dans la déclaration de la routine.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call (instruction)](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
