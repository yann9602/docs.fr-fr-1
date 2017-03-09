---
title: "TryCast Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.trycast"
  - "trycast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TryCast keyword"
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# TryCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Introduit une opération de conversion de type qui ne lève pas d'exception.  
  
## Notes  
 Si une tentative de conversion échoue, `CType` et `DirectCast` lèvent tous deux une erreur <xref:System.InvalidCastException>.  Cela peut affecter de façon défavorable la performance de votre application.  `TryCast` retourne [Nothing](../../../visual-basic/language-reference/nothing.md), afin qu'au lieu de devoir gérer une exception possible, vous devez seulement tester le résultat retourné par rapport à `Nothing`.  
  
 Utilisez le mot clé `TryCast` de la même façon que si vous utilisiez les mots clés [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md) et [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) .  Vous fournissez une expression comme le premier argument et un type dans lequel le convertir comme deuxième argument.  `TryCast` fonctionne uniquement sur des types références, tels que les classes et les interfaces.  Une relation d'héritage ou d'implémentation entre les deux types est requise.  Cela signifie qu'un type doit hériter de l'autre ou l'implémenter.  
  
## Erreurs et échecs  
 `TryCast` génère une erreur du compilateur s'il détecte qu'il n'y a aucune relation d'héritage ou d'implémentation.  Cependant, l'absence d'erreur du compilateur ne garantit pas une conversion réussie.  Si la conversion souhaitée est restrictive, elle peut échouer au moment de l'exécution.  Le cas échéant, `TryCast` retourne [Nothing](../../../visual-basic/language-reference/nothing.md).  
  
## Mots clés de conversion  
 Une comparaison des mots clés de conversion de type se présente comme suit.  
  
|||||  
|-|-|-|-|  
|Mot clé|Types de données|Relation d'argument|Échec lors de l'exécution|  
|[CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)|Tout type de données|Une conversion étendue ou restrictive doit être définie entre les deux types de données|Lève <xref:System.InvalidCastException>|  
|[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)|Tout type de données|Un type doit hériter de l'autre type ou l'implémenter|Lève <xref:System.InvalidCastException>|  
|`TryCast`|Types référence uniquement|Un type doit hériter de l'autre type ou l'implémenter|Retourne [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## Exemple  
 L'exemple suivant montre comment utiliser `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/visualbasic/trycast-operator_1.vb)]  
  
## Voir aussi  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)