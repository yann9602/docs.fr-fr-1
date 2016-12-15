---
title: "End &lt;keyword&gt; Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.EndDefinition"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "End keyword"
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End &lt;keyword&gt; Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsqu'il est suivi par un mot clé supplémentaire, il termine la définition du bloc d'instruction introduit par ce mot clé.  
  
## Syntaxe  
  
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
  
## Composants  
 `End`  
 Obligatoire.  Termine la définition de l'élément de programmation.  
  
 `AddHandler`  
 Obligatoire pour terminer un accesseur `AddHandler` commencé par une instruction `AddHandler` correspondante dans un [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) personnalisé.  
  
 `Class`  
 Obligatoire pour terminer une définition de classe commencée par un [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) correspondant.  
  
 `Enum`  
 Obligatoire pour terminer une définition d'énumération commencée par un [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) correspondant.  
  
 `Event`  
 Obligatoire pour terminer une définition d'événement `Custom` commencée par un [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) correspondant.  
  
 `Function`  
 Obligatoire pour terminer une définition de procédure `Function` commencée par un [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) correspondant.  Si l'exécution rencontre une instruction `End` `Function`, le contrôle est retourné au code appelant.  
  
 `Get`  
 Obligatoire pour terminer une définition de procédure `Property` commencée par un [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) correspondant.  Si l'exécution rencontre une instruction `End` `Get`, le contrôle est retourné à l'instruction demandant la valeur de la propriété.  
  
 `If`  
 Requis pour terminer une définition de bloc `If`...`Then`... `Else` commencée par une instruction `If` correspondante.  Consultez [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Obligatoire pour terminer une définition d'interface commencée par un [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) correspondant.  
  
 `Module`  
 Obligatoire pour terminer une définition de module commencée par un [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md) correspondant.  
  
 `Namespace`  
 Obligatoire pour terminer une définition d'espace de noms commencée par un [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) correspondant.  
  
 `Operator`  
 Obligatoire pour terminer une définition d'opérateur commencée par un [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) correspondant.  
  
 `Property`  
 Obligatoire pour terminer une définition de propriété commencée par un [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) correspondant.  
  
 `RaiseEvent`  
 Obligatoire pour terminer un accesseur `RaiseEvent` commencé par une instruction `RaiseEvent` correspondante dans un [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) personnalisé.  
  
 `RemoveHandler`  
 Obligatoire pour terminer un accesseur `RemoveHandler` commencé par une instruction `RemoveHandler` correspondante dans un [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) personnalisé.  
  
 `Select`  
 Requis pour terminer une définition de bloc `Select`...`Case` commencée par une instruction `Select` correspondante.  Consultez [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Obligatoire pour terminer une définition de procédure `Property` commencée par un [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) correspondant.  Si l'exécution rencontre une instruction `End` `Set`, le contrôle est retourné à l'instruction définissant la valeur de la propriété.  
  
 `Structure`  
 Obligatoire pour terminer une définition de structure commencée par un [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) correspondant.  
  
 `Sub`  
 Obligatoire pour terminer une définition de procédure `Sub` commencée par un [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) correspondant.  Si l'exécution rencontre une instruction `End` `Sub`, le contrôle est retourné au code appelant.  
  
 `SyncLock`  
 Requis pour terminer une définition de bloc `SyncLock` commencée par une instruction `SyncLock` correspondante.  Consultez [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Requis pour terminer une définition de bloc `Try`...`Catch`...`Finally` commencée par une instruction `Try` correspondante.  Consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Requis pour terminer une définition de boucle `While` commencée par une instruction `While` correspondante.  Consultez [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Requis pour terminer une définition de bloc `With` commencée par une instruction `With` correspondante.  Consultez [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## Notes  
 L'[End Statement](../../../visual-basic/language-reference/statements/end-statement.md), sans un mot clé supplémentaire, termine immédiatement l'exécution.  
  
 Lorsque précédé par un signe dièse \(`#`\), le mot clé `End` termine un bloc prétraitant introduit par la directive correspondante.  
  
 `#End`  
 Obligatoire.  Termine la définition du bloc de prétraitement.  
  
 `#ExternalSource`  
 Obligatoire pour terminer un bloc source externe commencé par un [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) correspondant.  
  
 `#If`  
 Requis pour terminer un bloc de compilation conditionnel commencé par une directive `#If` correspondante.  Consultez [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Obligatoire pour terminer un bloc de région source commencé par un [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) correspondant.  
  
## Notes du développeur sur Smart Device  
 L'instruction `End`, sans mot clé supplémentaire, n'est pas prise en charge.  
  
## Voir aussi  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)