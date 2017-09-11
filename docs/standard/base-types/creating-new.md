---
title: "Création de nouvelles chaînes"
description: "Création de nouvelles chaînes"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 639397c7-e694-43e0-845b-1681c62bd9fd
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="creating-new-strings"></a><span data-ttu-id="e248e-104">Création de nouvelles chaînes</span><span class="sxs-lookup"><span data-stu-id="e248e-104">Creating new strings</span></span>

<span data-ttu-id="e248e-105">Le .NET permet de créer des chaînes à l’aide d’une assignation simple, et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide de plusieurs paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="e248e-105">.NET  allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="e248e-106">Le .NET fournit également plusieurs méthodes dans la classe [System.String](xref:System.String) qui créent des objets String en combinant plusieurs chaînes, tableaux de chaînes ou objets.</span><span class="sxs-lookup"><span data-stu-id="e248e-106">.NET also provides several methods in the [System.String](xref:System.String) class that create new string objects by combining several strings, arrays of strings, or objects.</span></span> 

## <a name="creating-strings-using-assignment"></a><span data-ttu-id="e248e-107">Création de chaînes à l’aide d’une affectation</span><span class="sxs-lookup"><span data-stu-id="e248e-107">Creating Strings Using Assignment</span></span>

<span data-ttu-id="e248e-108">Le moyen le plus simple de créer un objet [String](xref:System.String) consiste à assigner un littéral de chaîne à un objet [String](xref:System.String).</span><span class="sxs-lookup"><span data-stu-id="e248e-108">The easiest way to create a new [String](xref:System.String) object is simply to assign a string literal to a [String](xref:System.String) object.</span></span> 

## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="e248e-109">Création de chaînes à l’aide d’un constructeur de classe</span><span class="sxs-lookup"><span data-stu-id="e248e-109">Creating Strings Using a Class Constructor</span></span>

<span data-ttu-id="e248e-110">Vous pouvez utiliser des surcharges du constructeur de classe [String](xref:System.String) pour créer des chaînes à partir de tableaux de caractères.</span><span class="sxs-lookup"><span data-stu-id="e248e-110">You can use overloads of the [String](xref:System.String) class constructor to create strings from character arrays.</span></span> <span data-ttu-id="e248e-111">Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.</span><span class="sxs-lookup"><span data-stu-id="e248e-111">You can also create a new string by duplicating a particular character a specified number of times.</span></span> 

## <a name="methods-that-return-strings"></a><span data-ttu-id="e248e-112">Méthodes retournant des chaînes</span><span class="sxs-lookup"><span data-stu-id="e248e-112">Methods that Return Strings</span></span>

<span data-ttu-id="e248e-113">Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.</span><span class="sxs-lookup"><span data-stu-id="e248e-113">The following table lists several useful methods that return new string objects.</span></span>

<span data-ttu-id="e248e-114">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="e248e-114">Method name</span></span> | <span data-ttu-id="e248e-115">Utilisation</span><span class="sxs-lookup"><span data-stu-id="e248e-115">Use</span></span>
----------- | ---
<span data-ttu-id="e248e-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="e248e-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span></span> | <span data-ttu-id="e248e-117">Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="e248e-117">Builds a formatted string from a set of input objects.</span></span>
<span data-ttu-id="e248e-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span><span class="sxs-lookup"><span data-stu-id="e248e-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span></span> | <span data-ttu-id="e248e-119">Génère des chaînes à partir de deux ou de plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="e248e-119">Builds strings from two or more strings.</span></span>
<span data-ttu-id="e248e-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span><span class="sxs-lookup"><span data-stu-id="e248e-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span></span> |<span data-ttu-id="e248e-121">Génère une nouvelle chaîne en combinant un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e248e-121">Builds a new string by combining an array of strings.</span></span>
<span data-ttu-id="e248e-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span><span class="sxs-lookup"><span data-stu-id="e248e-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span></span> | <span data-ttu-id="e248e-123">Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.</span><span class="sxs-lookup"><span data-stu-id="e248e-123">Builds a new string by inserting a string into the specified index of an existing string.</span></span>
<span data-ttu-id="e248e-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e248e-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span></span> | <span data-ttu-id="e248e-125">Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="e248e-125">Copies specified characters in a string into a specified position in an array of characters.</span></span>

