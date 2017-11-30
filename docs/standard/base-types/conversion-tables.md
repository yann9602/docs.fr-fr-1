---
title: Tableaux de Conversion de type dans .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="77a4c-102">Tableaux de Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="77a4c-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="77a4c-103">Une conversion étendue se produit quand une valeur d’un type est convertie en un autre type de taille égale ou supérieure.</span><span class="sxs-lookup"><span data-stu-id="77a4c-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="77a4c-104">Une conversion restrictive se produit quand une valeur d’un type est convertie en une valeur d’un autre type de taille inférieure.</span><span class="sxs-lookup"><span data-stu-id="77a4c-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="77a4c-105">Les tableaux de cette rubrique illustrent les comportements propres aux deux types de conversion.</span><span class="sxs-lookup"><span data-stu-id="77a4c-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="77a4c-106">conversions étendues</span><span class="sxs-lookup"><span data-stu-id="77a4c-106">Widening Conversions</span></span>  
 <span data-ttu-id="77a4c-107">Le tableau suivant décrit les conversions étendues qui peuvent être effectuées sans perte d’informations.</span><span class="sxs-lookup"><span data-stu-id="77a4c-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="77a4c-108">Type</span><span class="sxs-lookup"><span data-stu-id="77a4c-108">Type</span></span>|<span data-ttu-id="77a4c-109">Peut être converti sans perte de données en</span><span class="sxs-lookup"><span data-stu-id="77a4c-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="77a4c-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="77a4c-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="77a4c-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="77a4c-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="77a4c-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="77a4c-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="77a4c-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="77a4c-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="77a4c-117">Certaines conversions étendues en valeurs <xref:System.Single> ou <xref:System.Double> peut entraîner une perte de précision.</span><span class="sxs-lookup"><span data-stu-id="77a4c-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="77a4c-118">Le tableau suivant décrit les conversions étendues qui entraînent parfois une perte d’informations.</span><span class="sxs-lookup"><span data-stu-id="77a4c-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="77a4c-119">Type</span><span class="sxs-lookup"><span data-stu-id="77a4c-119">Type</span></span>|<span data-ttu-id="77a4c-120">Peut être converti en</span><span class="sxs-lookup"><span data-stu-id="77a4c-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="77a4c-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="77a4c-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="77a4c-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="77a4c-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="77a4c-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="77a4c-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="77a4c-124">conversions restrictives</span><span class="sxs-lookup"><span data-stu-id="77a4c-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="77a4c-125">Une conversion restrictive <xref:System.Single> ou <xref:System.Double> peut entraîner une perte d’informations.</span><span class="sxs-lookup"><span data-stu-id="77a4c-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="77a4c-126">Si le type cible ne peut pas exprimer correctement la grandeur de la source, le type résultant est défini sur la constante `PositiveInfinity` ou `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="77a4c-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="77a4c-127">`PositiveInfinity`résultat de la division d’un nombre positif par zéro et est également retourné lorsque la valeur d’un <xref:System.Single> ou <xref:System.Double> dépasse la valeur de la `MaxValue` champ.</span><span class="sxs-lookup"><span data-stu-id="77a4c-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="77a4c-128">`NegativeInfinity`résultat de la division d’un nombre négatif par zéro et est également retourné lorsque la valeur d’un <xref:System.Single> ou <xref:System.Double> tombe en dessous de la valeur de la `MinValue` champ.</span><span class="sxs-lookup"><span data-stu-id="77a4c-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="77a4c-129">Une conversion d’un <xref:System.Double> à un <xref:System.Single> risque de `PositiveInfinity` ou `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="77a4c-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="77a4c-130">Une conversion restrictive peut également entraîner une perte d’informations pour d’autres types de données.</span><span class="sxs-lookup"><span data-stu-id="77a4c-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="77a4c-131">Toutefois, un <xref:System.OverflowException> est levée si la valeur d’un type qui est en cours de conversion se situe en dehors de la plage spécifiée par le type de cible `MaxValue` et `MinValue` champs, ainsi que la conversion est vérifiée par le runtime pour vous assurer que la valeur de la cible type ne dépasse pas son `MaxValue` ou `MinValue`.</span><span class="sxs-lookup"><span data-stu-id="77a4c-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="77a4c-132">Les conversions qui sont effectuées avec la <xref:System.Convert?displayProperty=nameWithType> classe sont toujours vérifiées de cette manière.</span><span class="sxs-lookup"><span data-stu-id="77a4c-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="77a4c-133">Le tableau suivant répertorie les conversions qui lèvent une <xref:System.OverflowException> à l’aide de <xref:System.Convert?displayProperty=nameWithType> ou toute conversion contrôlée si le type converti se situe en dehors de la plage définie du type résultant.</span><span class="sxs-lookup"><span data-stu-id="77a4c-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="77a4c-134">Type</span><span class="sxs-lookup"><span data-stu-id="77a4c-134">Type</span></span>|<span data-ttu-id="77a4c-135">Peut être converti en</span><span class="sxs-lookup"><span data-stu-id="77a4c-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="77a4c-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="77a4c-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="77a4c-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="77a4c-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="77a4c-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="77a4c-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="77a4c-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="77a4c-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="77a4c-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="77a4c-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="77a4c-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="77a4c-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="77a4c-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="77a4c-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="77a4c-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="77a4c-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="77a4c-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="77a4c-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="77a4c-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="77a4c-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77a4c-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77a4c-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="77a4c-147">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="77a4c-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
