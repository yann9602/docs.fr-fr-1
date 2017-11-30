---
title: End, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a>End, instruction
Termine l’exécution immédiatement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez placer le `End` instruction n’importe où dans une procédure pour forcer l’application entière pour interrompre l’exécution. `End`Ferme tous les fichiers ouverts avec un `Open` instruction et efface toutes les variables de l’application. L’application se ferme dès qu’il n’y aucun programme contenant des références à ses objets et son code est en cours d’exécution.  
  
> [!NOTE]
>  Le `End` instruction met immédiatement fin à l’exécution de code et n’appelle pas la `Dispose` ou `Finalize` (méthode), ou tout autre code Visual Basic. Références d’objet détenus par d’autres programmes sont invalidés. Si un `End` est rencontrée dans une `Try` ou `Catch` bloc, le contrôle ne passe pas correspondant `Finally` bloc.  
  
 Le `Stop` instruction interrompt l’exécution, mais contrairement à `End`, il ne pas fermer tous les fichiers ou effacer toutes les variables, sauf si elle est placée dans un fichier exécutable compilé (.exe).  
  
 Étant donné que `End` met fin à votre application sans se préoccuper des ressources qui peuvent être ouverts, vous devez tenter de fermer correctement avant de l’utiliser. Par exemple, si votre application comporte des formulaires ouverts, vous devez les fermer avant de contrôle atteint la `End` instruction.  
  
 Vous devez utiliser `End` avec parcimonie et uniquement lorsque vous devez arrêter immédiatement. Les méthodes normales pour mettre fin à une procédure ([instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) et [instruction Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) permettent de fermer correctement la procédure, mais également le code appelant. Par exemple, une application console, peut simplement `Return` à partir de la `Main` procédure.  
  
> [!IMPORTANT]
>  Le `End` instruction appelle la <xref:System.Environment.Exit%2A> méthode de la <xref:System.Environment> classe dans le <xref:System> espace de noms. <xref:System.Environment.Exit%2A>exige que vous disposiez `UnmanagedCode` autorisation. Si vous ne le faites pas, un <xref:System.Security.SecurityException> erreur se produit.  
  
 Lorsqu’il est suivi par un mot clé supplémentaire, [fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) délimite la fin de la définition de la procédure appropriée ou le bloc. Par exemple, `End Function` termine la définition d’un `Function` procédure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `End` instruction pour mettre fin à l’exécution de code si l’utilisateur le demande.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Remarques sur le développement Smart Device  
 Cette instruction n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Stop (instruction)](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
