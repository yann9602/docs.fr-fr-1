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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 023f40969095627242d3652add853eb999c30c4b
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="changing-case"></a><span data-ttu-id="3fe30-104">Changement de casse</span><span class="sxs-lookup"><span data-stu-id="3fe30-104">Changing case</span></span>

<span data-ttu-id="3fe30-105">Si vous écrivez une application qui accepte l'entrée d'un utilisateur, vous ne pouvez jamais être sûr de la casse qu'il utilisera pour entrer les données.</span><span class="sxs-lookup"><span data-stu-id="3fe30-105">If you write an application that accepts input from a user, you can never be sure what case he or she will use to enter the data.</span></span> <span data-ttu-id="3fe30-106">Souvent, vous voulez que les chaînes aient une casse cohérente, en particulier si vous les affichez dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3fe30-106">Often, you want strings to be cased consistently, particularly if you are displaying them in the user interface.</span></span> <span data-ttu-id="3fe30-107">Le tableau suivant décrit deux méthodes de changement de casse.</span><span class="sxs-lookup"><span data-stu-id="3fe30-107">The following table describes two case-changing methods.</span></span>

<span data-ttu-id="3fe30-108">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="3fe30-108">Method name</span></span> | <span data-ttu-id="3fe30-109">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3fe30-109">Use</span></span>
----------- | ---
[<span data-ttu-id="3fe30-110">String.ToUpper</span><span class="sxs-lookup"><span data-stu-id="3fe30-110">String.ToUpper</span></span>](xref:System.String.ToUpper) | <span data-ttu-id="3fe30-111">Convertit tous les caractères d'une chaîne en majuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-111">Converts all characters in a string to uppercase.</span></span>
[<span data-ttu-id="3fe30-112">String.ToLower</span><span class="sxs-lookup"><span data-stu-id="3fe30-112">String.ToLower</span></span>](xref:System.String.ToLower) | <span data-ttu-id="3fe30-113">Convertit tous les caractères d'une chaîne en minuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-113">Converts all characters in a string to lowercase.</span></span>

> [!WARNING]  
> <span data-ttu-id="3fe30-114">Notez que les méthodes `String.ToUpper` et `String.ToLower` ne doivent pas être utilisées pour convertir des chaînes pour les comparer ou pour tester leur égalité.</span><span class="sxs-lookup"><span data-stu-id="3fe30-114">Note that the `String.ToUpper` and `String.ToLower` methods should not be used to convert strings in order to compare them or test them for equality.</span></span> 

## <a name="comparing-strings-of-mixed-case"></a><span data-ttu-id="3fe30-115">Comparaison de chaînes de casse mixte</span><span class="sxs-lookup"><span data-stu-id="3fe30-115">Comparing strings of mixed case</span></span>

<span data-ttu-id="3fe30-116">Pour comparer des chaînes de casse mixte et déterminer si elles sont égales, appelez l’une de leurs surcharges de la méthode [String](xref:System) `Equals` avec un paramètre *comparisonType*, puis indiquez une valeur [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) pour l’argument *comparisonType*.</span><span class="sxs-lookup"><span data-stu-id="3fe30-116">To compare strings of mixed case to determine whether they are equal, their, call one of the overloads of the [String](xref:System) `Equals` method with a *comparisonType* parameter, and provide a value of either [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for the *comparisonType* argument.</span></span> 

<span data-ttu-id="3fe30-117">Pour plus d’informations, consultez [Bonnes pratiques l’utilisation de chaînes](best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="3fe30-117">For more information, see [Best Practices for Using Strings](best-practices.md).</span></span> 

## <a name="toupper"></a><span data-ttu-id="3fe30-118">ToUpper</span><span class="sxs-lookup"><span data-stu-id="3fe30-118">ToUpper</span></span>

<span data-ttu-id="3fe30-119">La méthode [String.ToUpper](xref:System.String.ToUpper) change tous les caractères d’une chaîne en majuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-119">The [String.ToUpper](xref:System.String.ToUpper) method changes all characters in a string to uppercase.</span></span> <span data-ttu-id="3fe30-120">L’exemple suivant convertit la chaîne « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="3fe30-120">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="3fe30-121">d’une casse mixte en majuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-121">from mixed case to uppercase.</span></span>

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

## <a name="tolower"></a><span data-ttu-id="3fe30-122">ToLower</span><span class="sxs-lookup"><span data-stu-id="3fe30-122">ToLower</span></span>

<span data-ttu-id="3fe30-123">La méthode [String.ToLower](xref:System.String.ToLower) est similaire à la méthode précédente, mais elle convertit tous les caractères d’une chaîne en minuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-123">The [String.ToLower](xref:System.String.ToLower) method is similar to the previous method, but instead converts all the characters in a string to lowercase.</span></span> <span data-ttu-id="3fe30-124">L’exemple suivant convertit la chaîne « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="3fe30-124">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="3fe30-125">en minuscules.</span><span class="sxs-lookup"><span data-stu-id="3fe30-125">to lowercase.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3fe30-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fe30-126">See Also</span></span>

[<span data-ttu-id="3fe30-127">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="3fe30-127">Basic string operations</span></span>](basic-string-operations.md)

