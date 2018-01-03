---
title: "Fonctions et types de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683413c5-0312-4e60-8619-9a97bdc6e62a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: af102a0d6ca8ec1092c8b0909a7817cb053ab6c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-types-and-functions"></a>Fonctions et types de données
Les rubriques répertoriées dans le tableau suivant décrivent la prise en charge de LINQ to SQL pour les membres, les constructions et les casts du Common Language Runtime (CLR). Les membres et constructions pris en charge peuvent être utilisés dans vos requêtes LINQ to SQL.  
  
 Un élément non pris en charge dans le tableau signifie que LINQ to SQL ne peut pas traduire le membre, la construction ou le cast CLR pour qu'ils soient exécutés sur le serveur SQL Server. Vous pouvez toujours les utiliser dans votre code, mais ils doivent être évalués avant la traduction de la requête en données Transact-SQL ou après l'extraction des résultats de la base de données.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Mappage de type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)|Fournit une matrice détaillée des mappages entre les types CLR et les types SQL Server.|  
|[Types de données de base](../../../../../../docs/framework/data/adonet/sql/linq/basic-data-types.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Types de données Boolean](../../../../../../docs/framework/data/adonet/sql/linq/boolean-data-types.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Sémantique Null](../../../../../../docs/framework/data/adonet/sql/linq/null-semantics.md)|Fournit des liens vers des rubriques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] qui abordent les questions des types null et nullables.|  
|[Opérateurs de comparaison et opérateurs numériques](../../../../../../docs/framework/data/adonet/sql/linq/numeric-and-comparison-operators.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Opérateurs de séquence](../../../../../../docs/framework/data/adonet/sql/linq/sequence-operators.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[System.Convert, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-convert-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[System.DateTime, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTime?displayProperty=nameWithType>.|  
|[System.DateTimeOffset, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-datetimeoffset-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTimeOffset?displayProperty=nameWithType>.|  
|[System.Math, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-math-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[System.Object, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-object-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[System.String, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[System.TimeSpan, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.TimeSpan?displayProperty=nameWithType>.|  
|[Fonctionnalité non prise en charge](../../../../../../docs/framework/data/adonet/sql/linq/unsupported-functionality.md)|Décrit les fonctionnalités qui ne sont pas prises en charge dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Incompatibilité entre types SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)  
 [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Bibliothèque de classes .NET framework dans Visual Studio](http://msdn.microsoft.com/en-us/a03e374c-3d5c-4169-937b-49857ab273ae)
