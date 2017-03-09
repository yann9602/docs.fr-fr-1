---
title: "New Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.new"
  - "vb.NewConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constraints, Visual Basic generic types"
  - "generics [Visual Basic], constraints"
  - "constraints, New keyword"
  - "New constraint"
  - "New keyword"
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# New Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Présente une clause `New` pour créer une instance de l'objet, spécifie une contrainte de constructeur sur un paramètre de type ou identifie une procédure `Sub` en tant que constructeur de classe.  
  
## Notes  
 Dans une instruction de déclaration ou d'assignation, une clause `New` doit spécifier une classe définie à partir de laquelle l'instance peut être créée.  Cela signifie que la classe doit exposer un ou plusieurs constructeurs auxquels le code appelant peut accéder.  
  
 Vous pouvez utiliser une clause `New` dans une instruction de déclaration ou une instruction d'assignation.  Lorsque l'instruction est exécutée, elle appelle le constructeur approprié de la classe spécifiée, en passant les arguments que vous avez fournis.  L'exemple suivant illustre cela en créant des instances d'une classe `Customer` qui a deux constructeurs, l'un ne prenant aucun paramètre et l'autre prenant un paramètre de chaîne.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/visualbasic/new-operator_1.vb)]  
  
 Étant donné que les tableaux sont des classes, `New` peut créer une nouvelle instance de tableau, comme indiqué dans les exemples suivants.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/visualbasic/new-operator_2.vb)]  
  
 Le Common Language Runtime \(CLR\) lève une erreur <xref:System.OutOfMemoryException> s'il n'y a pas assez de mémoire pour créer la nouvelle instance.  
  
> [!NOTE]
>  Le mot clé `New` est aussi utilisé dans des listes de paramètres de type afin de spécifier que le type fourni doit exposer un constructeur sans paramètre accessible.  Pour plus d'informations sur les paramètres de type et les contraintes, consultez [Type List](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Pour créer une procédure de constructeur pour une classe, affectez au nom d'une procédure `Sub` le mot clé `New`.  Pour plus d'informations, consultez [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 Le mot clé `New` peut être utilisé dans les contextes suivants :  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 <xref:System.OutOfMemoryException>   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)