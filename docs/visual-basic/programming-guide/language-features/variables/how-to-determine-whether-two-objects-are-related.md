---
title: "How to: Determine Whether Two Objects Are Related (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inheritance, Visual Basic objects"
  - "objects [Visual Basic], inheritance"
  - "object variables, determining relation"
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Determine Whether Two Objects Are Related (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez comparer deux objets pour déterminer la relation qui existe éventuellement entre les classes à partir desquelles ils sont créés.  La méthode <xref:System.Type.IsInstanceOfType%2A> de la classe <xref:System.Type?displayProperty=fullName> retourne `True` si la classe indiquée hérite de la classe active ou si le type actif représente une interface prise en charge par la classe indiquée.  
  
### Pour déterminer si un objet hérite de la classe ou de l'interface d'un autre objet  
  
1.  Appelez la méthode <xref:System.Object.GetType%2A> sur l'objet que vous pensez être du type de base.  
  
2.  Sur l'objet <xref:System.Type?displayProperty=fullName> retourné par <xref:System.Object.GetType%2A>, appelez la méthode <xref:System.Type.IsInstanceOfType%2A>.  
  
3.  Dans la liste d'arguments pour <xref:System.Type.IsInstanceOfType%2A>, spécifiez l'objet que vous pensez être du type dérivé.  
  
     <xref:System.Type.IsInstanceOfType%2A> retourne `True` si son type d'argument hérite du type d'objet <xref:System.Type?displayProperty=fullName>.  
  
## Exemple  
 L'exemple ci\-dessous détermine si un objet représente une classe dérivée de la classe d'un autre objet.  
  
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
  
 Notez l'emplacement inattendu des deux variables objets dans l'appel à <xref:System.Type.IsInstanceOfType%2A>.  Le type de base supposé est utilisé pour générer la classe <xref:System.Type?displayProperty=fullName> et le type dérivé supposé est transmis sous forme d'argument à la méthode <xref:System.Type.IsInstanceOfType%2A>.  
  
## Voir aussi  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.IsInstanceOfType%2A>   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)