---
title: "Conversion de types&#160;.NET Framework en cha&#238;nes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Conversion de types&#160;.NET Framework en cha&#238;nes
Si vous voulez convertir un type .NET Framework en chaîne, utilisez la méthode **ToString**.  La méthode **ToString** retourne une représentation sous forme de chaîne du type passé.  Le tableau suivant répertorie les types .NET Framework qui retournent une chaîne dans un format qui mappe aux spécifications de schéma XML \(XSD\).  
  
|Type .NET Framework|Type de chaîne de retour|  
|-------------------------|------------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"\-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"\-INF"|  
|DateTime|Le format est yyyy\-MM\-ddTHH:mm:sszzzzzz et ses sous\-ensembles.|  
|TimeSpan|Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.|  
  
## Voir aussi  
 [Conversion des types de données XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)   
 [Conversion de chaînes en types de données .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)