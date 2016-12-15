---
title: "How to: Declare an Object by Using an Object Initializer (Visual Basic) | Microsoft Docs"
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
  - "declaring objects using object initializer"
  - "object initializers [Visual Basic]"
  - "initializers [Visual Basic]"
  - "Video How tos, Visual Basic"
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare an Object by Using an Object Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les initialiseurs d'objets vous permettent de déclarer et d'instancier une instance d'une classe dans une instruction unique.  De plus, vous pouvez initialiser simultanément un ou plusieurs membres de l'instance, sans appeler un constructeur paramétré.  
  
 Lorsque vous utilisez un initialiseur d'objet pour créer une instance d'un type nommé, le constructeur par défaut pour la classe est appelé, suivi par l'initialisation de membres désignés dans l'ordre que vous spécifiez.  
  
 La procédure suivante indique comment créer une instance d'une classe `Student` de trois façons différentes.  La classe possède, entre autres, des propriétés de prénom, de nom et d'année de classe.  Chacune des trois déclarations crée une nouvelle instance de `Student`, la propriété `First` ayant la valeur "Michael", la propriété `Last` la valeur "Tucker", et tous les autres membres leurs valeurs par défaut.  Le résultat de chaque déclaration dans la procédure est équivalent à l'exemple suivant, qui n'utilise pas d'initialiseur d'objet.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Pour une implémentation de la classe `Student`, consultez [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  Vous pouvez copier le code de cette rubrique pour définir la classe et créer une liste d'objets `Student` à utiliser.  
  
### Pour créer un objet de classe nommée à l'aide d'un initialiseur d'objet  
  
1.  Commencez la déclaration comme si vous projetiez d'utiliser un constructeur.  
  
     `Dim student1 As New Student`  
  
2.  Tapez le mot clé `With`, suivi d'une liste d'initialisation entre accolades.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Dans la liste d'initialisation, incluez chaque propriété que vous souhaitez initialiser et assignez\-lui une valeur initiale.  Le nom de la propriété est précédé d'un point.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Vous pouvez initialiser un ou plusieurs membres de la classe.  
  
4.  Vous pouvez également déclarer une nouvelle instance de la classe, puis lui assigner une valeur.  En premier lieu, déclarez une instance de `Student` :  
  
     `Dim student2 As Student`  
  
5.  Commencez par créer normalement une instance de `Student`.  
  
     `Dim student2 As Student = New Student`  
  
6.  Tapez `With`, puis un initialiseur d'objet pour initialiser un ou plusieurs membres de la nouvelle instance.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Vous pouvez simplifier la définition dans l'étape précédente en omettant `As Student`.  Dans ce cas, le compilateur détermine que `student3` est une instance de `Student` en utilisant l'inférence de type local.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Pour plus d'informations, consultez [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## Voir aussi  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)