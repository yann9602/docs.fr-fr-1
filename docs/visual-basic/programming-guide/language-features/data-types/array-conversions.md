---
title: "Array Conversions (Visual Basic) | Microsoft Docs"
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
  - "arrays [Visual Basic], converting type"
  - "type conversion, arrays"
  - "conversions, type"
  - "arrays [Visual Basic], data types"
  - "conversions, data type"
  - "object arrays, converting type"
  - "data type conversion, array conversions"
  - "conversions, array types"
  - "object arrays"
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Array Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez convertir un type tableau vers un autre type, pourvu que les conditions suivantes soient remplies :  
  
-   **Rang égal.** Les rangs des deux tableaux doivent être identiques ; autrement dit, les deux tableaux doivent avoir le même nombre de dimensions.  Toutefois, il n'est pas obligatoire que la longueur des dimensions respectives soit identique.  
  
-   **Type de données des éléments.** Les types de données des éléments des deux tableaux doivent être des types référence.  Vous ne pouvez pas convertir un tableau de type `Integer` en tableau `Long` ou même `Object`, parce que cette opération fait intervenir au moins un type valeur.  Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibilité.** Une conversion, qu'elle soit restrictive ou étendue, doit être possible entre les types d'éléments des deux tableaux.  Un exemple qui ne satisfait pas à cette condition est une tentative de conversion entre un tableau `String` et un tableau d'une classe dérivée de <xref:System.Attribute?displayProperty=fullName>.  Ces deux types n'ont rien en commun et aucune conversion n'existe entre eux.  
  
 Les conversions entre deux types tableau sont soit étendues, soit restrictives, selon qu'elles élargissent ou rétrécissent leurs éléments respectifs.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## Conversion vers un tableau de type Object  
 Lorsque vous déclarez un tableau `Object`, son type d'élément reste `Object` tant qu'il n'est pas initialisé.  Lorsque vous le configurez en tableau de classe particulière, il prend le type de cette classe.  Toutefois, son type sous\-jacent reste `Object` et vous pouvez ensuite le configurer en un autre tableau de classe non apparentée.  Étant donné que toutes les classes sont dérivées du type `Object`, vous pouvez modifier le type d'élément du tableau en remplaçant sa classe par toute autre classe.  
  
 Dans l'exemple ci\-dessous, aucune conversion n'existe entre les types `student` et `String`, mais ils sont tous deux dérivés du type `Object` et, par conséquent, toutes les assignations sont valides.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### Type sous\-jacent d'un tableau  
 Si vous déclarez à l'origine un tableau avec une classe particulière, son type d'élément sous\-jacent correspond à cette classe.  Par la suite, si vous le configurez en tableau de classe différente, une conversion doit être effectuée entre les deux classes.  
  
 Dans l'exemple ci\-après, `students` représente un tableau `student`.  Comme aucune conversion n'existe entre `String` et `student`, la dernière instruction se solde par un échec.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)