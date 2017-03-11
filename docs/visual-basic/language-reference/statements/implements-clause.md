---
title: "Implements Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ImplementsClause"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interface implementation, reimplementation"
  - "interface members, reimplementation"
  - "interface members, Implements keyword"
  - "interface members"
  - "members, reimplementation"
  - "interface implementation, Implements keyword"
  - "interface members, implementing"
  - "Implements keyword"
  - "Implements statement, about Implements"
  - "members, implementing"
  - "members, Implements keyword"
  - "reimplementation"
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Implements Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Indique qu'un membre de classe ou de structure fournit l'implémentation d'un membre défini dans une interface.  
  
## Notes  
 Le mot clé `Implements` est différent de l'instruction Implements \(voir [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)\).  Utilisez l'instruction `Implements` pour spécifier qu'une classe ou une structure implémente une ou plusieurs interfaces ; utilisez ensuite pour chaque membre le mot clé `Implements` pour spécifier quelle interface et quel membre il implémente.  
  
 Si une classe ou une structure implémente une interface, elle doit inclure l'instruction `Implements` directement après [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) ou [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) et doit implémenter tous les membres définis par l'interface.  
  
## Nouvelle implémentation  
 Dans une classe dérivée, vous pouvez implémenter de nouveau un membre d'interface que la classe de base a déjà implémenté.  Cette opération est différente de la substitution du membre de la classe de base à plusieurs égards :  
  
-   Le membre de la classe de base ne doit pas être [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) pour être de nouveau implémenté.  
  
-   Vous pouvez implémenter de nouveau le membre avec un nom différent.  
  
 Le mot clé `Implements` peut être utilisé dans les contextes suivants :  
  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)