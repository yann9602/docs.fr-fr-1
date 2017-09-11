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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="6ca92-102">Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca92-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="6ca92-103">Vous pouvez étendre le jeu de méthodes que vous pouvez utiliser pour les requêtes LINQ en ajoutant des méthodes d’extension pour le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="6ca92-104">Par exemple, en plus de la moyenne standard ou le nombre maximal d’opérations, vous pouvez créer une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ca92-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="6ca92-105">Vous pouvez également créer une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données spécifique pour une séquence de valeurs et retourne une nouvelle séquence.</span><span class="sxs-lookup"><span data-stu-id="6ca92-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="6ca92-106">Exemples de ces méthodes sont <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>et <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A></span><span class="sxs-lookup"><span data-stu-id="6ca92-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="6ca92-107">Lorsque vous étendez le <xref:System.Collections.Generic.IEnumerable%601>interface, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="6ca92-108">Pour plus d’informations, consultez [les méthodes d’Extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="6ca92-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="6ca92-109">Ajout d’une méthode d’agrégation</span><span class="sxs-lookup"><span data-stu-id="6ca92-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="6ca92-110">Une méthode d’agrégation calcule une valeur unique à partir d’un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ca92-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="6ca92-111">LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>et <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="6ca92-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="6ca92-112">Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension pour le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="6ca92-113">L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.</span><span class="sxs-lookup"><span data-stu-id="6ca92-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="6ca92-114">Vous appelez cette méthode d’extension pour toute collection énumérable de la même façon que vous appelez d’autres méthodes d’agrégation à partir de la <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ca92-115">Dans Visual Basic, vous pouvez utiliser un appel de méthode ou une syntaxe de requête standard pour la `Aggregate` ou `Group By` clause.</span><span class="sxs-lookup"><span data-stu-id="6ca92-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="6ca92-116">Pour plus d’informations, consultez [Clause Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6ca92-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="6ca92-117">L’exemple de code suivant montre comment utiliser le `Median` méthode pour un tableau de type `double`.</span><span class="sxs-lookup"><span data-stu-id="6ca92-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
<span data-ttu-id="6ca92-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="6ca92-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="6ca92-120">La surcharge d’une méthode d’agrégation pour accepter différents Types</span><span class="sxs-lookup"><span data-stu-id="6ca92-120">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="6ca92-121">Vous pouvez surcharger votre méthode d’agrégation afin qu’elle accepte des séquences de différents types.</span><span class="sxs-lookup"><span data-stu-id="6ca92-121">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="6ca92-122">L’approche standard consiste à créer une surcharge pour chaque type.</span><span class="sxs-lookup"><span data-stu-id="6ca92-122">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="6ca92-123">Une autre approche consiste à créer une surcharge qui prend un type générique et convertissez-le en un type spécifique à l’aide d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="6ca92-123">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="6ca92-124">Vous pouvez également combiner ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="6ca92-124">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="6ca92-125">Pour créer une surcharge pour chaque type.</span><span class="sxs-lookup"><span data-stu-id="6ca92-125">To create an overload for each type</span></span>  
 <span data-ttu-id="6ca92-126">Vous pouvez créer une surcharge spécifique pour chaque type que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="6ca92-126">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="6ca92-127">L’exemple de code suivant montre une surcharge de la `Median` méthode pour le `integer` type.</span><span class="sxs-lookup"><span data-stu-id="6ca92-127">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
<span data-ttu-id="6ca92-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="6ca92-129">Vous pouvez maintenant appeler le `Median` surcharges pour les deux `integer` et `double` types, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6ca92-129">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
<span data-ttu-id="6ca92-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="6ca92-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="6ca92-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="6ca92-133">Pour créer une surcharge générique</span><span class="sxs-lookup"><span data-stu-id="6ca92-133">To create a generic overload</span></span>  
 <span data-ttu-id="6ca92-134">Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques.</span><span class="sxs-lookup"><span data-stu-id="6ca92-134">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="6ca92-135">Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets d’un type générique en un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ca92-135">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="6ca92-136">Le code suivant montre une surcharge de la `Median` méthode qui prend le <xref:System.Func%602>délégué en tant que paramètre.</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="6ca92-136">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="6ca92-137">Ce délégué prend un objet de type générique T et retourne un objet de type `double`.</span><span class="sxs-lookup"><span data-stu-id="6ca92-137">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="6ca92-138">Vous pouvez maintenant appeler le `Median` méthode pour une séquence d’objets de tout type.</span><span class="sxs-lookup"><span data-stu-id="6ca92-138">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="6ca92-139">Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre délégué.</span><span class="sxs-lookup"><span data-stu-id="6ca92-139">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="6ca92-140">Dans Visual Basic, vous pouvez utiliser une expression lambda à cet effet.</span><span class="sxs-lookup"><span data-stu-id="6ca92-140">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="6ca92-141">En outre, si vous utilisez la `Aggregate` ou `Group By` clause au lieu de l’appel de méthode, vous pouvez passer toute valeur ou expression qui est dans la portée de cette clause.</span><span class="sxs-lookup"><span data-stu-id="6ca92-141">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="6ca92-142">L’exemple de code suivant montre comment appeler le `Median` méthode pour un tableau d’entiers et un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6ca92-142">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="6ca92-143">Pour les chaînes, la valeur médiane pour les longueurs de chaînes dans le tableau est calculée.</span><span class="sxs-lookup"><span data-stu-id="6ca92-143">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="6ca92-144">L’exemple montre comment passer le <xref:System.Func%602>déléguer le paramètre à la `Median` méthode pour chaque cas.</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="6ca92-144">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
<span data-ttu-id="6ca92-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="6ca92-146">Ajout d’une méthode qui retourne une Collection</span><span class="sxs-lookup"><span data-stu-id="6ca92-146">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="6ca92-147">Vous pouvez étendre le <xref:System.Collections.Generic.IEnumerable%601>interface avec une méthode de requête personnalisée qui retourne une séquence de valeurs.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-147">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="6ca92-148">Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-148">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6ca92-149">Ces méthodes peuvent être utilisés pour appliquer des transformations de données ou de filtres à une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ca92-149">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="6ca92-150">L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne chaque autre élément dans une collection, en commençant par le premier élément.</span><span class="sxs-lookup"><span data-stu-id="6ca92-150">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
<span data-ttu-id="6ca92-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6ca92-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="6ca92-152">Vous pouvez appeler cette méthode d’extension pour toute collection énumérable comme vous appelleriez d’autres méthodes de la <xref:System.Collections.Generic.IEnumerable%601>de l’interface, comme indiqué dans le code suivant :</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-152">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ca92-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ca92-153">See Also</span></span>  
 <span data-ttu-id="6ca92-154"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6ca92-154"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="6ca92-155"> [Méthodes d’extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="6ca92-155"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
