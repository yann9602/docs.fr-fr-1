---
title: "Friend (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Friend"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Friend, mot clé"
  - "Friend, modificateur d’accès"
  - "mot clé Friend, syntaxe"
  - "Protected Friend, combinaison de mots clés"
  - "mot clé Friend, et Protected"
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Friend (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de l'assembly qui contient leur déclaration.  
  
## Notes  
 Dans de nombreux cas, vous souhaitez que les éléments de programmation, tels que les classes et les structures, soient utilisés par l'assembly entier, pas uniquement par le composant qui les déclare.  Toutefois, vous ne pouvez pas les utiliser pour être accessible par le code en dehors de l'assembly \(par exemple, si l'application est propriétaire\).  Si vous souhaitez limiter l'accès à un élément de cette façon, vous pouvez la déclarer à l'aide de le modificateur d' `Friend` .  
  
 Le code d'autres classes, structures et modules compilés dans le même assembly peut accéder à tous les éléments `Friend` de cet assembly.  
  
 l'accès d'`Friend` est souvent le niveau par défaut pour les éléments de programmation d'une application, et `Friend` est le niveau d'accès par défaut d'une interface, d'un module, d'une classe, ou d'une structure.  
  
 Vous pouvez utiliser `Friend` uniquement au module, à l'interface, ou au niveau de l'espace de noms.  Par conséquent, le contexte de déclaration pour un élément d' `Friend` doit être un fichier source, espace de noms, une interface, d'un module, une classe, ou une structure ; il ne peut pas être une procédure.  
  
 Vous pouvez utiliser le modificateur `Friend` conjointement avec le modificateur [Protected](../../../visual-basic/language-reference/modifiers/protected.md) dans la même déclaration.  Cette combinaison confère accès d' `Friend` et accès protégé sur les éléments déclarés ; ils sont accessibles n'importe où dans le même assembly, de leur propre classe, et des classes dérivées.  Vous pouvez spécifier `Protected Friend` uniquement sur les membres d'une classe.  
  
 Pour une comparaison d' `Friend` et les autres modificateurs d'accès, consultez l' [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Vous pouvez spécifier qu'un autre assembly est un assembly friend, qui lui permet d'accéder à tous les types et membres marqués comme `Friend`.  Pour plus d'informations, consultez [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemple  
 La classe suivante utilise le modificateur `Friend` pour permettre à d'autres éléments de programmation du même assembly d'accéder à certains membres.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/friend_1.vb)]  
  
## Utilisation  
 Vous pouvez utiliser le modificateur d' `Friend` dans ces contextes :  
  
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
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instruction](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)