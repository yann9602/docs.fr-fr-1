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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Variance dans les Interfaces génériques (Visual Basic)
.NET framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. Prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces. Les interfaces suivantes sont maintenant variantes :  
  
-   <xref:System.Collections.Generic.IEnumerable%601>(T est covariant)</xref:System.Collections.Generic.IEnumerable%601>  
  
-   <xref:System.Collections.Generic.IEnumerator%601>(T est covariant)</xref:System.Collections.Generic.IEnumerator%601>  
  
-   <xref:System.Linq.IQueryable%601>(T est covariant)</xref:System.Linq.IQueryable%601>  
  
-   <xref:System.Linq.IGrouping%602>(`TKey` et `TElement` sont covariants)</xref:System.Linq.IGrouping%602>  
  
-   <xref:System.Collections.Generic.IComparer%601>(T est contravariant)</xref:System.Collections.Generic.IComparer%601>  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>(T est contravariant)</xref:System.Collections.Generic.IEqualityComparer%601>  
  
-   <xref:System.IComparable%601>(T est contravariant)</xref:System.IComparable%601>  
  
 La covariance autorise une méthode à avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface. Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable(Of Object)` et `IEnumerable(Of String)`. Le `IEnumerable(Of String)` interface n’hérite pas du `IEnumerable(Of Object)` interface. Toutefois, le `String` type hérite le `Object` type et dans certains cas, vous souhaiterez assigner des objets de ces interfaces entre eux. Cela est illustré dans l’exemple de code suivant.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Dans les versions antérieures du .NET Framework, ce code provoque une erreur de compilation dans Visual Basic avec `Option Strict On`. Mais vous pouvez désormais utiliser `strings` au lieu de `objects`, comme illustré dans l’exemple précédent, étant donné que le <xref:System.Collections.Generic.IEnumerable%601>interface est covariante.</xref:System.Collections.Generic.IEnumerable%601>  
  
 La contravariance permet à une méthode d’avoir des types d’arguments qui sont moins dérivés que celui spécifié par le paramètre générique de l’interface. Pour illustrer la contravariance, supposez que vous avez créé un `BaseComparer` pour comparer des instances de classe la `BaseClass` classe. La classe `BaseComparer` implémente l'interface `IEqualityComparer(Of BaseClass)`. Étant donné que le <xref:System.Collections.Generic.IEqualityComparer%601>interface est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances de classes qui héritent de la `BaseClass` classe</xref:System.Collections.Generic.IEqualityComparer%601> Cela est illustré dans l’exemple de code suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Pour plus d’exemples, consultez [à l’aide de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Variance dans les interfaces génériques est prise en charge pour les types de référence. Les types valeur ne gèrent pas la variance. Par exemple, `IEnumerable(Of Integer)` ne peut pas être converti implicitement en `IEnumerable(Of Object)`, car les entiers sont représentés par un type valeur.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes. Par exemple, bien que <xref:System.Collections.Generic.List%601>implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List(Of Object)` à `List(Of String)`.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.List%601> Ceci est illustré dans l’exemple de code suivant.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [Création d’Interfaces génériques de type Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [Interfaces génériques](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
