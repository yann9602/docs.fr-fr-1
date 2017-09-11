---
title: "Analyse de chaînes dans .NET"
description: "Analyse de chaînes dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-strings-in-net"></a><span data-ttu-id="d9002-104">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="d9002-104">Parsing strings in .NET</span></span>

<span data-ttu-id="d9002-105">Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="d9002-105">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="d9002-106">Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="d9002-106">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="d9002-107">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="d9002-107">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="d9002-108">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="d9002-108">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="d9002-109">Tout comme la mise en forme utilise un objet qui implémente l’interface [IFormatProvider](xref:System.IFormatProvider) pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface [IFormatProvider](xref:System.IFormatProvider) pour déterminer comment interpréter une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d9002-109">Just as formatting uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to provide culture-sensitive formatting information, parsing also uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="d9002-110">Pour plus d’informations, consultez [Mise en forme des types dans .NET](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d9002-110">For more information, see [Formatting Types in .NET](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d9002-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d9002-111">In This Section</span></span>

<span data-ttu-id="d9002-112">[Analyse de chaînes numériques dans .NET](parsing-numeric.md) : explique comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="d9002-112">[Parsing Numeric Strings in .NET](parsing-numeric.md) - Describes how to convert strings into .NET numeric types.</span></span>

<span data-ttu-id="d9002-113">[Analyse des chaînes de date et d’heure dans .NET](parsing-datetime.md) : explique comment convertir des chaînes en types `DateTime` .NET.</span><span class="sxs-lookup"><span data-stu-id="d9002-113">[Parsing Date and Time Strings in .NET](parsing-datetime.md) - Describes how to convert strings into .NET `DateTime` types.</span></span>

<span data-ttu-id="d9002-114">[Analyse d’autres chaînes dans .NET](parsing-other.md) : explique comment convertir des chaînes en types [Char](xref:System.Char), [Boolean](xref:System.Boolean) et [Enum](xref:System.Enum).</span><span class="sxs-lookup"><span data-stu-id="d9002-114">[Parsing Other Strings in .NET](parsing-other.md) - Describes how to convert strings into [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) types.</span></span>

<span data-ttu-id="d9002-115">[Mise en forme des types dans .NET](formatting-types.md) : décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="d9002-115">[Formatting Types in .NET](formatting-types.md) - Describes basic formatting concepts like format specifiers and format providers.</span></span>

<span data-ttu-id="d9002-116">[Conversion de type dans .NET](type-conversion.md) : explique comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="d9002-116">[Type Conversion in .NET](type-conversion.md) - Describes how to convert types.</span></span>

<span data-ttu-id="d9002-117">[Utilisation des types de base dans .NET](index.md) : décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.</span><span class="sxs-lookup"><span data-stu-id="d9002-117">[Working with Base Types in .NET](index.md) - Describes common operations that you can perform on .NET base types.</span></span>


