---
title: "Composite Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "classes [Visual Basic], composite types"
  - "types [Visual Basic], composite"
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Composite Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Outre les types de données élémentaires fournis par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez assembler des éléments de différents types pour créer des *types de données composites*, tels que des structures, des tableaux et des classes.  Vous pouvez créer des types de données composites à partir des types élémentaires et d'autres types composites.  Par exemple, vous pouvez définir un tableau d'éléments de structure ou une structure de membres de tableau.  
  
## Types de données  
 Un type composite diffère du type de données de l'ensemble de ses composants.  Par exemple, un tableau d'éléments `Integer` n'est pas du type de données `Integer`.  
  
 Un type de données de tableau est représenté normalement à l'aide du type d'élément, de parenthèses et de virgules si nécessaire.  Par exemple, un tableau unidimensionnel d'éléments `String` est représenté comme `String()` et un tableau à deux dimensions d'éléments `Boolean` est représenté comme `Boolean(,)`.  
  
## Types structure  
 Il n'existe pas de type de données englobant toutes les structures.  Au lieu de cela, chaque définition d'une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre.  Toutefois, si vous créez plusieurs instances de la même structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les considère comme correspondant au même type de données.  
  
## Types tableau  
 Il n'existe pas de type de données unique englobant tous les tableaux.  Le type de données d'une instance particulière d'un tableau est déterminé par les facteurs suivants :  
  
-   le fait qu'il s'agit d'un tableau ;  
  
-   le rang \(nombre de dimensions\) du tableau ;  
  
-   le type des éléments du tableau.  
  
 En particulier, la longueur d'une dimension ne fait pas partie du type de données de l'instance.  L'exemple suivant illustre ce comportement.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Dans l'exemple précédent, les variables tableau `arrayA` et `arrayB` sont considérées comme appartenant au même type de données \(`Byte()`\), bien qu'elles soient initialisées avec des longueurs différentes.  Les variables `arrayB` et `arrayC` ne sont pas du même type car leurs types d'éléments sont différents.  Les variables `arrayC` et `arrayD` ne sont pas du même type car leurs rangs sont différents.  Les variables `arrayD` et `arrayE` ont le même type \(`Short(,)`\) car leurs rangs et types d'éléments sont les mêmes, bien que `arrayD` ne soit pas encore initialisé.  
  
 Pour plus d'informations sur les tableaux, consultez [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Types classe  
 Il n'existe pas de type de données englobant toutes les classes.  Bien qu'une classe puisse hériter d'une autre classe, chacune est un type de données distinct.  Les différentes instances de la même classe sont du même type de données.  Si vous assignez une variable d'instance de classe à une autre, elles ont non seulement le même type de données, mais elles pointent vers la même instance de classe en mémoire.  
  
 Pour plus d'informations sur les classes, consultez [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Types génériques Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)