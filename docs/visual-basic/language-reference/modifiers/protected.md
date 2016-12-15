---
title: "Protected (Visual Basic) | Microsoft Docs"
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
  - "vb.Protected"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Protected Friend keyword combination"
  - "Protected keyword, and Friend"
  - "Protected keyword, syntax"
  - "Protected access modifier"
  - "Protected keyword"
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Protected (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que les éléments de programmation déclarés sont uniquement accessibles à partir de leur propre classe ou d'une classe dérivée.  
  
## Notes  
 Parfois un élément de programmation déclaré dans une classe contient des données sensibles ou du code restreint et vous souhaitez limiter l'accès à l'élément.  Toutefois, si la classe peut être héritée et si vous prévoyez une hiérarchie de classes dérivées, il peut s'avérer nécessaire pour ces classes dérivées d'accéder aux données ou au code.  Dans ce cas, vous souhaitez que l'élément soit à la fois accessible de la classe de base et de toutes les classes dérivées.  Pour limiter l'accès à un élément de cette manière, vous pouvez le déclarer avec `Protected`.  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Protected` seulement au niveau de la classe.  Cela signifie que le contexte de déclaration pour un élément `Protected` doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.  
  
-   **Modificateurs combinés.** Vous pouvez utiliser le modificateur`Protected` conjointement avec le modificateur [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dans la même déclaration.  Cette combinaison rend les éléments déclarés accessibles de partout dans le même assembly, de leur propre classe, et de classes dérivées.  Vous pouvez spécifier `Protected Friend` uniquement sur les membres d'une classe.  
  
## Comportement  
  
-   **Niveau d'accès.** Tout le code dans une classe peut accéder à ses éléments.  Le code dans toute classe qui dérive d'une classe de base peut accéder à tous les éléments `Protected` de la classe de base.  Cette règle est valable pour toutes les générations de dérivation.  Cela signifie qu'une classe peut accéder aux éléments `Protected` de la classe de base de la classe de base, et ainsi de suite.  
  
     L'accès protégé n'est pas un sur\-ensemble ou sous\-ensemble de l'accès ami.  
  
-   **Modificateurs d'accès.** Les mots clés qui spécifient le niveau d'accès portent le nom de *modificateurs d'accès*.  Pour obtenir une comparaison entre les modificateurs d'accès, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Protected` peut être utilisé dans les contextes suivants :  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)