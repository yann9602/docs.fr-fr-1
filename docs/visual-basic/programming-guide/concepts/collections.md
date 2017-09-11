---
title: Collections (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a><span data-ttu-id="819b6-102">Collections (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="819b6-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="819b6-103">Pour de nombreuses applications, vous voulez créer et gérer des groupes d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="819b6-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="819b6-104">Il existe deux manières de grouper des objets : en créant des tableaux d’objets ou des collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="819b6-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="819b6-105">Les tableaux sont particulièrement utiles pour la création et l’utilisation d’un nombre fixe d’objets fortement typés.</span><span class="sxs-lookup"><span data-stu-id="819b6-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="819b6-106">Pour plus d’informations sur les tableaux, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="819b6-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="819b6-107">Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets.</span><span class="sxs-lookup"><span data-stu-id="819b6-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="819b6-108">Contrairement aux tableaux, le groupe d’objets que vous utilisez peut être développé et réduit de manière dynamique selon les modifications de l’application.</span><span class="sxs-lookup"><span data-stu-id="819b6-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="819b6-109">Pour certaines collections, vous pouvez affecter une clé à tout objet que vous placez dans la collection de sorte à pouvoir récupérer rapidement l’objet à l’aide de la clé.</span><span class="sxs-lookup"><span data-stu-id="819b6-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="819b6-110">Une collection est une classe, vous devez déclarer une instance de la classe avant de pouvoir ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="819b6-111">Si votre collection contient des éléments de type de données qu’une seule, vous pouvez utiliser une des classes dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="819b6-112">Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté.</span><span class="sxs-lookup"><span data-stu-id="819b6-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="819b6-113">Quand vous récupérez un élément d’une collection générique, il n’est pas utile de déterminer son type de données ou de le convertir.</span><span class="sxs-lookup"><span data-stu-id="819b6-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="819b6-114">Pour les exemples de cette rubrique, vous devez inclure [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instructions pour le `System.Collections.Generic` et `System.Linq` espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="819b6-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="819b6-115">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="819b6-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="819b6-116">À l’aide d’une Collection Simple</span><span class="sxs-lookup"><span data-stu-id="819b6-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="819b6-117">Types de Collections</span><span class="sxs-lookup"><span data-stu-id="819b6-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="819b6-118">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="819b6-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="819b6-119">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="819b6-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="819b6-120">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="819b6-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="819b6-121">Classe de Collection Visual Basic</span><span class="sxs-lookup"><span data-stu-id="819b6-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="819b6-122">Implémentation d’une Collection de paires clé/valeur</span><span class="sxs-lookup"><span data-stu-id="819b6-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="819b6-123">Utilisation de LINQ pour accéder à une Collection</span><span class="sxs-lookup"><span data-stu-id="819b6-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="819b6-124">Tri d’une Collection</span><span class="sxs-lookup"><span data-stu-id="819b6-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="819b6-125">Définition d’une Collection personnalisée</span><span class="sxs-lookup"><span data-stu-id="819b6-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="819b6-126">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="819b6-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="819b6-127">Utilisation d’une collection simple</span><span class="sxs-lookup"><span data-stu-id="819b6-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="819b6-128">Les exemples de cette section utilisent le type générique <xref:System.Collections.Generic.List%601>(classe), qui vous permet de travailler avec une liste fortement typée d’objets.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="819b6-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="819b6-129">L’exemple suivant crée une liste de chaînes et parcourt ensuite les chaînes en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction.</span><span class="sxs-lookup"><span data-stu-id="819b6-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="819b6-130">Si le contenu d’une collection est connu à l’avance, vous pouvez utiliser un *initialiseur de collection* pour initialiser la collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="819b6-131">Pour plus d’informations, consultez [initialiseurs de Collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="819b6-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="819b6-132">L’exemple suivant est identique à l’exemple précédent, à la différence qu’un initialiseur de collection est utilisé pour ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="819b6-133">Vous pouvez utiliser un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) déclaration au lieu d’un `For Each` instruction pour effectuer une itération dans une collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="819b6-134">Pour cela, accédez aux éléments de la collection à la position d’index.</span><span class="sxs-lookup"><span data-stu-id="819b6-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="819b6-135">L’index des éléments commence à 0 et se termine au nombre d’éléments moins 1.</span><span class="sxs-lookup"><span data-stu-id="819b6-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="819b6-136">L’exemple suivant effectue une itération dans les éléments d’une collection à l’aide de `For…Next` au lieu de `For Each`.</span><span class="sxs-lookup"><span data-stu-id="819b6-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="819b6-137">L’exemple suivant supprime un élément de la collection en spécifiant l’objet à supprimer.</span><span class="sxs-lookup"><span data-stu-id="819b6-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="819b6-138">L’exemple suivant supprime les éléments d’une liste générique.</span><span class="sxs-lookup"><span data-stu-id="819b6-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="819b6-139">Au lieu d’un `For Each` instruction, un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) qui itère dans l’ordre décroissant est utilisée.</span><span class="sxs-lookup"><span data-stu-id="819b6-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="819b6-140">C’est parce que le <xref:System.Collections.Generic.List%601.RemoveAt%2A>(méthode), les éléments après un élément supprimé ont une valeur d’index inférieure.</xref:System.Collections.Generic.List%601.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="819b6-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="819b6-141">Pour le type d’éléments dans <xref:System.Collections.Generic.List%601>vous pouvez également définir votre propre classe.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="819b6-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="819b6-142">Dans l’exemple suivant, la `Galaxy` classe qui est utilisée par le <xref:System.Collections.Generic.List%601>est défini dans le code.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="819b6-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="819b6-143">Types de collections</span><span class="sxs-lookup"><span data-stu-id="819b6-143">Kinds of Collections</span></span>   
 <span data-ttu-id="819b6-144">Plusieurs collections courantes sont fournies par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="819b6-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="819b6-145">Chaque type de collection est conçu dans un but spécifique.</span><span class="sxs-lookup"><span data-stu-id="819b6-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="819b6-146">Certaines des classes de collection courantes sont décrites dans cette section :</span><span class="sxs-lookup"><span data-stu-id="819b6-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="819b6-147">@System.Collections.Genericclasses</span><span class="sxs-lookup"><span data-stu-id="819b6-147">@System.Collections.Generic classes</span></span>  
  
-   <span data-ttu-id="819b6-148">@System.Collections.Concurrentclasses</span><span class="sxs-lookup"><span data-stu-id="819b6-148">@System.Collections.Concurrent classes</span></span>  
  
-   <span data-ttu-id="819b6-149">@System.Collectionsclasses</span><span class="sxs-lookup"><span data-stu-id="819b6-149">@System.Collections classes</span></span>  
  
-   <span data-ttu-id="819b6-150">Visual Basic `Collection` (classe)</span><span class="sxs-lookup"><span data-stu-id="819b6-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="819b6-151">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="819b6-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="819b6-152">Vous pouvez créer une collection générique en utilisant l’une des classes dans le <xref:System.Collections.Generic>espace de noms.</xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="819b6-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="819b6-153">Une collection générique est utile quand chaque élément de la collection a le même type de données.</span><span class="sxs-lookup"><span data-stu-id="819b6-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="819b6-154">Une collection générique applique un typage fort en autorisant uniquement l’ajout des types de données souhaités.</span><span class="sxs-lookup"><span data-stu-id="819b6-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="819b6-155">Le tableau suivant répertorie certaines des classes fréquemment utilisées de la <xref:System.Collections.Generic?displayProperty=fullName>espace de noms :</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="819b6-156">Classe</span><span class="sxs-lookup"><span data-stu-id="819b6-156">Class</span></span>|<span data-ttu-id="819b6-157">Description</span><span class="sxs-lookup"><span data-stu-id="819b6-157">Description</span></span>|  
|---|---|  
|<span data-ttu-id="819b6-158"><xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="819b6-158"><xref:System.Collections.Generic.Dictionary%602></span></span>|<span data-ttu-id="819b6-159">Représente une collection de paires clé/valeur organisées en fonction de la clé.</span><span class="sxs-lookup"><span data-stu-id="819b6-159">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<span data-ttu-id="819b6-160"><xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="819b6-160"><xref:System.Collections.Generic.List%601></span></span>|<span data-ttu-id="819b6-161">Représente une liste d’objets accessibles par index.</span><span class="sxs-lookup"><span data-stu-id="819b6-161">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="819b6-162">Fournit des méthodes de recherche, de tri et de modification de listes.</span><span class="sxs-lookup"><span data-stu-id="819b6-162">Provides methods to search, sort, and modify lists.</span></span>|  
|<span data-ttu-id="819b6-163"><xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601></span><span class="sxs-lookup"><span data-stu-id="819b6-163"><xref:System.Collections.Generic.Queue%601></span></span>|<span data-ttu-id="819b6-164">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="819b6-164">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="819b6-165"><xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602></span><span class="sxs-lookup"><span data-stu-id="819b6-165"><xref:System.Collections.Generic.SortedList%602></span></span>|<span data-ttu-id="819b6-166">Représente une collection de paires clé/valeur triées par clé en fonction d’associé <xref:System.Collections.Generic.IComparer%601>implémentation.</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="819b6-166">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<span data-ttu-id="819b6-167"><xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601></span><span class="sxs-lookup"><span data-stu-id="819b6-167"><xref:System.Collections.Generic.Stack%601></span></span>|<span data-ttu-id="819b6-168">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="819b6-168">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="819b6-169">Pour plus d’informations, consultez [utilisé Types de collections couramment](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [sélection d’une classe de Collection](../../../standard/collections/selecting-a-collection-class.md)et <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-169">For additional information, see [Commonly Used Collection Types](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="819b6-170">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="819b6-170">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="819b6-171">Dans le .NET Framework 4 ou versions ultérieures, les collections de la <xref:System.Collections.Concurrent>espace de noms fournissent des opérations thread-safe efficaces pour accéder aux éléments de la collection à partir de plusieurs threads.</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="819b6-171">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="819b6-172">Les classes dans le <xref:System.Collections.Concurrent>espace de noms doit être utilisée au lieu de types correspondants dans le <xref:System.Collections.Generic?displayProperty=fullName>et <xref:System.Collections?displayProperty=fullName>chaque fois que plusieurs threads accèdent simultanément à la collection des espaces de noms.</xref:System.Collections?displayProperty=fullName> </xref:System.Collections.Generic?displayProperty=fullName> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="819b6-172">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=fullName> and <xref:System.Collections?displayProperty=fullName> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="819b6-173">Pour plus d’informations, consultez [Collections Thread-Safe](../../../standard/collections/threadsafe/index.md) et <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="819b6-173">For more information, see [Thread-Safe Collections](../../../standard/collections/threadsafe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="819b6-174">Certaines classes inclus dans le <xref:System.Collections.Concurrent>espace de noms sont <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="819b6-174">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="819b6-175">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="819b6-175">System.Collections Classes</span></span>    
 <span data-ttu-id="819b6-176">Les classes dans le <xref:System.Collections?displayProperty=fullName>espace de noms ne stockent pas les éléments comme des objets spécifiquement typés, mais comme des objets de type `Object`.</xref:System.Collections?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-176">The classes in the <xref:System.Collections?displayProperty=fullName> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="819b6-177">Dès que possible, vous devez utiliser les collections génériques dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms ou le <xref:System.Collections.Concurrent>espace de noms au lieu de types hérités dans le `System.Collections` espace de noms.</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="819b6-178">Le tableau suivant répertorie certaines des classes fréquemment utilisées dans les `System.Collections` espace de noms :</span><span class="sxs-lookup"><span data-stu-id="819b6-178">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="819b6-179">Classe</span><span class="sxs-lookup"><span data-stu-id="819b6-179">Class</span></span>|<span data-ttu-id="819b6-180">Description</span><span class="sxs-lookup"><span data-stu-id="819b6-180">Description</span></span>|  
|---|---|  
|<span data-ttu-id="819b6-181"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="819b6-181"><xref:System.Collections.ArrayList></span></span>|<span data-ttu-id="819b6-182">Représente un tableau d’objets dont la taille est augmentée de manière dynamique selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="819b6-182">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<span data-ttu-id="819b6-183"><xref:System.Collections.Hashtable></xref:System.Collections.Hashtable></span><span class="sxs-lookup"><span data-stu-id="819b6-183"><xref:System.Collections.Hashtable></span></span>|<span data-ttu-id="819b6-184">Représente une collection de paires clé/valeur qui sont organisées en fonction du code de hachage de la clé.</span><span class="sxs-lookup"><span data-stu-id="819b6-184">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<span data-ttu-id="819b6-185"><xref:System.Collections.Queue></xref:System.Collections.Queue></span><span class="sxs-lookup"><span data-stu-id="819b6-185"><xref:System.Collections.Queue></span></span>|<span data-ttu-id="819b6-186">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="819b6-186">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="819b6-187"><xref:System.Collections.Stack></xref:System.Collections.Stack></span><span class="sxs-lookup"><span data-stu-id="819b6-187"><xref:System.Collections.Stack></span></span>|<span data-ttu-id="819b6-188">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="819b6-188">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="819b6-189">Le <xref:System.Collections.Specialized>espace de noms fournit des classes de collection spécialisées et fortement typées, telles que les collections à chaîne uniqu’et les dictionnaires de liste liée et hybrides.</xref:System.Collections.Specialized></span><span class="sxs-lookup"><span data-stu-id="819b6-189">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="819b6-190">Classe de la collection Visual Basic</span><span class="sxs-lookup"><span data-stu-id="819b6-190">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="819b6-191">Vous pouvez utiliser Visual Basic <xref:Microsoft.VisualBasic.Collection>classe d’accéder à une collection d’éléments en utilisant soit un index numérique ou une `String` clé.</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="819b6-191">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="819b6-192">Vous pouvez ajouter des éléments à un objet de collection en spécifiant ou non une clé.</span><span class="sxs-lookup"><span data-stu-id="819b6-192">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="819b6-193">Si vous ajoutez un élément sans clé, vous devez utiliser son index numérique pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="819b6-193">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="819b6-194">Visual Basic `Collection` classe stocke tous ses éléments comme de type `Object`, de sorte que vous pouvez ajouter un élément de n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="819b6-194">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="819b6-195">Il n’existe aucun dispositif de protection contre l’ajout de types de données inappropriés.</span><span class="sxs-lookup"><span data-stu-id="819b6-195">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="819b6-196">Lorsque vous utilisez Visual Basic `Collection` (classe), le premier élément dans une collection a un index de 1.</span><span class="sxs-lookup"><span data-stu-id="819b6-196">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="819b6-197">Ce n’est pas le cas pour les classes de collection .NET Framework, pour lesquelles l’index de départ est 0.</span><span class="sxs-lookup"><span data-stu-id="819b6-197">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="819b6-198">Dès que possible, vous devez utiliser les collections génériques dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms ou le <xref:System.Collections.Concurrent>espace de noms au lieu de Visual Basic `Collection` classe</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="819b6-198">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="819b6-199">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Collection>.</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="819b6-199">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="819b6-200">Implémentation d’une collection de paires clé/valeur</span><span class="sxs-lookup"><span data-stu-id="819b6-200">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="819b6-201">Le <xref:System.Collections.Generic.Dictionary%602>collection générique vous permet d’accéder aux éléments d’une collection à l’aide de la clé de chaque élément à.</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="819b6-201">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="819b6-202">Chaque ajout au dictionnaire se compose d’une valeur et de sa clé associée.</span><span class="sxs-lookup"><span data-stu-id="819b6-202">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="819b6-203">Récupération d’une valeur à l’aide de sa clé est rapide, car la `Dictionary` classe est implémentée comme une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="819b6-203">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="819b6-204">L’exemple suivant crée un `Dictionary` collection et itère au sein du dictionnaire en utilisant un `For Each` instruction.</span><span class="sxs-lookup"><span data-stu-id="819b6-204">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <span data-ttu-id="819b6-205">À la place utiliser un initialiseur de collection pour générer le `Dictionary` collection, vous pouvez remplacer le `BuildDictionary` et `AddToDictionary` méthodes avec la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="819b6-205">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 <span data-ttu-id="819b6-206">L’exemple suivant utilise le <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>(méthode) et le <xref:System.Collections.Generic.Dictionary%602.Item%2A>propriété du `Dictionary` pour rechercher rapidement un élément par clé.</xref:System.Collections.Generic.Dictionary%602.Item%2A> </xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A></span><span class="sxs-lookup"><span data-stu-id="819b6-206">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="819b6-207">Le `Item` propriété vous permet d’accéder à un élément dans le `elements` collection à l’aide de la `elements(symbol)` code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="819b6-207">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="819b6-208">L’exemple suivant utilise à la place la <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>méthode trouver rapidement un élément par clé.</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A></span><span class="sxs-lookup"><span data-stu-id="819b6-208">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="819b6-209">Utilisation de LINQ pour accéder à une collection</span><span class="sxs-lookup"><span data-stu-id="819b6-209">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="819b6-210">LINQ (Language-Integrated Query) peut être utilisé pour accéder aux collections.</span><span class="sxs-lookup"><span data-stu-id="819b6-210">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="819b6-211">Les requêtes LINQ fournissent des fonctionnalités de filtrage, de classement et de regroupement.</span><span class="sxs-lookup"><span data-stu-id="819b6-211">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="819b6-212">Pour plus d’informations, consultez [mise en route de LINQ en Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="819b6-212">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="819b6-213">L’exemple suivant exécute une requête LINQ sur un type générique `List`.</span><span class="sxs-lookup"><span data-stu-id="819b6-213">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="819b6-214">La requête LINQ retourne une autre collection qui contient les résultats.</span><span class="sxs-lookup"><span data-stu-id="819b6-214">The LINQ query returns a different collection that contains the results.</span></span>  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a><span data-ttu-id="819b6-215">Tri d’une collection</span><span class="sxs-lookup"><span data-stu-id="819b6-215">Sorting a Collection</span></span>  
 <span data-ttu-id="819b6-216">L’exemple suivant illustre une procédure de tri d’une collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-216">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="819b6-217">L’exemple montre comment trier des instances de la `Car` classe qui sont stockés dans un <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="819b6-217">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="819b6-218">Le `Car` la classe implémente le <xref:System.IComparable%601>interface, ce qui nécessite que le <xref:System.IComparable%601.CompareTo%2A>méthode implémentée.</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="819b6-218">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="819b6-219">Chaque appel à la <xref:System.IComparable%601.CompareTo%2A>méthode effectue une comparaison unique qui est utilisée pour le tri.</xref:System.IComparable%601.CompareTo%2A></span><span class="sxs-lookup"><span data-stu-id="819b6-219">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="819b6-220">Code écrit par l’utilisateur dans le `CompareTo` méthode retourne une valeur pour chaque comparaison de l’objet actuel à un autre objet.</span><span class="sxs-lookup"><span data-stu-id="819b6-220">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="819b6-221">La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux.</span><span class="sxs-lookup"><span data-stu-id="819b6-221">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="819b6-222">Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».</span><span class="sxs-lookup"><span data-stu-id="819b6-222">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="819b6-223">Dans le `ListCars` (méthode), la `cars.Sort()` instruction trie la liste.</span><span class="sxs-lookup"><span data-stu-id="819b6-223">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="819b6-224">Cet appel à la <xref:System.Collections.Generic.List%601.Sort%2A>Procédé de la <xref:System.Collections.Generic.List%601>provoque la `CompareTo` méthode à appeler automatiquement pour le `Car` des objets dans le `List`.</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A></span><span class="sxs-lookup"><span data-stu-id="819b6-224">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a><span data-ttu-id="819b6-225">Définition d’une collection personnalisée</span><span class="sxs-lookup"><span data-stu-id="819b6-225">Defining a Custom Collection</span></span>  
 <span data-ttu-id="819b6-226">Vous pouvez définir une collection en implémentant le <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="819b6-226">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="819b6-227">Pour plus d’informations, consultez [l’énumération d’une Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="819b6-227">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="819b6-228">Bien que vous pouvez définir une collection personnalisée, il est généralement préférable d’utiliser plutôt les collections qui sont incluses dans le .NET Framework, qui sont décrites dans [types de Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="819b6-228">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="819b6-229">L’exemple suivant définit une classe de collection personnalisée nommée `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="819b6-229">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="819b6-230">Cette classe implémente le <xref:System.Collections.IEnumerable>interface, ce qui nécessite que le <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode implémentée.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="819b6-230">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="819b6-231">Le `GetEnumerator` méthode retourne une instance de la `ColorEnumerator` classe.</span><span class="sxs-lookup"><span data-stu-id="819b6-231">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="819b6-232">`ColorEnumerator`implémente le <xref:System.Collections.IEnumerator>interface, ce qui nécessite que le <xref:System.Collections.IEnumerator.Current%2A>propriété <xref:System.Collections.IEnumerator.MoveNext%2A>(méthode), et <xref:System.Collections.IEnumerator.Reset%2A>méthode implémentée.</xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="819b6-232">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a><span data-ttu-id="819b6-233">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="819b6-233">Iterators</span></span>  
 <span data-ttu-id="819b6-234">Un *itérateur* est utilisé pour effectuer une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="819b6-234">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="819b6-235">Un itérateur peut être une méthode ou un `get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="819b6-235">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="819b6-236">Un itérateur utilise un [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément de la collection une à la fois.</span><span class="sxs-lookup"><span data-stu-id="819b6-236">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="819b6-237">Vous appelez un itérateur en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction.</span><span class="sxs-lookup"><span data-stu-id="819b6-237">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="819b6-238">Chaque itération de la `For Each` boucle appelle l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="819b6-238">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="819b6-239">Lorsqu’un `Yield` instruction est atteint dans l’itérateur, une expression est retourné et l’emplacement actuel dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="819b6-239">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="819b6-240">L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="819b6-240">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="819b6-241">Pour plus d’informations, consultez [itérateurs (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="819b6-241">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="819b6-242">L’exemple suivant utilise une méthode Iterator.</span><span class="sxs-lookup"><span data-stu-id="819b6-242">The following example uses an iterator method.</span></span> <span data-ttu-id="819b6-243">La méthode iterator a un `Yield` instruction qui est à l’intérieur d’un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle.</span><span class="sxs-lookup"><span data-stu-id="819b6-243">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="819b6-244">Dans le `ListEvenNumbers` (méthode), chaque itération de la `For Each` corps de l’instruction crée un appel à la méthode de l’itérateur, qui passe à la prochaine `Yield` instruction.</span><span class="sxs-lookup"><span data-stu-id="819b6-244">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="819b6-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="819b6-245">See Also</span></span>  
 <span data-ttu-id="819b6-246">[Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-246">[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span></span>  
<span data-ttu-id="819b6-247"> [Concepts de programmation (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-247"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="819b6-248"> [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-248"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="819b6-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="819b6-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span><span class="sxs-lookup"><span data-stu-id="819b6-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span></span>  
<span data-ttu-id="819b6-251"> [Collections et Structures de données](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-251"> [Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
<span data-ttu-id="819b6-252"> [Création et manipulation de Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span><span class="sxs-lookup"><span data-stu-id="819b6-252"> [Creating and Manipulating Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span></span>  
<span data-ttu-id="819b6-253"> [Sélection d’une classe de Collection](../../../standard/collections/selecting-a-collection-class.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-253"> [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md) </span></span>  
<span data-ttu-id="819b6-254"> [Comparaisons et tris dans les Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span><span class="sxs-lookup"><span data-stu-id="819b6-254"> [Comparisons and Sorts Within Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span></span>  
<span data-ttu-id="819b6-255"> [Quand utiliser les collections génériques](../../../standard/collections/when-to-use-generic-collections.md)</span><span class="sxs-lookup"><span data-stu-id="819b6-255"> [When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md)</span></span>
