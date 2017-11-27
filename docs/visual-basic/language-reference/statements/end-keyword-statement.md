---
title: "Fin &lt;mot clé&gt; , instruction (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.EndDefinition
helpviewer_keywords: End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>Fin &lt;mot clé&gt; , instruction (Visual Basic)
Lorsque le suivi d’un mot clé supplémentaire, termine la définition du bloc d’instruction introduit par ce mot clé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a>Composants  
 `End`  
 Obligatoire. Termine la définition de l’élément de programmation.  
  
 `AddHandler`  
 Requis pour terminer une `AddHandler` accesseur commencé par une mise en correspondance `AddHandler` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Requis pour terminer une définition de classe commencée par un correspondant [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Requis pour terminer une définition d’énumération commencée par une mise en correspondance [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Requis pour terminer un `Custom` événement commencée par une mise en correspondance [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Requis pour terminer un `Function` procédure commencée par une mise en correspondance [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md). Si l’exécution rencontre une `End``Function` instruction, contrôle retourne au code appelant.  
  
 `Get`  
 Requis pour terminer un `Property` procédure commencée par une mise en correspondance [instruction Get](../../../visual-basic/language-reference/statements/get-statement.md). Si l’exécution rencontre une `End``Get` instruction, contrôle retourne à l’instruction demandant la valeur de propriété.  
  
 `If`  
 Requis pour terminer une `If`... `Then`... `Else` commencée par une mise en correspondance `If` instruction. Consultez [si... Puis... Else, instruction](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Requis pour terminer une définition d’interface commencée par un correspondant [instruction Interface](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Requis pour terminer une définition de module commencée par un correspondant [Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Requis pour terminer une définition de l’espace de noms commencée par un correspondant [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Requis pour terminer une définition d’opérateur commencée par un correspondant [Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Requis pour terminer une définition de propriété commencée par une mise en correspondance [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Requis pour terminer un `RaiseEvent` accesseur commencé par une mise en correspondance `RaiseEvent` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Requis pour terminer un `RemoveHandler` accesseur commencé par une mise en correspondance `RemoveHandler` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Requis pour terminer un `Select`... `Case` commencée par une mise en correspondance `Select` instruction. Consultez [sélectionnez... Cas d’instruction](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Requis pour terminer un `Property` procédure commencée par une mise en correspondance [instruction Set](../../../visual-basic/language-reference/statements/set-statement.md). Si l’exécution rencontre une `End``Set` instruction, contrôle retourne à l’instruction définissant la valeur de propriété.  
  
 `Structure`  
 Requis pour terminer une définition de structure commencée par une mise en correspondance [instruction Structure](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Requis pour terminer un `Sub` procédure commencée par une mise en correspondance [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md). Si l’exécution rencontre une `End``Sub` instruction, contrôle retourne au code appelant.  
  
 `SyncLock`  
 Requis pour terminer un `SyncLock` commencée par une mise en correspondance `SyncLock` instruction. Consultez [SyncLock, instruction](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Requis pour terminer un `Try`... `Catch`... `Finally` commencée par une mise en correspondance `Try` instruction. Consultez [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Requis pour terminer un `While` commencée par une mise en correspondance de boucle `While` instruction. Consultez [tandis que... End While, instruction](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Requis pour terminer un `With` commencée par une mise en correspondance `With` instruction. Consultez [avec... End With, instruction](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Remarques  
 Le [l’instruction End](../../../visual-basic/language-reference/statements/end-statement.md), sans mot clé supplémentaire, termine l’exécution immédiatement.  
  
 Lorsque précédé par un signe dièse (`#`), le `End` mot clé termine un bloc de prétraitement introduit par la directive correspondante.  
  
 `#End`  
 Obligatoire. Termine la définition du bloc de prétraitement.  
  
 `#ExternalSource`  
 Requis pour terminer un bloc source externe commencé par une mise en correspondance [Directive #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Requis pour terminer un bloc de compilation conditionnelle commencé par une mise en correspondance `#If` directive. Consultez [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Requis pour terminer un bloc de région source commencé par une mise en correspondance [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Remarques sur le développement Smart Device  
 La `End` instruction, sans mot clé supplémentaire, n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
