---
title: "Object Variable Assignment (Visual Basic) | Microsoft Docs"
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
  - "Nothing keyword, object variable assignment"
  - "object variables, initializing"
  - "variables [Visual Basic], initializing"
  - "objects [Visual Basic], current instance"
  - "object variables, assigning"
  - "variables [Visual Basic], object variables"
  - "current instance, defined"
  - "variables [Visual Basic], assigning"
  - "assignment statements, object variable assignment"
  - "Me keyword, as object variable"
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Object Variable Assignment (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous devez utiliser une instruction d'assignation normale pour assigner un objet à une variable objet.  Vous pouvez assigner une expression d'objet ou le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md), comme le montre l'exemple suivant.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` signifie qu'il n'y a pas d'objet actuellement assigné à la variable.  
  
## Initialisation  
 Lorsque votre code commence à s'exécuter, vos variables objet sont initialisées avec la valeur `Nothing`.  Les variables dont les déclarations incluent l'initialisation sont réinitialisées avec les valeurs que vous spécifiez quand les instructions de déclaration sont exécutées.  
  
 Vous pouvez inclure l'initialisation dans votre déclaration à l'aide du mot clé [New](../../../../visual-basic/language-reference/operators/new-operator.md).  Les instructions de déclaration suivantes déclarent des variables objets `testUri` et `ver` et leur assignent des objets spécifiques.  Chacune utilise l'un des constructeurs surchargés de la classe appropriée pour initialiser l'objet.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## Dissociation  
 La définition d'une variable objet à la valeur `Nothing` supprime l'association entre la variable et un objet spécifique.  Cela vous empêche de modifier accidentellement l'objet en modifiant la variable.  Cela vous permet également de déterminer si la variable objet pointe vers un objet valide, comme le montre l'exemple suivant.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Si l'objet référencé par votre variable se trouve dans une autre application, ce test ne permet pas de déterminer si cette application vient de se terminer ou d'invalider l'objet.  
  
 Une variable objet avec une valeur de `Nothing` est également appelée une *référence Null*.  
  
## Instance actuelle  
 L'*instance en cours* d'un objet est celle dans laquelle le code est en train de s'exécuter.  Étant donné que la totalité du code s'exécute dans une procédure, l'instance en cours est celle dans laquelle la procédure a été appelée.  
  
 Le mot clé `Me` sert de variable objet faisant référence à l'instance en cours.  Si une procédure n'est pas [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), elle peut utiliser le mot clé `Me` pour obtenir un pointeur vers l'instance en cours.  Les procédures partagées ne peuvent pas être associées à une instance spécifique d'une classe.  
  
 L'utilisation de `Me` est particulièrement utile pour passer l'instance en cours vers une procédure d'un autre module.  Par exemple, supposons que vous disposez de plusieurs documents XML et souhaitez leur ajouter un texte standard.  L'exemple suivant définit une procédure le permettant.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Chaque objet document XML peut ensuite appeler la procédure et passer son instance en cours sous forme d'argument.  C'est ce qu'illustre l'exemple suivant.  
  
```  
addStandardText(Me)  
```  
  
## Voir aussi  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Make an Object Variable Not Refer to Any Instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)