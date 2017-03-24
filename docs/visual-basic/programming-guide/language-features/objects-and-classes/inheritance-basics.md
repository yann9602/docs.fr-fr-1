---
title: "Principes fondamentaux de l’héritage (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 58aee9f8c348eb06daec2b8c9e332f3f2775bcb6
ms.lasthandoff: 03/13/2017

---
# <a name="inheritance-basics-visual-basic"></a>Éléments fondamentaux de l'héritage (Visual Basic)
Le `Inherits` instruction permet de déclarer une nouvelle classe, appelée une *classe dérivée*, basé sur une classe existante, appelée une *classe de base*. Les classes dérivées héritent et peuvent étendre, propriétés, méthodes, événements, champs et constantes définies dans la classe de base. La section suivante décrit certaines des règles pour l’héritage et les modificateurs que vous pouvez utiliser pour modifier les façon dont les classes héritent ou être héritées :  
  
-   Par défaut, toutes les classes peuvent être héritées, sauf si marqué avec la `NotInheritable` (mot clé). Les classes peuvent hériter d’autres classes dans votre projet ou de classes dans d’autres assemblys faisant référence à votre projet.  
  
-   Contrairement aux langages qui permettent l’héritage multiple, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permet l’héritage unique uniquement dans des classes ; autrement dit, les classes dérivées peuvent avoir qu’une seule classe de base. Bien que l’héritage multiple n’est pas autorisée dans les classes, les classes peuvent implémenter plusieurs interfaces, qui peuvent accomplir efficacement les mêmes objectifs.  
  
-   Pour empêcher l’exposition d’éléments restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base. Par exemple, un `Public` classe ne peut pas hériter une `Friend` ou un `Private` (classe) et un `Friend` classe ne peut pas hériter un `Private` classe.  
  
## <a name="inheritance-modifiers"></a>Modificateur d’héritage  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]présente les modificateurs pour prendre en charge l’héritage et les instructions de niveau classe suivantes :  
  
-   `Inherits`instruction : Spécifie la classe de base.  
  
-   `NotInheritable`modificateur : empêche les programmeurs d’utiliser la classe comme une classe de base.  
  
