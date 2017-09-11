---
title: "Variance dans les Interfaces génériques (Visual Basic) | Documents Microsoft"
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
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
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
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="79cf5-102">Variance dans les Interfaces génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79cf5-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="79cf5-103">.NET framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes.</span><span class="sxs-lookup"><span data-stu-id="79cf5-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="79cf5-104">Prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="79cf5-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="79cf5-105">Les interfaces suivantes sont maintenant variantes :</span><span class="sxs-lookup"><span data-stu-id="79cf5-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="79cf5-106"><xref:System.Collections.Generic.IEnumerable%601>(T est covariant)</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="79cf5-107"><xref:System.Collections.Generic.IEnumerator%601>(T est covariant)</xref:System.Collections.Generic.IEnumerator%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="79cf5-108"><xref:System.Linq.IQueryable%601>(T est covariant)</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="79cf5-109"><xref:System.Linq.IGrouping%602>(`TKey` et `TElement` sont covariants)</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="79cf5-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="79cf5-110"><xref:System.Collections.Generic.IComparer%601>(T est contravariant)</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="79cf5-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T est contravariant)</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="79cf5-112"><xref:System.IComparable%601>(T est contravariant)</xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="79cf5-113">La covariance autorise une méthode à avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="79cf5-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="79cf5-114">Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable(Of Object)` et `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="79cf5-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="79cf5-115">Le `IEnumerable(Of String)` interface n’hérite pas du `IEnumerable(Of Object)` interface.</span><span class="sxs-lookup"><span data-stu-id="79cf5-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="79cf5-116">Toutefois, le `String` type hérite le `Object` type et dans certains cas, vous souhaiterez assigner des objets de ces interfaces entre eux.</span><span class="sxs-lookup"><span data-stu-id="79cf5-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="79cf5-117">Cela est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="79cf5-117">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="79cf5-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="79cf5-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="79cf5-119">Dans les versions antérieures du .NET Framework, ce code provoque une erreur de compilation dans Visual Basic avec `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="79cf5-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="79cf5-120">Mais vous pouvez désormais utiliser `strings` au lieu de `objects`, comme illustré dans l’exemple précédent, étant donné que le <xref:System.Collections.Generic.IEnumerable%601>interface est covariante.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="79cf5-121">La contravariance permet à une méthode d’avoir des types d’arguments qui sont moins dérivés que celui spécifié par le paramètre générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="79cf5-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="79cf5-122">Pour illustrer la contravariance, supposez que vous avez créé un `BaseComparer` pour comparer des instances de classe la `BaseClass` classe.</span><span class="sxs-lookup"><span data-stu-id="79cf5-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="79cf5-123">La classe `BaseComparer` implémente l'interface `IEqualityComparer(Of BaseClass)`.</span><span class="sxs-lookup"><span data-stu-id="79cf5-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="79cf5-124">Étant donné que le <xref:System.Collections.Generic.IEqualityComparer%601>interface est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances de classes qui héritent de la `BaseClass` classe</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="79cf5-125">Cela est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="79cf5-125">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="79cf5-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="79cf5-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="79cf5-127">Pour plus d’exemples, consultez [à l’aide de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="79cf5-127">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="79cf5-128">Variance dans les interfaces génériques est prise en charge pour les types de référence.</span><span class="sxs-lookup"><span data-stu-id="79cf5-128">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="79cf5-129">Les types valeur ne gèrent pas la variance.</span><span class="sxs-lookup"><span data-stu-id="79cf5-129">Value types do not support variance.</span></span> <span data-ttu-id="79cf5-130">Par exemple, `IEnumerable(Of Integer)` ne peut pas être converti implicitement en `IEnumerable(Of Object)`, car les entiers sont représentés par un type valeur.</span><span class="sxs-lookup"><span data-stu-id="79cf5-130">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
<span data-ttu-id="79cf5-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="79cf5-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="79cf5-132">Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes.</span><span class="sxs-lookup"><span data-stu-id="79cf5-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="79cf5-133">Par exemple, bien que <xref:System.Collections.Generic.List%601>implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List(Of Object)` à `List(Of String)`.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="79cf5-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="79cf5-134">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="79cf5-134">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="79cf5-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79cf5-135">See Also</span></span>  
 <span data-ttu-id="79cf5-136">[Utilisation de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="79cf5-136">[Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span></span>  
<span data-ttu-id="79cf5-137"> [Création d’Interfaces génériques de type Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="79cf5-137"> [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span></span>  
<span data-ttu-id="79cf5-138"> [Interfaces génériques](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span><span class="sxs-lookup"><span data-stu-id="79cf5-138"> [Generic Interfaces](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span></span>  
<span data-ttu-id="79cf5-139"> [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="79cf5-139"> [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span></span>
