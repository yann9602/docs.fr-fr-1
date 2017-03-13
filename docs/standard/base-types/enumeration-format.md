---
title: "Chaînes de format d’énumération"
description: "Chaînes de format d’énumération"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 4d581898-99bc-42c3-816c-d8238f45096f
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 804884f75eb30764c0b8aaf2c8cd115029811157
ms.lasthandoff: 03/13/2017

---

# <a name="enumeration-format-strings"></a>Chaînes de format d’énumération

Vous pouvez utiliser la méthode [Enum.ToString](xref:System.Enum.ToString) pour créer un objet de chaîne qui représente la valeur numérique, hexadécimale ou de chaîne d’un membre d’énumération. Cette méthode prend l’une des chaînes de mise en forme d’énumération pour spécifier la valeur à retourner.

Les sections suivantes répertorient les chaînes de mise en forme d’énumération et les valeurs qu’elles retournent. Ces spécificateurs de format ne respectent pas la casse.

## <a name="the-g-or-g-format-strings"></a>Chaînes de format G ou g

Les chaînes de format G ou g affichent l’entrée d’énumération comme valeur de chaîne, dans la mesure du possible ; sinon, elles affichent la valeur entière de l’instance actuelle. Si l’énumération est définie avec l’attribut `Flags` défini, les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules. Si l’attribut `Flags` n’est pas défini, une valeur non valide s’affiche comme entrée numérique. L’exemple suivant illustre le spécificateur de format G.

```csharp
Console.WriteLine(ConsoleColor.Red.ToString("G"));         // Displays Red
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("G"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Red.ToString("G"))           ' Displays Red
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("G"))     ' Displays Hidden, Archive
```

## <a name="the-f-or-f-format-strings"></a>Chaînes de format F ou f

Les chaînes de format F ou f affichent l’entrée d’énumération comme valeur de chaîne, si possible. Si la valeur peut être complètement affichée comme somme des entrées de l’énumération (même si l’attribut `Flags` n’est pas présent), les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules. Si la valeur ne peut pas être complètement déterminée par les entrées de l’énumération, la valeur est mise en forme comme valeur entière. L’exemple suivant illustre le spécificateur de format F.

```csharp
Console.WriteLine(ConsoleColor.Blue.ToString("F"));       // Displays Blue
FileAttributes attributes = FileAttributes.Hidden | 
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("F"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Blue.ToString("F"))         ' Displays Blue
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("F"))     ' Displays Hidden, Archive
```

## <a name="the-d-or-d-format-strings"></a>Chaînes de format D ou d

Les chaînes de format D ou d affichent l’entrée d’énumération comme valeur entière dans la représentation la plus courte possible. L’exemple suivant illustre le spécificateur de format D.

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("D"));         // Displays 11
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("D"));                // Displays 34
````

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("D"))           ' Displays 11
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("D"))                  ' Displays 34 
```

## <a name="the-x-or-x-format-strings"></a>Chaînes de format X ou x

Les chaînes de format X ou x affichent l’entrée d’énumération comme valeur hexadécimale. La valeur est représentée avec des zéros non significatifs, afin qu’elle comporte au minimum huit chiffres. L’exemple suivant illustre le spécificateur de format X.

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("X"));   // Displays 0000000B
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("X"));          // Displays 00000022
```

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("X"))     ' Displays 0000000B
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("X"))            ' Displays 00000022 
```

## <a name="example"></a>Exemple

L’exemple suivant définit une énumération appelée `Colors` qui se compose de trois entrées : `Red`, `Blue` et `Green`.

 ```csharp
 public enum Color {Red = 1, Blue = 2, Green = 3}
```

```vb
Public Enum Color
   Red = 1
   Blue = 2
   Green = 3
End Enum
```

Une fois que l’énumération est définie, une instance peut être déclarée de la manière suivante.

```csharp
Color myColor = Color.Green;
```

```vb
Dim myColor As Color = Color.Green
```

La méthode `Color.ToString(System.String)` peut ensuite être utilisée pour afficher la valeur d’énumération de différentes manières, selon le spécificateur de format qui lui est passé.

```csharp
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("G"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("F"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("D"));
Console.WriteLine("The value of myColor is 0x{0}.", 
                  myColor.ToString("X"));
// The example displays the following output to the console:
//       The value of myColor is Green.
//       The value of myColor is Green.
//       The value of myColor is 3.
//       The value of myColor is 0x00000003.
```

```vb
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("G"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("F"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("D"))
Console.WriteLine("The value of myColor is 0x{0}.", _
                  myColor.ToString("X"))
' The example displays the following output to the console:
'       The value of myColor is Green.
'       The value of myColor is Green.
'       The value of myColor is 3.
'       The value of myColor is 0x00000003. 
```

## <a name="see-also"></a>Voir aussi

[Mise en forme des types](formatting-types.md)


