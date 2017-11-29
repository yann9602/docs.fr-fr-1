---
title: '#<a name="ifthenelse-directives"></a>If... Then... #Else, Directives'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else, directives
Compilation conditionnelle des blocs de code Visual Basic sélectionnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>Composants  
 `expression`  
 Requis pour `#If` et `#ElseIf` instructions, facultatif ailleurs. Toute expression, exclusivement consistant en une ou plusieurs constantes de compilation conditionnelle, les littéraux et les opérateurs, qui prend la valeur `True` ou `False`.  
  
 `statements`  
 Requis pour `#If` bloc d’instructions, facultatif ailleurs. Lignes de programme Visual Basic ou des directives de compilateur qui sont compilés si l’expression associée a la valeur `True`.  
  
 `#End If`  
 Met fin à la `#If` bloc d’instructions.  
  
## <a name="remarks"></a>Remarques  
 Sur la surface, le comportement de la `#If...Then...#Else` directives semble être le même que celui de la `If...Then...Else` instructions. Toutefois, le `#If...Then...#Else` directives évaluent ce qui est compilé par le compilateur, alors que le `If...Then...Else` instructions évaluent les conditions au moment de l’exécution.  
  
 Compilation conditionnelle est généralement utilisée pour compiler le même programme pour les différentes plateformes. Il est également utilisé pour empêcher le code d’apparaître dans un fichier exécutable de débogage. Code exclu lors de la compilation conditionnelle est totalement absent du fichier exécutable final, afin qu’il n’a aucun effet sur la taille ou des performances.  
  
 Quel que soit le résultat des évaluations, toutes les expressions sont évaluées à l’aide de `Option Compare Binary`. Le `Option Compare` instruction n’affecte pas les expressions dans `#If` et `#ElseIf` instructions.  
  
> [!NOTE]
>  Aucune forme d’une ligne de la `#If`, `#Else`, `#ElseIf`, et `#End If` directives existe. Aucun autre code ne peut apparaître sur la même ligne qu’une des directives.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `#If...Then...#Else` construction pour déterminer s’il faut compiler certaines instructions.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)  
 [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
