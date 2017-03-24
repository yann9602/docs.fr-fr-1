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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a>Collections (Visual Basic)
Pour de nombreuses applications, vous voulez créer et gérer des groupes d’objets connexes. Il existe deux manières de grouper des objets : en créant des tableaux d’objets ou des collections d’objets.  
  
 Les tableaux sont particulièrement utiles pour la création et l’utilisation d’un nombre fixe d’objets fortement typés. Pour plus d’informations sur les tableaux, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets. Contrairement aux tableaux, le groupe d’objets que vous utilisez peut être développé et réduit de manière dynamique selon les modifications de l’application. Pour certaines collections, vous pouvez affecter une clé à tout objet que vous placez dans la collection de sorte à pouvoir récupérer rapidement l’objet à l’aide de la clé.  
  
 Une collection est une classe, vous devez déclarer une instance de la classe avant de pouvoir ajouter des éléments à la collection.  
  
 Si votre collection contient des éléments de type de données qu’une seule, vous pouvez utiliser une des classes dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms.</xref:System.Collections.Generic?displayProperty=fullName> Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté. Quand vous récupérez un élément d’une collection générique, il n’est pas utile de déterminer son type de données ou de le convertir.  
  
> [!NOTE]
>  Pour les exemples de cette rubrique, vous devez inclure [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instructions pour le `System.Collections.Generic` et `System.Linq` espaces de noms.  
  
 **Dans cette rubrique**  
  
-   [À l’aide d’une Collection Simple](#BKMK_SimpleCollection)  
  
-   [Types de Collections](#BKMK_KindsOfCollections)  
  
    -   [Classes System.Collections.Generic](#BKMK_Generic)  
  
    -   [Classes System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [Classes System.Collections](#BKMK_Collections)  
  
    -   [Classe de Collection Visual Basic](#BKMK_VisualBasic)  
  
-   [Implémentation d’une Collection de paires clé/valeur](#BKMK_KeyValuePairs)  
  
-   [Utilisation de LINQ pour accéder à une Collection](#BKMK_LINQ)  
  
-   [Tri d’une Collection](#BKMK_Sorting)  
  
-   [Définition d’une Collection personnalisée](#BKMK_CustomCollection)  
  
-   [Itérateurs](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Utilisation d’une collection simple  
 Les exemples de cette section utilisent le type générique <xref:System.Collections.Generic.List%601>(classe), qui vous permet de travailler avec une liste fortement typée d’objets.</xref:System.Collections.Generic.List%601>  
  
 L’exemple suivant crée une liste de chaînes et parcourt ensuite les chaînes en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction.  
  
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
  
 Si le contenu d’une collection est connu à l’avance, vous pouvez utiliser un *initialiseur de collection* pour initialiser la collection. Pour plus d’informations, consultez [initialiseurs de Collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 L’exemple suivant est identique à l’exemple précédent, à la différence qu’un initialiseur de collection est utilisé pour ajouter des éléments à la collection.  
  
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
  
 Vous pouvez utiliser un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) déclaration au lieu d’un `For Each` instruction pour effectuer une itération dans une collection. Pour cela, accédez aux éléments de la collection à la position d’index. L’index des éléments commence à 0 et se termine au nombre d’éléments moins 1.  
  
 L’exemple suivant effectue une itération dans les éléments d’une collection à l’aide de `For…Next` au lieu de `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 L’exemple suivant supprime un élément de la collection en spécifiant l’objet à supprimer.  
  
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
  
 L’exemple suivant supprime les éléments d’une liste générique. Au lieu d’un `For Each` instruction, un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) qui itère dans l’ordre décroissant est utilisée. C’est parce que le <xref:System.Collections.Generic.List%601.RemoveAt%2A>(méthode), les éléments après un élément supprimé ont une valeur d’index inférieure.</xref:System.Collections.Generic.List%601.RemoveAt%2A>  
  
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
  
 Pour le type d’éléments dans <xref:System.Collections.Generic.List%601>vous pouvez également définir votre propre classe.</xref:System.Collections.Generic.List%601> Dans l’exemple suivant, la `Galaxy` classe qui est utilisée par le <xref:System.Collections.Generic.List%601>est défini dans le code.</xref:System.Collections.Generic.List%601>  
  
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
## <a name="kinds-of-collections"></a>Types de collections   
 Plusieurs collections courantes sont fournies par le .NET Framework. Chaque type de collection est conçu dans un but spécifique.  
  
 Certaines des classes de collection courantes sont décrites dans cette section :  
  
-   @System.Collections.Genericclasses  
  
-   @System.Collections.Concurrentclasses  
  
-   @System.Collectionsclasses  
  
-   Visual Basic `Collection` (classe)  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>Classes System.Collections.Generic  

 Vous pouvez créer une collection générique en utilisant l’une des classes dans le <xref:System.Collections.Generic>espace de noms.</xref:System.Collections.Generic> Une collection générique est utile quand chaque élément de la collection a le même type de données. Une collection générique applique un typage fort en autorisant uniquement l’ajout des types de données souhaités.  
  
 Le tableau suivant répertorie certaines des classes fréquemment utilisées de la <xref:System.Collections.Generic?displayProperty=fullName>espace de noms :</xref:System.Collections.Generic?displayProperty=fullName>  
  
|Classe|Description|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602>|Représente une collection de paires clé/valeur organisées en fonction de la clé.|  
|<xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601>|Représente une liste d’objets accessibles par index. Fournit des méthodes de recherche, de tri et de modification de listes.|  
|<xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601>|Représente une collection d’objets premier entré, premier sorti (FIFO).|  
|<xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602>|Représente une collection de paires clé/valeur triées par clé en fonction d’associé <xref:System.Collections.Generic.IComparer%601>implémentation.</xref:System.Collections.Generic.IComparer%601>|  
|<xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601>|Représente une collection d’objets dernier entré, premier sorti (LIFO).|  
  
 Pour plus d’informations, consultez [utilisé Types de collections couramment](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [sélection d’une classe de Collection](../../../standard/collections/selecting-a-collection-class.md)et <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>Classes System.Collections.Concurrent   
 Dans le .NET Framework 4 ou versions ultérieures, les collections de la <xref:System.Collections.Concurrent>espace de noms fournissent des opérations thread-safe efficaces pour accéder aux éléments de la collection à partir de plusieurs threads.</xref:System.Collections.Concurrent>  
  
 Les classes dans le <xref:System.Collections.Concurrent>espace de noms doit être utilisée au lieu de types correspondants dans le <xref:System.Collections.Generic?displayProperty=fullName>et <xref:System.Collections?displayProperty=fullName>chaque fois que plusieurs threads accèdent simultanément à la collection des espaces de noms.</xref:System.Collections?displayProperty=fullName> </xref:System.Collections.Generic?displayProperty=fullName> </xref:System.Collections.Concurrent> Pour plus d’informations, consultez [Collections Thread-Safe](../../../standard/collections/threadsafe/index.md) et <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent>  
  
 Certaines classes inclus dans le <xref:System.Collections.Concurrent>espace de noms sont <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>Classes System.Collections    
 Les classes dans le <xref:System.Collections?displayProperty=fullName>espace de noms ne stockent pas les éléments comme des objets spécifiquement typés, mais comme des objets de type `Object`.</xref:System.Collections?displayProperty=fullName>  
  
 Dès que possible, vous devez utiliser les collections génériques dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms ou le <xref:System.Collections.Concurrent>espace de noms au lieu de types hérités dans le `System.Collections` espace de noms.</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName>  
  
 Le tableau suivant répertorie certaines des classes fréquemment utilisées dans les `System.Collections` espace de noms :  
  
|Classe|Description|  
|---|---|  
|<xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>|Représente un tableau d’objets dont la taille est augmentée de manière dynamique selon les besoins.|  
|<xref:System.Collections.Hashtable></xref:System.Collections.Hashtable>|Représente une collection de paires clé/valeur qui sont organisées en fonction du code de hachage de la clé.|  
|<xref:System.Collections.Queue></xref:System.Collections.Queue>|Représente une collection d’objets premier entré, premier sorti (FIFO).|  
|<xref:System.Collections.Stack></xref:System.Collections.Stack>|Représente une collection d’objets dernier entré, premier sorti (LIFO).|  
  
 Le <xref:System.Collections.Specialized>espace de noms fournit des classes de collection spécialisées et fortement typées, telles que les collections à chaîne uniqu’et les dictionnaires de liste liée et hybrides.</xref:System.Collections.Specialized>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Classe de la collection Visual Basic  
 Vous pouvez utiliser Visual Basic <xref:Microsoft.VisualBasic.Collection>classe d’accéder à une collection d’éléments en utilisant soit un index numérique ou une `String` clé.</xref:Microsoft.VisualBasic.Collection> Vous pouvez ajouter des éléments à un objet de collection en spécifiant ou non une clé. Si vous ajoutez un élément sans clé, vous devez utiliser son index numérique pour y accéder.  
  
 Visual Basic `Collection` classe stocke tous ses éléments comme de type `Object`, de sorte que vous pouvez ajouter un élément de n’importe quel type de données. Il n’existe aucun dispositif de protection contre l’ajout de types de données inappropriés.  
  
 Lorsque vous utilisez Visual Basic `Collection` (classe), le premier élément dans une collection a un index de 1. Ce n’est pas le cas pour les classes de collection .NET Framework, pour lesquelles l’index de départ est 0.  
  
 Dès que possible, vous devez utiliser les collections génériques dans le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms ou le <xref:System.Collections.Concurrent>espace de noms au lieu de Visual Basic `Collection` classe</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName>  
  
 Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Collection>.</xref:Microsoft.VisualBasic.Collection>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implémentation d’une collection de paires clé/valeur   
 Le <xref:System.Collections.Generic.Dictionary%602>collection générique vous permet d’accéder aux éléments d’une collection à l’aide de la clé de chaque élément à.</xref:System.Collections.Generic.Dictionary%602> Chaque ajout au dictionnaire se compose d’une valeur et de sa clé associée. Récupération d’une valeur à l’aide de sa clé est rapide, car la `Dictionary` classe est implémentée comme une table de hachage.  
  
 L’exemple suivant crée un `Dictionary` collection et itère au sein du dictionnaire en utilisant un `For Each` instruction.  
  
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
  
 À la place utiliser un initialiseur de collection pour générer le `Dictionary` collection, vous pouvez remplacer le `BuildDictionary` et `AddToDictionary` méthodes avec la méthode suivante.  
  
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
  
 L’exemple suivant utilise le <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>(méthode) et le <xref:System.Collections.Generic.Dictionary%602.Item%2A>propriété du `Dictionary` pour rechercher rapidement un élément par clé.</xref:System.Collections.Generic.Dictionary%602.Item%2A> </xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> Le `Item` propriété vous permet d’accéder à un élément dans le `elements` collection à l’aide de la `elements(symbol)` code Visual Basic.  
  
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
  
 L’exemple suivant utilise à la place la <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>méthode trouver rapidement un élément par clé.</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>  
  
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
##  <a name="using-linq-to-access-a-collection"></a>Utilisation de LINQ pour accéder à une collection  
 LINQ (Language-Integrated Query) peut être utilisé pour accéder aux collections. Les requêtes LINQ fournissent des fonctionnalités de filtrage, de classement et de regroupement. Pour plus d’informations, consultez [mise en route de LINQ en Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 L’exemple suivant exécute une requête LINQ sur un type générique `List`. La requête LINQ retourne une autre collection qui contient les résultats.  
  
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
## <a name="sorting-a-collection"></a>Tri d’une collection  
 L’exemple suivant illustre une procédure de tri d’une collection. L’exemple montre comment trier des instances de la `Car` classe qui sont stockés dans un <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601> Le `Car` la classe implémente le <xref:System.IComparable%601>interface, ce qui nécessite que le <xref:System.IComparable%601.CompareTo%2A>méthode implémentée.</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601>  
  
 Chaque appel à la <xref:System.IComparable%601.CompareTo%2A>méthode effectue une comparaison unique qui est utilisée pour le tri.</xref:System.IComparable%601.CompareTo%2A> Code écrit par l’utilisateur dans le `CompareTo` méthode retourne une valeur pour chaque comparaison de l’objet actuel à un autre objet. La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux. Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».  
  
 Dans le `ListCars` (méthode), la `cars.Sort()` instruction trie la liste. Cet appel à la <xref:System.Collections.Generic.List%601.Sort%2A>Procédé de la <xref:System.Collections.Generic.List%601>provoque la `CompareTo` méthode à appeler automatiquement pour le `Car` des objets dans le `List`.</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A>  
  
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
## <a name="defining-a-custom-collection"></a>Définition d’une collection personnalisée  
 Vous pouvez définir une collection en implémentant le <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601> Pour plus d’informations, consultez [l’énumération d’une Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Bien que vous pouvez définir une collection personnalisée, il est généralement préférable d’utiliser plutôt les collections qui sont incluses dans le .NET Framework, qui sont décrites dans [types de Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) précédemment dans cette rubrique.  
  
 L’exemple suivant définit une classe de collection personnalisée nommée `AllColors`. Cette classe implémente le <xref:System.Collections.IEnumerable>interface, ce qui nécessite que le <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode implémentée.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable>  
  
 Le `GetEnumerator` méthode retourne une instance de la `ColorEnumerator` classe. `ColorEnumerator`implémente le <xref:System.Collections.IEnumerator>interface, ce qui nécessite que le <xref:System.Collections.IEnumerator.Current%2A>propriété <xref:System.Collections.IEnumerator.MoveNext%2A>(méthode), et <xref:System.Collections.IEnumerator.Reset%2A>méthode implémentée.</xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator>  
  
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
##  <a name="iterators"></a>Itérateurs  
 Un *itérateur* est utilisé pour effectuer une itération personnalisée sur une collection. Un itérateur peut être une méthode ou un `get` accesseur. Un itérateur utilise un [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément de la collection une à la fois.  
  
 Vous appelez un itérateur en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction. Chaque itération de la `For Each` boucle appelle l’itérateur. Lorsqu’un `Yield` instruction est atteint dans l’itérateur, une expression est retourné et l’emplacement actuel dans le code est conservé. L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.  
  
 Pour plus d’informations, consultez [itérateurs (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 L’exemple suivant utilise une méthode Iterator. La méthode iterator a un `Yield` instruction qui est à l’intérieur d’un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Dans le `ListEvenNumbers` (méthode), chaque itération de la `For Each` corps de l’instruction crée un appel à la méthode de l’itérateur, qui passe à la prochaine `Yield` instruction.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Concepts de programmation (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)   
 [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)   
 [Collections et Structures de données](../../../standard/collections/index.md)   
 [Création et manipulation de Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)   
 [Sélection d’une classe de Collection](../../../standard/collections/selecting-a-collection-class.md)   
 [Comparaisons et tris dans les Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md)   
 [Quand utiliser les collections génériques](../../../standard/collections/when-to-use-generic-collections.md)
