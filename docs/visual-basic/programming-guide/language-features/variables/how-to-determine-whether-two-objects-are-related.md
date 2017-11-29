---
title: "Comment : déterminer si deux objets sont liés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Comment : déterminer si deux objets sont liés (Visual Basic)
Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir de laquelle ils sont créés. Le <xref:System.Type.IsInstanceOfType%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe retourne `True` si la classe actuelle hérite de la classe spécifiée, ou si le type actuel est une interface prise en charge par la classe spécifiée.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Pour déterminer si un objet hérite de la classe ou une interface d’un autre objet  
  
1.  Sur l’objet que vous pensez peut être du type de base, appellent la <xref:System.Object.GetType%2A> (méthode).  
  
2.  Sur le <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A>, appelez le <xref:System.Type.IsInstanceOfType%2A> (méthode).  
  
3.  Dans la liste d’arguments <xref:System.Type.IsInstanceOfType%2A>, spécifiez l’objet que vous pensez être du type dérivé.  
  
     <xref:System.Type.IsInstanceOfType%2A>Retourne `True` si son type d’argument hérite le <xref:System.Type?displayProperty=nameWithType> type d’objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant détermine si un objet représente une classe dérivée de la classe d’un autre objet.  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 Notez l’emplacement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A>. Le type de base supposé est utilisé pour générer le <xref:System.Type?displayProperty=nameWithType> classe et le type dérivé supposé est passée comme argument à la <xref:System.Type.IsInstanceOfType%2A> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Guide pratique : déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
