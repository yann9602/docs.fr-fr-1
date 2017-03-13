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
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.lasthandoff: 03/13/2017

---

# <a name="creating-new-strings"></a>Création de nouvelles chaînes

Le .NET permet de créer des chaînes à l’aide d’une assignation simple, et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide de plusieurs paramètres différents. Le .NET fournit également plusieurs méthodes dans la classe [System.String](xref:System.String) qui créent des objets String en combinant plusieurs chaînes, tableaux de chaînes ou objets. 

## <a name="creating-strings-using-assignment"></a>Création de chaînes à l’aide d’une affectation

Le moyen le plus simple de créer un objet [String](xref:System.String) consiste à assigner un littéral de chaîne à un objet [String](xref:System.String). 

## <a name="creating-strings-using-a-class-constructor"></a>Création de chaînes à l’aide d’un constructeur de classe

Vous pouvez utiliser des surcharges du constructeur de classe [String](xref:System.String) pour créer des chaînes à partir de tableaux de caractères. Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois. 

## <a name="methods-that-return-strings"></a>Méthodes retournant des chaînes

Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.

Nom de la méthode | Utilisation
----------- | ---
[String.Format](xref:System.String.Format(System.String,System.Object)) | Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.
[String.Concat](xref:System.String.Concat(System.String,System.String)) | Génère des chaînes à partir de deux ou de plusieurs chaînes.
[String.Join](xref:System.String.Join(System.String,System.String[])) |Génère une nouvelle chaîne en combinant un tableau de chaînes.
[String.Insert](xref:System.String.Insert(System.Int32,System.String)) | Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.
[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32)) | Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.

### <a name="format"></a>Format

Vous pouvez utiliser la méthode `String.Format` pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets. Cette méthode convertit automatiquement tout objet passé en une chaîne. Par exemple, si votre application doit afficher une valeur [Int32](xref:System.Int32) et une valeur [DateTime](xref:System.DateTime) à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la méthode `Format`. Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](composite-format.md).

L’exemple suivant utilise la méthode `Format` pour créer une chaîne utilisant une variable de type integer.

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

Dans cet exemple, [DateTime.Now](xref:System.DateTime.Now) affiche la date et l’heure actuelles de la manière spécifiée par la culture associée au thread actuel.

### <a name="concat"></a>Concat

La méthode `String.Concat` peut être utilisée pour créer facilement un objet chaîne à partir de deux ou de plusieurs objets existants. Elle offre un moyen de concaténer des chaînes indépendamment du langage. Cette méthode accepte toute classe qui dérive de `System.Object`. L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.

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

### <a name="join"></a>Join

La méthode `String.Join` crée une chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation. Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.

L’exemple suivant utilise un espace pour lier un tableau de chaînes.

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

### <a name="insert"></a>Insert

La méthode `String.Insert` crée une chaîne en insérant une chaîne à une position spécifiée dans une autre chaîne. Cette méthode utilise un index de base zéro. L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.

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

### <a name="copyto"></a>CopyTo

La méthode `String.CopyTo`copie des fragments d’une chaîne dans un tableau de caractères. Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier. Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier. Tous les index sont de base zéro.

L’exemple suivant utilise la méthode `CopyTo` pour copier les caractères du mot « Hello » d’un objet String vers la première position d’un tableau de caractères.

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

## <a name="see-also"></a>Voir aussi

[Opérations de chaînes de base](basic-string-operations.md)

[Mise en forme composite](composite-format.md)


