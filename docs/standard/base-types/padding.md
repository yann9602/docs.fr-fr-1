---
title: "Remplissage de chaînes"
description: "Remplissage de chaînes"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: b6c5d4c8a35aebdfca88801118cdeba25c0a7e65

---

# <a name="padding-strings"></a>Remplissage de chaînes

Utilisez une des méthodes [System.String](xref:System.String) suivantes pour créer une chaîne qui se compose d’une chaîne d’origine remplie à l’aide de caractères de début ou de fin sur une longueur totale spécifiée. Le caractère de remplissage peut être un espace ou un caractère spécifié ; il apparaît donc aligné à droite ou aligné à gauche.

Nom de la méthode | Utilisation
----------- | ---
[String.PadLeft](xref:System.String.PadLeft(System.Int32)) | Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.
[String.PadRight](xref:System.String.PadRight(System.Int32)) | Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.

## <a name="padleft"></a>PadLeft

La méthode [String.PadLeft](xref:System.String.PadLeft(System.Int32)) crée une chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d’origine pour atteindre une longueur totale spécifiée. La méthode [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) utilise l’espace blanc comme caractère de remplissage et la méthode [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) vous permet de spécifier votre propre caractère de remplissage.

L’exemple de code suivant utilise la méthode [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) pour créer une chaîne longue de vingt caractères. L’exemple affiche « `--------Hello World!` » sur la console.

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a>PadRight

La méthode [String.PadRight](xref:System.String.PadRight(System.Int32)) crée une chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée. La méthode [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) utilise l’espace blanc comme caractère de remplissage et la méthode [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) vous permet de spécifier votre propre caractère de remplissage.

L’exemple de code suivant utilise la méthode [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) pour créer une chaîne longue de vingt caractères. L’exemple affiche « `Hello World!--------` » sur la console.

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a>Voir aussi

[Opérations de chaînes de base](basic-string-operations.md)




<!--HONumber=Nov16_HO3-->