### <a name="format"></a><span data-ttu-id="e248e-126">Format</span><span class="sxs-lookup"><span data-stu-id="e248e-126">Format</span></span>

<span data-ttu-id="e248e-127">Vous pouvez utiliser la méthode `String.Format` pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="e248e-127">You can use the `String.Format` method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="e248e-128">Cette méthode convertit automatiquement tout objet passé en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e248e-128">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="e248e-129">Par exemple, si votre application doit afficher une valeur [Int32](xref:System.Int32) et une valeur [DateTime](xref:System.DateTime) à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la méthode `Format`.</span><span class="sxs-lookup"><span data-stu-id="e248e-129">For example, if your application must display an [Int32](xref:System.Int32) value and a [DateTime](xref:System.DateTime) value to the user, you can easily construct a string to represent these values using the `Format` method.</span></span> <span data-ttu-id="e248e-130">Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](composite-format.md).</span><span class="sxs-lookup"><span data-stu-id="e248e-130">For information about formatting conventions used with this method, see the section on [composite formatting](composite-format.md).</span></span>

<span data-ttu-id="e248e-131">L’exemple suivant utilise la méthode `Format` pour créer une chaîne utilisant une variable de type integer.</span><span class="sxs-lookup"><span data-stu-id="e248e-131">The following example uses the `Format` method to create a string that uses an integer variable.</span></span>

```csharp
int numberOfFleas = 12;
string miscInfo = String.Format("Your dog has {0} fleas. " +
                                "It is time to get a flea collar. " + 
                                "The current universal date is: {1:u}.", 
                                numberOfFleas, DateTime.Now);
Console.WriteLine(miscInfo);
// The example displays the following output:
//       Your dog has 12 fleas. It is time to get a flea collar. 
//       The current universal date is: 2008-03-28 13:31:40Z.
```

```vb
Dim numberOfFleas As Integer = 12
Dim miscInfo As String = String.Format("Your dog has {0} fleas. " & _
                                       "It is time to get a flea collar. " & _ 
                                       "The current universal date is: {1:u}.", _ 
                                       numberOfFleas, Date.Now)
Console.WriteLine(miscInfo)
' The example displays the following output:
'       Your dog has 12 fleas. It is time to get a flea collar. 
'       The current universal date is: 2008-03-28 13:31:40Z.
```

<span data-ttu-id="e248e-132">Dans cet exemple, [DateTime.Now](xref:System.DateTime.Now) affiche la date et l’heure actuelles de la manière spécifiée par la culture associée au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="e248e-132">In this example, [DateTime.Now](xref:System.DateTime.Now) displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>

### <a name="concat"></a><span data-ttu-id="e248e-133">Concat</span><span class="sxs-lookup"><span data-stu-id="e248e-133">Concat</span></span>

