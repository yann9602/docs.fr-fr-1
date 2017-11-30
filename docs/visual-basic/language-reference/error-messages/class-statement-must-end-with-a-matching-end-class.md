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
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a>&#39; Classe &#39; instruction doit se terminer par une correspondance &#39; Classe de fin &#39;
`Class`permet de lancer un `Class` bloquer ; par conséquent, elle ne peut apparaître au début du bloc, avec une mise en correspondance `End Class` instruction termine le bloc. Soit vous avez un redondant `Class` instruction, ou vous n’avez pas terminé votre `Class` bloc avec `End Class`.  
  
 **ID d’erreur :** BC30481  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Recherchez et supprimez l’inutiles `Class` instruction.  
  
-   Conclure le `Class` bloc avec une mise en correspondance `End Class`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md)  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)
