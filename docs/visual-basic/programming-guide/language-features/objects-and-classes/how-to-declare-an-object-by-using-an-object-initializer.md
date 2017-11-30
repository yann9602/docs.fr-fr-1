---
title: "Comment : déclarer un objet à l'aide d'un initialiseur d'objet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Comment : déclarer un objet à l'aide d'un initialiseur d'objet (Visual Basic)
Initialiseurs d’objets permettent de déclarer et instancier une instance d’une classe dans une instruction unique. En outre, vous pouvez initialiser un ou plusieurs membres de l’instance en même temps, sans appeler un constructeur paramétrable.  
  
 Lorsque vous utilisez un initialiseur d’objet pour créer une instance d’un type nommé, le constructeur par défaut pour la classe est appelé, suivie de l’initialisation de membres désignés dans l’ordre que vous spécifiez.  
  
 La procédure suivante montre comment créer une instance d’un `Student` classe de trois façons différentes. La classe possède les prénom, nom, propriétés et de classe année, entre autres. Chacune des trois déclarations crée une nouvelle instance de `Student`, avec la propriété `First` défini sur « Michael, « propriété `Last` défini sur « Tucker », et tous les autres membres définissent à leurs valeurs par défaut. Le résultat de chaque déclaration dans la procédure est équivalent à l’exemple suivant, qui n’utilise pas un initialiseur d’objet.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Pour une implémentation de la `Student` de classe, consultez [Comment : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Vous pouvez copier le code de cette rubrique pour définir la classe et créer une liste de `Student` objets à utiliser.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Pour créer un objet de classe nommée à l’aide d’un initialiseur d’objet  
  
1.  Commencez la déclaration comme si vous avez planifié à utiliser un constructeur.  
  
     `Dim student1 As New Student`  
  
2.  Tapez le mot clé `With`, suivi d’une liste d’initialisation entre accolades.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Dans la liste d’initialisation, incluez chaque propriété que vous souhaitez initialiser et lui assigner une valeur initiale. Le nom de la propriété est précédé d’un point.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Vous pouvez initialiser un ou plusieurs membres de la classe.  
  
4.  Ou bien, vous pouvez déclarer une nouvelle instance de la classe et puis affectez-lui une valeur. Tout d’abord, déclarez une instance de `Student`:  
  
     `Dim student2 As Student`  
  
5.  Commencer la création d’une instance de `Student` de façon normale.  
  
     `Dim student2 As Student = New Student`  
  
6.  Type `With` et un initialiseur d’objet pour initialiser un ou plusieurs membres de la nouvelle instance.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Vous pouvez simplifier la définition dans l’étape précédente en omettant `As Student`. Si vous faites cela, le compilateur détermine que `student3` est une instance de `Student` à l’aide de l’inférence de type local.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Guide pratique : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [Initialiseurs d’objets : types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
