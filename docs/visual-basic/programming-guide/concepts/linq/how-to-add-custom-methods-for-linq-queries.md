---
title: "Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic) | Documents Microsoft"
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
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
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
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)
Vous pouvez étendre le jeu de méthodes que vous pouvez utiliser pour les requêtes LINQ en ajoutant des méthodes d’extension pour le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> Par exemple, en plus de la moyenne standard ou le nombre maximal d’opérations, vous pouvez créer une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs. Vous pouvez également créer une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données spécifique pour une séquence de valeurs et retourne une nouvelle séquence. Exemples de ces méthodes sont <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>et <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A>  
  
 Lorsque vous étendez le <xref:System.Collections.Generic.IEnumerable%601>interface, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable.</xref:System.Collections.Generic.IEnumerable%601> Pour plus d’informations, consultez [les méthodes d’Extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Ajout d’une méthode d’agrégation  
 Une méthode d’agrégation calcule une valeur unique à partir d’un ensemble de valeurs. LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>et <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A> Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension pour le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
 L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 Vous appelez cette méthode d’extension pour toute collection énumérable de la même façon que vous appelez d’autres méthodes d’agrégation à partir de la <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
> [!NOTE]
>  Dans Visual Basic, vous pouvez utiliser un appel de méthode ou une syntaxe de requête standard pour la `Aggregate` ou `Group By` clause. Pour plus d’informations, consultez [Clause Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 L’exemple de code suivant montre comment utiliser le `Median` méthode pour un tableau de type `double`.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>La surcharge d’une méthode d’agrégation pour accepter différents Types  
 Vous pouvez surcharger votre méthode d’agrégation afin qu’elle accepte des séquences de différents types. L’approche standard consiste à créer une surcharge pour chaque type. Une autre approche consiste à créer une surcharge qui prend un type générique et convertissez-le en un type spécifique à l’aide d’un délégué. Vous pouvez également combiner ces deux approches.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Pour créer une surcharge pour chaque type.  
 Vous pouvez créer une surcharge spécifique pour chaque type que vous souhaitez prendre en charge. L’exemple de code suivant montre une surcharge de la `Median` méthode pour le `integer` type.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Vous pouvez maintenant appeler le `Median` surcharges pour les deux `integer` et `double` types, comme indiqué dans le code suivant :  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>Pour créer une surcharge générique  
 Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques. Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets d’un type générique en un type spécifique.  
  
 Le code suivant montre une surcharge de la `Median` méthode qui prend le <xref:System.Func%602>délégué en tant que paramètre.</xref:System.Func%602> Ce délégué prend un objet de type générique T et retourne un objet de type `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Vous pouvez maintenant appeler le `Median` méthode pour une séquence d’objets de tout type. Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre délégué. Dans Visual Basic, vous pouvez utiliser une expression lambda à cet effet. En outre, si vous utilisez la `Aggregate` ou `Group By` clause au lieu de l’appel de méthode, vous pouvez passer toute valeur ou expression qui est dans la portée de cette clause.  
  
 L’exemple de code suivant montre comment appeler le `Median` méthode pour un tableau d’entiers et un tableau de chaînes. Pour les chaînes, la valeur médiane pour les longueurs de chaînes dans le tableau est calculée. L’exemple montre comment passer le <xref:System.Func%602>déléguer le paramètre à la `Median` méthode pour chaque cas.</xref:System.Func%602>  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>Ajout d’une méthode qui retourne une Collection  
 Vous pouvez étendre le <xref:System.Collections.Generic.IEnumerable%601>interface avec une méthode de requête personnalisée qui retourne une séquence de valeurs.</xref:System.Collections.Generic.IEnumerable%601> Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Ces méthodes peuvent être utilisés pour appliquer des transformations de données ou de filtres à une séquence de valeurs.  
  
 L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne chaque autre élément dans une collection, en commençant par le premier élément.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Vous pouvez appeler cette méthode d’extension pour toute collection énumérable comme vous appelleriez d’autres méthodes de la <xref:System.Collections.Generic.IEnumerable%601>de l’interface, comme indiqué dans le code suivant :</xref:System.Collections.Generic.IEnumerable%601>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [Méthodes d’extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
