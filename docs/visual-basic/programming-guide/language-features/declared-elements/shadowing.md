---
title: "Shadowing in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inheritance, shadowing"
  - "overriding, and shadowing"
  - "shadowing"
  - "duplicate names"
  - "shadowing, by inheritance"
  - "declared elements, referencing"
  - "shadowing, by scope"
  - "declared elements, hiding"
  - "naming conflicts, shadowing"
  - "declared elements, shadowing"
  - "shadowing, and overriding"
  - "scope, shadowing"
  - "Shadows keyword, about"
  - "objects [Visual Basic], names"
  - "names, shadowing"
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Shadowing in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Lorsque deux éléments de programmation partagent le même nom, l'un des deux peut masquer \(ou *occulter*\) l'autre.  Dans ce cas, l'élément occulté n'est pas disponible à des fins de référence ; en effet, lorsque votre code utilise le nom de l'élément, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] le résout vers l'élément occultant.  
  
## Objectif  
 L'objectif principal de l'occultation est de protéger la définition de vos membres de classe.  La classe de base peut subir un changement qui crée un élément du même nom que celui que vous avez déjà défini.  Dans ce cas, le modificateur `Shadows` oblige les références de votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.  
  
## Types d'occultation  
 Un élément peut occulter un autre élément de deux façons différentes.  L'élément occultant peut être déclaré dans une sous\-région de la région contenant l'élément occulté ; dans ce cas, l'occultation s'effectue *par l'intermédiaire de la portée*.  Une classe dérivante peut également redéfinir un membre d'une classe de base ; dans ce cas, l'occultation se produit *par l'intermédiaire de l'héritage*.  
  
### Occultation par l'intermédiaire de la portée  
 Des éléments de programmation du même module, de la même classe ou de la même structure peuvent avoir le même nom, mais une portée différente.  Lorsque deux éléments sont déclarés de cette façon et que le code fait référence au nom qu'ils partagent, l'élément à la portée la plus restreinte occulte l'autre élément \(la portée de bloc est la plus restreinte\).  
  
 Ainsi, un module peut définir une variable `Public` appelée `temp` et une procédure du module peut déclarer une variable locale également appelée `temp`.  Les références à `temp` à partir de la procédure accèdent à la variable locale, tandis que les références à `temp` à partir de l'extérieur de la procédure accèdent à la variable `Public`.  Dans ce cas, la variable `temp` de la procédure occulte la variable `temp` du module.  
  
 L'illustration suivante montre deux variables, toutes deux nommées `temp`.  La variable locale `temp` occulte la variable membre `temp` lorsque l'utilisateur y accède à partir de sa propre procédure `p`.  Toutefois, le mot clé `MyClass` outrepasse l'occultation et accède à la variable membre.  
  
 ![Diagramme graphique d'une occultation par portée](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
Occultation par l'intermédiaire de la portée  
  
 Pour obtenir un exemple d'occultation par l'intermédiaire de la portée, consultez [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### Occultation par héritage  
 Si une classe dérivée redéfinit un élément de programmation hérité d'une classe de base, l'élément qui redéfinit occulte l'élément d'origine.  Vous pouvez occulter n'importe quel type d'élément déclaré, ou ensemble d'éléments surchargés, avec un autre type.  Par exemple, une variable `Integer` peut occulter une procédure `Function`.  Si vous occultez une procédure par une autre procédure, vous pouvez utiliser une liste de paramètres différente et un type de retour différent.  
  
 L'illustration suivante montre une classe de base `b` et une classe dérivée `d` qui hérite de `b`.  La classe de base définit une procédure nommée `proc` et la classe dérivée l'occulte avec une autre procédure du même nom.  La première instruction `Call` accède au `proc` occultant dans la classe dérivée.  Toutefois, le mot clé `MyBase` outrepasse l'occultation et accède à la procédure occultée dans la classe de base.  
  
 ![Diagramme graphique d'une occultation par héritage](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
Occultation par héritage  
  
 Pour obtenir un exemple d'occultation par l'intermédiaire de l'héritage, consultez [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) et [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### Occultation et niveau d'accès  
 L'élément occultant n'est pas toujours accessible à partir du code à l'aide de la classe dérivée.  Par exemple, il peut être déclaré `Private`.  Dans ce cas, l'occultation échoue et le compilateur résout toute référence au même élément qu'il aurait en l'absence d'occultation.  Il s'agit de l'élément accessible qui présente le moins d'étapes de dérivation vers l'arrière à partir de la classe d'occultation.  Si l'élément occulté correspond à une procédure, la résolution est effectuée vers la version la plus proche accessible dotée des mêmes nom, liste de paramètres et type de retour.  
  
 L'exemple suivant montre une hiérarchie d'héritage de trois classes.  Chaque classe définit une procédure `Sub` `display` et chaque classe dérivée occulte la procédure `display` dans sa classe de base.  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 Dans l'exemple précédent, la classe dérivée `secondClass` occulte `display` avec une procédure `Private`.  Lorsque le module `callDisplay` appelle `display` dans `secondClass`, le code appelant est à l'extérieur de `secondClass` et par conséquent ne peut pas accéder à la procédure `display` privée.  L'occultation échoue et le compilateur résout la référence vers la procédure `display` de la classe de base.  
  
 Toutefois, la classe dérivée supplémentaire `thirdClass` déclare `display` comme `Public` ; par conséquent, le code dans `callDisplay` peut y accéder.  
  
## Occultation et substitution  
 Ne confondez pas l'occultation et la substitution.  Elles sont toutes deux utilisées lorsqu'une classe dérivée hérite d'une classe de base et elles redéfinissent un élément déclaré par un autre.  Il existe toutefois des différences notables entre l'occultation et la substitution.  Pour obtenir une comparaison, consultez [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## Occultation et surcharge  
 Si vous occultez le même élément de classe de base avec plusieurs éléments de votre classe dérivée, les éléments occultants deviennent des versions surchargées de cet élément.  Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## Accès à un élément occulté  
 Lorsque vous accédez à un élément à partir d'une classe dérivée, vous le faites normalement par l'instance en cours de cette classe dérivée, en qualifiant le nom de l'élément avec le mot clé `Me`.  Si votre classe dérivée occulte l'élément figurant dans la classe de base, vous pouvez accéder à l'élément de la classe de base en le qualifiant avec le mot clé `MyBase`.  
  
 Pour obtenir un exemple d'accès à un élément occulté, consultez [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### Déclaration de la variable objet  
 La façon dont vous créez la variable objet peut également déterminer si la classe dérivée accède à un élément occultant ou à l'élément occulté.  L'exemple suivant crée deux objets à partir d'une classe dérivée, mais l'un des objets est déclaré comme classe de base et l'autre comme classe dérivée.  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 Dans l'exemple précédent, la variable `basObj` est déclarée comme la classe de base.  L'assignation d'un objet `dervCls` à cette classe constitue une conversion étendue et est donc valide.  Toutefois, la classe de base ne pouvant pas accéder à la version occultante de la variable `z` dans la classe dérivée, le compilateur résout `basObj.z` à la valeur de la classe de base d'origine.  
  
## Voir aussi  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)