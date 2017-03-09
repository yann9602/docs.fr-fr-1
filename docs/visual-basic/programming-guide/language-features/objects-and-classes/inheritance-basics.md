---
title: "Inheritance Basics (Visual Basic) | Microsoft Docs"
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
  - "derived classes, inheritance"
  - "MyClass keyword, using"
  - "MyBase keyword, using"
  - "Inherits statement, inheritance"
  - "overriding, Overridable keyword"
  - "MustInherit keyword, using"
  - "Overrides keyword, using"
  - "inheritance"
  - "MustInherit classes"
  - "MustOverride keyword, using"
  - "classes [Visual Basic], derived"
  - "NotInheritable keyword, using"
  - "base classes, extending properties and methods"
  - "NotOverridable keyword, using"
  - "base classes, inheritance"
  - "abstract classes, inheritance"
  - "overriding, Overrides keyword"
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Inheritance Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'instruction `Inherits` permet de déclarer une nouvelle classe, appelée une *classe dérivée*, basée sur une classe existante, appelée une *classe de base*.  Les classes dérivées héritent des propriétés, des méthodes, des événements, des champs et des constantes de la classe de base et peuvent les étendre.  La section suivante décrit certaines règles de l'héritage et les modificateurs permettant de modifier la façon dont les classes peuvent hériter ou être héritées :  
  
-   Toutes les classes peuvent être héritées par défaut, sauf si elles sont marquées du mot clé `NotInheritable`.  Les classes peuvent hériter d'autres classes dans votre projet ou de classes dans d'autres assemblys faisant référence à votre projet.  
  
-   Contrairement aux langages autorisant des héritages multiples, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ne permet qu'un seul héritage dans des classes ; les classes dérivées ne peuvent avoir qu'une seule classe de base.  Bien que les héritages multiples ne soient pas autorisés dans les classes, les classes peuvent implémenter plusieurs interfaces, qui peuvent accomplir efficacement les mêmes buts.  
  
-   Pour empêcher l'exposition d'éléments restreints dans une classe de base, le type d'accès d'une classe dérivée doit être égal à sa classe de base ou être plus restrictif.  Par exemple, une classe `Public` ne peut pas hériter d'une classe `Friend` ou `Private`, et une classe `Friend` ne peut pas hériter d'une classe `Private`.  
  
## Modificateurs d'héritage  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] contient les instructions et les modificateurs de niveau classe suivants pour prendre en charge l'héritage :  
  
-   Instruction `Inherits` : spécifie la classe de base.  
  
-   Modificateur `NotInheritable` : empêche les programmeurs d'utiliser la classe comme une classe de base.  
  
-   Modificateur `MustInherit` : indique que la classe doit être utilisée uniquement comme une classe de base.  Les instances de la classe `MustInherit` ne peuvent pas être créées directement ; elles ne peuvent être créées que comme des instances de classe de base d'une classe dérivée  \(d'autres langages de programmation, tels que C\+\+ et C\#, utilisent le terme *classe abstraite* pour décrire une telle classe\).  
  
## Substitution de propriétés et de méthodes dans des classes dérivées  
 Par défaut, une classe dérivée hérite des propriétés et des méthodes de sa classe de base.  Si une propriété ou une méthode héritée doit se comporter différemment dans la classe dérivée, elle peut être *substituée*.  Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée.  Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :  
  
-   `Overridable` : permet la substitution d'une propriété ou d'une méthode d'une classe dans une classe dérivée.  
  
-   `Overrides` : substitue une propriété ou une méthode `Overridable` définie dans la classe de base.  
  
-   `NotOverridable`— Empêche une propriété ou une méthode d'être substituée dans une classe qui hérite.  Par défaut, les méthodes `Public` sont `NotOverridable`.  
  
