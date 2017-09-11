---
title: "Remplissage de chaînes"
description: "Remplissage de chaînes"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: bc3cc9028b232cc2ba6ca3130c4bdb261c4a0a42
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="padding-strings"></a><span data-ttu-id="10a07-104">Remplissage de chaînes</span><span class="sxs-lookup"><span data-stu-id="10a07-104">Padding strings</span></span>

<span data-ttu-id="10a07-105">Utilisez une des méthodes [System.String](xref:System.String) suivantes pour créer une chaîne qui se compose d’une chaîne d’origine remplie à l’aide de caractères de début ou de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10a07-105">Use one of the following [System.String](xref:System.String) methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="10a07-106">Le caractère de remplissage peut être un espace ou un caractère spécifié ; il apparaît donc aligné à droite ou aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="10a07-106">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>

<span data-ttu-id="10a07-107">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="10a07-107">Method name</span></span> | <span data-ttu-id="10a07-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="10a07-108">Use</span></span>
----------- | ---
<span data-ttu-id="10a07-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="10a07-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span></span> | <span data-ttu-id="10a07-110">Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10a07-110">Pads a string with leading characters to a specified total length.</span></span>
<span data-ttu-id="10a07-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="10a07-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span></span> | <span data-ttu-id="10a07-112">Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10a07-112">Pads a string with trailing characters to a specified total length.</span></span>

## <a name="padleft"></a><span data-ttu-id="10a07-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="10a07-113">PadLeft</span></span>

<span data-ttu-id="10a07-114">La méthode [String.PadLeft](xref:System.String.PadLeft(System.Int32)) crée une chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10a07-114">The [String.PadLeft](xref:System.String.PadLeft(System.Int32)) method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="10a07-115">La méthode [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) utilise l’espace blanc comme caractère de remplissage et la méthode [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="10a07-115">The [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) method uses white space as the padding character and the [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="10a07-116">L’exemple de code suivant utilise la méthode [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="10a07-116">The following code example uses the [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="10a07-117">L’exemple affiche « `--------Hello World!` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="10a07-117">The example displays "`--------Hello World!`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a><span data-ttu-id="10a07-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="10a07-118">PadRight</span></span>

<span data-ttu-id="10a07-119">La méthode [String.PadRight](xref:System.String.PadRight(System.Int32)) crée une chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10a07-119">The [String.PadRight](xref:System.String.PadRight(System.Int32)) method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="10a07-120">La méthode [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) utilise l’espace blanc comme caractère de remplissage et la méthode [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="10a07-120">The [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) method uses white space as the padding character and the [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="10a07-121">L’exemple de code suivant utilise la méthode [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="10a07-121">The following code example uses the [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="10a07-122">L’exemple affiche « `Hello World!--------` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="10a07-122">The example displays "`Hello World!--------`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a><span data-ttu-id="10a07-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10a07-123">See Also</span></span>

[<span data-ttu-id="10a07-124">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="10a07-124">Basic string operations</span></span>](basic-string-operations.md)


