---
title: "How to: Convert an Object to Another Type in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "objects [Visual Basic], converting"
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Convert an Object to Another Type in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez convertir une variable `Object` en un autre type de données en utilisant un mot clé de conversion, tel que [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## Exemple  
 L'exemple suivant convertit une variable `Object` en un `Integer` et un `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Si vous savez que le contenu d'une variable `Object` est d'un type de données particulier, il est préférable de convertir la variable en ce type de données.  Si vous continuez à utiliser la variable `Object`, vous occasionnez une *conversion boxing*, une *conversion unboxing* \(pour un type valeur\) ou une *liaison tardive* \(pour un type référence\).  Ces opérations nécessitent toutes un temps d'exécution supplémentaire et ralentissent les performances.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Référence à l'espace de noms <xref:System?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Object>   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)