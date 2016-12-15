---
title: "Generic Procedures in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
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
  - "generic methods, type inference"
  - "generics [Visual Basic], type inference"
  - "procedures, generic"
  - "generic procedures"
  - "type inference, generics"
  - "generic methods"
  - "type inference"
  - "generics [Visual Basic], procedures"
  - "generic procedures, type inference"
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Generic Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une *procédure générique*, appelée également *méthode générique*, est une procédure définie avec au moins un paramètre de type.  Cela permet au code appelant d'adapter les types de données à ses besoins à chaque fois qu'il appelle la procédure.  
  
 Une procédure n'est pas générique simplement du fait qu'elle est définie au sein d'une classe ou d'une structure générique.  Pour être générique, la procédure doit prendre au moins un paramètre de type, en plus de tous les paramètres normaux qu'il peut prendre.  Une classe ou une structure générique peut contenir des procédures non génériques. Une classe, une structure ou un module non générique peut contenir des procédures génériques.  
  
 Une procédure générique peut utiliser ses paramètres de type dans sa liste de paramètres normale, dans son type de retour le cas échéant et dans son code de procédure.  
  
## Inférence de type  
 Vous pouvez appeler une procédure générique sans fournir du tout d'arguments de type.  Si vous l'appelez de cette façon, le compilateur essaie de déterminer les types de données appropriés à passer aux arguments de type de la procédure.  C'est ce qu'on appelle l'*inférence de type*.  Le code suivant affiche un appel dans lequel le compilateur déduit qu'il doit passer le type `String` au paramètre de type `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Si le compilateur ne peut pas déduire les arguments de type à partir du contexte de votre appel, il signale une erreur.  Une cause possible d'une telle erreur est une incompatibilité de rang de tableau.  Par exemple, supposons que vous définissez un paramètre normal comme un tableau de paramètre de type.  Si vous appelez la procédure générique fournissant un tableau d'un rang différent \(nombre de dimensions\), l'incompatibilité entraîne l'échec de l'inférence du type.  Le code suivant affiche un appel dans lequel un tableau à deux dimensions est passé à une procédure qui attend un tableau unidimensionnel.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Vous pouvez appeler l'inférence de type uniquement en omettant tous les arguments de type.  Si vous fournissez un argument de type, vous devez les fournir tous.  
  
 L'inférence de type est prise en charge uniquement pour les procédures génériques.  Vous ne pouvez pas appeler l'inférence de type sur les classes, les structures, les interfaces ou les délégués génériques.  
  
## Exemple  
  
### Description  
 L'exemple suivant définit une procédure `Function` générique destinée à rechercher un élément particulier dans un tableau.  Il définit un paramètre de type et l'utilise pour construire les deux paramètres dans la liste de paramètres.  
  
### Code  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### Commentaires  
 L'exemple précédent nécessite la capacité à comparer `searchValue` par rapport à chaque élément de `searchArray`.  Pour garantir cette capacité, il contraint le paramètre de type `T` à implémenter l'interface <xref:System.IComparable%601>.  Le code utilise la méthode <xref:System.IComparable%601.CompareTo%2A> au lieu de l'opérateur `=`, parce qu'il n'y a aucune garantie qu'un argument de type fourni pour `T` prenne en charge l'opérateur `=`.  
  
 Vous pouvez tester la procédure `findElement` à l'aide du code suivant.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Les appels précédents à `MsgBox` affichent "0", "1" et "\-1" respectivement.  
  
## Voir aussi  
 [Types génériques Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [Comment : utiliser une classe générique](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Parameter List](../../../../visual-basic/language-reference/statements/parameter-list.md)