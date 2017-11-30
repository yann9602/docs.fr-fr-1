---
title: Conversion des tableaux (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a>Conversion des tableaux (Visual Basic)
Vous pouvez convertir un type tableau vers un autre type fourni les conditions suivantes :  
  
-   **Rang égal.** Les rangs des deux tableaux doivent être identiques, autrement dit, ils doivent avoir le même nombre de dimensions. Toutefois, les longueurs des dimensions respectives n’avez pas besoin être les mêmes.  
  
-   **Type de données d’élément.** Les types de données des éléments des deux tableaux doivent être des types référence. Vous ne pouvez pas convertir un `Integer` de tableau à un `Long` ou même à un `Object` de tableau, car au moins un type valeur est impliqué. Pour plus d’informations, consultez [les Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibilité.** Une conversion restrictive ou étendue doit être possible entre les types d’éléments des deux tableaux. Un exemple qui ne satisfait pas cette condition est une tentative de conversion entre un `String` tableau et un tableau d’une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>. Ces deux types n’ont rien en commun et aucune conversion n’existe entre eux.  
  
 Une conversion de type d’un tableau à un autre élargissent ou selon si la conversion des éléments respectifs est restrictive ou étendue. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Conversion en un tableau d’objets  
 Lorsque vous déclarez un `Object` tableau sans l’initialiser, son type d’élément est `Object` tant qu’il reste sans être initialisé. Lorsque vous la définissez dans un tableau d’une classe spécifique, il prend le type de cette classe. Toutefois, son type sous-jacent est toujours `Object`, et vous pouvez ensuite le configurer en un autre tableau de classe non apparentée. Étant donné que toutes les classes dérivent à partir de `Object`, vous pouvez modifier le type d’élément du tableau à partir de n’importe quelle classe à une autre classe.  
  
 Dans l’exemple suivant, aucune conversion n’existe entre les types `student` et `String`, mais les deux dérivent `Object`, de sorte que toutes les affectations sont valides.  
  
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
  
### <a name="underlying-type-of-an-array"></a>Type sous-jacent d’un tableau  
 Si vous déclarez à l’origine d’un tableau avec une classe particulière, son type d’élément sous-jacent est cette classe. Si vous lui affectez par la suite à un tableau d’une autre classe, il doit y avoir une conversion entre les deux classes.  
  
 Dans l’exemple suivant, `students` est un `student` tableau. Dans la mesure où il n’existe aucune conversion entre `String` et `student`, la dernière instruction échoue.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversion entre des chaînes et d’autres types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Comment : convertir un objet en un autre Type en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
