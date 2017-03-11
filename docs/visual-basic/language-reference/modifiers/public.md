---
title: "Public (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Public"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Public keyword"
  - "Public keyword, syntax"
  - "Public access modifier"
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Public (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie que certains éléments de programmation déclarés ne présentent aucune limitation d'accès.  
  
## Notes  
 Vous publiez généralement un ou plusieurs composants, tels qu'une bibliothèque de classes, afin que les éléments de programmation soient accessibles par n'importe quel code qui interagit avec votre assembly.  Pour octroyer cet accès illimité à un élément, vous pouvez le déclarer avec `Public`.  
  
 L'accès public représente le niveau normal pour un élément de programmation lorsque vous ne devez pas limiter son accès.  Notez que le niveau d'accès d'un élément déclaré dans une interface, un module, une classe ou une structure a la valeur par défaut `Public` si vous n'affectez pas une autre valeur.  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser le mot clé `Public` seulement au niveau du module, de l'interface ou de l'espace de noms.  Cela signifie que le contexte de déclaration pour un élément `Public` doit être un fichier source, un espace de noms, un module, une classe ou une structure, et ne peut pas être une procédure.  
  
## Comportement  
  
-   **Niveau d'accès.** Si le code peut accéder à un module, une classe ou une structure, il peut accéder à ses éléments `Public`.  
  
-   **Accès par défaut.** Variables locales dans une procédure à accès public par défaut sur lesquelles vous ne pouvez pas utiliser de modificateurs d'accès.  
  
-   **Modificateurs d'accès.** Les mots clés qui spécifient le niveau d'accès portent le nom de *modificateurs d'accès*.  Pour obtenir une comparaison entre les modificateurs d'accès, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Public` peut être utilisé dans les contextes suivants :  
  
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instruction](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instruction](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)