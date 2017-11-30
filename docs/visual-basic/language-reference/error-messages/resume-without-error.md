---
title: Reprendre sans gestion d'erreur
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a>Reprendre sans gestion d'erreur
A `Resume` instruction apparaît en dehors du code de gestion des erreurs ou le code est passé dans un gestionnaire d’erreurs, même si aucune erreur s’est produite.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Déplacer la `Resume` instruction dans un gestionnaire d’erreurs ou de le supprimer.  
  
2.  Passages à des étiquettes ne peuvent pas se produire entre procédures, recherchez dans la procédure pour l’étiquette qui identifie le Gestionnaire d’erreurs. Si vous trouvez une étiquette dupliquée spécifiée comme cible d’un `GoTo` instruction qui n’est pas un `On Error GoTo` instruction, modifiez l’étiquette de ligne pour s’accorder avec sa cible prévue.  
  
## <a name="see-also"></a>Voir aussi  
 [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
