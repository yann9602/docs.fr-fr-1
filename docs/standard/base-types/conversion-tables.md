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
# <a name="type-conversion-tables-in-net"></a>Tableaux de Conversion de type dans .NET
Une conversion étendue se produit quand une valeur d’un type est convertie en un autre type de taille égale ou supérieure. Une conversion restrictive se produit quand une valeur d’un type est convertie en une valeur d’un autre type de taille inférieure. Les tableaux de cette rubrique illustrent les comportements propres aux deux types de conversion.  
  
## <a name="widening-conversions"></a>conversions étendues  
 Le tableau suivant décrit les conversions étendues qui peuvent être effectuées sans perte d’informations.  
  
|Type|Peut être converti sans perte de données en|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Certaines conversions étendues en valeurs <xref:System.Single> ou <xref:System.Double> peut entraîner une perte de précision. Le tableau suivant décrit les conversions étendues qui entraînent parfois une perte d’informations.  
  
|Type|Peut être converti en|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>conversions restrictives  
 Une conversion restrictive <xref:System.Single> ou <xref:System.Double> peut entraîner une perte d’informations. Si le type cible ne peut pas exprimer correctement la grandeur de la source, le type résultant est défini sur la constante `PositiveInfinity` ou `NegativeInfinity`. `PositiveInfinity`résultat de la division d’un nombre positif par zéro et est également retourné lorsque la valeur d’un <xref:System.Single> ou <xref:System.Double> dépasse la valeur de la `MaxValue` champ. `NegativeInfinity`résultat de la division d’un nombre négatif par zéro et est également retourné lorsque la valeur d’un <xref:System.Single> ou <xref:System.Double> tombe en dessous de la valeur de la `MinValue` champ. Une conversion d’un <xref:System.Double> à un <xref:System.Single> risque de `PositiveInfinity` ou `NegativeInfinity`.  
  
 Une conversion restrictive peut également entraîner une perte d’informations pour d’autres types de données. Toutefois, un <xref:System.OverflowException> est levée si la valeur d’un type qui est en cours de conversion se situe en dehors de la plage spécifiée par le type de cible `MaxValue` et `MinValue` champs, ainsi que la conversion est vérifiée par le runtime pour vous assurer que la valeur de la cible type ne dépasse pas son `MaxValue` ou `MinValue`. Les conversions qui sont effectuées avec la <xref:System.Convert?displayProperty=nameWithType> classe sont toujours vérifiées de cette manière.  
  
 Le tableau suivant répertorie les conversions qui lèvent une <xref:System.OverflowException> à l’aide de <xref:System.Convert?displayProperty=nameWithType> ou toute conversion contrôlée si le type converti se situe en dehors de la plage définie du type résultant.  
  
|Type|Peut être converti en|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Convert?displayProperty=nameWithType>  
 [Conversion de type dans .NET](../../../docs/standard/base-types/type-conversion.md)
