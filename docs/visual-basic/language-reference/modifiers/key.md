---
title: "Key (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousKey"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], key"
  - "Key [Visual Basic]"
  - "Key keyword [Visual Basic]"
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Key (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le mot clé `Key` vous permet de spécifier le comportement des propriétés de types anonymes.  Seules les propriétés que vous désignez comme les propriétés de clé participent aux tests d'égalité entre des instances de type anonymes ou au calcul de valeurs de code de hachage.  Les valeurs des propriétés de clé ne peuvent pas être modifiées.  
  
 Vous désignez une propriété d'un type anonyme comme propriété de clé en plaçant le mot clé `Key` devant sa déclaration dans la liste d'initialisation.  Dans l'exemple suivant, `Airline` et `FlightNo` sont des propriétés de clé, à l'inverse de `Gate`.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_1.vb)]  
  
 Lorsqu'un nouveau type anonyme est créé, il hérite directement de <xref:System.Object>.  Le compilateur substitue trois membres hérités : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A>.  Le code de substitution produit pour <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> est basé sur les propriétés de clé.  Si le type ne présente pas de propriétés de clé, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.Equals%2A> ne sont pas substitués.  
  
## Égalité  
 Deux instances de type anonymes sont égales si elles sont des instances du même type et si les valeurs de leurs propriétés de clé sont égales.  Dans les exemples suivants, `flight2` est égale à `flight1` de l'exemple précédent parce que ce sont des instances du même type anonyme et qu'elles ont des valeurs correspondantes pour leurs propriétés de clé.  Toutefois, `flight3` n'est pas égale à `flight1` parce qu'elle a une valeur différente pour une propriété de clé, `FlightNo`.  L'instance `flight4` n'est pas du même type que `flight1` parce qu'elles désignent des propriétés différentes comme propriétés de clé.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_2.vb)]  
  
 Si deux instances sont déclarées uniquement avec des propriétés ne correspondant pas à une clé, avec un nom, un type, un ordre et une valeur identiques, les deux instances ne sont pas égales.  Une instance sans propriété de clé est uniquement égale à elle\-même.  
  
 Pour plus d'informations sur les conditions dans lesquelles deux instances de type anonyme sont des instances du même type anonyme, consultez [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## Calcul de code de hachage  
 Comme <xref:System.Object.Equals%2A>, la fonction de hachage définie dans <xref:System.Object.GetHashCode%2A> car un type anonyme est basé sur les propriétés de clé du type.  Les exemples suivants montrent l'interaction entre les propriétés de clé et les valeurs de code de hachage.  
  
 Les instances d'un type anonyme qui ont les mêmes valeurs pour toutes les propriétés de clé ont la même valeur de code de hachage, même si les propriétés ne correspondant pas à une clé n'ont pas de valeurs correspondantes.  L'instruction suivante retourne `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_3.vb)]  
  
 Les instances d'un type anonyme qui ont des valeurs différentes pour une ou plusieurs propriétés de clé ont des valeurs de code de hachage différentes.  L'instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_4.vb)]  
  
 Les instances de types anonymes qui désignent des propriétés différentes comme propriétés de clé ne sont pas des instances du même type.  Elles ont des valeurs de code de hachage différentes même lorsque les noms et valeurs de toutes les propriétés sont les mêmes.  L'instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_5.vb)]  
  
## Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peuvent pas être modifiées.  Par exemple, les champs `Airline` et `FlightNo` sont en lecture seule dans `flight1` dans les exemples précédents, mais `Gate` peut être modifié.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_6.vb)]  
  
## Voir aussi  
 [Anonymous Type Definition](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)