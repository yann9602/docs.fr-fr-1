---
title: "Analyse de chaînes dans .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="d34a2-102">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="d34a2-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="d34a2-103">Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="d34a2-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="d34a2-104">Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="d34a2-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="d34a2-105">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="d34a2-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="d34a2-106">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="d34a2-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="d34a2-107">Comme la mise en forme utilise un objet qui implémente le <xref:System.IFormatProvider> interface afin de fournir des informations de mise en forme dépendante de la culture, l’analyse également utilise un objet qui implémente le <xref:System.IFormatProvider> interface pour déterminer comment interpréter une représentation sous forme de chaîne .</span><span class="sxs-lookup"><span data-stu-id="d34a2-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="d34a2-108">Pour plus d’informations, consultez [mise en forme des Types](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d34a2-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d34a2-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d34a2-109">In This Section</span></span>  
 [<span data-ttu-id="d34a2-110">Analyse de chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="d34a2-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="d34a2-111">Décrit comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="d34a2-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="d34a2-112">Analyse de chaînes de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="d34a2-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="d34a2-113">Décrit comment convertir des chaînes dans .NET **DateTime** types.</span><span class="sxs-lookup"><span data-stu-id="d34a2-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="d34a2-114">Analyse d’autres chaînes</span><span class="sxs-lookup"><span data-stu-id="d34a2-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="d34a2-115">Décrit comment convertir des chaînes en **Char**, **booléenne**, et **Enum** types.</span><span class="sxs-lookup"><span data-stu-id="d34a2-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d34a2-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d34a2-116">Related Sections</span></span>  
 [<span data-ttu-id="d34a2-117">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="d34a2-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="d34a2-118">Décrit les concepts de mise en forme de base, comme des spécificateurs de format et fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="d34a2-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="d34a2-119">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="d34a2-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="d34a2-120">Décrit comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="d34a2-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="d34a2-121">Types de base</span><span class="sxs-lookup"><span data-stu-id="d34a2-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="d34a2-122">Décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.</span><span class="sxs-lookup"><span data-stu-id="d34a2-122">Describes common operations that you can perform on .NET base types.</span></span>
