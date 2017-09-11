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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a2cbf0a204a5a3af45f55a14c011518c7021f5b4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="40359-102">Création d’Interfaces génériques de type Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40359-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="40359-103">Vous pouvez déclarer des paramètres de type générique dans les interfaces comme covariant ou contravariant.</span><span class="sxs-lookup"><span data-stu-id="40359-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="40359-104">*Covariance* permet aux méthodes d’interface pour les types de retour plus dérivés que ceux définis par les paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="40359-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="40359-105">*La contravariance* permet aux méthodes d’interface d’avoir des types d’argument moins dérivés que ceux spécifiés par les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="40359-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="40359-106">Une d’interface générique qui est covariant ou contravariant paramètres de type générique est appelé *variante*.</span><span class="sxs-lookup"><span data-stu-id="40359-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40359-107">.NET framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes.</span><span class="sxs-lookup"><span data-stu-id="40359-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="40359-108">Pour la liste des variantes dans le .NET Framework, consultez [Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="40359-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="40359-109">Déclaration d’Interfaces génériques variantes</span><span class="sxs-lookup"><span data-stu-id="40359-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="40359-110">Vous pouvez déclarer des interfaces génériques de type variant à l’aide de la `in` et `out` mots clés pour les paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="40359-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40359-111"> `ByRef`paramètres Visual Basic ne peut pas être de type variant.</span><span class="sxs-lookup"><span data-stu-id="40359-111"> `ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="40359-112">Types valeur ne prennent pas en charge variance.</span><span class="sxs-lookup"><span data-stu-id="40359-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="40359-113">Vous pouvez déclarer un paramètre de type générique covariant à l’aide de la `out` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="40359-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="40359-114">Le type covariant doit satisfaire les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="40359-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="40359-115">Le type est utilisé uniquement comme type de retour de méthodes d’interface et non utilisé comme type d’arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="40359-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="40359-116">Ceci est illustré dans l’exemple suivant, dans lequel le type `R` est déclaré covariant.</span><span class="sxs-lookup"><span data-stu-id="40359-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     <span data-ttu-id="40359-117">Il existe une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="40359-117">There is one exception to this rule.</span></span> <span data-ttu-id="40359-118">Si vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type comme un paramètre de type générique pour le délégué.</span><span class="sxs-lookup"><span data-stu-id="40359-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="40359-119">Ceci est illustré par le type de `R` dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="40359-120">Pour plus d’informations, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [à l’aide de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="40359-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   <span data-ttu-id="40359-121">Le type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="40359-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="40359-122">Ceci est illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-122">This is illustrated in the following code.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 <span data-ttu-id="40359-123">Vous pouvez déclarer un contravariant de paramètre de type générique à l’aide de la `in` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="40359-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="40359-124">Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme un type de retour de méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="40359-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="40359-125">Le type contravariant peut également être utilisé pour les contraintes génériques.</span><span class="sxs-lookup"><span data-stu-id="40359-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="40359-126">Le code suivant montre comment déclarer une interface contravariante et utiliser une contrainte générique pour une de ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="40359-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 <span data-ttu-id="40359-127">Il est également possible de prendre en charge la covariance et contravariance dans la même interface, mais pour les paramètres de type différent, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 <span data-ttu-id="40359-128">Dans Visual Basic, vous ne pouvez pas déclarer événements dans des interfaces variantes sans spécifier le type délégué.</span><span class="sxs-lookup"><span data-stu-id="40359-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="40359-129">En outre, une interface variant ne peut pas avoir imbriqués classes, d’enums ou de structures, mais il peut inclure des interfaces imbriquées.</span><span class="sxs-lookup"><span data-stu-id="40359-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="40359-130">Ceci est illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-130">This is illustrated in the following code.</span></span>  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="40359-131">Implémentation d’Interfaces génériques de type Variant</span><span class="sxs-lookup"><span data-stu-id="40359-131">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="40359-132">Vous implémentez des interfaces génériques de type variant dans les classes en utilisant la même syntaxe qui est utilisée pour les interfaces invariantes.</span><span class="sxs-lookup"><span data-stu-id="40359-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="40359-133">L’exemple de code suivant montre comment implémenter une interface covariante dans une classe générique.</span><span class="sxs-lookup"><span data-stu-id="40359-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
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
  
 <span data-ttu-id="40359-134">Les classes qui implémentent des interfaces variantes sont invariantes.</span><span class="sxs-lookup"><span data-stu-id="40359-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="40359-135">Par exemple, prenons le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-135">For example, consider the following code.</span></span>  
  
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
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="40359-136">Extension d’Interfaces génériques variantes</span><span class="sxs-lookup"><span data-stu-id="40359-136">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="40359-137">Lorsque vous étendez une interface générique variante, vous devez utiliser le `in` et `out` mots clés pour spécifier explicitement si l’interface dérivée prend en charge la variance.</span><span class="sxs-lookup"><span data-stu-id="40359-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="40359-138">Le compilateur ne reconnaît pas la variance de l’interface qui est étendu.</span><span class="sxs-lookup"><span data-stu-id="40359-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="40359-139">Par exemple, considérez les interfaces suivantes.</span><span class="sxs-lookup"><span data-stu-id="40359-139">For example, consider the following interfaces.</span></span>  
  
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
  
 <span data-ttu-id="40359-140">Dans le `Invariant(Of T)` de l’interface, le paramètre de type générique `T` est invariant, alors que dans `IExtCovariant (Of Out T)`le paramètre de type est covariant, bien que les deux interfaces étendent la même interface.</span><span class="sxs-lookup"><span data-stu-id="40359-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="40359-141">La même règle est appliquée aux paramètres de type générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="40359-141">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="40359-142">Vous pouvez créer une interface qui étend l’interface générique dans lequel le paramètre type `T` est covariant et le paramètre de type générique de l’interface où elle est contravariant si dans l’extension de l’interface `T` est indifférent.</span><span class="sxs-lookup"><span data-stu-id="40359-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="40359-143">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-143">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="40359-144">Toutefois, si un paramètre de type générique `T` est déclaré covariant dans une interface, vous ne pouvez pas déclarer contravariant dans l’interface étendue, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="40359-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="40359-145">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-145">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="40359-146">Éviter l’ambiguïté</span><span class="sxs-lookup"><span data-stu-id="40359-146">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="40359-147">Lorsque vous implémentez des interfaces génériques variantes, la variance peut parfois entraîner d’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="40359-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="40359-148">Cela doit être évité.</span><span class="sxs-lookup"><span data-stu-id="40359-148">This should be avoided.</span></span>  
  
 <span data-ttu-id="40359-149">Par exemple, si vous implémentez explicitement la même interface générique variante avec les paramètres de type générique différents dans une classe, il peut créer une ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="40359-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="40359-150">Le compilateur ne produit pas d’erreur dans ce cas, mais il n’est pas spécifié de l’implémentation d’interface sera choisie lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="40359-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="40359-151">Cela pourrait entraîner des bogues subtils dans votre code.</span><span class="sxs-lookup"><span data-stu-id="40359-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="40359-152">Prenons l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="40359-152">Consider the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40359-153">Avec `Option Strict Off`, Visual Basic génère un avertissement du compilateur lorsqu’il y a une implémentation d’interface ambiguë.</span><span class="sxs-lookup"><span data-stu-id="40359-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="40359-154">Avec `Option Strict On`, Visual Basic génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="40359-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="40359-155">Dans cet exemple, il n’est pas spécifié comment la `pets.GetEnumerator` méthode choisit entre `Cat` et `Dog`.</span><span class="sxs-lookup"><span data-stu-id="40359-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="40359-156">Cela peut entraîner des problèmes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="40359-156">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40359-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40359-157">See Also</span></span>  
 <span data-ttu-id="40359-158">[Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="40359-158">[Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span></span>  
<span data-ttu-id="40359-159"> [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="40359-159"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
