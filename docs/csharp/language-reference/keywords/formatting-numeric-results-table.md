---
title: "Tableau des formats des résultats numériques (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="7e5c1-102">Tableau des formats des résultats numériques (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7e5c1-102">Formatting Numeric Results Table (C# Reference)</span></span>
<span data-ttu-id="7e5c1-103">Vous pouvez appliquer un format à un résultat numérique à l’aide de la méthode <xref:System.String.Format%2A?displayProperty=fullName>, ou par l’intermédiaire de la méthode <xref:System.Console.Write%2A?displayProperty=fullName> ou `String.Format`, qui appelle <xref:System.Console.WriteLine%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-103">You can format numeric results by using the <xref:System.String.Format%2A?displayProperty=fullName> method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> or <xref:System.Console.WriteLine%2A?displayProperty=fullName> method, which calls `String.Format`.</span></span> <span data-ttu-id="7e5c1-104">Le format est spécifié à l’aide de chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-104">The format is specified by using format strings.</span></span> <span data-ttu-id="7e5c1-105">Le tableau suivant contient les chaînes de format standard prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-105">The following table contains the supported standard format strings.</span></span> <span data-ttu-id="7e5c1-106">La chaîne de format prend la forme suivante : `Axx`, où `A` est le spécificateur de format et `xx` est le spécificateur de précision.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-106">The format string takes the following form: `Axx`, where `A` is the format specifier and `xx` is the precision specifier.</span></span> <span data-ttu-id="7e5c1-107">Le spécificateur de format contrôle le type de mise en forme appliquée à la valeur numérique, tandis que le spécificateur de précision contrôle le nombre de chiffres significatifs ou de décimales de la sortie formatée.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-107">The format specifier controls the type of formatting applied to the numeric value, and the precision specifier controls the number of significant digits or decimal places of the formatted output.</span></span> <span data-ttu-id="7e5c1-108">La valeur du spécificateur de précision est comprise entre 0 et 99.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-108">The value of the precision specifier ranges from 0 to 99.</span></span>  
  
 <span data-ttu-id="7e5c1-109">Pour plus d’informations sur les chaînes de format standard et personnalisées, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="7e5c1-109">For more information about standard and custom formatting strings, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="7e5c1-110">Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7e5c1-110">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
|<span data-ttu-id="7e5c1-111">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="7e5c1-111">Format Specifier</span></span>|<span data-ttu-id="7e5c1-112">Description</span><span class="sxs-lookup"><span data-stu-id="7e5c1-112">Description</span></span>|<span data-ttu-id="7e5c1-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="7e5c1-113">Examples</span></span>|<span data-ttu-id="7e5c1-114">Sortie</span><span class="sxs-lookup"><span data-stu-id="7e5c1-114">Output</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="7e5c1-115">C ou c</span><span class="sxs-lookup"><span data-stu-id="7e5c1-115">C or c</span></span>|<span data-ttu-id="7e5c1-116">Devise</span><span class="sxs-lookup"><span data-stu-id="7e5c1-116">Currency</span></span>|<span data-ttu-id="7e5c1-117">Console.Write("{0:C}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-117">Console.Write("{0:C}", 2.5);</span></span><br /><br /> <span data-ttu-id="7e5c1-118">Console.Write("{0:C}", -2.5);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-118">Console.Write("{0:C}", -2.5);</span></span>|<span data-ttu-id="7e5c1-119">$2.50</span><span class="sxs-lookup"><span data-stu-id="7e5c1-119">$2.50</span></span><br /><br /> <span data-ttu-id="7e5c1-120">($2.50)</span><span class="sxs-lookup"><span data-stu-id="7e5c1-120">($2.50)</span></span>|  
|<span data-ttu-id="7e5c1-121">D ou d</span><span class="sxs-lookup"><span data-stu-id="7e5c1-121">D or d</span></span>|<span data-ttu-id="7e5c1-122">Decimal</span><span class="sxs-lookup"><span data-stu-id="7e5c1-122">Decimal</span></span>|<span data-ttu-id="7e5c1-123">Console.Write("{0:D5}", 25);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-123">Console.Write("{0:D5}", 25);</span></span>|<span data-ttu-id="7e5c1-124">00025</span><span class="sxs-lookup"><span data-stu-id="7e5c1-124">00025</span></span>|  
|<span data-ttu-id="7e5c1-125">E ou e</span><span class="sxs-lookup"><span data-stu-id="7e5c1-125">E or e</span></span>|<span data-ttu-id="7e5c1-126">Scientifique</span><span class="sxs-lookup"><span data-stu-id="7e5c1-126">Scientific</span></span>|<span data-ttu-id="7e5c1-127">Console.Write("{0:E}", 250000);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-127">Console.Write("{0:E}", 250000);</span></span>|<span data-ttu-id="7e5c1-128">2.500000E+005</span><span class="sxs-lookup"><span data-stu-id="7e5c1-128">2.500000E+005</span></span>|  
|<span data-ttu-id="7e5c1-129">F ou f</span><span class="sxs-lookup"><span data-stu-id="7e5c1-129">F or f</span></span>|<span data-ttu-id="7e5c1-130">Virgule fixe</span><span class="sxs-lookup"><span data-stu-id="7e5c1-130">Fixed-point</span></span>|<span data-ttu-id="7e5c1-131">Console.Write("{0:F2}", 25);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-131">Console.Write("{0:F2}", 25);</span></span><br /><br /> <span data-ttu-id="7e5c1-132">Console.Write("{0:F0}", 25);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-132">Console.Write("{0:F0}", 25);</span></span>|<span data-ttu-id="7e5c1-133">25.00</span><span class="sxs-lookup"><span data-stu-id="7e5c1-133">25.00</span></span><br /><br /> <span data-ttu-id="7e5c1-134">25</span><span class="sxs-lookup"><span data-stu-id="7e5c1-134">25</span></span>|  
|<span data-ttu-id="7e5c1-135">G ou g</span><span class="sxs-lookup"><span data-stu-id="7e5c1-135">G or g</span></span>|<span data-ttu-id="7e5c1-136">Général</span><span class="sxs-lookup"><span data-stu-id="7e5c1-136">General</span></span>|<span data-ttu-id="7e5c1-137">Console.Write("{0:G}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-137">Console.Write("{0:G}", 2.5);</span></span>|<span data-ttu-id="7e5c1-138">2.5</span><span class="sxs-lookup"><span data-stu-id="7e5c1-138">2.5</span></span>|  
|<span data-ttu-id="7e5c1-139">N ou n</span><span class="sxs-lookup"><span data-stu-id="7e5c1-139">N or n</span></span>|<span data-ttu-id="7e5c1-140">Nombre</span><span class="sxs-lookup"><span data-stu-id="7e5c1-140">Number</span></span>|<span data-ttu-id="7e5c1-141">Console.Write("{0:N}", 2500000);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-141">Console.Write("{0:N}", 2500000);</span></span>|<span data-ttu-id="7e5c1-142">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="7e5c1-142">2,500,000.00</span></span>|  
|<span data-ttu-id="7e5c1-143">X ou x</span><span class="sxs-lookup"><span data-stu-id="7e5c1-143">X or x</span></span>|<span data-ttu-id="7e5c1-144">Hexadécimal</span><span class="sxs-lookup"><span data-stu-id="7e5c1-144">Hexadecimal</span></span>|<span data-ttu-id="7e5c1-145">Console.Write("{0:X}", 250);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-145">Console.Write("{0:X}", 250);</span></span><br /><br /> <span data-ttu-id="7e5c1-146">Console.Write("{0:X}", 0xffff);</span><span class="sxs-lookup"><span data-stu-id="7e5c1-146">Console.Write("{0:X}", 0xffff);</span></span>|<span data-ttu-id="7e5c1-147">FA</span><span class="sxs-lookup"><span data-stu-id="7e5c1-147">FA</span></span><br /><br /> <span data-ttu-id="7e5c1-148">FFFF</span><span class="sxs-lookup"><span data-stu-id="7e5c1-148">FFFF</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e5c1-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e5c1-149">See Also</span></span>  
 <span data-ttu-id="7e5c1-150">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e5c1-150">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7e5c1-151">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e5c1-151">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7e5c1-152">[Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="7e5c1-152">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="7e5c1-153">[Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="7e5c1-153">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 [<span data-ttu-id="7e5c1-154">string</span><span class="sxs-lookup"><span data-stu-id="7e5c1-154">string</span></span>](../../../csharp/language-reference/keywords/string.md)

