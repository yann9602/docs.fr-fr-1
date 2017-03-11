---
title: "Overridable (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Overridable"
  - "vb.Overridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elements, concrete"
  - "properties [Visual Basic], redefining"
  - "overriding, Overridable keyword"
  - "elements, virtual"
  - "virtual elements"
  - "procedures, overriding"
  - "concrete elements"
  - "procedures, redefining"
  - "Overridable keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Overridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'une propriété ou une procédure peut être substituée par une propriété ou une procédure de même nom dans une classe dérivée.  
  
## Notes  
 Le modificateur d' `Overridable` permet une propriété ou une méthode dans une classe soient substituées dans une classe dérivée.  Le modificateur de [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) empêché une propriété ou une méthode d'être substituée dans une classe dérivée.  Pour plus d'informations, consultez [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 si le modificateur d' `Overridable` ou d' `NotOverridable` n'est pas spécifié, le paramètre par défaut dépend de si la propriété ou la méthode substitue une propriété ou une méthode de classe de base.  si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, le paramètre par défaut est `Overridable`; sinon, il s'agit `NotOverridable`.  
  
 Vous pouvez effectuer une occultation ou une substitution pour redéfinir un élément hérité, mais les deux approches sont significativement différentes.  Pour plus d'informations, consultez [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Un élément qui peut être substitué est parfois référencé en tant qu'élément *virtuel*.  S'il peut être substitué, mais ne doit pas l'être, il est parfois également appelé élément *concret*.  
  
 Vous pouvez utiliser `Overridable` uniquement dans une propriété ou une instruction de déclaration de procédure.  
  
## Modificateurs combinés  
 vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une méthode d' `Private` .  
  
 Vous ne pouvez pas spécifier `Overridable` avec `MustOverride`, `NotOverridable` ou `Shared` dans la même déclaration.  
  
 Étant donné qu'un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.  
  
## Utilisation  
 Le modificateur `Overridable` peut être utilisé dans les contextes suivants :  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)