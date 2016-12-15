---
title: "#If...Then...#Else Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.#EndIf"
  - "#End If"
  - "#Then"
  - "#ElseIf"
  - "vb.#ElseIf"
  - "vb.#Else"
  - "vb.#If"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, compiling"
  - "#If directive [Visual Basic]"
  - "conditional compilation, directives"
  - "#End if directive [Visual Basic]"
  - "selective compiling"
  - "else directive (#else)"
  - "#Else directive [Visual Basic]"
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #If...Then...#Else Directives
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue une compilation conditionnelle des blocs de code Visual Basic sélectionnés.  
  
## Syntaxe  
  
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
  
## Composants  
 `expression`  
 Requis pour les instructions `#If` et `#ElseIf`, sinon, facultatives.  Toute expression, exclusivement constituée d'une ou plusieurs constantes de compilation conditionnelle, d'un ou plusieurs caractères littéraux et d'opérateurs, qui prend la valeur `True` ou `False`.  
  
 `statements`  
 Requis pour le bloc d'instruction `#If`, sinon, facultatifs.  Lignes de programme ou directives de compilation Visual Basic compilées si l'expression associée prend la valeur `True`.  
  
 `#End If`  
 Met fin au bloc d'instruction `#If`.  
  
## Notes  
 En apparence, le comportement des directives `#If...Then...#Else` semble identique à celui des instructions `If...Then...Else`.  Cependant, les directives `#If...Then...#Else` évaluent ce qui est compilé par le compilateur, alors que les instructions `If...Then...Else` évaluent les conditions au moment de l'exécution.  
  
 La compilation conditionnelle est généralement utilisée pour compiler le même programme sur différentes plateformes.  Elle est également utilisée pour éviter que le code de débogage n'apparaisse dans un fichier exécutable.  Le code exclu lors d'une compilation conditionnelle est totalement absent du fichier exécutable final, et n'a donc aucune incidence sur la taille de ce dernier ou sur les performances.  
  
 Quel que soit le résultat des évaluations, toutes les expressions sont évaluées à l'aide de `Option Compare Binary`.  L'instruction `Option Compare` n'affecte pas les expressions contenues dans les instructions `#If` et `#ElseIf`.  
  
> [!NOTE]
>  Les directives `#If`, `#Else`, `#ElseIf` et `#End If` n'existent pas sous la forme d'une ligne unique.  Aucun autre code ne peut figurer sur la même ligne que les directives.  
  
## Exemple  
 Cet exemple utilise la construction `#If...Then...#Else` pour déterminer la nécessité de compiler certaines instructions.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## Voir aussi  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)