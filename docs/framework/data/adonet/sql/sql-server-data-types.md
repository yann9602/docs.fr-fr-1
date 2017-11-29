---
title: "Types de données SQL Server et ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c675491a378d72d82a252d79a73379f494893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-data-types-and-adonet"></a>Types de données SQL Server et ADO.NET
SQL Server et le .NET Framework sont basés sur des systèmes de types différents, ce qui peut entraîner une perte de données potentielle. Afin de protéger l'intégrité des données, le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>) fournit des méthodes d'accesseur typé pour utiliser les données SQL Server. Vous pouvez également utiliser les énumérations des classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:System.Data.SqlClient.SqlParameter>.  
  
 Pour plus d’informations et une table qui décrit les données entre SQL Server et les types de données .NET Framework, les mappages de type, consultez [mappages de Type de données SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins des entreprises en termes d'utilisation des données de date et d'heure, structurées, semi-structurées et non structurées. Ceux-ci sont décrits dans la documentation en ligne de SQL Server 2008.  
  
 Les types de données SQL Server disponibles pour votre application varient en fonction de la version de SQL Server utilisée. Pour plus d'informations, consultez la version appropriée de la documentation en ligne de SQL Server dans le tableau suivant.  
  
 **Documentation en ligne de SQL Server**  
  
1.  [Types de données (moteur de base de données)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Dans cette section  
 [SqlTypes et le jeu de données](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.  
  
 [Gestion des valeurs Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Montre comment utiliser des valeurs null et la logique à trois valeurs.  
  
 [Comparaison du GUID et des valeurs uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Montre comment utiliser des valeurs GUID et d'identificateur unique dans SQL Server et le .NET Framework.  
  
 [Données de date et heure](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Explique comment utiliser les nouveaux types de données de date et d'heure introduits dans SQL Server 2008.  
  
 [UDT volumineux](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Montre comment récupérer des données des UDT volumineux introduits dans SQL Server 2008.  
  
 [Données XML dans SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Décrit comment utiliser des données XML récupérées dans SQL Server.  
  
## <a name="reference"></a>Référence  
 <xref:System.Data.DataSet>  
 Décrit la classe `DataSet` et tous ses membres.  
  
 <xref:System.Data.SqlTypes>  
 Décrit l'espace de noms `SqlTypes` et tous ses membres.  
  
 <xref:System.Data.SqlDbType>  
 Décrit l'énumération `SqlDbType` et tous ses membres.  
  
 <xref:System.Data.DbType>  
 Décrit l'énumération `DbType` et tous ses membres.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages de Type de données SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Configuration des paramètres et des Types de données de paramètre](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Paramètres table](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Données binaires et de valeur élevée SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
