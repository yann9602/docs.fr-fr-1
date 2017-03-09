---
title: "NotOverridable (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.NotOverridable"
  - "NotOverridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sealed methods"
  - "NotOverridable keyword"
  - "properties [Visual Basic], redefining"
  - "elements, sealed"
  - "sealed elements"
  - "procedures, overriding"
  - "procedures, redefining"
  - "overriding"
  - "methods [Visual Basic], sealed"
  - "properties [Visual Basic], overriding"
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# NotOverridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'une propriété ou une procédure ne peut pas être substituée dans une classe dérivée.  
  
## Notes  
 Le modificateur d' `NotOverridable` empêché une propriété ou une méthode d'être substituée dans une classe dérivée.  Le modificateur d' [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) permet une propriété ou une méthode dans une classe soient substituées dans une classe dérivée.  Pour plus d'informations, consultez [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 si le modificateur d' `Overridable` ou d' `NotOverridable` n'est pas spécifié, le paramètre par défaut dépend de si la propriété ou la méthode substitue une propriété ou une méthode de classe de base.  si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, le paramètre par défaut est `Overridable`; sinon, il s'agit `NotOverridable`.  
  
 Un élément qui ne peut pas être substitué est parfois appelé élément *sealed*.  
  
 Vous pouvez utiliser `NotOverridable` uniquement dans une propriété ou une instruction de déclaration de procédure.  Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui substitue une autre propriété ou procédure, c'est\-à\-dire, uniquement en association avec `Overrides`.  
  
## Modificateurs combinés  
 vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une méthode d' `Private` .  
  
 Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride`, `Overridable` ou `Shared` dans la même déclaration.  
  
## Utilisation  
 Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)