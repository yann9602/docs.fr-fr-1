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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="b63ed-102">Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b63ed-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="b63ed-103">.NET framework 3.5 introduit la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués dans tous les délégués dans c# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b63ed-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="b63ed-104">Cela signifie que vous pouvez affecter aux délégués non seulement les méthodes qui ont à faire correspondre les signatures, mais également des méthodes qui retournent plus dérivés (covariance) de types ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué.</span><span class="sxs-lookup"><span data-stu-id="b63ed-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="b63ed-105">Cela inclut les délégués génériques et non génériques.</span><span class="sxs-lookup"><span data-stu-id="b63ed-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="b63ed-106">Par exemple, prenons le code suivant, qui a deux classes et deux délégués : générique et non générique.</span><span class="sxs-lookup"><span data-stu-id="b63ed-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="b63ed-107">Lorsque vous créez des délégués de la `SampleDelegate` ou `SampleDelegate(Of A, R)` types, vous pouvez affecter l’une des méthodes suivantes à ces délégués.</span><span class="sxs-lookup"><span data-stu-id="b63ed-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="b63ed-108">L’exemple de code suivant illustre la conversion implicite entre la signature de méthode et le type délégué.</span><span class="sxs-lookup"><span data-stu-id="b63ed-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="b63ed-109">Pour plus d’exemples, consultez [à l’aide de la Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) et [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b63ed-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="b63ed-110">Variance dans les paramètres de Type générique</span><span class="sxs-lookup"><span data-stu-id="b63ed-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="b63ed-111">Dans .NET Framework 4 et versions ultérieures, vous pouvez activer la conversion implicite entre les délégués, afin que les délégués génériques qui ont des types différents spécifiés par les paramètres de type générique peuvent être affectés à l’autre, si les types sont héritées de l’autre comme requis par la variance.</span><span class="sxs-lookup"><span data-stu-id="b63ed-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="b63ed-112">Pour activer la conversion implicite, vous devez déclarer explicitement les paramètres génériques d’un délégué comme covariant ou contravariant à l’aide de la `in` ou `out` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="b63ed-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="b63ed-113">L’exemple de code suivant montre comment vous pouvez créer un délégué ayant un paramètre de type générique covariant.</span><span class="sxs-lookup"><span data-stu-id="b63ed-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="b63ed-114">Si vous utilisez uniquement prise en charge de la variance pour faire correspondre les signatures de méthode avec des types délégués et n’utilisent pas le `in` et `out` mots clés, vous pouvez trouver que quelquefois vous pouvez instancier des délégués avec des expressions ou méthodes lambda identiques, mais vous ne pouvez pas assigner un délégué à un autre.</span><span class="sxs-lookup"><span data-stu-id="b63ed-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="b63ed-115">Dans l’exemple de code suivant, `SampleGenericDelegate(Of String)` ne peut pas être converti explicitement en `SampleGenericDelegate(Of Object)`, bien que `String` hérite `Object`.</span><span class="sxs-lookup"><span data-stu-id="b63ed-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="b63ed-116">Vous pouvez résoudre ce problème en marquant le paramètre générique `T` avec la `out` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="b63ed-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="b63ed-117">Paramètres de Type des délégués génériques qui ont de variante dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b63ed-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="b63ed-118">.NET framework 4 a introduit la prise en charge des paramètres de type générique dans plusieurs délégués génériques existants :</span><span class="sxs-lookup"><span data-stu-id="b63ed-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="b63ed-119">`Action`délégués de la <xref:System>espace de noms, par exemple, <xref:System.Action%601>et <xref:System.Action%602></xref:System.Action%602> </xref:System.Action%601> </xref:System></span><span class="sxs-lookup"><span data-stu-id="b63ed-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="b63ed-120">`Func`délégués de la <xref:System>espace de noms, par exemple, <xref:System.Func%601>et <xref:System.Func%602></xref:System.Func%602> </xref:System.Func%601> </xref:System></span><span class="sxs-lookup"><span data-stu-id="b63ed-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="b63ed-121">Le <xref:System.Predicate%601>délégué</xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="b63ed-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="b63ed-122">Le <xref:System.Comparison%601>délégué</xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="b63ed-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="b63ed-123">Le <xref:System.Converter%602>délégué</xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="b63ed-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="b63ed-124">Pour plus d’informations et d’exemples, consultez [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b63ed-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="b63ed-125">Déclarer des paramètres de Type Variant dans les délégués génériques</span><span class="sxs-lookup"><span data-stu-id="b63ed-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="b63ed-126">Si un délégué générique est covariant ou les paramètres de type générique contravariant, il peut être appelé une *des délégués génériques variants*.</span><span class="sxs-lookup"><span data-stu-id="b63ed-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="b63ed-127">Vous pouvez déclarer un paramètre de type générique covariant dans un délégué générique à l’aide de la `out` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="b63ed-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="b63ed-128">Le type covariant peut être utilisé uniquement comme type de retour de méthode et non comme un type d’arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="b63ed-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="b63ed-129">L’exemple de code suivant montre comment déclarer un délégué générique covariant.</span><span class="sxs-lookup"><span data-stu-id="b63ed-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
<span data-ttu-id="b63ed-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b63ed-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="b63ed-131">Vous pouvez déclarer un contravariant de paramètre de type générique dans un délégué générique à l’aide de la `in` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="b63ed-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="b63ed-132">Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme un type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="b63ed-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="b63ed-133">L’exemple de code suivant montre comment déclarer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="b63ed-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
<span data-ttu-id="b63ed-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b63ed-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
> <span data-ttu-id="b63ed-135"> `ByRef`paramètres en Visual Basic ne peut pas être marquées en tant que variant.</span><span class="sxs-lookup"><span data-stu-id="b63ed-135"> `ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="b63ed-136">Il est également possible de prendre en charge de variance et la covariance dans le même délégué, mais pour les paramètres de type différents.</span><span class="sxs-lookup"><span data-stu-id="b63ed-136">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="b63ed-137">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="b63ed-137">This is shown in the following example.</span></span>  
  
<span data-ttu-id="b63ed-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b63ed-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="b63ed-139">Instanciation et appel de délégués génériques variants</span><span class="sxs-lookup"><span data-stu-id="b63ed-139">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="b63ed-140">Vous pouvez instancier et appeler des délégués variants comme vous instanciez et appelez des délégués invariants.</span><span class="sxs-lookup"><span data-stu-id="b63ed-140">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="b63ed-141">Dans l’exemple suivant, le délégué est instancié par une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="b63ed-141">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
<span data-ttu-id="b63ed-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b63ed-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="b63ed-143">Combinaison de délégués génériques variants</span><span class="sxs-lookup"><span data-stu-id="b63ed-143">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="b63ed-144">Vous ne devez pas combiner les délégués variants.</span><span class="sxs-lookup"><span data-stu-id="b63ed-144">You should not combine variant delegates.</span></span> <span data-ttu-id="b63ed-145">Le <xref:System.Delegate.Combine%2A>méthode ne prend pas en charge la conversion des délégués variants et attend les délégués d’être exactement du même type.</xref:System.Delegate.Combine%2A></span><span class="sxs-lookup"><span data-stu-id="b63ed-145">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="b63ed-146">Cela peut entraîner une exception runtime lorsque vous combinez des délégués à l’aide du <xref:System.Delegate.Combine%2A>(méthode) (en c# et Visual Basic) ou à l’aide de la `+` (opérateur) (en c#), comme illustré dans l’exemple de code suivant.</xref:System.Delegate.Combine%2A></span><span class="sxs-lookup"><span data-stu-id="b63ed-146">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
<span data-ttu-id="b63ed-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b63ed-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="b63ed-148">Variance dans les paramètres de Type générique pour les Types valeur et référence</span><span class="sxs-lookup"><span data-stu-id="b63ed-148">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="b63ed-149">Variance pour les paramètres de type générique est pris en charge pour les types de référence.</span><span class="sxs-lookup"><span data-stu-id="b63ed-149">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="b63ed-150">Par exemple, `DVariant(Of Int)`ne peut pas être converti implicitement en `DVariant(Of Object)` ou `DVariant(Of Long)`, car entier est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="b63ed-150">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="b63ed-151">L’exemple suivant montre que la variance de type générique à laquelle les paramètres n'est pas pris en charge pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="b63ed-151">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="b63ed-152">Conversion simplifiée des délégués dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b63ed-152">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="b63ed-153">Conversion simplifiée des délégués permet davantage de flexibilité pour faire correspondre les signatures de méthode aux types délégués.</span><span class="sxs-lookup"><span data-stu-id="b63ed-153">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="b63ed-154">Par exemple, il vous permet d’omettre des spécifications de paramètres et omettre les valeurs de retour de fonction lorsque vous assignez une méthode à un délégué.</span><span class="sxs-lookup"><span data-stu-id="b63ed-154">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="b63ed-155">Pour plus d’informations, consultez [la Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="b63ed-155">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63ed-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b63ed-156">See Also</span></span>  
 <span data-ttu-id="b63ed-157">[Génériques](https://msdn.microsoft.com/library/ms172192) </span><span class="sxs-lookup"><span data-stu-id="b63ed-157">[Generics](https://msdn.microsoft.com/library/ms172192) </span></span>  
<span data-ttu-id="b63ed-158"> [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="b63ed-158"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
