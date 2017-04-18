---
title: "Création d’Interfaces génériques de type Variant (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 324e2a906e84950aa9019bbf68a524458492646e
ms.lasthandoff: 03/13/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Création d’Interfaces génériques de type Variant (Visual Basic)
Vous pouvez déclarer des paramètres de type générique dans les interfaces comme covariant ou contravariant. *Covariance* permet aux méthodes d’interface pour les types de retour plus dérivés que ceux définis par les paramètres de type générique. *La contravariance* permet aux méthodes d’interface d’avoir des types d’argument moins dérivés que ceux spécifiés par les paramètres génériques. Une d’interface générique qui est covariant ou contravariant paramètres de type générique est appelé *variante*.  
  
> [!NOTE]
>  .NET framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. Pour la liste des variantes dans le .NET Framework, consultez [Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Déclaration d’Interfaces génériques variantes  
 Vous pouvez déclarer des interfaces génériques de type variant à l’aide de la `in` et `out` mots clés pour les paramètres de type générique.  
  
> [!IMPORTANT]
>  `ByRef`paramètres Visual Basic ne peut pas être de type variant. Types valeur ne prennent pas en charge variance.  
  
 Vous pouvez déclarer un paramètre de type générique covariant à l’aide de la `out` (mot clé). Le type covariant doit satisfaire les conditions suivantes :  
  
-   Le type est utilisé uniquement comme type de retour de méthodes d’interface et non utilisé comme type d’arguments de méthode. Ceci est illustré dans l’exemple suivant, dans lequel le type `R` est déclaré covariant.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Il existe une exception à cette règle. Si vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type comme un paramètre de type générique pour le délégué. Ceci est illustré par le type de `R` dans l’exemple suivant. Pour plus d’informations, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Le type n’est pas utilisé comme contrainte générique pour les méthodes d’interface. Ceci est illustré dans le code suivant.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Vous pouvez déclarer un contravariant de paramètre de type générique à l’aide de la `in` (mot clé). Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme un type de retour de méthodes d’interface. Le type contravariant peut également être utilisé pour les contraintes génériques. Le code suivant montre comment déclarer une interface contravariante et utiliser une contrainte générique pour une de ses méthodes.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Il est également possible de prendre en charge la covariance et contravariance dans la même interface, mais pour les paramètres de type différent, comme indiqué dans l’exemple de code suivant.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 Dans Visual Basic, vous ne pouvez pas déclarer événements dans des interfaces variantes sans spécifier le type délégué. En outre, une interface variant ne peut pas avoir imbriqués classes, d’enums ou de structures, mais il peut inclure des interfaces imbriquées. Ceci est illustré dans le code suivant.  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implémentation d’Interfaces génériques de type Variant  
 Vous implémentez des interfaces génériques de type variant dans les classes en utilisant la même syntaxe qui est utilisée pour les interfaces invariantes. L’exemple de code suivant montre comment implémenter une interface covariante dans une classe générique.  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 Les classes qui implémentent des interfaces variantes sont invariantes. Par exemple, prenons le code suivant.  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Extension d’Interfaces génériques variantes  
 Lorsque vous étendez une interface générique variante, vous devez utiliser le `in` et `out` mots clés pour spécifier explicitement si l’interface dérivée prend en charge la variance. Le compilateur ne reconnaît pas la variance de l’interface qui est étendu. Par exemple, considérez les interfaces suivantes.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 Dans le `Invariant(Of T)` de l’interface, le paramètre de type générique `T` est invariant, alors que dans `IExtCovariant (Of Out T)`le paramètre de type est covariant, bien que les deux interfaces étendent la même interface. La même règle est appliquée aux paramètres de type générique contravariant.  
  
 Vous pouvez créer une interface qui étend l’interface générique dans lequel le paramètre type `T` est covariant et le paramètre de type générique de l’interface où elle est contravariant si dans l’extension de l’interface `T` est indifférent. Ceci est illustré dans l’exemple de code suivant.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Toutefois, si un paramètre de type générique `T` est déclaré covariant dans une interface, vous ne pouvez pas déclarer contravariant dans l’interface étendue, ou vice versa. Ceci est illustré dans l’exemple de code suivant.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Éviter l’ambiguïté  
 Lorsque vous implémentez des interfaces génériques variantes, la variance peut parfois entraîner d’ambiguïté. Cela doit être évité.  
  
 Par exemple, si vous implémentez explicitement la même interface générique variante avec les paramètres de type générique différents dans une classe, il peut créer une ambiguïté. Le compilateur ne produit pas d’erreur dans ce cas, mais il n’est pas spécifié de l’implémentation d’interface sera choisie lors de l’exécution. Cela pourrait entraîner des bogues subtils dans votre code. Prenons l’exemple de code suivant.  
  
> [!NOTE]
>  Avec `Option Strict Off`, Visual Basic génère un avertissement du compilateur lorsqu’il y a une implémentation d’interface ambiguë. Avec `Option Strict On`, Visual Basic génère une erreur du compilateur.  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 Dans cet exemple, il n’est pas spécifié comment la `pets.GetEnumerator` méthode choisit entre `Cat` et `Dog`. Cela peut entraîner des problèmes dans votre code.  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
