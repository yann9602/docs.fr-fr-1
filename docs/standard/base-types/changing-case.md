---
title: Changement de casse
description: Changement de casse
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 023f40969095627242d3652add853eb999c30c4b
ms.lasthandoff: 03/13/2017

---

# <a name="changing-case"></a>Changement de casse

Si vous écrivez une application qui accepte l'entrée d'un utilisateur, vous ne pouvez jamais être sûr de la casse qu'il utilisera pour entrer les données. Souvent, vous voulez que les chaînes aient une casse cohérente, en particulier si vous les affichez dans l'interface utilisateur. Le tableau suivant décrit deux méthodes de changement de casse.

Nom de la méthode | Utilisation
----------- | ---
[String.ToUpper](xref:System.String.ToUpper) | Convertit tous les caractères d'une chaîne en majuscules.
[String.ToLower](xref:System.String.ToLower) | Convertit tous les caractères d'une chaîne en minuscules.

> [!WARNING]  
> Notez que les méthodes `String.ToUpper` et `String.ToLower` ne doivent pas être utilisées pour convertir des chaînes pour les comparer ou pour tester leur égalité. 

## <a name="comparing-strings-of-mixed-case"></a>Comparaison de chaînes de casse mixte

Pour comparer des chaînes de casse mixte et déterminer si elles sont égales, appelez l’une de leurs surcharges de la méthode [String](xref:System) `Equals` avec un paramètre *comparisonType*, puis indiquez une valeur [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) pour l’argument *comparisonType*. 

Pour plus d’informations, consultez [Bonnes pratiques l’utilisation de chaînes](best-practices.md). 

## <a name="toupper"></a>ToUpper

La méthode [String.ToUpper](xref:System.String.ToUpper) change tous les caractères d’une chaîne en majuscules. L’exemple suivant convertit la chaîne « Hello World! » d’une casse mixte en majuscules.

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a>ToLower

La méthode [String.ToLower](xref:System.String.ToLower) est similaire à la méthode précédente, mais elle convertit tous les caractères d’une chaîne en minuscules. L’exemple suivant convertit la chaîne « Hello World! » en minuscules.

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a>Voir aussi

[Opérations de chaînes de base](basic-string-operations.md)

