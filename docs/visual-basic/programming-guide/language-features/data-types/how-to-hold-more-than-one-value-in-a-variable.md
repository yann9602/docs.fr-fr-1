---
title: "How to: Hold More Than One Value in a Variable (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "arrays [Visual Basic], compilation errors"
  - "types [Visual Basic], composite"
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Hold More Than One Value in a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une variable contient plusieurs valeurs si vous la déclarez comme étant un *type de données composite*.  
  
 Les [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluent des structures, des tableaux et des classes.  Une variable d'un type de données composite peut contenir une combinaison de types de données élémentaires et d'autres types composites.  Les structures et les classes peuvent contenir du code aussi bien que des données.  
  
### Pour stocker plusieurs valeurs dans une variable  
  
1.  Déterminez le type de données composite que vous souhaitez utiliser pour votre variable.  
  
2.  Si le type de données composite n'est pas déjà défini, définissez\-le afin que votre variable puisse l'utiliser.  
  
    -   Définissez une structure à l'aide d'une [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Définissez un tableau à l'aide d'une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Définissez une classe à l'aide d'une [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Déclarez votre variable avec une instruction `Dim`.  
  
4.  Faites suivre le nom de variable d'une clause `As`.  
  
5.  Faites suivre le mot clé `As` du nom du type de données composite approprié.  
  
## Voir aussi  
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)