---
title: "Private (Visual Basic) | Microsoft Docs"
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
  - "vb.Private"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Private keyword"
  - "Private keyword, syntax"
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Private (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'un ou plusieurs éléments de programmation déclarés sont uniquement accessibles à partir de leur contexte de déclaration, y compris à partir des types contenus.  
  
## Notes  
 Si un élément de programmation représente des fonctionnalités exclusives ou contient des données confidentielles, vous souhaitez généralement limiter son accès aussi strictement que possible.  Vous obtenez une limitation maximale en autorisant uniquement le module, la classe ou la structure qui le définit à y avoir accès.  Pour limiter l'accès à un élément de cette manière, vous pouvez le déclarer avec `Private`.  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Private` seulement au niveau du module.  Cela signifie que le contexte de déclaration pour un élément `Private` doit être un module, une classe ou une structure et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
## Comportement  
  
-   **Niveau d'accès.** Tout le code d'un contexte de déclaration peut accéder à ses éléments `Private`.  Cela inclut le code dans un type contenu, tel qu'une classe imbriquée ou une expression d'assignation dans une énumération.  Aucun code à l'extérieur du contexte de déclaration ne peut accéder à ses éléments `Private`.  
  
-   **Modificateurs d'accès.** Les mots clés qui spécifient le niveau d'accès portent le nom de *modificateurs d'accès*.  Pour obtenir une comparaison entre les modificateurs d'accès, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Private` peut être utilisé dans les contextes suivants :  
  
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instruction](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instruction](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)