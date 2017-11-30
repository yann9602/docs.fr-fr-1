---
title: Stop, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="stop-statement-visual-basic"></a>Stop, instruction (Visual Basic)
Suspend l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez placer `Stop` instructions n’importe où dans les procédures pour suspendre l’exécution. À l’aide de la `Stop` instruction est similaire à la configuration d’un point d’arrêt dans le code.  
  
 Le `Stop` instruction interrompt l’exécution, mais contrairement à `End`, il ne pas fermer tous les fichiers ou effacer toutes les variables, sauf si elle est placée dans un fichier exécutable compilé (.exe).  
  
> [!NOTE]
>  Si la `Stop` est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé. Cela est vrai quel que soit le si le code a été compilé en mode débogage ou de la vente au détail.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `Stop` instruction pour suspendre l’exécution à chaque itération du `For...Next` boucle.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
