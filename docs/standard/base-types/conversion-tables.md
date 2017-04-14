---
title: "Tables de conversion de types dans .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversions étendues"
  - "conversions restrictives"
  - "conversion de type, table"
  - "convertir des types, conversions restrictives"
  - "convertir des types, conversions étendues"
  - "types de base, convertir"
  - "tables (.NET Framework), conversions de types"
  - "types de données (.NET Framework), convertir"
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Tables de conversion de types dans .NET Framework
Une conversion étendue se produit lorsqu'une valeur d'un type est convertie en un autre type de taille égale ou supérieure.  Une conversion restrictive se produit lorsqu'une valeur d'un type est convertie en une valeur d'un autre type de taille inférieure.  Les tableaux de cette rubrique illustrent les comportements dont font preuve les deux types de conversion.  
  
## Conversions étendues  
 Le tableau suivant décrit les conversions étendues qui peuvent être effectuées sans perte d'information.  
  
|Type|Peut être converti sans perte de données en|  
|----------|-------------------------------------------------|  
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
  
 Certaines conversions étendues en valeurs <xref:System.Single> ou <xref:System.Double> peuvent entraîner une perte de précision.  Le tableau suivant décrit les conversions étendues qui peuvent parfois entraîner une certaine perte d'information.  
  
|Type|Peut être converti en|  
|----------|---------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## Conversions restrictives  
 Une conversion restrictive en <xref:System.Single> ou <xref:System.Double> peut entraîner une perte d'information.  Si le type cible ne peut pas exprimer correctement la grandeur de la source, la valeur du type qui en résulte est celle de la constante `PositiveInfinity` ou `NegativeInfinity`.  `PositiveInfinity` est le résultat de la division d'un nombre positif par zéro et est également retourné lorsque la valeur d'un <xref:System.Single> ou d'un <xref:System.Double> dépasse la valeur du champ `MaxValue`.  `NegativeInfinity` est le résultat de la division d'un nombre négatif par zéro et est également retourné lorsque la valeur d'un <xref:System.Single> ou d'un <xref:System.Double> est inférieure à la valeur du champ `MinValue`.  Une conversion d'un <xref:System.Double> en un <xref:System.Single> peut entraîner une valeur `PositiveInfinity` ou `NegativeInfinity`.  
  
 Une conversion restrictive peut également entraîner une perte d'informations pour d'autres types de données.  Toutefois, un <xref:System.OverflowException> est levé si la valeur d'un type en cours de conversion se situe en dehors de la plage spécifiée par les champs `MaxValue` et `MinValue` du type cible et que la conversion fait l'objet d'une vérification par le runtime pour s'assurer que la valeur du type cible ne dépasse pas sa valeur `MaxValue` ou `MinValue`.  Les conversions qui sont effectuées avec la classe <xref:System.Convert?displayProperty=fullName> sont toujours vérifiées de cette façon.  
  
 Le tableau suivant répertorie les conversions qui lèvent un <xref:System.OverflowException> en utilisant <xref:System.Convert?displayProperty=fullName> ou toute conversion contrôlée si le type converti se situe en dehors de la plage définie du type résultant.  
  
|Type|Peut être converti en|  
|----------|---------------------------|  
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
  
## Voir aussi  
 <xref:System.Convert?displayProperty=fullName>   
 [Conversion de type dans le .NET Framework](../../../docs/standard/base-types/type-conversion.md)