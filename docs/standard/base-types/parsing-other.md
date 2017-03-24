---
title: "Analyse d’autres chaînes dans .NET"
description: "Analyse d’autres chaînes dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 67670b10-3df4-45ea-8908-5ba3f056887c
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-other-strings-in-net"></a>Analyse d’autres chaînes dans .NET

Outre des chaînes numériques et [DateTime](xref:System.DateTime), vous pouvez analyser des chaînes qui représentent les types [Char](xref:System.Char), [Boolean](xref:System.Boolean) et [Enum](xref:System.Enum) dans des types de données.

## <a name="char"></a>Char

La méthode d’analyse statique associée au type de données [Char](xref:System.Char) est utile pour la conversion d’une chaîne qui contient un caractère unique en une valeur Unicode. L’exemple de code suivant analyse une chaîne en un caractère Unicode.

```csharp
string MyString1 = "A";
char MyChar = Char.Parse(MyString1);
// MyChar now contains a Unicode "A" character.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="boolean"></a>Booléen

Le type de données [Boolean](xref:System.Boolean) contient une méthode [Parse](xref:System.Boolean.Parse(System.String)) que vous pouvez utiliser pour convertir une chaîne représentant une valeur `Boolean` en type `Boolean` réel. Cette méthode ne respecte pas la casse et peut analyser une chaîne contenant « True » ou « False ». La méthode `Parse` associée au type `Boolean` peut aussi analyser des chaînes entourées d’espaces blancs. Si une autre chaîne est passée, une [FormatException](xref:System.FormatException) est levée.

L’exemple de code suivant utilise la méthode `Parse` pour convertir une chaîne en valeur `Boolean`.

```csharp
string MyString2 = "True";
bool MyBool = bool.Parse(MyString2);
// MyBool now contains a True Boolean value.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="enumeration"></a>Énumération

Vous pouvez utiliser la méthode [Parse](xref:System.Enum.Parse(System.Type,System.String)) statique pour initialiser un type d’énumération avec la valeur d’une chaîne. Cette méthode accepte le type d’énumération que vous analysez, la chaîne à analyser et un indicateur `Boolean` facultatif indiquant si l’analyse respecte la casse. La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d’un ou plusieurs espaces vides (aussi appelés espaces blancs). Quand la chaîne contient plusieurs valeurs, celle de l’objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération OR au niveau du bit.

L’exemple suivant utilise la méthode `Parse` pour convertir une représentation sous forme de chaîne en valeur d’énumération. L’énumération [DayOfWeek](xref:System.DayOfWeek) est initialisée à Thursday à partir d’une chaîne.

```csharp
string MyString3 = "Thursday";
DayOfWeek MyDays = (DayOfWeek)Enum.Parse(typeof(DayOfWeek), MyString3);
Console.WriteLine(MyDays);
// The result is Thursday.
```

```vb
Dim MyString3 As String = "Thursday"
Dim MyDays As DayOfWeek = CType([Enum].Parse(GetType(DayOfWeek), MyString3), DayOfWeek)
Console.WriteLine("{0:G}", MyDays)
' The result is Thursday.
```

## <a name="see-also"></a>Voir aussi

[Analyse de chaînes dans .NET](parsing-strings.md)

[Mise en forme des types dans .NET](formatting-types.md)

[Conversion de type dans .NET](type-conversion.md)


