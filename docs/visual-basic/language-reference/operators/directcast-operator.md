---
title: "DirectCast Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.directCast"
  - "directCast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DirectCast keyword"
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# DirectCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Introduit une opération de conversion de type basée sur l'héritage ou l'implémentation.  
  
## Notes  
 `DirectCast` n'utilise pas les routines d'assistance d'exécution Visual Basic pour la conversion, par conséquent, il peut en quelque sorte donner de meilleures performances que `CType` lors de la conversion vers et à partir du type de données `Object`.  
  
 Utilisez le mot clé `DirectCast` de la même façon que si vous utilisiez les mots clés [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md) et [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) .  Vous fournissez une expression comme le premier argument et un type dans lequel le convertir comme deuxième argument.  `DirectCast` requiert un héritage ou une relation d'implémentation entre les types de données des deux arguments.  Cela signifie qu'un type doit hériter de l'autre ou l'implémenter.  
  
## Erreurs et échecs  
 `DirectCast` génère une erreur du compilateur s'il détecte qu'il n'y a aucune relation d'héritage ou d'implémentation.  Cependant, l'absence d'erreur du compilateur ne garantit pas une conversion réussie.  Si la conversion souhaitée est restrictive, elle peut échouer au moment de l'exécution.  Le cas échéant, l'exécution lève une erreur <xref:System.InvalidCastException>.  
  
## Mots clés de conversion  
 Une comparaison des mots clés de conversion de type se présente comme suit.  
  
|||||  
|-|-|-|-|  
|Mot clé|Types de données|Relation d'argument|Échec lors de l'exécution|  
|[CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)|Tout type de données|Une conversion étendue ou restrictive doit être définie entre les deux types de données|Lève <xref:System.InvalidCastException>|  
|`DirectCast`|Tout type de données|Un type doit hériter de l'autre type ou l'implémenter|Lève <xref:System.InvalidCastException>|  
|[TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)|Types référence uniquement|Un type doit hériter de l'autre type ou l'implémenter|Retourne [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## Exemple  
 L'exemple suivant illustre deux utilisations de `DirectCast`, une qui échoue au moment de l'exécution et une qui réussit.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/visualbasic/directcast-operator_1.vb)]  
  
 Dans l'exemple précédent, le type run\-time de `q` est `Double`.  `CType` réussit parce que `Double` peut être converti en `Integer`.  Toutefois, la première utilisation de `DirectCast` échoue au moment de l'exécution parce que le type d'exécution de `Double` n'a aucune relation d'héritage avec `Integer`, bien qu'une conversion existe.  La deuxième utilisation de `DirectCast` réussit parce qu'elle convertit depuis le type <xref:System.Windows.Forms.Form> vers le type <xref:System.Windows.Forms.Control> duquel <xref:System.Windows.Forms.Form> hérite.  
  
## Voir aussi  
 <xref:System.Convert.ChangeType%2A?displayProperty=fullName>   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)