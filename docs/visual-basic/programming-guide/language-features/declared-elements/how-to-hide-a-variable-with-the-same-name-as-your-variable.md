---
title: "How to: Hide a Variable with the Same Name as Your Variable (Visual Basic) | Microsoft Docs"
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
  - "declarations, elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez masquer une variable en l'*occultant*, c'est\-à\-dire en la redéfinissant avec une variable du même nom.  Vous pouvez occulter la variable à masquer de deux manières :  
  
-   **Occultation par l'intermédiaire de la portée.** Vous pouvez l'occulter par l'intermédiaire de la portée en la redéclarant dans une sous\-région de la région contenant la variable à masquer.  
  
-   **Occultation par héritage.** Si la variable à masquer est définie au niveau de la classe, vous pouvez l'occulter par l'intermédiaire de l'héritage en la rédeclarant avec le mot clé [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) dans une classe dérivée.  
  
## Deux manières de masquer une variable  
  
#### Pour masquer une variable en l'occultant par l'intermédiaire de la portée  
  
1.  Déterminez la région qui définit la variable à masquer et déterminez une sous\-région dans laquelle la redéfinir avec votre variable.  
  
    |Région de variable|Sous\-région autorisée pour la redéfinir|  
    |------------------------|----------------------------------------------|  
    |Module|Classe dans le module|  
    |Classe|Sous\-classe dans la classe<br /><br /> Procédure dans la classe|  
  
     Vous ne pouvez pas redéfinir de variable de procédure dans un bloc au sein de cette procédure, par exemple dans une construction `If`...`End If` ou une boucle `For`.  
  
2.  Créez la sous\-région si elle n'existe pas déjà.  
  
3.  Dans la sous\-région, écrivez à une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) qui déclare la variable occultante.  
  
     Lorsque le code à l'intérieur de la sous\-région fait référence au nom de variable, le compilateur résout la référence à la variable occultante.  
  
     L'exemple suivant illustre l'occultation par l'intermédiaire de la portée, ainsi qu'une référence qui outrepasse l'occultation.  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     L'exemple précédent déclare la variable `num` à la fois au niveau du module et au niveau de la procédure \(dans la procédure `show`\).  La variable locale `num` occulte la variable de niveau module `num` dans `show` ; par conséquent, la variable locale a la valeur 2.  Toutefois, il n'existe aucune variable locale pour occulter `num` dans la procédure `useModuleLevelNum`.  Par conséquent, `useModuleLevelNum` définit la valeur de la variable au niveau du module à 1.  
  
     L'appel `MsgBox` à l'intérieur de `show` outrepasse le mécanisme d'occultation en qualifiant `num` avec le nom du module.  Par conséquent, il affiche la variable au niveau du module au lieu de la variable locale.  
  
#### Pour masquer une variable en l'occultant par l'intermédiaire de l'héritage  
  
1.  Assurez\-vous que la variable à masquer est déclarée dans une classe et au niveau de la classe \(en dehors de toute procédure\).  Sinon, vous ne pouvez pas l'occulter par héritage.  
  
2.  Définissez une classe dérivée de la classe de la variable s'il n'en n'existe pas déjà une.  
  
3.  À l'intérieur de la classe dérivée, écrivez une instruction `Dim` qui déclare votre variable.  Incluez le mot clé [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) dans la déclaration.  
  
     Lorsque le code de la classe dérivée fait référence au nom de la variable, le compilateur résout la référence à votre variable.  
  
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
  
     L'exemple précédent déclare la variable `shadowString` dans la classe de base et la masque dans la classe dérivée.  La procédure `showStrings` dans la classe dérivée affiche la version occultante de la chaîne lorsque le nom `shadowString` n'est pas qualifié.  Elle affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le mot clé `MyBase`.  
  
## Programmation fiable  
 L'occultation introduit plusieurs versions d'une variable avec le même nom.  Lorsqu'une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de plusieurs facteurs, tels que l'emplacement de l'instruction de code et la présence d'une chaîne qualifiante.  Cela peut augmenter le risque de référence à une version non souhaitée d'une variable occultée.  Vous pouvez réduire ce risque en qualifiant complètement toutes les références à une variable occultée.  
  
## Voir aussi  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)