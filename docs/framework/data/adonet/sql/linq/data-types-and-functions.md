---
title: "Fonctions et types de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 683413c5-0312-4e60-8619-9a97bdc6e62a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Fonctions et types de donn&#233;es
Les rubriques répertoriées dans le tableau suivant décrivent la prise en charge de LINQ to SQL pour les membres, les constructions et les casts du Common Language Runtime \(CLR\).  Les membres et constructions pris en charge peuvent être utilisés dans vos requêtes LINQ to SQL.  
  
 Un élément non pris en charge dans le tableau signifie que LINQ to SQL ne peut pas traduire le membre, la construction ou le cast CLR pour qu'ils soient exécutés sur le serveur SQL Server.  Vous pouvez toujours les utiliser dans votre code, mais ils doivent être évalués avant la traduction de la requête en données Transact\-SQL ou après l'extraction des résultats de la base de données.  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Mappage de type SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)|Fournit une matrice détaillée des mappages entre les types CLR et les types SQL Server.|  
|[Types de données de base](../../../../../../docs/framework/data/adonet/sql/linq/basic-data-types.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Types de données Boolean](../../../../../../docs/framework/data/adonet/sql/linq/boolean-data-types.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Sémantique Null](../../../../../../docs/framework/data/adonet/sql/linq/null-semantics.md)|Fournit des liens vers des rubriques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] qui abordent les questions des types null et nullables.|  
|[Opérateurs de comparaison et opérateurs numériques](../../../../../../docs/framework/data/adonet/sql/linq/numeric-and-comparison-operators.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Opérateurs de séquence](../../../../../../docs/framework/data/adonet/sql/linq/sequence-operators.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Méthodes System.Convert](../../../../../../docs/framework/data/adonet/sql/linq/system-convert-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Méthodes System.DateTime](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTime?displayProperty=fullName>.|  
|[Méthodes System.DateTimeOffset](../../../../../../docs/framework/data/adonet/sql/linq/system-datetimeoffset-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTimeOffset?displayProperty=fullName>.|  
|[Méthodes System.Math](../../../../../../docs/framework/data/adonet/sql/linq/system-math-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Méthodes System.Object](../../../../../../docs/framework/data/adonet/sql/linq/system-object-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Méthodes System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|Résume les différences de comportement par rapport au [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].|  
|[Méthodes System.TimeSpan](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.TimeSpan?displayProperty=fullName>.|  
|[Fonctionnalités non prises en charge](../../../../../../docs/framework/data/adonet/sql/linq/unsupported-functionality.md)|Décrit les fonctionnalités qui ne sont pas prises en charge dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
  
## Voir aussi  
 [Incompatibilité entre types SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)   
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)   
 [.NET Framework Class Library in Visual Studio](http://msdn.microsoft.com/fr-fr/a03e374c-3d5c-4169-937b-49857ab273ae)