<span data-ttu-id="e248e-134">La méthode `String.Concat` peut être utilisée pour créer facilement un objet chaîne à partir de deux ou de plusieurs objets existants.</span><span class="sxs-lookup"><span data-stu-id="e248e-134">The `String.Concat` method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="e248e-135">Elle offre un moyen de concaténer des chaînes indépendamment du langage.</span><span class="sxs-lookup"><span data-stu-id="e248e-135">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="e248e-136">Cette méthode accepte toute classe qui dérive de `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="e248e-136">This method accepts any class that derives from `System.Object`.</span></span> <span data-ttu-id="e248e-137">L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="e248e-137">The following example creates a string from two existing string objects and a separating character.</span></span>

```csharp
string helloString1 = "Hello";
string helloString2 = "World!";
Console.WriteLine(String.Concat(helloString1, ' ', helloString2));
// The example displays the following output:
//      Hello World!
```

```vb
Dim helloString1 As String = "Hello"
Dim helloString2 As String = "World!"
Console.WriteLine(String.Concat(helloString1, " "c, helloString2))
' The example displays the following output:
'      Hello World!
```

### <a name="join"></a><span data-ttu-id="e248e-138">Join</span><span class="sxs-lookup"><span data-stu-id="e248e-138">Join</span></span>

<span data-ttu-id="e248e-139">La méthode `String.Join` crée une chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="e248e-139">The `String.Join` method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="e248e-140">Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e248e-140">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>

<span data-ttu-id="e248e-141">L’exemple suivant utilise un espace pour lier un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e248e-141">The following example uses a space to bind a string array.</span></span>

```csharp
string[] words = {"Hello", "and", "welcome", "to", "my" , "world!"};
Console.WriteLine(String.Join(" ", words));
// The example displays the following output:
//      Hello and welcome to my world!
```

```vb
Dim words() As String = {"Hello", "and", "welcome", "to", "my" , "world!"}
Console.WriteLine(String.Join(" ", words))
' The example displays the following output:
'      Hello and welcome to my world!
```

### <a name="insert"></a><span data-ttu-id="e248e-142">Insert</span><span class="sxs-lookup"><span data-stu-id="e248e-142">Insert</span></span>

<span data-ttu-id="e248e-143">La méthode `String.Insert` crée une chaîne en insérant une chaîne à une position spécifiée dans une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="e248e-143">The `String.Insert` method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="e248e-144">Cette méthode utilise un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="e248e-144">This method uses a zero-based index.</span></span> <span data-ttu-id="e248e-145">L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.</span><span class="sxs-lookup"><span data-stu-id="e248e-145">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>

```csharp
string sentence = "Once a time.";   
 Console.WriteLine(sentence.Insert(4, " upon"));
 // The example displays the following output:
 //      Once upon a time.
```

```vb
Dim sentence As String = "Once a time."   
 Console.WriteLine(sentence.Insert(4, " upon"))
 ' The example displays the 
```

### <a name="copyto"></a><span data-ttu-id="e248e-146">CopyTo</span><span class="sxs-lookup"><span data-stu-id="e248e-146">CopyTo</span></span>

<span data-ttu-id="e248e-147">La méthode `String.CopyTo`copie des fragments d’une chaîne dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="e248e-147">The `String.CopyTo` method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="e248e-148">Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="e248e-148">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="e248e-149">Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="e248e-149">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="e248e-150">Tous les index sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="e248e-150">All indexes are zero-based.</span></span>

<span data-ttu-id="e248e-151">L’exemple suivant utilise la méthode `CopyTo` pour copier les caractères du mot « Hello » d’un objet String vers la première position d’un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="e248e-151">The following example uses the `CopyTo` method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>

```csharp
string greeting = "Hello World!";
char[] charArray = {'W','h','e','r','e'};
Console.WriteLine("The original character array: {0}", new string(charArray));
greeting.CopyTo(0, charArray,0 ,5);
Console.WriteLine("The new character array: {0}", new string(charArray));
// The example displays the following output:
//       The original character array: Where
//       The new character array: Hello
```

```vb
Dim greeting As String = "Hello World!"
Dim charArray() As Char = {"W"c, "h"c, "e"c, "r"c, "e"c}
Console.WriteLine("The original character array: {0}", New String(charArray))
greeting.CopyTo(0, charArray,0 ,5)
Console.WriteLine("The new character array: {0}", New String(charArray))
' The example displays the following output:
'       The original character array: Where
'       The new character array: Hello
```

## <a name="see-also"></a><span data-ttu-id="e248e-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e248e-152">See Also</span></span>

[<span data-ttu-id="e248e-153">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="e248e-153">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="e248e-154">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="e248e-154">Composite formatting</span></span>](composite-format.md)


