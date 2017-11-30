---
title: "Conversion de types .NET Framework en chaînes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3abe140e62f112a15a1ad1b1b2a79c14364b26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-net-framework-types-to-strings"></a>Conversion de types .NET Framework en chaînes
Si vous souhaitez convertir un type .NET Framework en chaîne, utilisez la **ToString** (méthode). Le **ToString** méthode retourne une représentation sous forme de chaîne du type passé dans. Le tableau suivant répertorie les types .NET Framework qui retournent une chaîne dans un format qui mappe aux spécifications de schéma XML (XSD).  
  
|Type .NET Framework|Type de chaîne de retour|  
|-------------------------|--------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Le format est yyyy-MM-ddTHH:mm:sszzzzzz et ses sous-ensembles.|  
|TimeSpan|Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion de Types de données XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Conversion de chaînes en Types de données .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