-   `MustInherit`modificateur — Spécifie que la classe est conçue pour une utilisation comme classe de base uniquement. Instances de `MustInherit` classes ne peuvent pas être créées directement ; ils ne peuvent être créées des instances de classe comme base d’une classe dérivée. (Autres langages de programmation, tels que C++ et c#, utilisent le terme *classe abstraite* pour décrire une telle classe.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Substitution de propriétés et méthodes des Classes dérivées  
 Par défaut, une classe dérivée hérite des propriétés et méthodes de sa classe de base. Si une propriété héritée ou une méthode doit se comporter différemment dans la classe dérivée peut être *substitué*. Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée. Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :  
  
-   `Overridable`: Permet à une propriété ou une méthode dans une classe soit substitué dans une classe dérivée.  
  
-   `Overrides`: Remplace une `Overridable` propriété ou méthode définie dans la classe de base.  
  
-   `NotOverridable`— Empêche une propriété ou méthode d’être substitué dans une classe qui hérite. Par défaut, `Public` méthodes sont `NotOverridable`.  
  
-   `MustOverride`— Requiert qu’une classe dérivée de substituer la propriété ou méthode. Lorsque le `MustOverride` mot clé est utilisé, la définition de méthode se compose uniquement le `Sub`, `Function`, ou `Property` instruction. Aucune autre instruction n’est autorisées et, en particulier sans `End Sub` ou `End Function` instruction. `MustOverride`les méthodes doivent être déclarées dans `MustInherit` classes.  
  
 Supposons que vous souhaitez définir des classes pour gérer les salaires. Vous pouvez définir un type générique `Payroll` classe contenant un `RunPayroll` méthode permettant de calculer les salaires pour une semaine type. Vous pouvez ensuite utiliser `Payroll` en tant que classe de base pour le plus spécialisé `BonusPayroll` classe, qui peut être utilisée lors de la distribution de primes aux employés.  
  
 Le `BonusPayroll` classe peut hériter et remplacer, le `PayEmployee` méthode définie dans la base de `Payroll` (classe).  
  
 L’exemple suivant définit une classe de base, `Payroll,` et une classe dérivée, `BonusPayroll`, ce qui substitue une méthode héritée, `PayEmployee`. Une procédure, `RunPayroll`, crée et passe ensuite un `Payroll` objet et un `BonusPayroll` objet à une fonction, `Pay`, qui exécute la `PayEmployee` méthode des deux objets.  
  
 [!code-vb[VbVbalrOOP&#28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>Le mot clé MyBase  
 Le `MyBase` (mot clé) se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe. `MyBase`est fréquemment utilisé pour accéder aux membres de classe de base qui sont substitués ou occultés dans une classe dérivée. En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.  
  
 Par exemple, supposons que vous créez une classe dérivée qui substitue une méthode héritée de la classe de base. La méthode substituée peut appeler la méthode dans la classe de base et modifiez la valeur de retour comme indiqué dans le fragment de code suivant :  
  
 [!code-vb[VbVbalrOOP&#109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 La liste suivante décrit les restrictions sur l’utilisation de `MyBase`:  
  
-   `MyBase`fait référence à la classe de base immédiate et à ses membres hérités. Il ne peut pas être utilisé pour accéder à `Private` membres dans la classe.  
  
-   `MyBase`est un mot clé, pas un objet réel. `MyBase`ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans un `Is` comparaison.  
  
-   La méthode qui `MyBase` qualifie ne devra pas être définies dans la classe de base immédiate ; il peut être défini à la place dans une classe de base héritée indirectement. Pour une référence qualifiée par `MyBase` pour compiler correctement, une classe de base doit contenir une méthode qui correspond au nom et aux types de paramètres qui apparaissent dans l’appel.  
  
-   Vous ne pouvez pas utiliser `MyBase` pour appeler `MustOverride` méthodes de la classe de base.  
  
-   `MyBase`ne peut pas être utilisé pour se qualifier lui-même. Par conséquent, le code suivant n’est pas valide :  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`ne peut pas être utilisé dans des modules.  
  
-   `MyBase`ne peut pas être utilisé pour accéder aux membres de classe de base qui sont marquées comme `Friend` si la classe de base se trouve dans un autre assembly.  
  
 Pour plus d’informations et un autre exemple, consultez [Comment : accéder à une Variable masquée par une classe dérivée de](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>Le mot clé MyClass  
 Le `MyClass` (mot clé) se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe implémentée comme à l’origine. `MyClass`semblable à `Me`, mais chaque méthode et propriété appeler sur `MyClass` est traitée comme si la méthode ou propriété ont été [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Par conséquent, la méthode ou propriété n’est pas affectée par la substitution dans une classe dérivée.  
  
-   `MyClass`est un mot clé, pas un objet réel. `MyClass`ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans un `Is` comparaison.  
  
-   `MyClass`fait référence à la classe conteneur et à ses membres hérités.  
  
-   `MyClass`peut être utilisé en tant que qualificateur pour `Shared` membres.  
  
-   `MyClass`ne peut pas être utilisé à l’intérieur d’un `Shared` (méthode), mais peut être utilisé à l’intérieur d’une méthode d’instance pour accéder à un membre partagé d’une classe.  
  
-   `MyClass`ne peut pas être utilisé dans des modules standard.  
  
-   `MyClass`peut être utilisé pour désigner une méthode définie dans une classe de base et ne possède aucune implémentation de la méthode fournie dans cette classe. Cette référence a la même signification que `MyBase.` *méthode*.  
  
 L’exemple suivant compare `Me` et `MyClass`.  
  
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
  
 Même si `derivedClass` substitue `testMethod`, le `MyClass` mot-clé dans `useMyClass` annule les effets de substitution et le compilateur résout l’appel vers la version de classe de base de `testMethod`.  
  
## <a name="see-also"></a>Voir aussi  
 [Inherits (instruction)](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
