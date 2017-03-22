---
title: "Variance dans les délégués (Visual Basic) | Documents Microsoft"
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
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a>Variance dans les délégués (Visual Basic)
.NET framework 3.5 introduit la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués dans tous les délégués dans c# et Visual Basic. Cela signifie que vous pouvez affecter aux délégués non seulement les méthodes qui ont à faire correspondre les signatures, mais également des méthodes qui retournent plus dérivés (covariance) de types ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Cela inclut les délégués génériques et non génériques.  
  
 Par exemple, prenons le code suivant, qui a deux classes et deux délégués : générique et non générique.  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 Lorsque vous créez des délégués de la `SampleDelegate` ou `SampleDelegate(Of A, R)` types, vous pouvez affecter l’une des méthodes suivantes à ces délégués.  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 L’exemple de code suivant illustre la conversion implicite entre la signature de méthode et le type délégué.  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 Pour plus d’exemples, consultez [à l’aide de la Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) et [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Variance dans les paramètres de Type générique  
 Dans .NET Framework 4 et versions ultérieures, vous pouvez activer la conversion implicite entre les délégués, afin que les délégués génériques qui ont des types différents spécifiés par les paramètres de type générique peuvent être affectés à l’autre, si les types sont héritées de l’autre comme requis par la variance.  
  
 Pour activer la conversion implicite, vous devez déclarer explicitement les paramètres génériques d’un délégué comme covariant ou contravariant à l’aide de la `in` ou `out` (mot clé).  
  
 L’exemple de code suivant montre comment vous pouvez créer un délégué ayant un paramètre de type générique covariant.  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 Si vous utilisez uniquement prise en charge de la variance pour faire correspondre les signatures de méthode avec des types délégués et n’utilisent pas le `in` et `out` mots clés, vous pouvez trouver que quelquefois vous pouvez instancier des délégués avec des expressions ou méthodes lambda identiques, mais vous ne pouvez pas assigner un délégué à un autre.  
  
 Dans l’exemple de code suivant, `SampleGenericDelegate(Of String)` ne peut pas être converti explicitement en `SampleGenericDelegate(Of Object)`, bien que `String` hérite `Object`. Vous pouvez résoudre ce problème en marquant le paramètre générique `T` avec la `out` (mot clé).  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Paramètres de Type des délégués génériques qui ont de variante dans le .NET Framework  
 .NET framework 4 a introduit la prise en charge des paramètres de type générique dans plusieurs délégués génériques existants :  
  
-   `Action`délégués de la <xref:System>espace de noms, par exemple, <xref:System.Action%601>et <xref:System.Action%602></xref:System.Action%602> </xref:System.Action%601> </xref:System>  
  
-   `Func`délégués de la <xref:System>espace de noms, par exemple, <xref:System.Func%601>et <xref:System.Func%602></xref:System.Func%602> </xref:System.Func%601> </xref:System>  
  
-   Le <xref:System.Predicate%601>délégué</xref:System.Predicate%601>  
  
-   Le <xref:System.Comparison%601>délégué</xref:System.Comparison%601>  
  
-   Le <xref:System.Converter%602>délégué</xref:System.Converter%602>  
  
 Pour plus d’informations et d’exemples, consultez [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Déclarer des paramètres de Type Variant dans les délégués génériques  
 Si un délégué générique est covariant ou les paramètres de type générique contravariant, il peut être appelé une *des délégués génériques variants*.  
  
 Vous pouvez déclarer un paramètre de type générique covariant dans un délégué générique à l’aide de la `out` (mot clé). Le type covariant peut être utilisé uniquement comme type de retour de méthode et non comme un type d’arguments de méthode. L’exemple de code suivant montre comment déclarer un délégué générique covariant.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Vous pouvez déclarer un contravariant de paramètre de type générique dans un délégué générique à l’aide de la `in` (mot clé). Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme un type de retour de méthode. L’exemple de code suivant montre comment déclarer un délégué générique contravariant.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  `ByRef`paramètres en Visual Basic ne peut pas être marquées en tant que variant.  
  
 Il est également possible de prendre en charge de variance et la covariance dans le même délégué, mais pour les paramètres de type différents. L'exemple suivant le démontre.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Instanciation et appel de délégués génériques variants  
 Vous pouvez instancier et appeler des délégués variants comme vous instanciez et appelez des délégués invariants. Dans l’exemple suivant, le délégué est instancié par une expression lambda.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
### <a name="combining-variant-generic-delegates"></a>Combinaison de délégués génériques variants  
 Vous ne devez pas combiner les délégués variants. Le <xref:System.Delegate.Combine%2A>méthode ne prend pas en charge la conversion des délégués variants et attend les délégués d’être exactement du même type.</xref:System.Delegate.Combine%2A> Cela peut entraîner une exception runtime lorsque vous combinez des délégués à l’aide du <xref:System.Delegate.Combine%2A>(méthode) (en c# et Visual Basic) ou à l’aide de la `+` (opérateur) (en c#), comme illustré dans l’exemple de code suivant.</xref:System.Delegate.Combine%2A>  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance dans les paramètres de Type générique pour les Types valeur et référence  
 Variance pour les paramètres de type générique est pris en charge pour les types de référence. Par exemple, `DVariant(Of Int)`ne peut pas être converti implicitement en `DVariant(Of Object)` ou `DVariant(Of Long)`, car entier est un type valeur.  
  
 L’exemple suivant montre que la variance de type générique à laquelle les paramètres n'est pas pris en charge pour les types valeur.  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Conversion simplifiée des délégués dans Visual Basic  
 Conversion simplifiée des délégués permet davantage de flexibilité pour faire correspondre les signatures de méthode aux types délégués. Par exemple, il vous permet d’omettre des spécifications de paramètres et omettre les valeurs de retour de fonction lorsque vous assignez une méthode à un délégué. Pour plus d’informations, consultez [la Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](https://msdn.microsoft.com/library/ms172192)   
 [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
