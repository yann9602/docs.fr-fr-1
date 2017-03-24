---
title: "Itérateurs (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
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
ms.openlocfilehash: 4ea1e21bd8cc392889c477e78338384ed05d4cbb
ms.lasthandoff: 03/13/2017

---
# <a name="iterators-visual-basic"></a>Itérateurs (Visual Basic)
Un *itérateur* peut être utilisé pour parcourir les collections telles que des listes et des tableaux.  
  
 Une méthode d’itérateur ou `get` accesseur effectue une itération personnalisée sur une collection. Une méthode d’itérateur utilise le [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément un à la fois. Lorsqu’un `Yield` instruction est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d’itérateur est appelée.  
  
 Consommation d’un itérateur depuis le code client en utilisant un [For Each... Suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instruction, ou en utilisant une requête LINQ.  
  
 Dans l’exemple suivant, la première itération de la `For Each` boucle provoque l’exécution dans le `SomeNumbers` jusqu'à ce que la première méthode d’itérateur `Yield` instruction est atteinte. Cette itération renvoie la valeur 3, et l’emplacement actuel dans la méthode iterator est conservé. Sur l’itération suivante de la boucle, l’exécution de la méthode iterator continue à partir de laquelle elle s’est arrêtée, et s’arrête encore lorsqu’elle atteint un `Yield` instruction. Cette itération renvoie la valeur 5, et l’emplacement actuel dans la méthode iterator est conservé à nouveau. La boucle se termine lorsque la fin de la méthode d’itérateur.  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 Le type de retour d’une méthode d’itérateur ou `get` accesseur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 Vous pouvez utiliser un `Exit Function` ou `Return` instruction à la fin de l’itération.  
  
 Une fonction d’itérateur de Visual Basic ou `get` déclaration d’accesseur comprend un [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md) modificateur.  
  
 Itérateurs ont été introduites dans Visual Basic dans Visual Studio 2012.  
  
 **Dans cette rubrique**  
  
-   [Itérateur simple](#BKMK_SimpleIterator)  
  
-   [Création d’une classe de Collection](#BKMK_CollectionClass)  
  
-   [Try (blocs)](#BKMK_TryBlocks)  
  
-   [Méthodes anonymes](#BKMK_AnonymousMethods)  
  
-   [Utilisation d’itérateurs avec une liste générique](#BKMK_GenericList)  
  
-   [Informations sur la syntaxe](#BKMK_SyntaxInformation)  
  
-   [Implémentation technique](#BKMK_Technical)  
  
-   [Utilisation d’itérateurs](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Tous les exemples dans la rubrique à l’exception de l’exemple d’itérateur Simple, vous devez inclure [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instructions pour le `System.Collections` et `System.Collections.Generic` espaces de noms.  
  
##  <a name="BKMK_SimpleIterator"></a>Itérateur simple  
 L’exemple suivant comprend une seule `Yield` instruction qui est à l’intérieur d’un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Dans `Main`, chaque itération de la `For Each` corps de l’instruction crée un appel à la fonction d’itérateur, qui passe à la prochaine `Yield` instruction.  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <a name="BKMK_CollectionClass"></a>Création d’une classe de Collection  
 Dans l’exemple suivant, la `DaysOfTheWeek` la classe implémente le <xref:System.Collections.IEnumerable>interface, ce qui nécessite un <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable> Le compilateur appelle implicitement la `GetEnumerator` méthode qui retourne un <xref:System.Collections.IEnumerator>.</xref:System.Collections.IEnumerator>  
  
 Le `GetEnumerator` méthode retourne chaque chaîne une à la fois à l’aide de la `Yield` instruction et un `Iterator` modificateur est dans la déclaration de fonction.  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 L’exemple suivant crée un `Zoo` classe qui contient une collection des animaux.  
  
 Le `For Each` instruction qui fait référence à l’instance de classe (`theZoo`) appelle implicitement la `GetEnumerator` méthode. Le `For Each` instructions qui font référence à la `Birds` et `Mammals` utilisation de propriétés la `AnimalsForType` nommé iterator (méthode).  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <a name="BKMK_TryBlocks"></a>Try (blocs)  
 Visual Basic permet un `Yield` instruction dans le `Try` bloquer d’un [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` bloc qui a un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc.  
  
 L’exemple suivant inclut `Try`, `Catch`, et `Finally` blocs dans une fonction d’itérateur. Le `Finally` bloc dans la fonction d’itérateur s’exécute avant le `For Each` fin de l’itération.  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 A `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.  
  
 Si le `For Each` corps (au lieu de la méthode iterator) lève une exception, une `Catch` bloc dans la fonction d’itérateur n’est pas exécuté, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. Un `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.  
  
##  <a name="BKMK_AnonymousMethods"></a>Méthodes anonymes  
 Dans Visual Basic, une fonction anonyme peut être une fonction d’itérateur. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 L’exemple suivant comprend une méthode d’itérateur non valide les arguments. La méthode retourne le résultat d’un itérateur anonyme qui décrit les éléments de collection.  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 Si la validation à la place à l’intérieur de la fonction d’itérateur, la validation ne peut pas être effectuée avant le démarrage de la première itération de la `For Each` corps.  
  
##  <a name="BKMK_GenericList"></a>Utilisation d’itérateurs avec une liste générique  
 Dans l’exemple suivant, la `Stack(Of T)` classe générique implémente la <xref:System.Collections.Generic.IEnumerable%601>interface générique.</xref:System.Collections.Generic.IEnumerable%601> Le `Push` méthode assigne des valeurs à un tableau de type `T`. Le <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>méthode retourne les valeurs de tableau à l’aide de la `Yield` relevé.</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>  
  
 Outre le générique <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>méthode, non générique <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode doit également être implémentée.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> C’est parce que <xref:System.Collections.Generic.IEnumerable%601>hérite <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601> L’implémentation non générique diffère à l’implémentation de générique.  
  
 L’exemple utilise des itérateurs nommés pour prendre en charge différentes méthodes d’itération de la même collection de données. Ces itérateurs sont les `TopToBottom` et `BottomToTop` propriétés et le `TopN` (méthode).  
  
 Le `BottomToTop` déclaration de propriété comprend le `Iterator` (mot clé).  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
  
```  
  
##  <a name="BKMK_SyntaxInformation"></a>Informations sur la syntaxe  
 Un itérateur peut se produire en tant que méthode ou `get` accesseur. Un itérateur ne peut pas se produire dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Une conversion implicite doit exister dans le type d’expression dans la `Yield` instruction pour le type de retour de l’itérateur.  
  
 Dans Visual Basic, une méthode d’itérateur ne peut avoir aucune `ByRef` paramètres.  
  
 Dans Visual Basic, « Générer » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’elle est utilisée dans un `Iterator` méthode ou `get` accesseur.  
  
##  <a name="BKMK_Technical"></a>Implémentation technique  
 Bien que vous écriviez un itérateur comme une méthode, le compilateur traduit en une classe imbriquée qui est, en effet, une machine à états. Cette classe effectue le suivi de la position de l’itérateur tant que la `For Each...Next` boucle dans le code client se poursuit.  
  
 Pour voir ce que fait le compilateur, vous pouvez utiliser l’outil Ildasm.exe pour afficher le code de langage intermédiaire Microsoft généré pour une méthode d’itérateur.  
  
 Lorsque vous créez un itérateur pour un [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), vous n’avez pas à implémenter l’ensemble <xref:System.Collections.IEnumerator>interface.</xref:System.Collections.IEnumerator> Lorsque le compilateur détecte l’itérateur, il génère automatiquement les `Current`, `MoveNext`, et `Dispose` méthodes de la <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>interface.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator>  
  
 À chaque itération successive de la `For Each…Next` boucle (ou l’appel direct à `IEnumerator.MoveNext`), le corps de code itérateur suivant reprend après la précédente `Yield` instruction. Ensuite, il continue à l’autre `Yield` instruction jusqu'à la fin du corps d’itérateur, ou jusqu'à ce qu’un `Exit Function` ou `Return` est rencontrée.  
  
 Itérateurs ne gèrent pas la <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>méthode.</xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName> Pour effectuer une itération nouveau à partir du début, vous devez vous procurer un nouvel itérateur.  
  
 Pour plus d’informations, consultez la [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification.md).  
  
##  <a name="BKMK_UseOfIterators"></a>Utilisation d’itérateurs  
 Itérateurs permettent de maintenir la simplicité d’un `For Each` en boucle lorsque vous avez besoin d’utiliser un code complexe pour remplir une séquence de la liste. Cela peut être utile lorsque vous souhaitez effectuer les opérations suivantes :  
  
-   Modifier l’ordre de la liste après le premier `For Each` itération de boucle.  
  
-   Éviter de charger entièrement une grande liste avant la première itération d’un `For Each` boucle. Une extraction paginée pour charger un lot de lignes de la table est un exemple. Un autre exemple est le <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>(méthode), qui implémente les itérateurs dans le .NET Framework.</xref:System.IO.DirectoryInfo.EnumerateFiles%2A>  
  
-   Encapsuler l’établissement de la liste dans l’itérateur. Dans la méthode de l’itérateur, vous pouvez générer la liste et génère ensuite chaque résultat dans une boucle.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic></xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [For Each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Instruction yield](../../../visual-basic/language-reference/statements/yield-statement.md)   
 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
