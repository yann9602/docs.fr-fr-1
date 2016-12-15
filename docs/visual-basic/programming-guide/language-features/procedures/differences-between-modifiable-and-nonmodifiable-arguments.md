---
title: "Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, arguments"
  - "procedure arguments"
  - "arguments [Visual Basic], nonmodifiable"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], modifiable"
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Lorsque vous appelez une procédure, vous lui passez généralement un ou plusieurs arguments.  Chaque argument correspond à un élément de programmation sous\-jacent.  Les éléments sous\-jacents et les arguments peuvent être modifiables ou non.  
  
## Éléments modifiables et non modifiables  
 Un élément de programmation peut être un *élément modifiable* dont la valeur peut changer ou un *élément non modifiable* dont la valeur reste fixe une fois qu'il est créé.  
  
 Le tableau suivant répertorie les éléments de programmation modifiables et non modifiables.  
  
|Éléments modifiables|Éléments non modifiables|  
|--------------------------|------------------------------|  
|Variables locales \(déclarées à l'intérieur des procédures\), comprenant les variables objet, sauf en lecture seule|Variables, champs et propriétés en lecture seule|  
|Champs \(variables membres de modules, de classes et de structures\), sauf en lecture seule|Constantes et littéraux|  
|Propriétés, sauf en lecture seule|Membres d'énumération|  
|Éléments de tableau|Expressions \(même si elles contiennent des éléments modifiables\)|  
  
## Arguments modifiables et non modifiables  
 Un *argument modifiable* est un élément comprenant un élément sous\-jacent modifiable.  Le code appelant peut stocker une nouvelle valeur à n'importe quel moment, et si vous passez l'argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), le code de la procédure peut également modifier l'élément sous\-jacent du code appelant.  
  
 Un *argument non modifiable* possède un élément non modifiable sous\-jacent ou est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  La procédure ne peut pas modifier l'élément sous\-jacent dans le code appelant, même si cet élément est modifiable.  Si cet élément est non modifiable, le code appelant ne peut pas le modifier.  
  
 La procédure appelée peut modifier sa copie locale de l'argument non modifiable, mais cette modification n'affecte pas l'élément sous\-jacent dans le code appelant.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)