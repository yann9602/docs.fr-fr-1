---
title: "How to: Access a Variable Hidden by a Derived Class (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "qualification, of element names"
  - "base classes, accessing elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declared elements, referencing"
  - "variables [Visual Basic], accessing hidden"
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access a Variable Hidden by a Derived Class (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque le code d'une classe dérivée accède à une variable, le compilateur résout normalement la référence vers la version accessible la plus proche, à savoir la version accessible avec le moins d'étapes de dérivation vers l'arrière de la classe accédante.  Si la variable est définie dans la classe dérivée, le code accède normalement à cette définition.  
  
 Si la variable de classe dérivée occulte une variable de la classe de base, elle masque la version de classe de base.  Toutefois, vous pouvez accéder à la variable de classe de base en la qualifiant avec le mot clé `MyBase`.  
  
### Pour accéder à une variable de classe de base masquée par une classe dérivée  
  
-   Dans une instruction d'expression ou d'assignation, faites précéder le nom de la variable du mot clé `MyBase` et d'un point \(`.`\).  
  
     Le compilateur résout la référence vers la version de classe de base de la variable.  
  
     L'exemple suivant illustre l'occultation par l'intermédiaire de l'héritage.  Il effectue deux références, une qui accède à la variable occultante et une qui outrepasse l'occultation.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     L'exemple précédent déclare la variable `shadowString` dans la classe de base et la masque dans la classe dérivée.  La procédure `showStrings` dans la classe dérivée affiche la version occultante de la chaîne lorsque le nom `shadowString` n'est pas qualifié.  Elle affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le mot clé `MyBase` .  
  
## Programmation fiable  
 Pour réduire le risque de référence à une version non souhaitée d'une variable occultée, vous pouvez effectuer une qualification complète de toutes les références vers une variable occultée.  L'occultation introduit plusieurs versions d'une variable avec le même nom.  Lorsqu'une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de plusieurs facteurs, tels que l'emplacement de l'instruction de code et la présence d'une chaîne qualifiante.  Cela peut augmenter le risque de référence à la version incorrecte de la variable.  
  
## Voir aussi  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)