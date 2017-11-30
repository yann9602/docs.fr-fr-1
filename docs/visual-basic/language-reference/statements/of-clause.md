---
title: Of, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="of-clause-visual-basic"></a>Of, clause (Visual Basic)
Introduit un `Of` clause qui identifie un *le paramètre de type* sur un *générique* classe, structure, interface, délégué ou procédure. Pour plus d’informations sur les types génériques, consultez [des Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>À l’aide du mot clé  
 Le code suivant exemple utilise le `Of` mot clé pour définir le contour d’une classe qui prend deux paramètres de type. Il *contraint* le `keyType` paramètre par le <xref:System.IComparable> interface, ce qui signifie que le code utilisateur doit fournir un argument de type qui implémente <xref:System.IComparable>. Cela est nécessaire afin que les `add` procédure peut appeler le <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> (méthode). Pour plus d’informations sur les contraintes, consultez [Type liste](../../../visual-basic/language-reference/statements/type-list.md).  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Si vous terminez la définition de classe précédente, vous pouvez construire une variété de `dictionary` classes à partir de celui-ci. Les types que vous fournissez à `entryType` et `keyType` déterminer quel type d’entrée de la classe contient et le type de clé associe à chaque entrée. En raison de la contrainte, vous devez fournir au `keyType` un type qui implémente <xref:System.IComparable>.  
  
 L’exemple de code suivant crée un objet qui contient `String` entrées et associe un `Integer` clé avec chacun d’eux. `Integer`implémente <xref:System.IComparable> et par conséquent satisfait la contrainte sur `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Le mot clé `Of` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IComparable>  
 [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
