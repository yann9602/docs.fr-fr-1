---
title: 'Comment : initialiser une variable tableau en Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Comment : initialiser une variable tableau en Visual Basic
Vous initialisez une variable tableau en incluant le littéral dans un `New` clause et en spécifiant les valeurs initiales du tableau. Vous pouvez spécifier le type ou pouvoir être déduit à partir des valeurs du littéral de tableau. Pour plus d’informations sur la façon dont le type est déduit, consultez « Remplissage d’un tableau avec des valeurs initiales » dans [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Pour initialiser une variable tableau à l’aide d’un littéral de tableau  
  
-   Dans le `New` clause, ou lorsque vous affectez la valeur de tableau, fournissez les valeurs d’élément à l’intérieur des accolades (`{}`). L’exemple suivant montre plusieurs façons de déclarer, créer et initialiser une variable pour contenir un tableau qui comporte des éléments de type `Char`.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Après l’exécution de chaque instruction, le tableau créé a une longueur de 3, avec des éléments à l’index 0 à l’index 2 contenant les valeurs initiales. Si vous fournissez à la fois la limite supérieure et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu'à la limite supérieure.  
  
     Notez que vous n’êtes pas obligé de spécifier la limite supérieure d’index si vous fournissez des valeurs d’éléments dans un littéral de tableau. Si aucune limite supérieure n’est spécifiée, la taille du tableau est déduite en fonction du nombre de valeurs dans le littéral de tableau.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Pour initialiser une variable de tableau multidimensionnel à l’aide de littéraux de tableau  
  
-   Imbriquer des valeurs à l’intérieur des accolades (`{}`) entre accolades. Vérifiez que les littéraux de tableaux imbriqués que tous déduits en tant que tableaux du même type et de longueur. L’exemple de code suivant montre plusieurs exemples d’initialisation de tableau multidimensionnel.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Vous pouvez explicitement spécifier les limites du tableau, ou les ignorer et indiquer au compilateur de déduire les limites du tableau selon les valeurs du littéral de tableau. Si vous fournissez à la fois les limites supérieures et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu'à la limite supérieure de chaque dimension. L’exemple suivant montre plusieurs façons de déclarer, créer et initialiser une variable pour contenir un tableau à deux dimensions qui comporte des éléments de type`Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Après l’exécution de chaque instruction, le tableau créé contient six éléments initialisés qui ont des index `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, et `(1,2)`. Chaque emplacement de tableau contient la valeur `10`.  
  
-   L’exemple suivant effectue une itération dans un tableau multidimensionnel. Dans une application de console Windows qui est écrit en Visual Basic, collez le code à l’intérieur de la `Sub Main()` (méthode). Les commentaires dernière affichent la sortie.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Pour initialiser une variable tableau en escalier à l’aide de littéraux de tableau  
  
-   Imbriquer des valeurs de l’objet à l’intérieur des accolades (`{}`). Bien que vous pouvez également imbriquer des littéraux de tableau qui spécifient des tableaux de longueurs différentes, dans le cas d’un tableau en escalier, assurez-vous que les littéraux de tableaux imbriqués sont placés entre parenthèses (`()`). Les parenthèses forcent l’évaluation des littéraux de tableaux imbriqués et les tableaux obtenus sont utilisés comme valeurs initiales du tableau en escalier. L’exemple de code suivant montre deux exemples de l’initialisation de tableau en escalier.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   L’exemple suivant effectue une itération dans un tableau en escalier. Dans une application de console Windows qui est écrit en Visual Basic, collez le code à l’intérieur de la `Sub Main()` (méthode).  Les dernière commentaires dans le code affichent la sortie.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dépannage des tableaux](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
