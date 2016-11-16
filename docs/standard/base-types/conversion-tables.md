---
title: Tables de conversion de types
description: Tables de conversion de types
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d602f260-e7cf-49c8-a37f-731f40e4a538
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 01e15d9dc3881c7e2e4ea17db666991d72aa1b84

---

# <a name="type-conversion-tables"></a>Tables de conversion de types

Une conversion étendue se produit quand une valeur d’un type est convertie en un autre type de taille égale ou supérieure. Une conversion restrictive se produit quand une valeur d’un type est convertie en une valeur d’un autre type de taille inférieure. Les tableaux de cette rubrique illustrent les comportements propres aux deux types de conversion.

## <a name="widening-conversions"></a>Conversions étendues

Type | Peut être converti sans perte de données en
---- | -------------------------------------
[Byte](xref:System.Byte) | [UInt16](xref:System.UInt16), [Int16](xref:System.Int16), [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Single](xref:System.Single), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[SByte](xref:System.SByte) | [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [Single](xref:System.Single), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[Int16](xref:System.Int16) | [Int32](xref:System.Int32), [Int64](xref:System.Int64), [Single](xref:System.Single), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[UInt16](xref:System.UInt16) | [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Single](xref:System.Single), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[Char](xref:System.Char) | [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Single](xref:System.Single), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[Int32](xref:System.Int32) | [Int64](xref:System.Int64), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[UInt32](xref:System.UInt32) | [Int64](xref:System.Int64), [UInt64](xref:System.UInt64), [Double](xref:System.Double), [Decimal](xref:System.Decimal)
[Int64](xref:System.Int64) | [Decimal](xref:System.Decimal)
[UInt64](xref:System.UInt64) | [Decimal](xref:System.Decimal)
[Single](xref:System.Single) | [Double](xref:System.Double)

Certaines conversions étendues en valeurs [Single](xref:System.Single) ou [Double](xref:System.Double) peuvent entraîner une perte de précision. Le tableau suivant décrit les conversions étendues qui entraînent parfois une perte d’informations.

Type | Peut être converti en
---- | -------------------
[Int32](xref:System.Int32) | [Single](xref:System.Single)
[UInt32](xref:System.UInt32) | [Single](xref:System.Single)
[Int64](xref:System.Int64) | [Single](xref:System.Single), [Double](xref:System.Double)
[UInt64](xref:System.UInt64) | [Single](xref:System.Single), [Double](xref:System.Double)
[Decimal](xref:System.Decimal) | [Single](xref:System.Single), [Double](xref:System.Double)

## <a name="narrowing-conversions"></a>Conversions restrictives

Une conversion restrictive en [Single](xref:System.Single) ou [Double](xref:System.Double) peut entraîner une perte d’informations. Si le type cible ne peut pas exprimer correctement la grandeur de la source, le type résultant est défini sur la constante `PositiveInfinity` ou `NegativeInfinity`. `PositiveInfinity` est obtenu en divisant un nombre positif par zéro et est également retourné quand la valeur d’un [Single](xref:System.Single) ou d’un [Double](xref:System.Double) dépasse la valeur du champ `MaxValue`. `NegativeInfinity` est obtenu en divisant un nombre négatif par zéro et est également retourné quand la valeur d’un [Single](xref:System.Single) ou d’un [Double](xref:System.Double) tombe sous la valeur du champ `MinValue`. Une conversion d’un [Double](xref:System.Double) en un [Single](xref:System.Single) peut avoir pour résultat `PositiveInfinity` ou `NegativeInfinity`.

Une conversion restrictive peut également entraîner une perte d’informations pour d’autres types de données. Toutefois, un [OverflowException](xref:System.OverflowException) est levé si la valeur d’un type en cours de conversion se situe en dehors de la plage spécifiée par les champs `MaxValue` et `MinValue` du type cible, et la conversion est vérifiée par le runtime pour garantir que la valeur du type cible ne dépasse pas sa valeur `MaxValue` ou `MinValue`. Les conversions effectuées avec la classe [System.Convert](xref:System.Convert) sont toujours vérifiées de cette façon.

Le tableau suivant répertorie les conversions qui lèvent un [OverflowException](xref:System.OverflowException) à l’aide de [System.Convert](xref:System.Convert) ou toute conversion contrôlée si la valeur du type converti se situe en dehors de la plage définie du type résultant.

Type | Peut être converti en
---- | -------------------
[Byte](xref:System.Byte) | [SByte](xref:System.SByte)
[SByte](xref:System.SByte) | [Byte](xref:System.Byte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)
[Int16](xref:System.Int16) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16)
[UInt16](xref:System.UInt16) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16)
[Int32](xref:System.Int32) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32)
[UInt32](xref:System.UInt32) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32)
[Int64](xref:System.Int64) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)
[UInt64](xref:System.UInt64) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64)
[Decimal](xref:System.Decimal) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)
[Single](xref:System.Single) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)
[Double](xref:System.Double) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)

## <a name="see-also"></a>Voir aussi

[System.Convert](xref:System.Convert)

[Conversion de type](type-conversion.md)




<!--HONumber=Nov16_HO1-->


