---
title: Erase, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Erase, instruction (Visual Basic)
Permet de libérer des variables tableau et de libérer la mémoire utilisée pour leurs éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Composants  
 `arraylist`  
 Obligatoire. Liste des variables tableau à effacer. Les variables multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Remarques  
 La `Erase` instruction peut apparaître uniquement au niveau de la procédure. Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure mais pas au niveau de la classe ou le module.  
  
 Le `Erase` instruction équivaut à assigner `Nothing` à chaque variable tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Erase` instruction pour effacer deux tableaux et libérer leur mémoire (1 000 et 100 éléments de stockage, respectivement). La `ReDim` instruction assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)
