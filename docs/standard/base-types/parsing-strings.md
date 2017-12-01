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
# <a name="parsing-strings-in-net"></a>Analyse de chaînes dans .NET
Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base. Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure. La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`. Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent. Comme la mise en forme utilise un objet qui implémente le <xref:System.IFormatProvider> interface afin de fournir des informations de mise en forme dépendante de la culture, l’analyse également utilise un objet qui implémente le <xref:System.IFormatProvider> interface pour déterminer comment interpréter une représentation sous forme de chaîne . Pour plus d’informations, consultez [mise en forme des Types](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)  
 Décrit comment convertir des chaînes en types numériques .NET.  
  
 [Analyse de chaînes de date et d’heure](../../../docs/standard/base-types/parsing-datetime.md)  
 Décrit comment convertir des chaînes dans .NET **DateTime** types.  
  
 [Analyse d’autres chaînes](../../../docs/standard/base-types/parsing-other.md)  
 Décrit comment convertir des chaînes en **Char**, **booléenne**, et **Enum** types.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)  
 Décrit les concepts de mise en forme de base, comme des spécificateurs de format et fournisseurs de format.  
  
 [Conversion de type dans .NET](../../../docs/standard/base-types/type-conversion.md)  
 Décrit comment convertir des types.  
  
 [Types de base](../../../docs/standard/base-types/index.md)  
 Décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.
