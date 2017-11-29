---
title: "Variance dans les interfaces génériques (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="4e8aa-102">Variance dans les interfaces génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="4e8aa-103">.NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="4e8aa-104">La prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="4e8aa-105">Les interfaces suivantes sont maintenant variantes :</span><span class="sxs-lookup"><span data-stu-id="4e8aa-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="4e8aa-106"><xref:System.Collections.Generic.IEnumerable%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-107"><xref:System.Collections.Generic.IEnumerator%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-108"><xref:System.Linq.IQueryable%601> (T est covariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-109"><xref:System.Linq.IGrouping%602> (`TKey` et `TElement` sont covariants)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-110"><xref:System.Collections.Generic.IComparer%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="4e8aa-112"><xref:System.IComparable%601> (T est contravariant)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="4e8aa-113">La covariance permet à une méthode d’avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="4e8aa-114">Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable<Object>` et `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="4e8aa-115">L’interface `IEnumerable<String>` n’hérite pas de l’interface `IEnumerable<Object>`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="4e8aa-116">Toutefois, le type `String` hérite du type `Object` et, dans certains cas, vous pouvez assigner des objets de ces interfaces de l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="4e8aa-117">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="4e8aa-118">Dans les versions antérieures du .NET Framework, ce code provoque une erreur de compilation en C# avec `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="4e8aa-119">Cependant, vous pouvez désormais utiliser `strings` au lieu d’`objects`, comme illustré dans l’exemple précédent, parce que l’interface <xref:System.Collections.Generic.IEnumerable%601> est covariante.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="4e8aa-120">La contravariance permet à une méthode d’avoir des types d’argument moins dérivés que ceux spécifiés par le paramètre générique de l’interface.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="4e8aa-121">Pour illustrer la contravariance, supposez que vous avez créé une classe `BaseComparer` pour comparer des instances de la classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="4e8aa-122">La classe `BaseComparer` implémente l'interface `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="4e8aa-123">Étant donné que l’interface <xref:System.Collections.Generic.IEqualityComparer%601> est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances des classes qui héritent de la classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="4e8aa-124">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-124">This is shown in the following code example.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 <span data-ttu-id="4e8aa-125">Pour obtenir d’autres exemples, consultez [Utilisation de la variance dans les interfaces pour les collections génériques (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="4e8aa-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="4e8aa-126">La variance dans les interfaces génériques est prise en charge uniquement pour les types référence.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="4e8aa-127">Les types valeur ne prennent pas en charge la variance.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-127">Value types do not support variance.</span></span> <span data-ttu-id="4e8aa-128">Par exemple, `IEnumerable<int>` ne peut pas être converti implicitement en `IEnumerable<object>`, car les entiers sont représentés par un type valeur.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="4e8aa-129">Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="4e8aa-130">Par exemple, même si <xref:System.Collections.Generic.List%601> implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List<Object>` en `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="4e8aa-131">En voici une illustration dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4e8aa-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e8aa-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e8aa-132">See Also</span></span>  
 [<span data-ttu-id="4e8aa-133">Utilisation de la variance dans les interfaces pour les collections génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="4e8aa-134">Création d’interfaces génériques de type variant (C#)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="4e8aa-135">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="4e8aa-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="4e8aa-136">Variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="4e8aa-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