-   `MustOverride` : la propriété ou la méthode doit être substituée par une classe dérivée.  Lorsque le mot clé `MustOverride` est utilisé, la définition de méthode se compose uniquement de l'instruction `Sub`, `Function` ou `Property`.  Aucune autre instruction n'est autorisée et, en particulier, aucune instruction `End Sub` ni `End Function`.  Les méthodes `MustOverride` doivent être déclarées dans les classes `MustInherit`.  
  
 Supposons que vous souhaitiez définir des classes pour gérer les salaires.  Vous pouvez définir une classe générique `Payroll` qui contient une méthode `RunPayroll` permettant de calculer les salaires pour une semaine type.  Vous pouvez ensuite utiliser `Payroll` comme une classe de base pour une classe `BonusPayroll` plus spécialisée qui peut être utilisée lors de la distribution de primes aux employés.  
  
 La classe `BonusPayroll` peut hériter et substituer la méthode `PayEmployee` définie dans la classe de base `Payroll`.  
  
 L'exemple suivant définit une classe de base `Payroll,` et une classe dérivée `BonusPayroll` pour substituer une méthode héritée nommée `PayEmployee`.  Une procédure, `RunPayroll`, crée et passe ensuite un objet `Payroll` et un objet `BonusPayroll` à une fonction, `Pay`, qui exécute la méthode `PayEmployee` sur les deux objets.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#28)]  
  
## MyBase, mot clé  
 Le mot clé `MyBase` se comporte comme une variable objet qui fait référence à la classe de base de l'instance actuelle d'une classe.  `MyBase` est fréquemment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée.  `MyBase.New` est, en particulier, utilisé pour appeler explicitement un constructeur de classe de base à partir d'un constructeur de classe dérivée.  
  
 Supposons par exemple que vous créez une classe dérivée qui substitue une méthode héritée d'une classe de base.  La méthode substituée peut appeler la méthode dans la classe de base et modifier la valeur de retour, comme illustré dans le fragment de code suivant :  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#109)]  
  
 La liste suivante décrit les restrictions de l'utilisation de `MyBase` :  
  
-   `MyBase` fait référence à la classe de base immédiate et à ses membres hérités.  Il ne peut pas être utilisé pour accéder aux membres `Private` de cette classe.  
  
-   `MyBase` est un mot clé, et non pas un objet réel.  `MyBase` ne peut pas être assigné à une variable, passé à des procédures, ni utilisé dans une comparaison `Is`.  
  
-   La méthode qualifiée par `MyBase` ne doit pas être définie dans la classe de base immédiate, mais dans une classe de base héritée indirectement.  Pour compiler correctement une référence qualifiée par `MyBase`, une classe de base doit contenir une méthode qui correspond au nom et aux types de paramètres apparaissant dans l'appel.  
  
-   Vous ne pouvez pas utiliser `MyBase` pour appeler des méthodes de la classe de base `MustOverride`.  
  
-   `MyBase` ne peut pas être utilisé pour se qualifier lui\-même.  Le code suivant est donc non valide :  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` ne peut pas être utilisé dans des modules.  
  
-   `MyBase` ne peut pas être utilisé pour accéder à des membres d'une classe de base marqués `Friend` si la classe de base se situe dans un assembly différent.  
  
 Pour plus d'informations et pour obtenir un autre exemple, consultez [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## MyClass, mot clé  
 Le mot clé `MyClass` se comporte comme une variable objet qui fait référence à l'instance actuelle d'une classe telle qu'elle a été implémentée initialement.  `MyClass` est semblable à `Me`, mais chaque appel de méthode et de propriété sur `MyClass` est traité comme si la méthode ou la propriété était [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).  Par conséquent, la méthode ou la propriété n'est pas affectée par la substitution dans une classe dérivée.  
  
-   `MyClass` est un mot clé, et non pas un objet réel.  `MyClass` ne peut pas être assigné à une variable, passé à des procédures, ni utilisé dans une comparaison `Is`.  
  
-   `MyClass` fait référence à la classe conteneur et à ses membres hérités.  
  
-   `MyClass` peut être utilisé en tant que qualificateur pour les membres `Shared`.  
  
-   Vous ne pouvez pas utiliser `MyClass` dans une méthode `Shared`, mais vous pouvez l'employer à l'intérieur d'une méthode d'instance pour accéder à un membre partagé d'une classe.  
  
-   `MyClass` ne peut pas être utilisé dans des modules standard.  
  
-   `MyClass` peut être utilisé pour désigner une méthode définie dans une classe de base et ne possède aucune implémentation de la méthode fournie dans cette classe.  La signification de cette référence est identique à la `MyBase.`*Méthode*.  
  
 L'exemple suivant compare `Me` et `MyClass`.  
  
```  
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 Même si `derivedClass` substitue `testMethod`, le mot clé `MyClass` de `useMyClass` annule les effets de la substitution, et le compilateur résout l'appel vers la version de la classe de base de `testMethod`.  
  
## Voir aussi  
 [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)