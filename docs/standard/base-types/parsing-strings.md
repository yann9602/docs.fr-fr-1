---
title: "Analyse de cha&#238;nes dans .NET Framework | Microsoft Docs"
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
  - "analyser de chaînes, à propos de l’analyse de chaînes"
  - "IFormatProvider (interface), analyse de chaînes"
  - "types de base, analyse de chaînes"
  - "Parse (méthode)"
  - "analyser des chaînes"
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Analyse de cha&#238;nes dans .NET Framework
Une opération d'analyse convertit une chaîne représentant un type de base .NET Framework en ce type de base.  Par exemple, une opération d'analyse est utilisée pour convertir une chaîne en un nombre à virgule flottante, ou en une valeur de date et de temps.  La méthode la plus utilisée pour exécuter une opération d'analyse est la méthode `Parse`.  L'analyse étant l'opération inverse de la mise en forme \(qui consiste à convertir un type de base en sa représentation sous forme de chaîne\), de nombreuses règles et conventions identiques s'appliquent.  À l'instar de la mise en forme qui utilise un objet implémentant l'interface <xref:System.IFormatProvider> pour fournir des informations relatives à la mise en forme dépendante de la culture, l'analyse utilise, elle aussi, un objet qui implémente l'interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne.  Pour plus d'informations, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md).  
  
## Dans cette section  
 [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)  
 Décrit la façon de convertir des chaînes en types numériques .NET Framework.  
  
 [Analyse des chaînes de date et d'heure](../../../docs/standard/base-types/parsing-datetime.md)  
 Décrit la façon de convertir des chaînes en types **DateTime** .NET Framework.  
  
 [Analyse d'autres chaînes](../../../docs/standard/base-types/parsing-other.md)  
 Décrit la façon de convertir des chaînes en types **Char**, **Boolean** et **Enum**.  
  
## Rubriques connexes  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)  
 Décrit les concepts de base de la mise en forme tels que les spécificateurs de format et les fournisseurs de format.  
  
 [Conversion de type dans le .NET Framework](../../../docs/standard/base-types/type-conversion.md)  
 Décrit la façon de convertir les types.  
  
 [Types de base](../../../docs/standard/base-types/index.md)  
 Décrit les opérations communes que vous pouvez effectuer sur les types de base .NET Framework.