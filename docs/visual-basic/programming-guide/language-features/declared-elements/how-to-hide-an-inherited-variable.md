---
title: "How to: Hide an Inherited Variable (Visual Basic) | Microsoft Docs"
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
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
  - "variables [Visual Basic], hiding inherited"
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Hide an Inherited Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une classe dérivée hérite de toutes les définitions de sa classe de base.  Si vous souhaitez définir une variable à l'aide du même nom qu'un élément de la classe de base, vous pouvez masquer \(ou *occulter*\) cet élément de classe de base lorsque vous définissez votre variable dans la classe dérivée.  Si vous procédez ainsi, le code de la classe dérivée accède à votre variable à moins qu'il n'outrepasse de manière explicite le mécanisme occultant.  
  
 L'une des autres raisons pour lesquelles vous pourriez souhaiter masquer une variable héritée serait pour la protéger de la révision de classe de base.  La classe de base peut subir une modification qui altère l'élément dont vous héritez.  Si cela se produit, le modificateur `Shadows` force les références de la classe dérivée à être résolues vers votre variable plutôt que vers l'élément de classe de base.  
  
### Pour masquer une variable héritée  
  
1.  Assurez\-vous que la variable à masquer est déclarée au niveau de la classe \(en dehors de toute procédure\).  Autrement, il n'est pas nécessaire de la masquer.  
  
2.  À l'intérieur de votre classe dérivée, écrivez une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) qui déclare votre variable.  Utilisez le même nom que celui de la variable héritée.  
  
3.  Incluez le mot clé [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) dans la déclaration.  
  
     Lorsque le code de la classe dérivée fait référence au nom de la variable, le compilateur résout la référence à votre variable.  
  
     L'exemple suivant illustre l'occultation d'une variable héritée.  
  
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
  
     L'exemple précédent déclare la variable `shadowString` dans la classe de base et la masque dans la classe dérivée.  La procédure `showStrings` dans la classe dérivée affiche la version occultante de la chaîne lorsque le nom `shadowString` n'est pas qualifié.  Elle affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le mot clé `MyBase`.  
  
## Programmation fiable  
 L'occultation introduit plusieurs versions d'une variable avec le même nom.  Lorsqu'une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de plusieurs facteurs, tels que l'emplacement de l'instruction de code et la présence d'une chaîne qualifiante.  Cela peut augmenter le risque de référence à une version non souhaitée d'une variable occultée.  Vous pouvez réduire ce risque en qualifiant complètement toutes les références à une variable occultée.  
  
## Voir aussi  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)