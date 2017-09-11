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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="11a0b-104">Analyse d’autres chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="11a0b-104">Parsing other strings in .NET</span></span>

<span data-ttu-id="11a0b-105">Outre des chaînes numériques et [DateTime](xref:System.DateTime), vous pouvez analyser des chaînes qui représentent les types [Char](xref:System.Char), [Boolean](xref:System.Boolean) et [Enum](xref:System.Enum) dans des types de données.</span><span class="sxs-lookup"><span data-stu-id="11a0b-105">In addition to numeric and [DateTime](xref:System.DateTime) strings, you can also parse strings that represent the types [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) into data types.</span></span>

## <a name="char"></a><span data-ttu-id="11a0b-106">Char</span><span class="sxs-lookup"><span data-stu-id="11a0b-106">Char</span></span>

<span data-ttu-id="11a0b-107">La méthode d’analyse statique associée au type de données [Char](xref:System.Char) est utile pour la conversion d’une chaîne qui contient un caractère unique en une valeur Unicode.</span><span class="sxs-lookup"><span data-stu-id="11a0b-107">The static parse method associated with the [Char](xref:System.Char) data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="11a0b-108">L’exemple de code suivant analyse une chaîne en un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="11a0b-108">The following code example parses a string into a Unicode character.</span></span>

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

## <a name="boolean"></a><span data-ttu-id="11a0b-109">Booléen</span><span class="sxs-lookup"><span data-stu-id="11a0b-109">Boolean</span></span>

<span data-ttu-id="11a0b-110">Le type de données [Boolean](xref:System.Boolean) contient une méthode [Parse](xref:System.Boolean.Parse(System.String)) que vous pouvez utiliser pour convertir une chaîne représentant une valeur `Boolean` en type `Boolean` réel.</span><span class="sxs-lookup"><span data-stu-id="11a0b-110">The [Boolean](xref:System.Boolean) data type contains a [Parse](xref:System.Boolean.Parse(System.String)) method that you can use to convert a string that represents a `Boolean` value into an actual `Boolean` type.</span></span> <span data-ttu-id="11a0b-111">Cette méthode ne respecte pas la casse et peut analyser une chaîne contenant « True » ou « False ».</span><span class="sxs-lookup"><span data-stu-id="11a0b-111">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="11a0b-112">La méthode `Parse` associée au type `Boolean` peut aussi analyser des chaînes entourées d’espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="11a0b-112">The `Parse` method associated with the `Boolean` type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="11a0b-113">Si une autre chaîne est passée, une [FormatException](xref:System.FormatException) est levée.</span><span class="sxs-lookup"><span data-stu-id="11a0b-113">If any other string is passed, a [FormatException](xref:System.FormatException) is thrown.</span></span>

<span data-ttu-id="11a0b-114">L’exemple de code suivant utilise la méthode `Parse` pour convertir une chaîne en valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="11a0b-114">The following code example uses the `Parse` method to convert a string into a `Boolean` value.</span></span>

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

## <a name="enumeration"></a><span data-ttu-id="11a0b-115">Énumération</span><span class="sxs-lookup"><span data-stu-id="11a0b-115">Enumeration</span></span>

<span data-ttu-id="11a0b-116">Vous pouvez utiliser la méthode [Parse](xref:System.Enum.Parse(System.Type,System.String)) statique pour initialiser un type d’énumération avec la valeur d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="11a0b-116">You can use the static [Parse](xref:System.Enum.Parse(System.Type,System.String)) method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="11a0b-117">Cette méthode accepte le type d’énumération que vous analysez, la chaîne à analyser et un indicateur `Boolean` facultatif indiquant si l’analyse respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="11a0b-117">This method accepts the enumeration type you are parsing, the string to parse, and an optional `Boolean` flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="11a0b-118">La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d’un ou plusieurs espaces vides (aussi appelés espaces blancs).</span><span class="sxs-lookup"><span data-stu-id="11a0b-118">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="11a0b-119">Quand la chaîne contient plusieurs valeurs, celle de l’objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération OR au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="11a0b-119">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>

<span data-ttu-id="11a0b-120">L’exemple suivant utilise la méthode `Parse` pour convertir une représentation sous forme de chaîne en valeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="11a0b-120">The following example uses the `Parse` method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="11a0b-121">L’énumération [DayOfWeek](xref:System.DayOfWeek) est initialisée à Thursday à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="11a0b-121">The [DayOfWeek](xref:System.DayOfWeek) enumeration is initialized to Thursday from a string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="11a0b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11a0b-122">See Also</span></span>

[<span data-ttu-id="11a0b-123">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="11a0b-123">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="11a0b-124">Mise en forme des types dans .NET</span><span class="sxs-lookup"><span data-stu-id="11a0b-124">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="11a0b-125">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="11a0b-125">Type conversion in .NET</span></span>](type-conversion.md)


