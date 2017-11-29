---
title: "L’instruction ne peut pas se terminer un bloc en dehors d’une ligne &#39; si &#39; instruction"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords: BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>L’instruction ne peut pas se terminer un bloc en dehors d’une ligne &#39; si &#39; instruction
Une seule ligne `If` instruction contient plusieurs instructions séparées par un signe deux-points ( :), y compris un `End` instruction pour un bloc de contrôle en dehors de la ligne unique `If`. Une ligne `If` instructions n’utilisent pas la `End If` instruction.  
  
 **ID d’erreur :** BC32005  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Déplacer la ligne unique `If` instruction en dehors du bloc de contrôle qui contient le `End If` instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
